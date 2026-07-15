**Kenya's Mobile Money Revolution-Financial Inclusion and Economic Growth**

This project explores how M-Pesa's growth tracks with financial inclusion across Kenya - An end-to-end data pipeline analyzing Kenya's mobile money growth using CBK and World Bank data. This project investigates county level financial inclusion gaps and evaluates how digital transactional infrastructure tracks with macro-level economic indicators.

**Project Overview**

In 2024, KES 8.7 trillion moved through Kenya's mobile money agents- 53% of the country's entire GDP. But that's a national number and it hides a real gap: inclusion isn't even across Kenya's 47 counties. Some, like Nairobi and Kiambu are saturated; others lag far behind. 
Growing up in Kenya using M-Pesa, this isn't just a dataset, it's a lived experience. Kenya is a reference case the rest of the world poitnts to for mobile money and financial inclusion and I want to go past the headline number and actually show where that growth reached people and where it didn't.  
This project builds an automated pipeline that pulls 18 years of Central Bank data(2007-present), the FinAccess county-level survey and World Bank economic indicators transitioning into a data driven narrative by building an automated pipeline that ingests, cleans, tests and models public financial data into interactive, geospatial county by county insights.

**Problem Statement**

Has mobile money's growth in Kenya actually closed the financial inclusion gap, or has it mostly deepened access in places that were already well-served? Answering that today means manually cross-referencing three sources that were never build to talk to each other. This project reconciles them into one queryable warehouse and one dashboard.

**Core Analytical Objectives:**

1. Automatically pull data from CBK, FinAccess and the World Bank instead of collecting it manually.
2. Clean and standardize the three data sources.
3. Keep raw data separate from cleaned data in BigQuery.
4. Growth Trajectory: Track the 20-year scaling velocity of Kenyan mobile money agents, active users and absolute transaction values.
5. Geospatial Equity: Quantify financial inclusion variations across Kenya's 47 counties to map localized infrastructure gaps.
6. Macro Correlation: Evaluate if regional financial inclusion metrics directly correlate with localized Gross County Product(GCP) and national economic growth

**Architecture**


<img width="891" height="262" alt="Architecture drawio" src="https://github.com/user-attachments/assets/3b98dbc4-1a12-46c9-b6c7-1a7b3eee0669" />



**Data Sources**

|Source| What it gives | Coverage|
|---|---|---|
|Central Bank of Kenya|Monthly active agents, transaction volume|2007-present|
|FinAccess Survey|Inclusion rate per county|Survey years only, not monthly|
|World Bank API|GDP, National inclusion indicators|Annual|

**Components**

**Python** - Extraction and Cleaning scripts, one per source before combining.

**Cloud Composer(Airflow)** - Runs the extraction scripts on a schedule instead of me manually re-dowloading CBK's monthly report every month.

**Google cloud storage**- All untouched raw files are stored here first, so I always have the original CBK|FinAccess|World Bank exports as backup.

**BigQuery** - This splits into the three datasets that do each one job.
   - raw_data - One table per source, exactly as extracted.
   - Staging - cleaned views; this is where county names get standardized and dates from three different formats parsed into one.
   - Analytics - The joined, partitioned table the dashboard actually reads from.

**Looker Studio** - Connects only to analytics, never to raw or staging, so the dashboard stays fast.

**What the dashboard shows**

   - Opening stat: The national GDP figure, so the scale is clear before drilling into counties.
   - County Map: Inclusion rate by county - actual findings.
   - 18-year time series : Agent count and transaction volume from near-zero to today.
   - GDP growth overlaid against mobile money growth, to check the correlation.

**Built with**
|Layer|Tool|
|---|---|
|Extraction|Python|
|Scheduling|Airflow|
|Raw storage|Google Cloud Storage|
|Warehouse|Bigquery|
|Dashboard|Looker Studio|
|Version Control|Github|





 
