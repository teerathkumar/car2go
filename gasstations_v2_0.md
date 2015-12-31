# Get all gas stations #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides a list of car2go gas stations in context of specific location like ulm or austin in KML format.
KML is a file format used to display geographic data in an Earth browser such as Google Earth, Google Maps, and Google Maps for mobile. More information about KML can be found here: <a href='http://code.google.com/intl/de/apis/kml/documentation/kmlreference.html'>KML Reference at code.google.com</a>

The gas stations can be used to refuel a car2go. The customer can use the car2go fuel card to pay at those gas stations.


| **Access:** |public |
|:------------|:------|
| **URL:**    |http://www.car2go.com/api/v2.0/gasstations |
| **Method:** |GET    |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | location identifier string of the home location for which the vehicles are searched for, e.g. "ulm", "austin". |
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |




### Request Examples ###
```

 GET http://www.car2go.com/api/v2.0/gasstations?loc=ulm
 
```

```

 GET http://www.car2go.com/api/v2.0/gasstations?loc=austin
 
```





### Response ###
The KML file defines a placemark tag for each car2go gas station. The placemark tag defines following sub tags:
> <ul>
<blockquote><li>name - The name of the gas station</li>
<li>description - empty</li>
<li>point- the coordinates of the gas station</li>
<li>extendeddata - empty</li>
</ul></blockquote>



### Response Examples ###
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <kml xmlns:ns3="urn:oasis:names:tc:ciq:xsdschema:xAL:2.0" xmlns:ns2="http://www.w3.org/2005/Atom"
 	xmlns="http://www.opengis.net/kml/2.2">
 	<Document>
 		<description>CAR2GO Gas Stations</description>
 		<Style id="car2go">
 			<IconStyle>
 				<Icon>
 					<href>http://www.car2go.com/common/images/openapi/marker_fuel.png
 					</href>
 				</Icon>
 				<hotSpot y="0.0" x="0.0" />
 			</IconStyle>
 		</Style>
 		<Placemark>
 			<name>Shell, Europestreet 44</name>
 			<description></description>
 			<styleUrl>#car2go</styleUrl>
 			<ExtendedData />
 			<Point>
 				<coordinates>10.033742,48.38719,0</coordinates>
 			</Point>
 		</Placemark>
 	</Document>
 </kml>
 
```

A JSON response example:
> <p />
```

 {"placemarks":[{"coordinates":"[9.987988,48.358829,0]","name":"Shell, Hauptstrasse 12"},{"coordinates":"[9.990183,48.404832,0]","name":"Shell, Karlstrasse 38"}]}
 
```





### TestMode ###










(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12