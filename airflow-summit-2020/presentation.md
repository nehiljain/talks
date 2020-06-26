# Building Reuseable and Trustworthy ELT pipelines
## A templated approach



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
4. Downfall of the data engineer
   1. You get attention when things are broken


---


---

## The Big Idea

Design Pattern with implementation/example
Our jobs is to built frameworks and **infra**
Meta data engineering
Standardization
Define a dag
SSOT Dag
Empower non-technical folks to setup data integration
Who does this appeal to
  Data Engineers managing EL pipelines in house (why open source is popular)
  Looking to reduce cost for data pipeline
  Reduce barrier to entry with data analytics

---

1. Analyse Airflow Github Project
2. Goals
   1. Weekly/Monthly metrics
   2.
3. meta data engineering
4. config ad code

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
- Requires work for getting it production ready inside data pipeline
- High barrier to entry
  - Building
  - Running in production reliably
- Community needs some work

---

## T - DBT

- Scale best practices
- Resuable consitent analytics code
- Simple incremental models for big data
- Cross-org analytics
- Maintainable sql
- Modular code

---

- lets look at
- define dbt commands
- define dbt test commands


---

## Testing - GE

- Trigger the dag after the source passes data checks

---

## Bring it all together

Glue it all together
Airflow does what it does best - Orchestrate
Operators for all the above
Yaml declaration for dry

---

## Benifits of this approach

1. Easily to debug code
2. Speed to delivery
3. Tests
4. Auto-Docs

---

## Some problems it doesnt solve

- Making analytics folks write enough/good data tests
- Operational creep
-

---


## Future

1. Meltano
2.
