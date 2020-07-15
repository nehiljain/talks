slidenumbers: true
list: #555555, ✦, left
footer: DBT Office Hours, *[@nehiljain](https://twitter.com/nehiljain)*

[.background-color: #1A4E66]

# Using Airflow to Orchestrate dbt


---


# Outline

1. Context
2. Authoring
3. Orchestration
4. Deployments
5. Post Deployment


---
[.background-color: #D48533]
# Context


---


# Hello 👋!

- Data engineer @ SnapTravel
- Data infrastructure, Data engineering, Analytics engineering
- ![inline](https://nehiljain.com/images/stitch-icon.png) + ![inline](https://nehiljain.com/images/airflow-icon.png) + ![inline](https://surveymonkey-assets.s3.amazonaws.com/survey/280222649/324d7fd3-51ee-4548-91f7-a1dffbd9b555.png) + ![inline](https://raw.githubusercontent.com/PrefectHQ/prefect/master/docs/.vuepress/public/logos/dbt.png) stack


---

# SnapTravel

- Travel Startup, Toronto
- Team of 8
- 86 Sources, 300 models


---

# Purpose


Share 🧰 DBT pipelines
💡 Community with lessons learnt
👂 feedback


^
- toolset
- inspire community
- get feedback

---

# What is airflow?

<br>

<br>

---


![](https://i.ibb.co/tZJy50D/stop.jpg)


---
[.build-lists: true]

# What is airflow?

- Open Source
- Programmatic Workflow Management
- Primitives:
  - Dags
  - Tasks
  - Operators
  - Hooks


---
[.background-color: #3C696B]

# Authoring

^
all of this is dbt pipeline specific

---
[.background-color: #3C696B]
## Tasks

---

# BashOperator

- Execute any bash command
- `stdout` goes to logs

![inline](https://i.ibb.co/Yfm7M4R/bashoperator.png)

---

# DBT Operators

![inline](https://i.ibb.co/c1ssxTB/airflow-operators.png)

Thanks Andrew @ GoCardless

---

# DBT Operators

- Easier to read
- Extensible
- 🔔 Lacking completeness

![right fit](https://i.ibb.co/c1ssxTB/airflow-operators.png)

---
[.background-color: #3C696B]
## Dags

---

# DagFactory

![inline](https://i.ibb.co/Z20QYrd/Image-2020-07-13-at-3-39-07-PM.png)


---

# DagFactory

- Yaml for static configs
- No python
- No airflow primitives
- Templated

![right fit](https://i.ibb.co/Z20QYrd/Image-2020-07-13-at-3-39-07-PM.png)

---

# Airflow Dag Creation Plugin

![inline](https://raw.githubusercontent.com/lattebank/airflow-dag-creation-manager-plugin/master/images/dag_config.png)

---

# Airflow Dag Creation Plugin

- Onetime setup
- Speed
- No python
- No airflow primitives
- No local setup
- 🔔 Version Control
- 🔔 Review

![right fit](https://raw.githubusercontent.com/lattebank/airflow-dag-creation-manager-plugin/master/images/dag_config.png)

---
[.background-color: #404040]

# Orchestration

---

# Integration

- DBT Project as a package

![inline 90%](https://i.ibb.co/80s9PGZ/dbt-package.png)

- Monorepo: Airflow + DBT

---

# Types Jobs

[.build-lists: true]

- One Time
- Sources ELT
- De-coupled with sources
- Convert dbt dag to airflow dag

^
Minimise the number of jobs

---

# One Time

- `dbt deps`
- `dbt seed`
- `dbt docs generate`
- Run inside CI Pipeline

---

# Source ELT

`dbt run -m source:datasource+`

![inline](https://i.ibb.co/RC6sjQK/Airflow-Talk-EL-Singer.png)


---


# De-coupled with sources: Nightly

```yaml
nightly_dbt_dag:
  default_args:
    owner: 'dbt_owner'
    start_date: 2018-01-01
  schedule_interval: '0 3 * * *'
  description: 'This is the nightly dbt dag'
  tasks:
    source_freshness_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt source snapshot-freshness'
    dbt_run_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt run -m tag:nightly'
      dependencies: [source_freshness_task]
    dbt_test_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt test -m tag:nightly'
      dependencies: [dbt_run_task]
```

---


# De-coupled with sources: Hourly

```yaml
hourly_dbt_dag:
  default_args:
    owner: 'dbt_owner'
    start_date: 2018-01-01
  schedule_interval: '0 * * * *'
  description: 'This is the hourly dbt dag'
  tasks:
    source_freshness_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt source snapshot-freshness'
    dbt_run_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt run --exclude tag:nightly'
      dependencies: [source_freshness_task]
    dbt_test_task:
      operator: airflow.operators.bash_operator.BashOperator
      bash_command: 'dbt test --exclude tag:nightly'
      dependencies: [dbt_run_task]
```

---

# Adhoc Jobs

- Tag adhoc
  - Cold Start
  - Backfill incremental models
- 🔔 Exclude adhoc for all the other runs

---

[.background-color: #D48533]
# Deployment

---

# Astronomer

[.column]
- Airflow as a service
- Great cli
- Active contributors
- Easy deployment and system monitoring
- Good support

[.column]
![fit 90%](https://assets.astronomer.io/website/img/AWithStars.png)

---

# Google Cloud Compose

[.column]
- All things similar to Astronomer
- Sync code via GCS
- GCP all the way

[.column]
![](https://miro.medium.com/max/700/1*O9dHIq7oQQgEq5YU-fhykA.png)


---

# Self-Hosted

- [Use official docker image](https://hub.docker.com/r/apache/airflow)
- [Use official helm chart](https://github.com/helm/charts/tree/master/stable/airflow)

---
[.background-color: #3C696B]
# Post Deployment

---

# Monitoring

- Healthchecks.io

![inline](https://healthchecks.io/static/img/my_checks.png)

---

# My favourite metrics

- Success Rate
- Run Durations
- Queue Rate

^
- Number of times success/ Total number of times
- End time - Start time
  - should be under the tag of nightly or hourly
- Queued runs and warehouse queries

---
[.build-lists: true]

# Triaging

- Keep those tests in check
- Round robin
- Regularly track your toil
  - Tests > Freshness > Run
- Retrospectives



---
[.build-lists: true]

# Keep it up

- Fix Tests
  * Fix the data
  * Fix the test
  * Tag and wait for a fix
- Regular cost and metrics review

---
[.background-color: #1A4E66]

# 🙏 Thank you

---

# Q & A


Nehil Jain
<br>
Slack: @nehiljain
[nehiljain.com](nehiljain.com)


---

# Resources

1. https://www.youtube.com/watch?v=YWtfU0MQZ_4
2. https://github.com/gocardless/airflow-dbt/
3. https://github.com/ajbosco/dag-factory
4. https://github.com/lattebank/airflow-dag-creation-manager-plugin
5. https://healthchecks.io/
6. https://www.astronomer.io/
7. https://about.gitlab.com/handbook/business-ops/data-team/how-we-work/duties/#triager
8. https://www.crowdcast.io/e/airflowsummit/15
9. https://www.crowdcast.io/e/airflowsummit/14
10. https://analyticsmayhem.com/dbt/schedule-dbt-models-with-apache-airflow/?icmp=related
11. https://meltano.com/
