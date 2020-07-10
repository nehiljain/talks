theme: Poster, 7
text: #000000, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue
header: #000000, alignment(center), line-height(0.7), text-scale(1.0), Rubik Medium

---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]

# [fit] Building <br> Reusable  and  Trustworthy <br> ELT pipelines

---

[.header: #000000, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]


## Hello 👋!

- Lead data engineering @ SnapTravel
- Data Infrastructure, data engineering, analytics engineering, service infrastructure
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack

---


[.header: #FCA831, alignment(center), line-height(0.7), text-scale(0.6), Rubik Medium]
[.background-color: #03488B]

## Been there felt that?


---

## 🙋 Been there felt that? 🙋‍♂️

- Toil
- Cannot scale Data Analytics
- Data Discovery
- Data Trust
- Throw over the boundary, ambiguous ownership

^
- Hire data engineer per data analyst
- You get attention when things are broken
- ambiguous ownership
- Testing
- This dashboard seems to be broken.” Well, there go all your plans for the day. You know you’ll be spending the next few hours trying to figure out what went wrong.
- Documentation

---

# So much debt


- Solve the same problem again and again
- Undocumented and Untested final result
- Most breakages are caused by other people


^
- Data integration vendors don't have IAC

---

> ..build tools, infrastructure, frameworks and services
-- Maxime Beauchemin

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

![fit](https://i.ibb.co/F7YMQfb/1479132315-1296081.jpg)

^
- Metadata engineering
- Design Pattern with implementation/example

---
# Case Study: Analyse Airflow Repository

1. Analyze the # of issues and pr daily
2. Minimal amount of code/effort
3. Secret Sauce (Meltano)

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

- SAS companies have a lot of data sources
- Reduced complexity
- Reduce cost
- Timing of data supply vs data engineer vs data analyst vs business owner


^

- analysts are closest to the business
- SAS companies have a lot of data sources
- Brittle components ~ Agile decision making
- Reduced complexity
- Reduce cost
- Timing of data supply vs data engineer vs data analyst vs business owner

---

![fit](https://i.ibb.co/P6VYCmr/TIming-Airflow-Talk-EL-Singer-1.png)



^
- Agile decision making
- people solving the problem can solve it

---

# EL - Singer

- Taps and targets

![inline fill](https://p91.f3.n0.cdn.getcloudapp.com/items/6qu2JEKl/Screen%20Recording%202020-07-06%20at%2006.18%20pm.gif)


---

## EL - Singer

- Taps and targets
- Magic
  - Standardized communication
  - Incremental out of the box
  - Documentation

^
- Unix inspired
- JSON
- language-agnostic

---

# T - DBT


- What is DBT?

![inline](https://p91.f3.n0.cdn.getcloudapp.com/items/yAuYnKOk/Image%202020-07-07%20at%206.46.26%20pm.png?v=9ca3e6c736f212c269f9d4cd014467bf)


^
- dbt model -> SQL statement
  - relationships between models
- Transformations in SQL
  - SQL low learning curve

---

## T - DBT

- Why DBT?
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

## Testing - GE

- Test if the data supply is good before you can trigger the dag

---

## Bring it all together

![inline](https://i.ibb.co/RC6sjQK/Airflow-Talk-EL-Singer.png)



---
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue ]

## Some problems it doesn't solve

- Visualisation/BI
- Analytics code coverage
- Setting up great QA vs Prod environments
- Singer community

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
[.header: #ffffff, alignment(center), line-height(1.0), text-scale(1.0), Rubik Medium]
[.background-color: #000000]
[.text: #ffffff, alignment(left), line-height(0.9), text-scale(0.8), Helvetica Neue ]

## Who is a <br> data engineer?

---

> A data engineer's job is to **help** an organisation move and process data
-- Chris Riccomini

---

> A data engineer's job is to **help** an organisation **move** and **process data**
-- Chris Riccomini

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


