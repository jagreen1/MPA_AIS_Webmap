# MPA_AIS_Webmap
# Baltic Marine Protected Area and Near-Realtime Marine Vessel AIS Webmap:
[Baltic Sea Near-Realtime Marine Vessel Activity Webmap](https://jagreen1.github.io/MPA_AIS_Webmap/Baltic_AIS_Webmap_Final.html) <br>

This webmap displays Marine Protecta Area (MPA) and near-realtime marine vessel AIS position/activity information throughout the Baltic Sea. 

Automatic Identification System (AIS) is automatic marine vessel tracking system used for collision avoidance, identification and location and activity information. Vessels equipped with AIS transponders/transceivers and VHF Radio automatically broadcast information at regular intervals.
AIS provide information such as unique identification (ex. Maritime Mobile Service Identity (MMSI)), position (GPS), navigational status (NavStat), course, heading, and speed. This navigation and traffic information acts in complement of marine radar.
Ships equipped with AIS transceivers can be tracked by coastal AIS base stations or by AIS satellites. Satellite AIS (S-AIS) is used to tracks the location of vessels out in the open oceans and far away from terrestrial-based AIS systems.

**Examples of Satellite-based AIS:**

Country | Insitution/Organization/Company | Satellite/Constellation
------------- | ------------ | -------------
Canada | exactEarth/L3Harris Corporation | Iridium NEXT Satellite Constellation
Denmark | Aalborg University/Danish Maritime Safety Administration| AAUSAT3
India | Indian Space Research Organisation | Resourcesat-2
Luxembourg|Luxspace/ORBCOMM |  VesselSat-1 & VesselSat-2
Norway| Kongsberg Seatex| AISSat-1
United States| ORBCOMM| ORBCOMM Generation 2 Satellite Constellation
United States| SpaceQuest | AprizeSat-3 & AprizeSat-4

## Project Development: 
Locating openly avaliable AIS data proved incredibly challenging. I realize I had been niave in thinking that AIS data would be made freely avalaible. There are a plethora of companies and networks with AIS data APIs, however access must be purchased through api credits/substrictions or require setting up and providing your own AIS data to a network.
The original plan of this project was to use AIS data to monitor near-real time marine vessel activity around Marine Protected Areas in the Indo-pacific. Illegal fishing and resource extraction activities (net/explosive/cyanide fishing, coral mining, mangrove cutting) within marine protected areas (MPAs) are significant issue althroughout the Indo-pacific. Illegal fishing vessels (primarily chinese) often try to hide their activities by turning off AIS systems. AIS and satellite monitoring are often used to track illegal fishing vessels.
Unfortunately, none of the various Global AIS data products are freely avaliable. After considerable searching I identified open acess AIS data for marine vessels in the Baltic Sea, and transitions the focus of this map to the Baltic Region. If given access to any of the global AIS data products, this webmap can easily map any other part of the world just by modfying the input geojson api url.


## Webmap Screenshot:
![Example Map Screenshot]()

## Mapbox Studio Style:
[Custom Map Style](https://jagreen1.github.io/MonarchButterflyWebMap/Minimalist-Environmental_Style.json) <br>
This map features a custom map style that was developed in Mapbox Studio and downloaded as a json file.

## Data: 
*Note: All data is in WGS84 GCS.*

<ins>AIS Data:</ins> <br>
Open source AIS information for the Baltic Region was obtain from the Finish transporation company Fintraffic.

Fintraffic Website: ttps://www.digitraffic.fi/

Fintraffic Marine Data Products: https://www.digitraffic.fi/meriliikenne/

Fintraffic Near-Realtime AIS Data API: https://meri.digitraffic.fi/api/v1/locations/latest <br>


<ins>MPA Data:</ins> <br>
Marine Protected Area GIS data was sourced from the World Database on Protected Areas (WDPA), the most comprehensive global database of terrestrial and marine protected areas.
A 1.3Gb shapefile of all Global Protected Areas was obtained from the WDPA website. In QGIS I selected the subset of all protected areas within the Baltic Region, and exported them into their own feature collection. As the WDPAI dataset is a combition of marine and terrestrial protected areas, I made sure to filter out all of the fully terrestrial protected areas. Next, I reduced the size of the file by simplified the coordinate precision by truncating the Lat/Long coordinate values from 15 to 8 decimal places. I also removed all attribute fields that were not going to be displayed in the map. Finally, this dataset was exported to GeoJson and uploaded to GitHub. <br>

The World Database on Protected Areas (WDPA): https://www.protectedplanet.net/en/thematic-areas/wdpa?tab=WDPA <br>
Baltic Sea MPA Geojson Dataset - [Geojson Feature Collection](https://raw.githubusercontent.com/jagreen1/MPA_AIS_Webmap/master/Baltic_MPA.geojson) <br>

<ins>Map Icons:</ins> <br>

Clustered Ship Icons:
<img src="https://cdn2.iconfinder.com/data/icons/maps-and-navigation-glyph-1/128/41-512.png" height="40" width="40">

Unclustered (Color-Coded) Ship Icons:
![Yellow Ship](https://jagreen1.github.io/MPA_AIS_Webmap/yellow_ship.png)
![Dark Purple Ship](https://jagreen1.github.io/MPA_AIS_Webmap/dark_purple_ship.png)
![Yellow Green Ship](https://jagreen1.github.io/MPA_AIS_Webmap/yellow-green_ship.png)
![Red Ship](https://jagreen1.github.io/MPA_AIS_Webmap/red_ship.png)
![Orange Ship](https://jagreen1.github.io/MPA_AIS_Webmap/orange_ship.png)
![Purple Ship](https://jagreen1.github.io/MPA_AIS_Webmap/purple_ship.png)
![Blue Ship](https://jagreen1.github.io/MPA_AIS_Webmap/blue_ship.png)

## Reflective analysis:




## Critique Session: 

