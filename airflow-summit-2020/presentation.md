# Building Reuseable and Trustworthy ELT pipelines
## A templated approach


---

## Hello 👋!

- Lead data @ SnapTravel
- Data Infrastructure, data engineering, analytics engineering, service infrastructure
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack

---

## What is data engineering?

---

"A data engineer's job is to **help** an organisation move and process data"

- Chris Riccomini

---

## Stories

1. Toil
2. Data Trust
3. Data Discovery
4. Throw over the boundary overhead
5. Cannot scale without analysts
6. Datapipeline vendors dont have IAC

^
hire data engineer per data analyst


---

## So much debt

1. Solve the same problem again and again
2. Undocumented and Untested final result
3. Most breakages are caused by other people
4. You get attention when things are broken


---

"..build tools, infrastructure, frameworks and services"

- Maxime Beauchemin


---

## The Big Idea

- Meta data engineering
- Design Pattern with implementation/example
- Standardization
- SSOT Dag


---

## The Big Idea


- Empower non-technical folks to setup data integration
- Who does this appeal to
  - Data Engineers managing EL pipelines in house (why open source is popular)
  - Looking to reduce cost for data pipeline
  - Reduce barrier to entry with data analytics

---

## Case Study: Analyse Airflow Github Project

1. Daily/Weekly/Monthly metrics
2. Minimal amount of code/effort
3. Secret Sauce (Meltano)

---

## ETL vs ELT

- analysts are closest to the business
- sas companies have a lot of data sources
- Brittle components ~ Agile decision making
- Reduced complexity
- Reduce cost


^
- people solving the problem can solve it

---

## EL - Singer

- Taps and targets
- Magic
  - Standardized communication
  - Documentation

---

## EL - Singer - Lacking


- Work for getting it production ready inside data pipeline
- Building new taps
- Running in production reliably
- Community needs some support

---

## T - DBT

- What is DBT?
- Maintainable sql
- Modular code
- Scale best practices
- Resuable consitent analytics code
- Simple incremental models for big data
- Cross-org analytics

---

## Testing - GE

<Need help .. weak>

- Trigger the dag after the source passes data checks0

---

## Bring it all together

<Need help .. weak>

Airflow does what it does best - Orchestrate
Glue it all together with Meltano
Walk through meltano yml config

---

## Benifits of this approach

1. Easily to debug code
2. Speed to delivery
3. Tests
4. Auto-Docs

---

## Some problems it doesnt solve

- Making analytics folks write enough/good data tests
- Operational creep in data eng

---


## Future

1. Standardized tools for self serve data integration and processing
2. Contribute to Meltano
3. Contribute to singer taps and targets



---

## Resources

1. [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/)
2. [The Future of Data Engineering](https://riccomini.name/future-data-engineering)
3. [Downfall of the data engineer](https://medium.com/@maximebeauchemin/the-downfall-of-the-data-engineer-5bfb701e5d6b)
4. [Supercharging your ETL with Airflow and Singer](https://www.stitchdata.com/blog/supercharging-etl-with-airflow-and-singer/)
5. [Singer | Open Source ETL](https://www.singer.io/#what-it-is)
6. [Why we are building an open source platform for ELT pipelines - Meltano](https://meltano.com/blog/2020/05/13/why-we-are-building-an-open-source-platform-for-elt-pipelines/)
7. [Projects · meltano / Meltano · GitLab](https://gitlab.com/meltano/meltano)
8. [Advanced Data Engineering Patterns with Apache Airflow by Maxime Beauchemin on Prezi Next](https://prezi.com/p/adxlaplcwzho/advanced-data-engineering-patterns-with-apache-airflow/)
9. Youtube video about dbt packages



