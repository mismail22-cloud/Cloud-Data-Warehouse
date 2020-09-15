# Purpose of Music Inventory Data warehouse:
As a Startup , Sparkify needs to get the full power of Information and Insights that can be got from data.This Insights can provide Sparkify with knowledge over Users Usages ,their preferences , locations & top demanded songs so that Sparkify Managment can take the right decisions on the right time to be able to act correctly towards the market.
This DWH will serve the need to avail Sparkify Managment with the Required Insights and Information so that they can take the optimum decisions.


# Data warehouse solution design:

## 1.The Data warehouse is hosted on AWS Cloud where Redshift database is used as SaaS.
This helps to reduce the upfront Infrastructure costs for Sparkify.
Also will help to pay as per the resources consumed by Sparkify.
Adding to that the flexibility to Scale up or down according to the Data sizes and traffic loads that may differ from time period to another.
Noting that this will be very beneficial in case of Startup Company like Sparkify.

## 2.Database Model:
### a.The Model is Dimensional Star Schema Model consisting of one Fact Table "FACT_SONGPLAY" surrounded by Dimensions "DIM_SONG","DIM_ARTIST","DIM_USER","DIM_TIME".This Helps to have high performance of the analytical queries that will run on top of this dimensional model.

### b.There is a staging layer for landing the Files from S3 Bucket , This Staging layer consists of two tables "STG_EVENT","STG_SONG".


## 3.ETL Solution 
The ETL Solution consists of two main parts:
### a.Landing the Data: Redshift Copy Command is used to pull the Data from S3 Bucket to Staging tables "STG_EVENT","STG_SONG" on Redshift Database.Redshift Copy Command make use of File partitioning and parallel load the files to the tables.

### b.Populating the DWH Model:
ETL Inserts are used to populate the Dimensional Model Fact and Dimensions.Upsert technique implemented by procedural begin end transaction block on Redshift.This is used when populating the dimensions so that to avoid duplicates.




