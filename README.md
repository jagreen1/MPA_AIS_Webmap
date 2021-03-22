# MPA_AIS_Webmap
# Baltic Marine Protected Area and Marine Vessel AIS Webmap:
[Baltic Sea Near-Realtime Marine Vessel Activity Webmap](https://jagreen1.github.io/MPA_AIS_Webmap/Baltic_AIS_Webmap_Final.html) <br>

This webmap displays near-realtime information about 

Automatic Identification System (AIS) is automatic marine vessel tracking system used for collision avoidance, identification and location and activity information. Vessels equipped with AIS transponders/transceivers and VHF Radio automatically broadcast information at regular intervals.
AIS provide information such as unique identification (ex. Maritime Mobile Service Identity (MMSI)), position (GPS), navigational status (NavStat), course, heading, and speed. This navigation and traffic information acts in complement of marine radar.
Ships equipped with AIS transceivers can be tracked by coastal AIS base stations or by AIS satellites. Satellite AIS (S-AIS) is used to tracks the location of vessels out in the open oceans and far away from terrestrial-based AIS systems.

**Examples of Satellite-based AIS:**

Canada
exactEarth/L3Harris Corporation
- Iridium NEXT Satellite Constellation

Denmark
Aalborg University/Danish Maritime Safety Administration
- AAUSAT3

India
Indian Space Research Organisation
- Resourcesat-2 (contains a S-AIS payload)

Luxembourg
Luxspace/ORBCOMM  
- VesselSat-1
- VesselSat-2

Norway
Kongsberg Seatex
- AISSat-1

United States
ORBCOMM
- ORBCOMM Generation 2 Satellites

United States
SpaceQuest
- AprizeSat-3
- AprizeSat-4

## Project Development: 
Locating openly avaliable AIS data proved incredibly challenging. I realize I had been niave in thinking that AIS data would be made freely avalaible. There are a plethora of companies and networks with AIS data APIs, however access must be purchased through api credits/substrictions or require setting up and providing your own AIS data to a network.
The original plan of this project was to use AIS data to monitor near-real time marine vessel activity around Marine Protected Areas in the Indo-pacific. Illegal fishing and resource extraction activities (net/explosive/cyanide fishing, coral mining, mangrove cutting) within marine protected areas (MPAs) are significant issue althroughout the Indo-pacific. Illegal fishing vessels (primarily chinese) often try to hide their activities by turning off AIS systems. AIS and satellite monitoring are often used to track illegal fishing vessels.
Unfortunately, none of the various Global AIS data products are freely avaliable. After considerable searching I identified open acess AIS data for marine vessels in the Baltic Sea, and transitions the focus of this map to the Baltic Region. If given access to any of the global AIS data products, this webmap can easily map any other part of the world just by modfying the input geojson api url.


## Webmap Screenshot:
![Example Map Screenshot](https://jagreen1.github.io/MonarchButterflyWebMap/Example_WebMap_Screenshot.PNG)

## Mapbox Studio Style:
[Custom Map Style](https://jagreen1.github.io/MonarchButterflyWebMap/Minimalist-Environmental_Style.json) <br>
This map features a custom map style that was developed in Mapbox Studio and downloaded as a json file.

## Data: 
Data Source - [Journey North Migration Data](https://journeynorth.org/sightings/querylist.html?season=fall&map=monarch-adult-fall&year=2018&submit=View+Data)<br>
Monarch Sighting Geojson Data - [Geojson Feature Collection](https://jagreen1.github.io/MonarchButterflyWebMap/2018MonarchSightings.geojson)<br>

Data for 2018 adult monarch butterfly sightings was obtained from the [Journey North' citizen science website](https://journeynorth.org/sightings/querylist.html?season=fall&map=monarch-adult-fall&year=2018&submit=View+Data). Data from public reported sightings between August 1, 2018 and December 31, 2018 were entered into a csv file. The data was then converted into a [geojson feature collection](https://jagreen1.github.io/MonarchButterflyWebMap/2018MonarchSightings.geojson) following the WGS84 GCS, using the Open Data Institute's 'CSV to GeoJSON' webtool. 

[Monarch Butterfly Image](https://www.hiclipart.com/free-transparent-background-png-clipart-qdsai) <br>
The copyright-free monarch butterfly image used to represent the data points was obtained from (https://www.hiclipart.com). <br>


<ins>AIS Data:</ins>
Open source AIS information for the Baltic Region was obtain from the Finish transporation company Fintraffic.

Fintraffic Website: ttps://www.digitraffic.fi/

Fintraffic Marine Data Products: https://www.digitraffic.fi/meriliikenne/

Fintraffic Near-Realtime AIS Data API: https://meri.digitraffic.fi/api/v1/locations/latest


<ins>MPA Data:</ins>
Marine Protected Area GIS data was sourced from the World Database on Protected Areas (WDPA), the most comprehensive global database of terrestrial and marine protected areas.
A 1.3Gb shapefile of all Global Protected Areas was obtained from the WDPA website. In QGIS I selected the subset of all protected areas within the Baltic Region, and exported them into their own feature collection. As the WDPAI dataset is a combition of marine and terrestrial protected areas, I made sure to filter out all of the fully terrestrial protected areas. Next, I reduced the size of the file by simplified the coordinate precision by truncating the Lat/Long coordinate values from 15 to 8 decimal places. I also removed all attribute fields that were not going to be displayed in the map. Finally, this dataset was exported to GeoJson and uploaded to GitHub. 

The World Database on Protected Areas (WDPA): https://www.protectedplanet.net/en/thematic-areas/wdpa?tab=WDPA
Baltic Sea MPA Geojson Dataset - [Geojson Feature Collection](https://jagreen1.github.io/MPA_AIS_Webmap/Baltic_MPA.geojson)


*Note: All data in this WebMap are in WGS84 GCS.*

## Reflective analysis:




## Critique Session: 

