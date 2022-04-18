Summary
In 2015, a large Harmful Algal Bloom event known as "the Blob" led to the closure of Dungeness Crab fisheries in the coastal states of Washington, Oregon, and California. Other related events were increased deaths of seabirds, marine mammals, other local fish species. Harmful Algal Bloom events are characterized by rapid growth, followed by rapid decay of aquatic cyanobacteria. This rapid change in biomass has ecological impacts on the ecosystem, with the potential for human health risks. In the case of California, the most common Harmful Algal Bloom species group is Pseudo-nitzchia. A byproduct of rapid growth and decay of Pseudo-nitzchia is domoic acid, which is known to cause death in marine mammals and birds. It is also the cause of Amensic Shellfish poisoning in humans, as domoic acid is a biotoxin that accumulates in fish and shellfish. 

With recent climate change and nutrient pollution issues, Harmful Algal Blooms have become recognized as a national threat by Congress (HABHRCA 2018). Following the Blob event of 2015, NOAA has conducted many socio-economic and socio-cultural studies about the impacts of Harmful Algal Blooms on West Coast fishing communities. Given the importance of Harmful Algal Blooms, we develop two research questions: 1) what chemical, geographical, and physical factors set the stage for harmful algal bloom events, 2) are harmful algal blooms increasing over time.

Investigators
Curtis Cha & Bryce O'Brien, MEM Candidates - CEM Concentration, EDA Spring 2022

Keywords
Harmful Algal Blooms, Southern California, Pseudo-nitzschia, Alexandrium

Database Information

The raw data used to to answer the two research questions are sourced from the regional HAB monitoring system of Southern California, which is managed by the Southern California Coastal Ocean Observing System. At five locations, weekly sampling is conducted to measure concentrations of different nutrients, sea surface temperature, salinity, and several algae species. Two specific raw files are taken from this source, HAB Occurrences and Water Quality, and processed into hab_occ_processed and water_qual_procesed. Combining these processed two data sets produces the processed data set "hab_occ_wq", which lists the response variables and explanatory variables for each sampling event. 

Linear models were produced and used to create two csv's "AL_LM_Coefficient_Cities" and "PN_LM_Coefficient_Cities".

Folder Structure 

This repository contains the following two files; HABS_Final_Report.rmd and Data. The Data Folder is further split into three folders: Output, Processed, and Raw. The Raw Folder contains two csv files: hab_occ_raw and water_qual_raw. The Processed Folder contains three csv files: hab_occ_processed, water_qual_processed, and hab_occ_wq. The Output Folder contains two .csv's and two .png's, "AL_LM_Coefficients_Cities.csv", "PN_LM_Coefficients_Cities", "Alexandrium Over Time", and "Pseudo-nitzchia Over Time".

Metadata

hab_occ_raw: File contains biological data on samples
- Columns:
  -- id: sample id with location and time
  -- basisOfRecord: method of sampling
  -- occurenceID: sample id with location, time, and algal species measured
  -- organismQuantity: number of cells/L
  -- organismQuantityType: unit of measurement
  -- occurrenceStatus: algal presence or absence
  -- organismName: name of algae
  -- eventID: sampleID
  -- taxonID: ID of algae in algaebase.org
  -- scientificNameID: ID of algae in marinespecies.org
  -- scientificName: scientific name of algae
  -- kingdom: kingdom of algea

water_quality: File contains chemical and physical data on samples
  -- id	: sample ID 
  -- measurementID : sample ID with measurement type
  -- measurementType : type of measurement
  -- measurementTypeID : link to measurement type in NERC server
  -- measurementValue	: amount measured
  -- measurementUnit : unit of measurement
  -- measurementUnitID : NA
  
hab_occ_processed: processed form of hab_occ_raw
  -- id: sample ID
  -- Akashiwo sanguinea ( cells/L ): measurement value of algal species
  -- Alexandrium ( cells/L ): measurement value of algal species
  -- Dinophysis ( cells/L ): measurement value of algal species	
  -- Lingulodinium polyedra ( cells/L ): measurement value of algal species	
  -- Pseudo-nitzschia delicatissima ( cells/L ): measurement value of algal species	
  -- Pseudo-nitzschia seriata ( cells/L ): measurement value of algal species
  
