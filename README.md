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

You will want to think analytically about your data. At this stage you might sort and
format your data to make it easier to perform calculations, combine data from multiple sources and create tables with your results!

Stakeholder Questions :thought_balloon: and Insights Found :test_tube:

- How have greenhouse gas emissions changed since the introduction of EV?

  We see a downward trend for both the sum and average of CO2 emissions across all Vehicle Types since the introduction of EVs in 2012. Even though our number of vehicles in our dataset vary, the trend still continues across the board. 
  
- What is the trend in average GHG emissions per vehicle type for EVs and traditional vehicles since the introduction of EVs?

  Since the introduction of EVs for Sedans/Wagons, we see a 8.21% decrease in average CO2 emissions from 2012 to 2022. When we look at the Total CO2 Emissions for Sedans/Wagons we see 4283.41 g/mi in 2012 compared to 3931.79 g/mi in 2022. The same trend continues for all the vehicle types in our dataset. 
 
- How does the adoption of EVs correlate with changes in overall greenhouse gas emissions from the automotive sector?

  It is important to note that EV (Electric Vehicles) do not release CO2 the same way combustions engines do. This is not to say that EV vehicles do not contribute to any CO2 emissions. The production of EV batteries and charging stations do contribute to GHG emissions. In this case, we would need more data for a complete analysis. It is also important to point out that other factors like advancements in fuel efficiency, changes in driving patterns and shifts in consumer preferences can all play a role in changes in CO2 emissions from gasoline vehicles. 
 
- Are there any significant differences in emission trends among different vehicle types when comparing EVs to traditional vehicles?

  While it's evident that there's a downward trend in emissions across various vehicle types, it's important to note that the comparison between EVs and traditional vehicles requires additional data. This is because EVs do not produce greenhouse gas emissions in the same manner as traditional combustion engines. Therefore, a comprehensive understanding of emission trends among different vehicle types necessitates a more thorough analysis, taking into account the unique emission profiles of EVs and traditional vehicles.

  With the data we have and to ensure consistency, we used a sample size of 305 vehicles per vehicle type. From our random samples, we see that Pickups have contributed the most CO2 emissions at a total of 150,333.18 g/mi. while Sedan/Wagons contribute the least at a total of 110,144.19 g/mi. 

- Are electric vehicles (EVs) more fuel-efficient compared to traditional internal combustion engine vehicles across different vehicle types (SUVs, Trucks, Sedans, etc.) and manufacturers?

  Note that EVs rely solely on battery power in order to get from point A to point B. Although they don’t rely on ‘gallons’, the term (MPG or MPGe) is used as a unit of measurement in the US, Canada and the UK while other countries use Kilometers per liter (km/L). Perhaps in the future when EVs become the norm, we will develop a new term to better represent their range efficiency.

  From our analysis, we can see that EVs are definitely more efficient. In our dataset the lowest EVs MPG range was 89.14 MPG, and has only gone up from there over the years to a Max of 129.83 MPG. If we compare this to the Max MPG of traditional vehicles we get 38.49 MPG, while the minimum goes down to 8.99 MPG. When we look across different vehicle type, we can see that Pickups are the least fuel efficient at an average of 18.59 MPG, while Sedans/Wagons hold the highest average at 24.65 MPG. 

- How does fuel economy of EVs compare to that of traditional vehicles within each vehicle type and across different manufacturers? Which vehicle types and manufacturers produce the most fuel-efficient vehicles, and are there any notable differences in fuel efficiency trends between EVs and traditional vehicles?

  Like stated earlier and with our data, we see EVs have the best fuel economy compared to traditional vehicles regardless of its vehicle type. Smaller vehicles reign supreme with the best fuel efficeincy for EVs. While Sedans/Wagons have the best avg fuel economy for traditional vehicles, Pickups have the worst. Across different manufacturers the best traditional vehicle average is held by Hyundai at 24.65 MPG. The worst is held by the multi-brand manufacturer Stellantis at 28.57 MPG. 

- What factors contribute to variations in fuel efficiency among different vehicle types and manufacturers?

  One significant factor contributing to variations in fuel efficiency is the vehicle's footprint (measured in square feet). The footprint describes the physical dimensions of a vehicle and can provide insights. For instance, pickups typically have poorer fuel efficiency compared to sedans and wagons due in part to their larger average footprint. According to our dataset, pickups have an average footprint of 62.43 square feet, whereas sedans and wagons have an average footprint of 46.34 square feet.

  Another factor influencing fuel efficiency is advancements in technology. Over time, improvements in fuel efficiency technology have led to better miles per gallon. We see an average of 20.19 MPG across all vehicles since 1975 to 2000. Meanwhile from 2001 to 2022 we have an average of 24.53 MPG. Clearly  proving that fuel efficiency has increased due to advancements in tech. 


## 5. Share




## 6. Act
