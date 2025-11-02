# UrbanCompleteStreetQuality-Woitas

**Project Overview:**

In this project, the "Complete Street Quality" of three primary transit Urban Boulevards in Calgary was assessed. These Urban Boulevards were assessed based on metrics of Walkability, Urban Realm Quality, and Multimodality. These metrics were converted into qualtifiable attributes which include the following: 

Wide Sidewalks (2.5m or more), Complete Walking Connections, Unimpacted Pedestrian Travel, Green Buffering, Integrated Land Use, Dedicated Space for Rapid Transit, and Dedicated Bike Infrastructure. 

The block space of each Urban Boulevard was assessed, and was broken into 0.5m segments for analysis. These segments were then averaged for each criteria to produce a final "Completeness" score. This analysis assesses the sustainability of Calgary based on how well Urban Boulevards are designed to suit the needs of pedestrians, cyclists, and transit users, in addition to how well these streets have been retrofitted to conform to policy guidance.

**Folder Structure:**

Folder Name: Data_Woitas<br>
-> Data_Raw: contains unprocessed data files used as variables in analysis
- Impervious_Surface_2021<br>

-> Data_Processed: contains data files that have been filtered for the analysis, and files with new fields added as a result of the analysis. All CSV files can be converted into feature classes using X/Y fields in the tables.
> Filtered:<br>
> - Buildings: contains building polygons along the three Urban Boulevards<br>
> - Trees_Green_Buffer_16th: point layer for trees acting as green buffers (16th Avenue NW)<br>
> - Trees_Green_Buffer_17th: point layer for trees acting as green buffers (17th Avenue SE)<br>
> - Trees_Green_Buffer_Centre: point layer for trees acting as green buffers (Centre Street North)<br>

> New:<br>
> - Study_Area_16_Ave_NW: (line) represents study area / block faces, contains mode sidewalk width value
> - Study_Area_16AVENW_Split: (line) block faces split into 0.5m segments, contains data on sidewalks, sidewalk impacts, integrated land use, green buffering, and dedicated lanes
> - Study_Area_17_Ave_SE: (line) represents study area / block faces, contains mode sidewalk width value
> - Study_Area_17AVESE_Split: (line) block faces split into 0.5m segments, contains data on sidewalks, sidewalk impacts, integrated land use, green buffering, and dedicated lanes
> - Study_Area_Centre_St_North: (line) represents study area / block faces, contains mode sidewalk width value
> - Study_Area_CentreSTN_Split: (line) block faces split into 0.5m segments, contains data on sidewalks, sidewalk impacts, integrated land use, green buffering, and dedicated lanes

**Field Descriptions for 'New' files in the Data_Processed folder:**<br>
- Has_MAX_BRT: whether or not a MAX Bus line runs along the road
- SIDEWALK_AREA: area of sidewalk measured within 0.5m segment (metres squared)
- HOV: whether or not the road segment has a marked High Occupancy Vehicle (HOV) lane
- IMPACTED: whether or not the walking segment is impacted by a driveway
- BLOCK_ID: Id of block the segment is associated with (for joining back)
- INTEGRATED_LU: whether or not the segment is associated with integrated land use
- GREEN_BUFFER: whether or not there is a green buffer between the road and walking space adjacent to the segment
- SIDEWALK_WIDTH: mode value of sidewalk width per block (metres)
- Shape_Lenth: length (metres)

**Coordinate Reference System:** NAD 1983 3TM 114

**Data Sources / Acknowledgments:**

*All data used for this analysis was taken from the City of Calgary's Open Data Portal*

City of Calgary. (n.d.). City of Calgary’s Open Data Portal. Open Calgary. https://data.calgary.ca/ 

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



**Methods Summary:**
- Wide Sidewalks (2.5m or more): filtered Impervious_Surfaces_2021 to only sidewalks. Buffered the 0.5m segment, used the Summarize Within tool to capture SIDEWALK_AREA. Tied it back to the line segment, and divided SIDEWALK_AREA by Shape_Length to get a sidewalk width. Selected the mode value from each block for most common sidewalk width.
- Complete Walking Connections: based on the same analysis as the previous criteria. Mode sidewalk of zero = incomplete walking connection.
- Unimpacted Pedestrian Travel: highlighted segments where driveways impacted sidewalk based on sattellite imagery, field IMPACTED =  "Yes".
- Green Buffering: used Public_Trees layer and buffered from sidewalk to road segment to select trees acting as green buffers. Copied selected features into a new layer and buffered those points into a polygon. Used buffer from road to determine where GREEN_BUFFER = "Yes".
- Integrated Land Use: Used Buildings layer to indentify buildings along the boulevard, and Impervious_Surfaces_2021 to identify pavevd driving spaces. Buffered from road segment, and used Summarize Within tool on both layers. If only buildings found within buffer, INTEGRATED_LU = "Yes".
- Dedicated Space for Rapid Transit: highlighted segments where dedicated space was found based on sattellite imagery, field HOV =  "Yes".
- Dedicated Bike Infrastructure: used Calgary_Bikeways layer and filtered to "Cycle Tracks". Determined if bikeways and road segment intersected (none did so a new field was not created).
