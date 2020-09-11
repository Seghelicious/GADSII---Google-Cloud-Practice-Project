# GCP Fundamentals: Getting Started with Big Query

## Objectives
#### At the end of this lab, I would be able to

- Load data from Cloud Storage into BigQuery using the GCP Console
- Perform a query on the data in BigQuery using the bq command.

### Steps

#### 1. Load Data from Cloud Storage into BigQuery using the GCP Console.
###### On the GCP Console, I navigated to BigQuery. I created a new dataset within my project by selecting the project in the Resources section, then clicking on *CREATE DATASET* button. 
###### In the Create Dataset dialog, I entered *logdata* for Dataset ID and United States(US) for Data Location, then clicking the *Create Dataset* at the bottom of the page.
###### I created a table *logdata* to store the data in CSV.I selected *Google Cloud Storage* and typed the following command in the  field provided. In the Verify File Format, *CSV* was selected.
            gs://cloud-training/gcpfci/access_log.csv

###### In the Destination section, *logdata* remains the name of the dataset, the table name is *accesslog* and *Native table* is selected as the table type. 
###### In the *Schema* section, *Check Schema and Input Parameters* is selected for *Auto Detect*.
###### The remaining variales are accepted as the default, *Create Table* is selected.


#### 2. Perform a query on the data in BigQuery using the bq command.

###### To view the dataset and associated tables, I executed the following command in the Cloud Shell
            bq show qwiklabs-gcp-04-5ed10ce57ecc:logdata.accesslog

###### The output was the table schema with the datatypes, the data the table was last modified, the total number of rows and the size of the table (bytes).

###### I  ran the following query via the  command line
            bq query "select string_field_10 as request, count(*) as requestcount from logdata.accesslog group by request order by requestcount desc"

###### This query returns a count of all the of GET requests of urls received by the string_field_10 web server, in descending order. From the results returned, It can be seen that the 

- GET /store HTTP/1.0   has the highest number of requests with 337293 requests 
- GET /favicon.ico HTTP/1.0   has the lowest number of requests with 55845 request.
