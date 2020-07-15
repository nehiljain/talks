theme: Poster, 7
text: #000000, alignment(left), line-height(0.9), text-scale(0.8), PT Sans
header: #000000, alignment(center), line-height(0.7), text-scale(1.0), Playfair Display
slidenumbers: true
footer-style: #000000, alignment(right), line-height(0.9), text-scale(0.8), PT Sans
footer: Airflow Summit 2020, *[@nehiljain](https://twitter.com/nehiljain)*

[.header: #ffffff, alignment(center), line-height(0.9), text-scale(0.3), Playfair Display]
[.background-color: #000000]
[.footer-style: #ffffff, alignment(right), line-height(0.9), text-scale(0.8), PT Sans]

![](https://i.ibb.co/44qq2pj/Whats-App-Image-2020-07-13-at-2-32-38-PM.jpg)
# Building <br> Reusable and Trustworthy <br> pipelines


^
- Hi
- Happy to be here, what an exciting event
- Joining you all from Toronto
- Thank you for the great content

---

## Outline

1. Context
2. Design Requirements
3. Proposed Solution
4. Example Code


---

![](https://i.ibb.co/wKgRQ7z/Whats-App-Image-2020-07-13-at-10-03-00-PM-2.jpg)
## Context


---

[.header: #000000, alignment(center), line-height(1.0), text-scale(1.0), Playfair Display]


## Hello 👋!

- Data engineer @ SnapTravel
- Data infrastructure, Data engineering, Analytics engineering
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack

---

## Purpose

[.text: #000000, alignment(left), line-height(1.3), text-scale(0.8), PT Sans]

Share 🧰 BI pipelines
💡 Community with lessons learnt
👂 feedback


^
- toolset
- inspire community
- get fedback

---

## How are my company 📈?

- `gross_revenue`
- `contribution_margin`
- `number_of_active_users`
- `retention_rate`
- `conversion_rate`


^
- Very common use case
  - Definition revenue changing
- Non trivial to calculate
- Eg. Definition of Revenue keeps changing

---

## Hows my airflow repo 📈?

- `number_prs_merged`
- `number_prs_closed_without_merge`
- `number_prs_opened`
- `number_of_commit`


^
I am one of the Eng Leaders
Metrics in Context for Data-Driven Engineering Leaders

---


![fit](https://i.ibb.co/7pF6zQJ/Airflow-ELT-Solution-1.png)

^
most common and traditional approach


---

[.text: #000000, alignment(left), line-height(1.1), text-scale(0.8), PT Sans]
[.build-lists: true]

## Let us consider

- The pipeline failed <br> after a few days of productionization
- Now I want to focus on issues
- Gitlab released a new version of API
- I want to analyze other apache projects too
- Github produced similar insights and their numbers didn't match mine

^
- failed because
  - data broke, null values in the index column
- issues, comments etc
- schema changes, analysts usage
- loss of trust

---

## 🙋 Been there done that? 🙋‍♂️


---

## Classify the problems

- Toil
- Data Discovery
- Data Trust
- Throw over the boundary
- Ambiguous ownership
- Cannot scale Data Analytics

^
- toil
  - requirements keep changing
  - tightly coupled components need tweaking
  - hire data engineer per data analyst
- Imp tables not documented
- You get attention when things are broken
- Testing
- Most breakages are caused by others
- long cycle to delivery
- Documentation

---

## What can we do to solve this?

![](https://i.ibb.co/gryrfG8/Whats-App-Image-2020-07-12-at-5-56-34-PM.jpg)

---

> ..build tools, infrastructure, frameworks and services
-- Maxime Beauchemin

![inline](https://i.ibb.co/80mjgdT/rise-eng.png)

---

## Design Requirements

![](/Users/nehiljain/Downloads/WhatsApp Image 2020-07-12 at 9.25.45 PM.jpeg)

---

![](https://i.ibb.co/W25hyxM/no-patience-amazon.jpg)

^
- Super fast delivery
- Reuseable elements

---

## Single Source of Truth

- Standardization
- Data Lineage
- Empower non-technical folks

^
- Specificity to use case
- 1 place to see the status and history
- 1 thing to learn
- Move towards self-serve
- Easy to learn for non technical folks as there are not too many moving parts


---

## Easy to consume


- Airflow + Other OSS
- Ideally `pip install awesome-elt-tool`
- Low barrier to entry for data analytics
- Operational creep

^
- Data Engineers primary consumers
- Self Serve data integration
- Open source and no vendor lock-in with upfront costs
- Reduce cost


---

## Promote data integrity

- Test the raw data supply
- Automated analytics testing

![inline](https://bigdata-madesimple.com/wp-content/uploads/2018/10/Accuracy.gif)



---

## Meta Data Engineering

![inline](https://i.ibb.co/F7YMQfb/1479132315-1296081.jpg)

^
- Metadata engineering
- Design Pattern with implementation/example



---


![fit](https://i.ibb.co/P6VYCmr/Timing-Airflow-Talk-EL-Singer-1.png)


^
- Agile decision making
- People solving the problem can solve it

---

## Proposed Solution
![](https://i.ibb.co/d6svkcs/Whats-App-Image-2020-07-12-at-9-27-46-PM.jpg)

---

## Conceptually

![inline](https://i.ibb.co/RC6sjQK/Airflow-Talk-EL-Singer.png)

---

## ETL vs ELT

- Load once and transform
- Reduced complexity
- Reduce cost
- Speed of delivery


^
- ETL requires work to manually script various use-cases into a pipeline
- Sas companies have a lot of data sources
- Possible because of cloud-based data warehouses
- Flexibility of capturing all the data
- Speed of delivery
  - data always available
  - Brittle components ~ Agile decision making
  - analysts are closest to the business
- Reduced complexity
- Reduce cost

---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Playfair Display]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), PT Sans ]

![](https://i.ibb.co/gdKB5Hd/Whats-App-Image-2020-07-13-at-2-30-20-PM.jpg)

## Validate your source data

---



![inline](https://i.ibb.co/W5hmCQz/great-expectations-logo.png)

[.text: #000000, alignment(left), line-height(0.9), text-scale(0.5), PT Sans]



[.column]

- `expect_column_to_exist`
- `expect_table_row_count_to_be_between`
- `expect_table_row_count_to_equal`
- `expect_multicolumn_values_to_be_unique`
- `expect_column_values_to_not_be_null`
- `expect_column_values_to_be_null`
- `expect_column_fancy_statistic_to_be`


[.column]
![inline](https://www.kindpng.com/picc/m/574-5747046_python-pandas-logo-transparent-hd-png-download.png)
![inline](https://hakin9.org/wp-content/uploads/2019/08/connect-a-flask-app-to-a-mysql-database-with-sqlalchemy-and-pymysql.jpg)
![inline](https://miro.medium.com/max/1088/0*AmYXrtpALhMlQcZI.png)
![inline](https://spark.apache.org/images/spark-logo-trademark.png)

^
- Declarative assertions like expect col to not have null or expect col to have min and max of foo and bar
- Data sources
- Examine batch of data

^
- A python library
- Helps you validate your expectations against a batch of data

---

## Why?

- Profiling
- Data Docs <-> Tests
- Send notifications automatically


^
- cli tool for automation
- extensive

---

[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Playfair Display]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), PT Sans ]

![](https://i.ibb.co/tBkMQtx/Whats-App-Image-2020-07-13-at-10-03-01-PM.jpg)
## Extract - Load

---


## Singer - What?


![inline](https://i.ibb.co/TLXTPc7/Tap-and-Targets.png)

^
- Open Source Standard
- Data extraction and loading
- Taps -  extract and output to standard stream
- Target - consume data and put it somewhere

---

```bash
tap-github --config tap_config.json | target-postgres --config target_config.json >> state.json
```

---

## Singer - Why?

- Standardized communication
- Incremental out of the box
- Documentation
- See your data in under 10 mins

^
- Unix inspired, low complexity
- JSON
- rich data types
- language agnostic
- human readable for debugging
- maintains state for incremental

---


![fit](https://i.ibb.co/HG40Mns/screencapture-www-singer-io-1594430740171.png)

---

## It's a long list

![fit](https://i.ibb.co/HG40Mns/screencapture-www-singer-io-1594430740171.png)


---

[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Playfair Display]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), PT Sans ]

![](https://i.ibb.co/fn3JYjQ/Whats-App-Image-2020-07-14-at-8-49-56-PM.jpg)
## Transform

---

## DBT - What?


![inline](https://p91.f3.n0.cdn.getcloudapp.com/items/yAuYnKOk/Image%202020-07-07%20at%206.46.26%20pm.png?v=9ca3e6c736f212c269f9d4cd014467bf)


^
- Transform data effectively
- Reads and writes from warehouse
- powerful cloud data warehouses enable
- Transformations in SQL

---

![fit](https://i.ibb.co/Qjt5syP/dbt-model-dependency-gif.gif)

^
- dbt model -> SQL statement
  - relationships between models

---

![fit](https://docs.getdbt.com/img/docs/building-a-dbt-project/dbt-docs-screenshot.png)

---


## DBT - Why?

- *Modular code*

![inline fill](https://i.ibb.co/Nxqq3Vc/modular-code.png)

---


## DBT - Why?


- Modular code
- *Testing is 1st Class*

![inline fill](https://i.ibb.co/qxfyDWW/tests-code.png)

---


## DBT - Why?



- Modular code
- Testing is 1st Class
- *Data documentation is 1st Class*

![inline fill](https://i.ibb.co/sQqnLNf/document-code.png)



---

## Great adoption

![inline](https://lh3.googleusercontent.com/Y8QSqzwK-xiFncHoUBmhttKuJe7NsH6Nu_eIXv8j7Z8wV4O-IoGhwrC6zrBdl40nbohPHEb0u5qn3D2B33x4bwsZv3YpBpa9Yqm2dO8KLPnqU1j1GBlQPpSddzN3b-0Cj_dNZ4Gy)


---

## All together

![inline](https://i.ibb.co/RC6sjQK/Airflow-Talk-EL-Singer.png)

---

## Meltano

- Open Source, GitLab
- Self Hosted

```
pip3 install meltano
meltano init airflow-analytics-project
meltano add extractor tap-github
meltano add loader target-postgres
meltano add transformer dbt
meltano add transform tap-github
# add env variables
meltano elt tap-gitlab target-postgres --transform=run --job_id=gitlab-to-postgres
meltano add orchestrator airflow
```

^
The team is hungry for feedback


---

## Let's look at the code

---


![fit](https://i.ibb.co/q9f0Qtx/full-code.png)

---

![fit](https://i.ibb.co/q9f0Qtx/full-code.png)
## A templated approach

---

![fit](https://i.ibb.co/Pmn9ckJ/extract-code.png)

---

![fit](https://i.ibb.co/4gwVZv1/loader-code.png)


---

![fit](https://i.ibb.co/6bwpbsp/transformer-code.png)

---

![fit](https://i.ibb.co/FHXW3HG/airflow-dag-config.png)

---

![](https://i.ibb.co/T0PdZC8/Whats-App-Image-2020-07-14-at-8-49-57-PM.jpg)

## Sit back & Relax


---


## Some challenges out there

- Visualisation/BI layer
- Analytics code coverage
- Singer community

^
- There can be tranforms done in the last mile of Bi layer which can break when you schema of the transformed models change
Analysts are new to the game of software engineering practices
Singer community can be challenging to work with sometimes

---


## Key Takeaways

- Standardized tooling
- ELT >> ETL
- GE + Singer + DBT orchestrated by Airflow


^
- Self serve for same problems
- Meltano is a great initiative by Gitlab worth checking out
  - Shout out to Douwe


---

![](https://i.ibb.co/S67FVVt/Whats-App-Image-2020-07-13-at-10-03-00-PM.jpg)

## Thanks

---

![](https://i.ibb.co/TbJK4Bz/Whats-App-Image-2020-07-14-at-8-49-56-PM-1.jpg)

## Q & A

---

# Resources

- [Meltano Project](https://meltano.com/)
- [Advanced Data Engineering Patterns with Apache Airflow by Maxime Beauchemin](https://prezi.com/p/adxlaplcwzho/advanced-data-engineering-patterns-with-apache-airflow/)
- [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/)
- [The Future of Data Engineering](https://riccomini.name/future-data-engineering)
- [Downfall of the data engineer](https://medium.com/@maximebeauchemin/the-downfall-of-the-data-engineer-5bfb701e5d6b)
- [Supercharging your ETL with Airflow and Singer](https://www.stitchdata.com/blog/supercharging-etl-with-airflow-and-singer/)

---

# Resources

- [Singer | Open Source ETL](https://www.singer.io/#what-it-is)
- [Why we are building an open-source platform for ELT pipelines - Meltano](https://meltano.com/blog/2020/05/13/why-we-are-building-an-open-source-platform-for-elt-pipelines/)
- [Dbt Docs](https://docs.getdbt.com/docs/introduction)
- []