water_quality_processed: processed form of water_quality_raw
  -- id: sample ID
  -- Ammonium ( uM ): concentration of chemical	     -- Avg_Chloro ( mg/m3 ): mean concentration of chlorophyll
  -- Avg_Phaeo ( mg/m3 ): mean concentration of phaeopigment
  -- Chl1 ( mg/m3 ): concentration of chlorophyll
  -- Chl2 ( mg/m3 ): concentration of chlorophyll
  -- Nitrate ( uM ): concentration of nutrient
  -- Nitrite ( uM ): concentration of nutrient
  -- Nitrite_Nitrate ( uM ): concentration of nutrient
  -- pDA ( ng/mL ): concentration of domoic acid	 
  -- Phaeo1 ( mg/m3 ): concentration of chemical
  -- Phaeo2 ( mg/m3 ): concentration of chemical
  -- Phosphate ( uM ): concentration of nutrient
  -- Silicate ( uM ): concentration of nutrient
  -- Temp ( Celsius ): measurement of temperature
  -- Salinity ( PSS ): measuremtn of salinity

hab_occ_wq: output of merging hab_occ_processed and water_qual_processed, for a given sample, there is biological, chemical, and physical data

  -- id: sample ID
  -- Alexandrium ( cells/L ): concentration of algae species
  -- Pseudo-nitzschia seriata ( cells/L ): concentration of algae species
  -- Ammonium ( uM ):	concentration of nutrient
  -- Nitrate ( uM ): concentration of nutrient
  -- Nitrite ( uM ): concentration of nutrient
  -- Phosphate ( uM ): concentration of nutrient
  -- Silicate ( uM ): concentration of nutrient
  -- Temp ( Celsius ): measure of temperature
  -- locationID: location of sample
  -- eventDate: date of sample

AL_LM_Coefficients_Cities: for the algae species group Alexandrium, at each sample location, there is a linear regression model predicting algae concentration from the variables in hab_occ_wq. Each row represents one linear model at a given sample location

  -- Site: sampling location of linear model
  -- NH4: coefficient of variable
  -- NO2: coefficient of variable
  -- NO3: coefficient of variable
  -- SiO3: coefficient of variable
  -- PO4: coefficient of variable
  -- Month: coefficient of variable
  -- Year: coefficient of variable
  -- R-sq.: r-squared value of linear 
  
PN_LM_Coefficients_Cities: for the algae species group Pseudo-nitzchia, at each sample location, there is a linear regression model predicting algae concentration from the variables in hab_occ_wq. Each row represents one linear model at a given sample location.

  -- Site: sampling location of linear model
  -- NH4: coefficient of variable
  -- NO2: coefficient of variable
  -- NO3: coefficient of variable
  -- SiO3: coefficient of variable
  -- PO4: coefficient of variable
  -- Month: coefficient of variable
  -- Year: coefficient of variable
  -- R-sq.: r-squared value of linear 

Scripts/Code




QA/QC

One major issue with this data set is the presence of NA's for biologica, chemical, and physical measurements. There are several periods of times where samples lack any data for certain features such as algal concentrations for one species or nutrient concentrations. 

To assure quality in answering our research questions, two specific algal species were selected as response variables and certain environmental variables were selected as explanatory variables. For determining the linear relationship between algae and their local environment, NA's were dropped from the data set. For conducting a time series analysis, the NA's in nutrient concentrations and Sea Surface Temperature were filled in using extrapolation. One fallback to using extrapolation is filling in NA's using a linear approximation, when certain nutrients could follow a non-linear trend due to a human pollution event. Assuming certain events are recorded in the data, extrapolation is justified as nutrients take time to disperse and temperature rises and decreases in increments.

.