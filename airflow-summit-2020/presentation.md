theme: Poster, 3
text: #ffffff, alignment(left), line-height(0.9), text-scale(1.0), Roboto Regular
header: #ffffff, alignment(center), line-height(0.7), text-scale(1.0), Rubik Medium

for color scheme https://www.slideteam.net/color-palette-for-presentation-blue-and-yellow.html
---

# [fit] Building <br> Reusable  and  Trustworthy <br> ELT pipelines
### A templated approach


---

## Hello 👋!

- Lead data engineering @ SnapTravel
- Data Infrastructure, data engineering, analytics engineering, service infrastructure
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack

---

## Who is a <br> data engineer?

---

> A data engineer's job is to **help** an organisation move and process data
-- Chris Riccomini

---

> A data engineer's job is to **help** an organisation **move** and **process data**
-- Chris Riccomini

---

# Been there felt that?


---

## 🙋 Been there felt that? 🙋‍♂️

1. Cannot scale Data Analytics
2. Toil
3. Data Trust
4. Data Discovery
5. Throw over the boundary

^
- Data pipeline vendors don't have IAC
  - multiple consoles
- Testing
- Documentation
- Hire data engineer per data analyst

---

## So much debt

0. You get attention when things are broken
1. Solve the same problem again and again
2. Undocumented and Untested final result
3. Most breakages are caused by other people

---

> ..build tools, infrastructure, frameworks and services
-- Maxime Beauchemin

---

## My approach

---

# Super fast analytics

![](https://i.ibb.co/W25hyxM/no-patience-amazon.jpg)

^
- Super fast delivery
- Reuseable elements

---

![fit](https://i.ibb.co/F7YMQfb/1479132315-1296081.jpg)

^
- Metadata engineering
- Design Pattern with implementation/example

---

## The Big Idea

<todo: add a image of data supply chain with da and bo>

- Standardization
- SSOT Dag
- Empower non-technical folks

---

## The Big Idea

- Airflow + Other OSS
- Reduce barrier to entry for data analytics
- Convert data pipeline from liabilities to assets

^
- Self Serve data integration
- Open source and not vendor lock in with upfront costs
- Reduce debt and cost

---

## Case Study: Analyse Airflow Repository

1. Analyze the # of issues and pr daily
2. Minimal amount of code/effort
3. Secret Sauce (Meltano)

---

## ETL vs ELT

- analysts are closest to the business
- SAS companies have a lot of data sources
- Brittle components ~ Agile decision making
- Reduced complexity
- Reduce cost
- Timing of data supply vs data engineer vs data analyst vs business owner


^
- people solving the problem can solve it

---

## EL - Singer

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
- unix inspired
- json
- language agnostic

---

## T - DBT

- What is DBT?
- Maintainable SQL
- Modular code
- Scale best practices
- Reusable consistent analytics code
- Simple incremental models for big data
- Cross-org analytics

---

## Testing - GE

- Test if the data supply is good before you can trigger the dag

---

## Bring it all together

- Airflow is the glue to bring the ecosystem together

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

## EL - Singer - Lacking

- Reliable production deployments
- Workflow and community engagement
- Catalog


---

## Benefits of this approach

1. Easily to debug code
2. Speed to delivery
3. Tests
4. Auto-Docs

---

## Some problems it doesn't solve

- Analytics code test coverage
- Operational creep in data eng

---


## Future

1. Standardized tools for self serve data integration and processing
2. Help develop Meltano (or an Alternative)
3. Coverage of singer taps and targets



---

## Resources

1. [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/)
2. [The Future of Data Engineering](https://riccomini.name/future-data-engineering)
3. [Downfall of the data engineer](https://medium.com/@maximebeauchemin/the-downfall-of-the-data-engineer-5bfb701e5d6b)
4. [Supercharging your ETL with Airflow and Singer](https://www.stitchdata.com/blog/supercharging-etl-with-airflow-and-singer/)
5. [Singer | Open Source ETL](https://www.singer.io/#what-it-is)
6. [Why we are building an open-source platform for ELT pipelines - Meltano](https://meltano.com/blog/2020/05/13/why-we-are-building-an-open-source-platform-for-elt-pipelines/)
7. [Projects · meltano / Meltano · GitLab](https://gitlab.com/meltano/meltano)
8. [Advanced Data Engineering Patterns with Apache Airflow by Maxime Beauchemin](https://prezi.com/p/adxlaplcwzho/advanced-data-engineering-patterns-with-apache-airflow/)
9. Youtube video about dbt packages



