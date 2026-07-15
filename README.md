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



[Uploadin<mxfile host="app.diagrams.net">
  <diagram name="Page-1" id="sGXEQiTs38_PxsY-nEmu">
    <mxGraphModel dx="774" dy="498" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="850" pageHeight="1100" math="0" shadow="0">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        <mxCell id="2cEXos8URo4YvycPx09E-31" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-1" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;entryX=0.5;entryY=0;entryDx=0;entryDy=0;" target="2cEXos8URo4YvycPx09E-9">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-1" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="Central Bank of Kenya" vertex="1">
          <mxGeometry height="60" width="120" x="40" y="80" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-10" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-2" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" target="2cEXos8URo4YvycPx09E-9" value="">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-2" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="CBK FinAccess Survey" vertex="1">
          <mxGeometry height="60" width="120" x="40" y="180" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-26" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-3" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;entryX=0.5;entryY=1;entryDx=0;entryDy=0;" target="2cEXos8URo4YvycPx09E-9">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-3" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="World Bank API" vertex="1">
          <mxGeometry height="60" width="120" x="40" y="280" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-16" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-9" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" target="2cEXos8URo4YvycPx09E-15" value="">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-9" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="Cloud Storage&lt;br&gt;&lt;div&gt;BigQuery&lt;/div&gt;" vertex="1">
          <mxGeometry height="60" width="120" x="200" y="180" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-18" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-15" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" target="2cEXos8URo4YvycPx09E-17" value="">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-15" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="BigQuery:&lt;div&gt;Raw_Data&lt;/div&gt;" vertex="1">
          <mxGeometry height="60" width="120" x="360" y="180" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-20" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-17" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" target="2cEXos8URo4YvycPx09E-19" value="">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-17" parent="1" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#d5e8d4;strokeColor=#82b366;" value="&lt;div&gt;BigQuery:&lt;/div&gt;&lt;div&gt;Staging&lt;/div&gt;" vertex="1">
          <mxGeometry height="80" width="90" x="520" y="170" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-22" edge="1" parent="1" source="2cEXos8URo4YvycPx09E-19" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" value="">
          <mxGeometry relative="1" as="geometry">
            <mxPoint x="810" y="210" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-19" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="BigQuery:&lt;div&gt;Analytics&lt;/div&gt;" vertex="1">
          <mxGeometry height="60" width="120" x="650" y="180" as="geometry" />
        </mxCell>
        <mxCell id="2cEXos8URo4YvycPx09E-32" parent="1" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" value="Looker Studio Dashboard" vertex="1">
          <mxGeometry height="60" width="120" x="810" y="180" as="geometry" />
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
g Architecture (1).drawio…]()

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





 
