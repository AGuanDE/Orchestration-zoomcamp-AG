# Orchestration-zoomcamp-AG
Repo for week 2 module on kestra and orchestration

### Goal: update existing kestra flows with data for 2021 yellow and green taxis.

Steps:
- set up flows on kestra locally and validate flows
- push to dev branch on github
- PR / merge to main
- sync flows and files to kestra on prod (Google cloud)

### Challenge: find out how to loop over the combination of Year-Month and taxi-type using ForEach task which triggers the flow for each combination using a Subflow task.

**ForEach tasks**
- Purpose: useful for scenarios where multiple similar tasks need to be run for different inputs.

``` yaml
type: "io.kestra.plugin.core.flow.ForEach"
```

I used a python script to generate every combination of taxi, year and month, then copied it to the values property of the forEach task. For future, learn how to create this combination more efficiently (use a json file or us a script to make it dynamic).

``` yaml
id: taxi-loop
namespace: kestra-forloop-test
description: "Loop over each taxi-type, year, and month combination and trigger the subflow"

tasks:
  - id: for-each
    type: io.kestra.plugin.core.flow.ForEach
    values:
      [
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "01"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "02"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "03"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "04"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "05"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "06"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "07"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "08"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "09"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "10"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "11"
        },
        {
            "taxi": "yellow",
            "year": "2019",
            "month": "12"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "01"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "02"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "03"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "04"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "05"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "06"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "07"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "08"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "09"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "10"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "11"
        },
        {
            "taxi": "yellow",
            "year": "2020",
            "month": "12"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "01"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "02"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "03"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "04"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "05"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "06"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "07"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "08"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "09"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "10"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "11"
        },
        {
            "taxi": "yellow",
            "year": "2021",
            "month": "12"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "01"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "02"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "03"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "04"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "05"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "06"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "07"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "08"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "09"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "10"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "11"
        },
        {
            "taxi": "green",
            "year": "2019",
            "month": "12"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "01"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "02"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "03"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "04"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "05"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "06"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "07"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "08"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "09"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "10"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "11"
        },
        {
            "taxi": "green",
            "year": "2020",
            "month": "12"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "01"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "02"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "03"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "04"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "05"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "06"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "07"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "08"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "09"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "10"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "11"
        },
        {
            "taxi": "green",
            "year": "2021",
            "month": "12"
        }
      ]
    tasks: 
      - id: send_to_postgres_taxi
        type: io.kestra.plugin.core.flow.Subflow
        flowId: taxi-postgres
        namespace: kestra-forloop-test
        inputs: 
          my_input: "{{ taskrun.value }}"

```




resources: 
- Pull data from: https://github.com/DataTalksClub/nyc-tlc-data/releases/tag/green/download


## Homework:

1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?
- 128.3 MB (answer)
- 134.5 MB
- 364.7 MB
- 692.6 MB

2. What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?
- {{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv
- green_tripdata_2020-04.csv (answer)
- green_tripdata_04_2020.csv
- green_tripdata_2020.csv

3. How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?
- 13,537.299
- 24,648,499 (answer)
- 18,324,219
- 29,430,127

``` sql
SELECT SUM(row_count) AS total_rows
FROM (
  SELECT COUNT(*) AS row_count FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_01`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_02`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_03`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_04`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_05`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_06`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_07`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_08`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_09`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_10`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_11`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.yellow_tripdata_2020_12`
) AS all_counts;
```

4. How many rows are there for the Green Taxi data for all CSV files in the year 2020?
- 5,327,301
- 936,199
- 1,734,051 (answer)
- 1,342,034

``` sql
SELECT SUM(row_count) AS total_rows
FROM (
  SELECT COUNT(*) AS row_count FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_01`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_02`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_03`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_04`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_05`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_06`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_07`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_08`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_09`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_10`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_11`
  UNION ALL
  SELECT COUNT(*) FROM `kestra-project-449307.zoomcamp.green_tripdata_2020_12`
) AS all_counts;
```

5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file?
- 1,428,092
- 706,911
- 1,925,152 (answer)
- 2,561,031

6. How would you configure the timezone to New York in a Schedule trigger?
- Add a timezone property set to EST in the Schedule trigger configuration
- Add a timezone property set to America/New_York in the Schedule trigger configuration (answer)
- Add a timezone property set to UTC-5 in the Schedule trigger configuration
- Add a location property set to New_York in the Schedule trigger configuration
