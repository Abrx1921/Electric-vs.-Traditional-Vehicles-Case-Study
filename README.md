# Case Study: Electric vs. Traditional Vehicles CO2 Emissions and Fuel Efficiency 
**Excel + SQL + Tableau Data Analysis Project**

**Author: Abraham Saenz Sigala**

**Date: May 4, 2024**

[Tableau Dashboard](https://public.tableau.com/app/profile/abraham.saenz.sigala/viz/GHGEmissionsandFuelEfficiencyDashboard/DashboardGHGandFuelEfficiency)

[Tableau Stakeholder Presentation](https://public.tableau.com/app/profile/abraham.saenz.sigala/viz/GHGandFuelEfficiencyPresentation/PresentationGHGandFuelEfficiencyPresentation)

##

### The Phases of Data Analysis

#### 1. Ask :thought_balloon:

#### 2. Prepare :package:

#### 3. Process :soap:

#### 4. Analyze :test_tube:

#### 5. Share :bar_chart:

#### 6. Act :clapper:

### Scenario

The EPA is interested in the possible benefits or disadvantages in Electric vs. Traditional Combustion Vehicles. They want to know about CO2 emissions and Fuel Efficiency between different manufacturers in order to implement stricter regulations and incentivise the production of eviormentaly friendly vehicles. Consumers are also interested in which vehicles are in their best interest (fuel efficient) when inquiring about different vehicle types and manufacturers. Your team wants to find insights for your stakeholders inorder to aid in the reduction of green house gas emissions and increased fuel efficiency. 

## 1. Ask

It's impossible to solve a problem if you don’t know what it is. Ask Questions!

:flashlight: **Business Task: Analyze EPA Dataset to discover insights about Electric vs. Traditional Vehicles GHG Emissions and Fuel Efficiency**

Primary Stakeholders: 

Enviromental Protection Agency (EPA): Organization Responsible for monitoring and regulating vehicle emissions, the EPA has a vested interest in understanding the enviormental impact of electric and traditional vehicles on GHG emissions.

Secondary Stakeholders: 

Consumers: Interested in understanding the enviormental impact of their vehicle choices and the fuel efficiency performance of different vehicle types and manufacturers. 

## 2. Prepare

Decide what data you need to collect in order to answer your questions. 

[Data Source](https://catalog.data.gov/dataset/the-epa-automotive-trends-report-greenhouse-gas-emissions-fuel-economy-and-technology-sinc) and [License](https://edg.epa.gov/EPA_Data_License.html)

The EPA Automotive Trends Report Dataset contains 5,392 rows and 54 columns spanning a 47-year period (1975 to 2022).

:pencil: Data Passes ROCCC Approach:

- Reliability: Annual Report from the U.S. Environmental Protection Agency
- Original:  Includes complete and accurate data about new light-duty vehicle greenhouse gas. 
- Comprehensive: Dataset contains Manufacturer, Model Year, Regulatory Class, Vehicle Type, CO2, MPG, Footprint, Production, Production Share.
- Current: Updated annually to include the most up to date data available for all model years.
- Cited: Intended for public access and use in accordance with the existing license agreement.

:construction: Dataset Limitations:

- All model years from 2023 are preliminary. Meaning models are subject to revisions/adjustments as more accurate and verified info becomes available throughout the year. May not represent the final figures. 
- Dataset is based on production values for vehicles sold in the United States, specific to each model year. It should be noted that this dataset does not encompass global vehicle production. 
- Data is based on lab tests that may not accurately reflect real-world driving conditions and are subject to limitations in accuracy. 
- It is important to note that EV do not release CO2 the same way combustions engines do. This is not to say that EV vehicles do not contribute to any CO2 emissions. The production of EV batteries and charging stations contribute to GHG emissions. In this case, we would need more data for a complete analysis. 
- Note that other factors like advancements in fuel efficiency, changes in driving patterns and shifts in consumer preferences can all play a role in reduction in CO2 emissions from gasoline vehicles overtime.
- The dataset exclusively comprises full electric vehicles (EVs) meeting our analysis criteria, with Tesla being the sole manufacturer included.

## 3. Process

Clean data is the best data. You will need to clean up data to get rid of any errors, inaccuracies, or inconsistencies.

:hammer_and_wrench: Tool: Google Sheets/Excel

:microscope: Examine [EPA Original Dataset](https://docs.google.com/spreadsheets/d/1rBMlYg6ZQNN2H0o_i8nSKf-ulyKhAjj6asA3752hdHk/edit?usp=sharing)

Clean Dataset for Analysis:

- Removed 45 columns that are not necessary for our analysis.
- Rename Columns for clarity
- Removed any Preliminary 2023 years from Model Year column using find and replace since they may not represent final figures.
- Special characters represented by "-" have been replaced with null values in the dataset, accurately reflecting their absence or lack of data. 
- Remove Null Values for MPG since this will be necessary for our analysis and it will also filter out any other null values for C02, Production and Production Share. 
- Round CO2, MPG and Footprint columns to the nearest hundredth. 
- Delete any rows that have a Production and Production Share of 0. 
- Identify and remove any duplicates. 
- Cleaned Dataset now contains 9 Columns and 4062 Rows. 
- Prepare the dataset for extraction as a .CSV file and further cleaning and organization in SQL.

:soap: [EPA Cleaned Dataset Spreadsheets](https://docs.google.com/spreadsheets/d/1jSmtlchz_qp5gazKbNC2RV0mAZywj1FEzzAAMoDOwew/edit?usp=sharing)

:hammer_and_wrench: Tool: SQL/BigQuery 

- Upload cleaned dataset to SQL and ensure the schema datatypes are correct.
- Preview the dataset
- Remove/Identify duplicates 
- Identify the different attributes under regulatory class and vehicle types.
- Identify the number of different manufacturers in dataset.
- Identify the number of manufacturers per vehicle type in the dataset

Create multiple tables for streamline a analysis

- Table 1: Create a table filtering for 'All' occurrences in the dataset. 1852 Rows
- Table 2: Create a table for Manufacturers that Omits occurrences in ‘All’. 2209 Rows
- Table 3: Create a table where there is a consistent amount of vehicles per vehicle type (Omit Tesla as it could skew mpg results due to its high mpg)
- Table 4: Create a table where there is a consistent amount of vehicles per vehicle type (Tesla Included)

:soap: [EPA Cleaned Dataset Queries](https://console.cloud.google.com/bigquery?sq=1014993859659:78a48edfd2e5460a8af6d2d12f389c08)

Upload new tables to SQL to begin analysis and answer stakeholder questions

## 4. Analyze





## 5. Share




## 6. Act
