---
title: "Blue Green Deploys Dbt Snowflake"
date: 2020-05-02T09:24:24-04:00
draft: true
---

## Blue Green deploys in Snowflake + DBT

 #blog #blogpost #draft

As the maintainer of the Analytics stack at SnapTravel, I have gotten a variety of experience with the Modern Data stack.

One of the recent challenges the data team faces is: how to move fast with the ever changing business needs and fast growing big data in delivering reliable business insights. I thought using DBT incremental runs for event stream datasets and using appropriate snowflake warehouse sizes was enough to solve the problem. I was wrong, recently, after analyzing past few downtimes in our BI layer, I realized that all of them are related to backfilling  incremental models on billions of rows. Here, I am going to describe the problem and a proposed approach to solve it.

## The Problem

Eventstream datasets are the biggest chunk of our data warehouse storage. This means that it requires proportionally larger resources or time to transform them. Most commonly, transformations are done incrementally in favour of performance and speed to delivery. But the problem is when you have to run this transformation query on the whole dataset it takes a very long time. Think about the cold start or full refreshes of the dataset for schema changes, those are common cases of when this happens.  So if we want to deploy such models to production while the previous version is being used by the reporting layer, there is downtime. Most of these runs are one-offs because the schema changes are not that frequent. In many cases, the analytics engineer runs a one-off migration/backfill script and manually  communicates status of the job to the end users.

Let us consider the following **scenario**.

Present : You have 2 events that are combined into a metric using session_ids. The size of the tables are depicted in yellow notes.

![scenario-present](https://p91.f3.n0.cdn.getcloudapp.com/items/eDu6Rnop/Image%202020-05-02%20at%209.32.13%20AM.png)

Future: Price is being added to `product_event_1`. We need to change the models and have to run a full refresh to calculate the new fields for all rows.

![scenario-future](https://p91.f3.n0.cdn.getcloudapp.com/items/xQuW6OvW/Image%202020-05-02%20at%209.34.04%20AM.png)

The problem is:

* Toil of managing ad-hoc  jobs for backfilling
* Test failures are very expensive at this stage

### Its Impact

* Reduced downtime
* Reduced toil
* Ability to rollback

### Proposed solution

We can learn from Continuous Delivery best practices that Blue Green deploys are a way to solve this problem. So below is my proposed solution to perform blue/green deployments with dbt and snowflake.

**What are blue-green deploys?**
Blue-Green deployment approach is one where you have two identical environments, labeled Blue and green respectively. One is *live* for on production, lets call that Green. The other environment is Blue which is used for doing the development/new changes. Once the changes to the Blue deployment are complete and verified then there is a switch over between them. Blue becomes green (active) and green becomes blue (inactive).

Features from dbt and snowflake which the proposed solution relies on:

* [Zero-copy clone](https://www.youtube.com/watch?v=yQIMmXg7Seg): Ability to inexpensively copy data from a database or schema or table within a few seconds.
* [Materialized models](https://docs.getdbt.com/docs/building-a-dbt-project/building-models/materializations/)
  * [Incremental](https://docs.getdbt.com/docs/building-a-dbt-project/building-models/materializations/#incremental): Insert or update records into a table since the last time run
  * [Insert by period](https://github.com/fishtown-analytics/dbt-utils#insert_by_period-source): Insert records into a table one period (i.e. hour, day, week) at a time.

**Infrastructure Setup:**

1. DBT repo has 2 branches, pre-prod and prod
2. Green environment for `dbt run` prod branch code with incremental models on a daily/hourly schedule
3. Blue environment for `dbt run` pre-prod branch code with full refresh models on an external trigger
4. Inside snowflake `analytics.public` schema is production
5. Inside snowflake `analytics.public_upcoming` schema is pre-prod

Blue DBT runs should only run parts of lineage graph that are heavily incremental and should be selecting models based code diff between pre-prod and prod files.

**The process:**

1. After code is merged and ready to deploy. The CI pipeline triggers a dbt run job with the latest pre-prod code in blue deployment.
2. The job does
   1. Clones public schema to `analytics.public_upcoming`
   2. Full refreshes the data
   3. Verifies the output
3. Switch Over
   1. Rename `analytics.public` -> `analytics.public_snapshot_YYYY-MM-DD`
   2. Rename `analytics.public_upcoming` -> `analtyics.public`

4. Something goes wrong back rollback to `analytics.public_snapshot_YYYY-MM-DD`

5. Runs verify script or dbt tests

6. If step 6 was successful then rename  `analytics.public_snapshot_YYYY-MM-DD` -> `analytics.public_upcoming`

7. If step 7 was unsuccessful then rename `analytics.public_snapshot_YYYY-MM-DD` -> `analytics.public`

8. A weekly job to clean up drops all the old `analytics.public_snapshot_YYYY-MM-*`

### Verification Script

* Verification script should try and match on ids of the two cols for missing data between blue and green
