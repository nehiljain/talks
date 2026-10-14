# Outline
https://pretalx.com/apache-airflow-summit-bay-area-2020/talk/review/Q3WNKPGR7LYYNMZTGLBSJTSC9NXAKBJ7


## Introduction
## Common problems we face

	* Custom code for data source. 1:1 mappings for source to destinations
	* ETLs bottleneck, not fast as biz landscape changes are
	* Depletion o f trust. Wrong decisions made, bad data in production
	* Data pipelines blamed, wrong data produced by source
	* Bugs in data transformations reaching production
	* Debugging Pipelines slow
	* Engineer Analyst hand-off painful
	* No documentation of assumptions of our data

## ETL vs ELT
## Singer

* Tap - stream of records from a source
* Target  - data loading script. load it into a file, API or database.
* Unix inspired
* Any combination
* Best practices are shipped
* Code example

## Great Expectations

* Framework for specifying assumptions of datasaet
* Works with pipelines: batch
* Out of Box expectations
* Code Example
* Features explanation

## DBT

* SQL first transformation tool
* Built for analysts
* Testing and docs/catalog by dbt
* Code example


## Airflow 
* Does what it is does bestL Orchestrate
* Provide operators to invoke the above without pain
* Future : declarative dag genration
* Yaml Dag - Dag Factory
