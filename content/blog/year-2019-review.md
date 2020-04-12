+++
title = "Year 2019 Review"
date = 2020-03-13T22:51:50-04:00
description = ""
+++


# Year-end review — 2019



It is too late for the traditional “Year-end review” article but it is still worth reviewing my 2019 for my own sake. I was browsing Julia Evan’s [blog](https://jvns.ca/) (high recommended!) where I got the inspiration to do this. She does yearly reviews and has been doing it consistently for 5 years in a row. It’s pretty incredible to binge read them. I want to start on my own journey of reviews and see where that goes. I am confident that there will be nuggets here that can be useful for you too. So here we go.

**What I learned**

* I learned the advantages of ELT over ETL in data engineering. Transformations are the most brittle part of the pipeline. The extraction and load usually fit into reusable patterns. ELT >> ETL

* What is analytics engineering and its place in the organization? I conceptualize them as data analysts on steroids.

* Sprint vs Kanban for the data team. Most “data as a service” teams are better off using Kanban due to every changing goal of the team for that week. In scrum, the goal is to have a pre-defined set of work that the team commits on finishing which is great for agile product teams.

* Building a network and support of mentors is so helpful. I was able to get a lot of useful advice on things like data stack, data trust issues, and data team structure in the organization.

* There is value in doing the same thing over and over again. Persistence precedes flow state in any activity. I thoroughly enjoyed my dragon boating season.

## Life-changing events

**Dragon Boat Camp — April**

I got a chance to go to Tampa Bay, Florida for a dragon boating camp. It was my first time attending a sport-specific training camp. 🤔 So many first time events this year! I didn’t have any expectations going in but oh man! It was intense. We paddle 120km in 5 days. I was in a boat with some of the strongest men in the Canada Dragon Boat community. It built a lot of mental strength and stamina in me to just keep up with them. After the trip, I have looked at handling pain differently than before. Character building from enduring the training camp was a life changer. I learned that for most of the problems, we often give in earlier than we should. We should remind ourselves of the long terms vision when challenged with hard things. I found the old saying to be true, the harder the challenge the sweeter the victory of overcoming it.

**Solo Trip to the UK — July**

This was a great trip. I learned that I am the happiest if I get good weather and I am physically active/outdoors for most of the day. I went hiking in Edinburgh and running on the banks of the River Thames in London. It was pretty cool and satisfying. I was able to turn off my daily work brain and think creatively about the larger problems that excite me. I have been thinking about the problem of a huge lack of trust in data, ownership of data across the stack and data discovery. During my rest period in the hostels, I toyed around with DBT, connected with [Stephen](https://twitter.com/sjwhitworth?lang=en) and thought about what would a new world of our analytics stack would look like. Now thinking back and connecting the dots. I feel the introduction of DBT in our stack completely changed the culture and efficiency of the team.

**What went well**

* [Astronomer](http://astronomer.io/) + [Stitch](https://www.stitchdata.com/): I made a move from hosting airflow myself to migrating self-hosted Airflow to Astronomer Airflowand migration ETLs to stitch where possible. This made the team a lot more productive. For eg., Ingesting data from a custom source went from 2 weeks to 3 days, and standard source like Facebook ads from 1–2 weeks to 10 mins. The data architecture @ SnapTravel became simpler. This was huge for me as a team lead.

* Custom Airflow Operators: I worked with the team to get good coverage of operators and hooks for all data sources and destinations we extract and load data from in SnapTravel. This has continually paid huge 💰 dividends to us in getting stuff done quickly when it comes to building pipelines.

* [DBT](https://www.getdbt.com/') project: I introduced DBT to the team which solved a lot of problems in our company related to data trust, data discoverability, change management and reusable work with best practices.

* [Big Data Toronto talk](https://twitter.com/nehiljain/status/1138906155642707973?s=20): I gave my first conference talk. Thanks to folks at Snowflake to give me a chance. I think it went pretty well. I learned that the AV systems used in conferences are still pretty archaic.

* [Bear App](https://bear.app/): I fell in 💕 with it. It has changed my note-taking style and habit. After cycling through a dozen apps this one has stuck for more than a year. I feel like I have been able to build my knowledge library in bear since I started using it and can’t live without it anymore.

**What I want to improve on**

* Solve the problem of ownership of broken data or pipelines that are cross-team/cross-functional. The current setup if a week where the data team is sandwiched between a source (engineering teams) and end-users(business teams). Most of the problems are generated by the source, identified by end-users but expected to be fixed by the data team who built the pipe. I feel there is a brighter land out there where ownership is clearly defined and delegated.

* Figure out effective data discovery processes. Documentation for data is hard ([https://www.locallyoptimistic.com/post/data_dictionaries/](https://www.locallyoptimistic.com/post/data_dictionaries/)). I have found that just adding docs on data models isn’t enough.

* Decipher the engineer/manager pendulum as charity defines it in her [post](https://charity.wtf/2017/05/11/the-engineer-manager-pendulum/).

* Get rid of my sugar addiction. Those damn croissants! If I die early it will be mostly because of the amount of sugar I eat 😢

* Manage expectations more effectively as a Lead for a team. There have been times where I could do a better job of managing the expectations of my manager in regard to my team.

* Build a network of experts around me. I need a strong network to thrive in this world.

* Stretch and add yoga in my weekly routine. To reduce injury I should focus more on the recovery as well and not just growing strength endurance.

All in all, it was a fantastic year for me personally. I will work on some of the things from “needs improvement” this year. The theme of this year is “expansion” while the theme of the last one was “laying the groundwork”. Also, an elusive goal of writing more on this blog. Reminder to myself: Writing is super important! If you don't know what I am talking about go read [bit.ly/excellent-blog](http://bit.ly/excellent-blog)
