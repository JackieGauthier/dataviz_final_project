# Data Visualization 

> Jacqueline Gauthier 

## Mini-Project 1: name of project


Motivation:

This visualization project aims to raise awareness about water pollution in the United States by visualizing data on water releases by industrial facilities. I was motivated to complete this project because I am interested in protecting the environment and I am worried about pollution. It uncovers patterns and trends in the data, highlighting variations across different geographic areas.


Dataset:
The data was downloaded from https://www.propublica.org/datastore/dataset/toxic-air-pollution-hot-spots and put into my data folder.

Data Summary:

FacilityID: Unique identifier for each facility in the Toxic Release Inventory (TRI).
FacilityNumber: Internal identifier unique to each facility.
FRSID: EPA's Facility Registry System (FRS) ID.
Latitude/Longitude: Geographic coordinates of the facility.
GridCode/X/Y: Grid-based location identifiers.
LatLongSource/LLYear/LLNotes: Information about the source and reliability of latitude and longitude data.
RadialDistance: Distance from the approximate center point of the grid.
FacilityName/Street/City/County/State/ZIPCode: Details about the facility's location.
FIPS/STFIPS: Federal Information Processing Standard codes for county and state identification.
DUNS/ParentDUNS/ParentName/StandardizedParentCompany: Business identification details.
Region: EPA region where the facility is located.
FederalFacilityFlag/FederalAgencyName: Federal status and agency details.
PublicContactName/Phone/Extension/Email: Contact information for public inquiries.
StackHeight/Velocity/Diameter/Temperature: Parameters related to facility emissions.
StackHeightSource/StackVelocitySource/StackDiameterSource/StackTemperatureSource: Sources of information for stack parameters.
StackHeightNEIYear/StackVelocityNEIYear/StackDiameterNEIYear/StackTemperatureNEIYear: National Emissions Inventory version years for stack parameters.
ChromHexPercent/ChromSource: Chromium release details.
NewIndustryFlag/ModeledNAICS/NAICSCode3-6Digit: Industry classification details.
FinalReach/FinalCOMID/ReachSource/DistanceToReach: Information about water discharge reaches and distances.
HEM3ID/DistanceToHEM3: National Weather Service station identifiers and distances.
LLConfirmed/WaterReleases/ModeledReleases/ModChromReleases: Flags indicating confirmed location, water releases, and modeled data.



Project Structure:
dataviz_mini-project_01/
|- dataviz_mini-project_01.Rproj
|- data/
|--- facilities_for_data_store.csv
|--- hotspot_perimeters_for_data_store.geojson
|--- hotspot_gridsquares_for_data_store.geojson
|--- toxmaps_data_dictionaries
|- report/
|--- rsa_analysis_data_viz.nb.Rmd
|--- rsa_analysis_data_viz.nb.html 
|- README.md


