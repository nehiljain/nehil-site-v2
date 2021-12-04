---
ship30 metadata:
 - industry audience
 - aspirational or anthropological
 - ways
 - credibility 1
---

The data platform landscape has changed drastically over the past 5 years. It has become easier, no matter the size. Faster data processing has led to a massive shift in how businesses operate and how data drives riches for businesses.  I want to dive into some of the gaps we have observed at Quantumblack while working on enterprise architectures.


Participating in the data economy comes with its challenges. The tooling and ways of working are changing drastically. Understanding the context of the change and future state of the architecture will future proof you from leap frogging your company's data platform. It will improve your speed of delivery, cost of utilizing data across the enterprise and hiring the right talent.
Now, let's dive in.

# Quick Background Story:

In the 1970s, OLAP extensions to OLTP were developed to perform analyses to support business leaders. SQL was lingua franca but not as powerful. This was because the databases were designed with row-oriented i/o and didn't have access to a large amount of memory to hold the processed data. The datasets generated were of magnitude {{file size}} and so they were just good enough

## Rise of Data Warehouses (Teradata, Sybase, Oracle)

Once the datasets started becoming untameable in those OLAP systems, Data WareHouses (DWH) was born. Let's call these Gen 1 DWH. These were designed from scratch to have column-oriented i/o which lent itself well to analytical queries. They used proprietary formats to store data in On-Prem infrastructure deployments. There was a massive vendor lock-in problem. Scaling up or down was expensive and limited as well.

## Data-lake hype

Around this time, Map Reduce was born at Google which changed the data landscape drastically for the first time. Map Reduce allowed for processing big data on commodity hardware. The design of map-reduce didn't lend itself well to SQL. So people used programming languages like Java, Python to engineer data pipelines using Map Reduce. This gave birth to a data lake where organizations can store all their data and then use custom map-reduce scripts to analyze them.

## Spark for the win

A decade ago, the next big advancement in data processing technologies was Spark. Spark was much faster with its in-memory processing and lend itself to a more elegant design for data processing code. This quickly became the de facto system to handle data at scale. Python (PySpark) rose as the popular data engineering language that was used to write spark jobs and glue systems together. 

In parallel to this, native python data analysis libraries Pandas and NumPy were growing significantly. The libraries' success is tied to the features it offered at the time and the explosive growth in the data science, analytics, and engineering fields. This brought Python to the main stage of data analysis and engineering. At this point, you can learn python and do pretty much anything in the data world i.e. EDA, data transformations, pipelining work, and machine learning. Python democratized data science and engineering to the masses and moved traditionally SQL workflows into procedural data pipelines. SQL felt clunky and lower leverage activity as compared to coding in python.

## Cloud Data Warehouses lowers the barrier

On the OLAP front, there was a new generation of cloud-native data warehouses (CDWH) were being built by the cloud providers. They essentially innovated on taking SQL code and running it on massive datasets efficiently. This lowered the complexity of the data processing code required to generate insights.
Snowflake, Big Query, and Redshift are some of the popular CDWH. These encapsulated the complexity of massively parallel programming behind the succinct interface of SQL.


## Self-serving data products:

Data silos are bad and the future state involves making data accessible across the enterprise to inspire data driven workflows.

Currently, many enterprises find it hard to unlock the full potential of their data assets. Common stories along these lines are "I did not know we have this dataset!", "How do I make sense of this table and why are my numbers not matching?", and "My work is blocked on getting data for X from the data team for weeks!".

{{Insert stories of the future and future state}}

## Robust and reliable data sets:

You cannot drive actions/change in your org if you dont have data trust.

Currently, many teams fight over the meaning and correctness of their numbers instead of the impact of their choice based on data. Common stories alone the lines of, "The tables or pipelines are always broken and I have wasted a lot of my time wrestling with the data team instead of doing my work", "Your total revenue for last year seems to be oddly low, I high doubt the insights in your presentation", and "{{another story}}

Now, tell them a quick story or give them a quick example so they can see it in action. What are things like for someone who doesn't do this vs someone who does? What's the mini transformation that can occur?

## Speed to delivering biz value from AI/Analytics:

Tell the reader why this matters.
Now, tell them a quick story or give them a quick example so they can see it in action. What are things like for someone who doesn't do this vs someone who does? What's the mini transformation that can occur?

## AI as a service:

Tell the reader why this matters.
Now, tell them a quick story or give them a quick example so they can see it in action. What are things like for someone who doesn't do this vs someone who does? What's the mini transformation that can occur?

## Lower cost to maintain AI in production and continue to deliver impact:

Tell the reader why this matters.
Now, tell them a quick story or give them a quick example so they can see it in action. What are things like for someone who doesn't do this vs someone who does? What's the mini transformation that can occur?

Finally, tell the reader what you hope for them.
And wish them well on their journey forward.
