# UrbanCompleteStreetQuality-Woitas

**Project Overview:**

In this project, the "Complete Street Quality" of three primary transit Urban Boulevards in Calgary was assessed. These Urban Boulevards were assessed based on metrics of Walkability, Urban Realm Quality, and Multimodality. These metrics were converted into qualtifiable attributes which include the following: 

Wide Sidewalks (2.5m or more), Complete Walking Connections, Unimpacted Pedestrian Travel, Green Buffering, Integrated Land Use, Dedicated Space for Rapid Transit, and Dedicated Bike Infrastructure. 

The block space of each Urban Boulevard was assessed, and was broken into 0.5m segments for analysis. These segments were then averaged for each criteria to produce a final "Completeness" score. This analysis assesses the sustainability of Calgary based on how well Urban Boulevards are designed to suit the needs of pedestrians, cyclists, and transit users, in addition to how well these streets have been retrofitted to conform to policy guidance.

**Folder Structure:**

Folder Name: Data_Woitas<br>
Data_Raw: contains unprocessed data files used as variables in analysis
- Impervious_Surface_2021<br>

Data_Processed: contains data files that have been filtered for the analysis, and files with new fields added as a result of the analysis

Filtered:<br>
- Buildings<br>
- Trees_Green_Buffer_16th<br>
- Trees_Green_Buffer_17th<br>
- Trees_Green_Buffer_Centre<br>

New:<br>
- Study_Area_16_Ave_NW
- Study_Area_16AVENW_Split
- Study_Area_17_Ave_SE
- Study_Area_17AVESE_Split
- Study_Area_Centre_St_North
- Study_Area_CentreSTN_Split

**Coordinate Reference System:** NAD 1983 3TM 114

**Data Sources:**

City of Calgary. (2016). Calgary Bikeways [Data set]. City of Calgary Open Data Portal. Retrieved September 24, 2025, from
  https://data.calgary.ca/Transportation-Transit/Calgary-Bikeways/jjqk-9b73/about_data
  
City of Calgary. (2018). Public Trees [Data set]. City of Calgary Open Data Portal. Retrieved September 24, 2025, from
  https://data.calgary.ca/Environment/Public-Trees/tfs4-3wwa/about_data
  
City of Calgary. (2020-b). Buildings [Data set]. City of Calgary Open Data Portal. Retrieved September 24, 2025, from
  https://data.calgary.ca/Base-Maps/Buildings/uc4c-6kbd/about_data
  
City of Calgary. (2020-c). Street Centerline [Data set]. City of Calgary Open Data Portal. Retrieved September 24, 2025, from
  https://data.calgary.ca/Transportation-Transit/Street-Centreline/4dx8-rtm5/about_data
  
City of Calgary. (2022). Impervious Surface 2021 [Data set]. City of Calgary Open Data Portal. Retrieved September 24, 2025, from
  https://data.calgary.ca/Environment/Impervious-Surface-2021/rgsu-3v7u/about_data

**Field Descriptions for new files in the Data_Processed folder:**<br>
- Has_MAX_BRT: whether or not a MAX Bus line runs along the road
- SIDEWALK_AREA: area of sidewalk measured within 0.5m segment (metres squared)
- HOV: whether or not the road segment has a marked High Occupancy Vehicle (HOV) lane
- IMPACTED: whether or not the walking segment is impacted by a driveway
- BLOCK_ID: Id of block the segment is associated with (for joining back)
- INTEGRATED_LU: whether or not the segment is associated with integrated land use
- GREEN_BUFFER: whether or not there is a green buffer between the road and walking space adjacent to the segment
- SIDEWALK_WIDTH: mode value of sidewalk width per block (metres)


