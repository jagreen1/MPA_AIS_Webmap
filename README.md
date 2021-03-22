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
Locating openly avaliable AIS data proved incredibly challenging. I realize I had been niave in thinking that AIS data would be made freely avalaible. There are a plethora of companies and networks with AIS data APIs, however they can only be accessed through the purchasing of api credits/substrictions, or by providing your own AIS data to a shared network. <br>

The original plan of this project was to use AIS data to monitor near-real time marine vessel activity around Marine Protected Areas in the Indo-pacific. Illegal fishing and resource extraction activities (net/explosive/cyanide fishing, coral mining, mangrove cutting) within marine protected areas (MPAs) are significant issue althroughout the Indo-pacific. Illegal fishing vessels (primarily chinese) often try to hide their activities by turning off AIS systems. AIS and satellite monitoring are often used to track illegal fishing vessels. <br>

Unfortunately, none of the various Global AIS data products are freely avaliable. After considerable searching I identified open acess AIS data for marine vessels in the Baltic Sea, and transitions the focus of this map to the Baltic Region. If given access to any of the global AIS data products, this webmap can easily map any other part of the world just by modfying the input geojson api url.


## Webmap Screenshot:
Example of Clustered Marine Vessels 
<img src="https://raw.githubusercontent.com/jagreen1/MPA_AIS_Webmap/gh-pages/Lab2_Example_Screenshot_Clustered.PNG">

Example of Unclustered Marine Vessels
<img src="https://raw.githubusercontent.com/jagreen1/MPA_AIS_Webmap/gh-pages/Lab2_Example_Screenshot_Unclustered.PNG">


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


decisions/insight

This webmap displays Marine Protecta Area (MPA) and near-realtime marine vessel AIS position/activity information throughout the Baltic Sea. It was designed for European marine traffic regulators and fishery management authorities such as the European Fisheries Control Agency. The objective of the webmap is to present near-real time monitoring of marine vessels to identify ships located in Marine Protected Areas (MPA) in the Baltic Sea. This webmap additionally give information about the navigation status (*NavStat*), helping to understand the a ships current activity and providing context for the location of the vessel. 


Interactivity & Key Map Features

This map was designed such that clustering was a central aspect of visualization. When the map is zoomed out, many of the marine vessels will overlap due to their close proximity. I designed a series of clustering layers such that all ships in a defined radius appear as ship icon, and the total number of ships within that cluster are displayed as a text value in a circle to the top right of the clustered ship icon. As the map is zoomed in and the location of multiple ships no longer fall within overlaping radius they will appear as one of a set different ship icons with various colors.

Clustering can provide an improve viewing experience if the user only wishes to look in a specific area. However, clustering prevents the user from gaining a holistic or big-picture understanding. Therefore, I also created an unclustered layer that can be toggled on to display all ship points at once. I found that this layer was highly valuable in help to visualize marine routes/highways, something that is not expressed in the clustered view.  

Another key aspect of the map is that the ships point in different direction based on their current *heading*. This works by rotating the map's ship icons according to the features' *heading* property. By default, the ship icons point North or 90°. The icons were therefore rotated by *heading* - 90.

The layers toggle button in the upper left-corner of the map allows the user to turn the layeres on and off. When initially loaded only the MPA layer and Clustered Ships grouped layers have layout *visibility* values of "visible", while the Unclusterd Ships layer have a *visibiliity* of "none" and therefore not visible. When one of the three toggle buttons is clicked, the corresponding group of layers have their visibility properties switched; making them appear or disappear. Additionally, the buttons are also highlighted when the mouse moves over them, and change color when clicked or unclicked.

When the clustered ship layers are clicked, the map zooms in and pans to the individual cluster. If the unclustered ship points are clicked a PopUp appears with  key AIS information including: Maritime Mobile Service Identity (MMSI), navigation status (NavStat), vessel heading, position accuracy, and timestamps. A PopUp is also displayed when the Marine Protected Area (MPA) features are clicked, providing information including WDPA parcel id, name, english designation, status, and ISO3 country code.


UI Visuals/Map Style

I created two text boxes for the title/description and the legend. The description box tells the user how to interact with the map, and the legend explains the different NavStat color scheme. These boxes were made to be partially transparent allowing the user to see the map underneath. Making the boxes fully opaque would clash with the underlying map. I choose to place the two text boxes on the right in such a way that they wouldn't take up to much space. The layer toggle button was placed in the upper left-corner as not to busy the right side of the map. I choose to use a light colored basemap that clearly highlights between land and sea. I originally intended on using a high-resolution satellite imagery layer, however the sea/ocean are very dark in satellite imagery which makes it difficult to see the ship icons. I showed it to some peers for advice and they recomended I stick to a brighter basemap for improved visibility. For the unclustered ship icons, I choose to use bright and solid coloration that clearly stand out from the light blue colored water. The vast majority of ships will always have a NavStat value of 0 indicating they are "under way using engine". I choose to color these ships bright yellow which contrasts most with the light blue water. Ships with a NavStat value of 7 and therefore "engaged in fishing" were colored bright red to provide for enhanced visibility. Red was also used because of its societal perception as a representation of "bad" or "negative", in this case fishing being a potentially harmful environmental activity.


## Peer Critiques: 

