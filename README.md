# Data Pipeline

To prepare data for our [industry impact page](https://model.earth/localsite/info/), we'll be using [GitHub Actions](/community/projects/#github-actions) and two processes that estimate gaps in census employment data: Eckert Linear Objective Functions and Machine Learning.  


[Using Machine Learning for Census Business Data Gaps](research)
We process local NAICS industry lists into:
1. [State files with county employment levels](https://github.com/modelearth/community-data/tree/master/us/state) 
2. [Zipcode files with employment levels](https://github.com/modelearth/community-data/tree/master/us/zipcodes/naics) 
3. [International trade](international)  

The local industry lists are loaded in the browser (client-side) to filter [US EPA Industry Input-Output Charts](../../../io/charts/) which use [static JSON USEEIO impact data](https://github.com/modelearth/io/tree/main/build/api).  

**Our NAICS pipeline**
1. [Generate state county files](https://github.com/modelearth/community-data) for 2 to 6 digit NAICS industries for static hosting on Github.  
To avoid gaps in county industry data, we'll use this [2018 data from Eckert](https://github.com/modelearth/community-data/tree/master/process/cbp).  
2. Compare with output from our [Machine Learning script](research).  
3. Our **[new comparison report](/localsite/info/naics/)** updates our [EPA Local Industries Impact Report](../../info/).  
4. We're also working with [Commodity Flow Survey (CFS)](https://github.com/modelearth/commodity-flow-survey) NAICS data.

Data source: US Bureau of Labor Statistics (BLS)
Our older links: [Industries by county](https://github.com/modelearth/community-data/tree/master/us/state) | [Industries by zipcode](../../../community/industries/)  
[Samples of Merging Input-Output Data for Totals](totals) | [WebStorm Notes](https://docs.google.com/document/d/1BKxx5Q5rtNgZ9cD-Hsgdi_nEL1YPCfPhKjbnIqMgCRI/edit?usp=sharing)

<!--
[Embeddable IO Widgets](../../charts) use the [static JSON files](https://github.com/modelearth/io/tree/main/build/api) output from the [USEEIO API](https://github.com/USEPA/USEEIO_API/wiki).
We recommend that you work in [USEEIO-widgets repo](../../charts) if you are interested in interacting with the API data.
-->


## Community Data File Format

Our NAICS county CSV files have the following columns - [Sample File](https://github.com/modelearth/community-data/blob/master/us/zipcodes/naics/3/0/3/1/8/zipcode30318-census-naics6-2018.csv)<!--[Sample File](https://github.com/modelearth/community-data/blob/master/us/state/GA/naics/GA_data_filled.csv)-->  

**In File Name**
- Zip, FIPS (5-digit state-county ID) or CountryCode (3-characters)  
- NaicsLevel - ActivityProducedBy (6-digit naics)  

**Columns**
- Naics - ActivityProducedBy (6-digit naics)  
- Establishments - Other (Number of Extablishments)  
- Employees - Employment FlowAmount (Number of Employees)  
- Payroll - US Dollars (Annual Wages)
- Population - Included with our Machine Learning output
<br>


# US Data Sources

BLS, EPA's USEEIO and Flowsa (BEA, Energy, Water, more)

## US Census - County Business Patterns (CBP)


## US Bureau of Labor Statistics (BLS)

<!--
Quarterly Census of Employment and Wages (QCEW) - Includes Latitude and Longitude of establishments
-->

## US Census - Quarterly Workforce Indicators (QWI)

Used by [Drawdown Georgia](https://cepl.gatech.edu/projects/Drawdown-Georgia) - [Emissions Dashboard](https://drawdownga.gatech.edu/) for 3-digit NAICS

<a href="https://www.census.gov/data/developers/data-sets/qwi.html">Quarterly Workforce Indicators (QWI)</a>  
[QWI provides 2, 3 and 4 digit NAICS Industries](https://lehd.ces.census.gov/data/schema/latest/lehd_public_use_schema.html#_industry)

<!--
We may combine QWI data with BLS data to estimate 6-digit naics employment and payroll based on the number of firms in a county and additional county attributes.
-->

<!--
* [US Department of Commerce](https://github.com/USEPA/flowsa/wiki/Available-Data#flow-by-activity-datasets)
-->

## US EPA - Flowsa Flow-By-Activity Datasets for USEEIO

[View Ecosystem](../../../io/about/api/) - The US EPA Flowsa data processing library includes:

* [US Bureau of Economic Analysis (BEA)](https://www.bea.gov/data/industries/gross-output-by-industry)
GDP Gross Output, Make Before Redefinitions, Use Before Redefinitions

* [US Bureau of Land Management Public Land Statistics](https://www.blm.gov/about/data/public-land-statistics)

* [Bureau of Labor Statistics Quarterly Census of Employment and Wages](https://www.bls.gov/cew/)  
View our [Flowsa Python scripts](flowsa)

* [Water Withdrawals for the United States](https://pubs.acs.org/doi/abs/10.1021/es903147k?journalCode=esthag)

* [Census Bureau County Business Patterns](https://www.census.gov/programs-surveys/cbp.html)

* [Energy Information Administration - Energy Consumption Survey](https://www.eia.gov/consumption/)
[Manufacturing](https://www.eia.gov/consumption/manufacturing/), [Commercial Buildings](https://www.eia.gov/consumption/commercial/) - Land, Water, Energy - County, Regional and National

* [Inventory of U.S. Greenhouse Gas Emissions and Sinks](https://www.epa.gov/ghgemissions/inventory-us-greenhouse-gas-emissions-and-sinks)

* [Environmental Protection Agency National Emissions Inventory](https://www.epa.gov/air-emissions-inventories/national-emissions-inventory-nei)

* [More Flowsa data sources...](https://github.com/USEPA/flowsa/wiki/Available-Data#flow-by-activity-datasets) 

<br>


# Display Datasets


#### Embeddable Datasets
<!-- ../#mapview=country -->
[Beyond Carbon State Map](../../../apps/beyondcarbon/#mapview=state) - More embedding samples: [Community Pages](../../../apps)

[Impact Charts](../../../io/charts/) - US Environmentally-Extended Input-Output (USEEIO) - Goods and Services 

[Impact Profiles](../../../io/template/) - Using Environmental Product Declarations (EPDs)


#### Data Sources and Prep

[Community Datasets](https://github.com/modelearth/community-data/) - NAICS Industry Data with Gaps Filled  

[Machine Learning Algorithms for NAICS industries](https://github.com/modelearth/machine-learning/) - US Bureau of Labor Statistics (BLS)

[Impact Heatmap from JSON](/io/build/sector_list.html?view=mosaic&count=50) - [Earlier Goods and Service Heatmap Mockup](../../../community/start/dataset/)


#### Opportunties for further integration

[Google Data Commons Setup](datacommons)  

[DataUSA.io Setup](datausa)  

[Census Reporter](../../../community/resources/censusreporter/)
<!--

[EPA Flowsa Setup](flowsa) - includes U.S. Bureau of Labor Statistics (BLS) industry data  

---
<br>
Are any maps or navigation standards using YAML for layer lists (instead of [json](ga-layers.json)?)  
[YAML Sample](https://nodeca.github.io/js-yaml/) - [Source](https://github.com/nodeca/js-yaml)
-->