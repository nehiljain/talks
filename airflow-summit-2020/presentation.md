theme: Poster, 7
text: #000000, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue
header: #000000, alignment(center), line-height(0.7), text-scale(1.0), Rubik Medium

---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]

# [fit] Building <br> Reusable  and  Trustworthy <br> ELT pipelines

Footer: Airflow Summit 2020


^
HI
Happy to be here, what an exciting event
I am joinng you all from Toronto


---


1. Context
2. Motivation
3. Proposed Solution
4. Example Code


---

[.header: #000000, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]


## Hello 👋!

- Lead data engineering @ SnapTravel
- Data Infrastructure, data engineering, analytics engineering, service infrastructure
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack

---

## How are my Metrics?

- `gross_revenue`
- `contribution_margin`
- `number_of_active_users`
- `retention_rate`
- `conversion_rate`


^
- Very common use case
- Non trivial to calculate
- Eg. Definition of Revenue keeps changing

---

## What part of Airflow repo needs my attention?

- `number_prs_merged`
- `number_prs_closed_without_merge`
- `number_prs_opened`
- `number_of_commit`


^
I am one of the Eng Leaders
Metrics in Context for Data-Driven Engineering Leaders

---

## Solution 1

< todo: add image for etl>

^
most common and traditional approach


---

## Now consider scenarios

- When I pushed to production, the pipeline failed after a few days
- Now I want to focus on issues
- Gitlab released a new version of API
- I want to analyze other apache projects too
- Github produced similar insights and their numbers didn't match mine

---

[.header: #FCA831, alignment(center), line-height(0.7), text-scale(0.6), Rubik Medium]
[.background-color: #03488B]

## Been there felt that?


---

## 🙋 Been there felt that? 🙋‍♂️

- Toil
- Data Discovery
- Data Trust
- Throw over the boundary, ambiguous ownership
- Cannot scale Data Analytics

^
- Hire data engineer per data analyst
- You get attention when things are broken
- ambiguous ownership
- Testing
- This dashboard seems to be broken.” Well, there go all your plans for the day. You know you’ll be spending the next few hours trying to figure out what went wrong.
- Documentation

---

## What can I do to solve this?

<todo: add think emoji>

---

> ..build tools, infrastructure, frameworks and services
-- Maxime Beauchemin

<todo: ref to rise of data engineer>

---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue ]


## Design Requirements

---

![](https://i.ibb.co/W25hyxM/no-patience-amazon.jpg)

^
- Super fast delivery
- Reuseable elements

---

## Single Source of Truth

<todo: add a image of data supply chain with da and bo>

- Standardization
- Data Lineage
- Empower non-technical folks

^
- Specificity to use case
- Move towards self-serve
- Easy to learn for non technical folks as there are not too many moving parts


---

## Easy to consume

- Low barrier to entry for data analytics
- Airflow + Other OSS
- Ideally `pip install awesome-elt`
- Operational creep

^
- Self Serve data integration
- Open source and not vendor lock in with upfront costs
- Reduce debt and cost

---

## Promote data integrity

- Test the raw data supply
- Automated analytics testing

![inline](https://bigdata-madesimple.com/wp-content/uploads/2018/10/Accuracy.gif)

---


![fit](https://i.ibb.co/P6VYCmr/Timing-Airflow-Talk-EL-Singer-1.png)


^
- Agile decision making
- People solving the problem can solve it


---

![fit](https://i.ibb.co/F7YMQfb/1479132315-1296081.jpg)

^
- Metadata engineering
- Design Pattern with implementation/example

---

## A templated approach

---

```yaml

version: 1
send_anonymous_usage_stats: true
project_id: 85d9741e-9e24-4178-a48c-2ac05e886fc1
plugins:
  extractors:
  - name: tap-github
    namespace: tap_github
    pip_url: tap-github
    executable: tap-github
    capabilities:
    - discover
    - properties
  loaders:
  - name: target-postgres
    pip_url: git+https://github.com/meltano/target-postgres.git
  orchestrators:
  - name: airflow
    pip_url: wtforms==2.2.1 apache-airflow==1.10.2
  files:
  - name: airflow
    pip_url: git+https://gitlab.com/meltano/files-airflow.git
schedules:
- name: gitlab-to-postgres
  extractor: tap-github
  loader: target-postgres
  transform: skip
  interval: '@hourly'
  start_date: 2020-07-05 00:00:00
```

---

## ETL vs ELT

- SAS companies have a lot of data sources
- Reduced complexity
- Reduce cost
- Speed of delivery


^
- ETL requires work to manually script various usecases into a pipeline
- ELT is load once and transform as much as you want (speed)
- Possible because of cloud based data warehouses

- Flexibility of capturing all the data
- Speed of delivery
  - data always available
  - Brittle components ~ Agile decision making
  - analysts are closest to the business
- Reduced complexity
- Reduce cost

---


## Conceptually

![inline](https://i.ibb.co/RC6sjQK/Airflow-Talk-EL-Singer.png)

## Testing - GE

- Its about expectations
-


^
- Declarative assertions like expect col to not have null or expect col to have min and max of foo and bar
- Data sources
- Examine batch of data

^
- A python library and cli tool
- Helps you validate your expectations against a batch of data


---

## Magic

- Profiling
- Data Docs
- Send notifications automatically


^
extensive

---

# EL - Singer

- Taps and targets

<todo: image of tap and target>

^
focus on the what

---

## EL - Singer

- Magic
  - Standardized communication
  - Incremental out of the box
  - Documentation

^
- WHY
- Unix inspired
- JSON
- language-agnostic

---


![fit](https://i.ibb.co/HG40Mns/screencapture-www-singer-io-1594430740171.png)

---

## Its a long list

![fit](https://i.ibb.co/HG40Mns/screencapture-www-singer-io-1594430740171.png)


---

# T - DBT


- What is DBT?

![inline](https://p91.f3.n0.cdn.getcloudapp.com/items/yAuYnKOk/Image%202020-07-07%20at%206.46.26%20pm.png?v=9ca3e6c736f212c269f9d4cd014467bf)


^
- Focus on what
- dbt model -> SQL statement
  - relationships between models
- Transformations in SQL
  - SQL low learning curve

---

![fit](https://docs.getdbt.com/img/docs/building-a-dbt-project/dbt-docs-screenshot.png)

---


## T - DBT

- Magic
  - Modular code
  - Testing is 1st Class
  - Data documentation support
  - De-coupled read vs write location
  - Great adoption


^
- Reusable consistent analytics code
- Simple incremental models for big data
- Cross-org analytics


---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue ]


---

## Case Study Report


---

## Code Sample

---
## Some challenges out there

- Visualisation/BI layer
- Analytics code coverage
- Singer community

^
There can be tranforms done in the last mile of Bi layer which can break when you schema of the transformed models change
Analyts are new to the game of software engineering practices
Singer community can be challenging to work with sometimes

---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue ]

## Key Takeaways

- Standardized tooling
- ELT >> ETL
- GE + Singer + DBT orchestrated by Airflow

^
- Self serve for same problems
- Meltano is a great initiative by Gitlab worth checking out
  - Shout out to Douwe


---

# Resources

1. [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/)
2. [The Future of Data Engineering](https://riccomini.name/future-data-engineering)
3. [Downfall of the data engineer](https://medium.com/@maximebeauchemin/the-downfall-of-the-data-engineer-5bfb701e5d6b)
4. [Supercharging your ETL with Airflow and Singer](https://www.stitchdata.com/blog/supercharging-etl-with-airflow-and-singer/)
5. [Singer | Open Source ETL](https://www.singer.io/#what-it-is)
6. [Why we are building an open-source platform for ELT pipelines - Meltano](https://meltano.com/blog/2020/05/13/why-we-are-building-an-open-source-platform-for-elt-pipelines/)
7. [Projects · meltano / Meltano · GitLab](https://gitlab.com/meltano/meltano)
8. [Advanced Data Engineering Patterns with Apache Airflow by Maxime Beauchemin](https://prezi.com/p/adxlaplcwzho/advanced-data-engineering-patterns-with-apache-airflow/)
9. Youtube video about dbt packages


