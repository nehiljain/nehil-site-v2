+++
title = "Airflow Summit CFP 2020"
date = 2020-04-11T22:28:14-04:00
description = ""
+++


# Title

Building Reuseable and Trustworthy ELT pipelines (A templated approach)

# TLDR

To improve automation of data pipelines, I propose a universal approach to ELT pipeline that optimizes for data integrity, extensibility, and speed to delivery. The workflow is built using open source tools and standards like Apache Airflow, Singer, Great Expectations, and DBT.

# Abstract

Templating ETLs is challenging! The creation and maintenance of data pipelines in production require hard work to manage bugs in code and bad data. 

I like to propose a data pipeline pattern that can simplify building pipelines while optimizing for data integrity and observability. The workflow is built using open source tools like Singer, Great Expectations, and DBT. 

Goals:

* Make **EL**T simple and fast to implement
* Validate your assumptions of the data before you make it available for use
* Allow analysts/data scientists add pain-free contributions to EL**T** using SQL
* Generate data documentation, failure logs for quick recovery, and fixes outages in your pipeline

Target Audience:

* Approachable to any level of developer
* Novice data personals interested in starting ELT workflow and learning about different tools of the ecosystem
* Intermediate+ developers interested in supercharging their pipeline with Write Audit Publish pattern and reducing pipeline debt

Links:
CFP: https://pretalx.com/apache-airflow-summit-bay-area-2020/me/submissions/DFWRJC/
Talk Outline: https://gist.github.com/nehiljain/8fc66eba4f2734ec6e4a9f372b1d9fc0