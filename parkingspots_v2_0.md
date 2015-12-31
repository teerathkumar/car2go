# Get all parking spots #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides a list of car2go parking spots for a specific location like ulm or austin in KML format.
KML is a file format used to display geographic data in an Earth browser such as Google Earth, Google Maps, and Google Maps for mobile. More information about KML can be found here: <a href='http://code.google.com/intl/de/apis/kml/documentation/kmlreference.html'>KML Reference at code.google.com</a>

The parking spots are especially dedicated for car2go vehicles.


| **Access:** |public |
|:------------|:------|
| **URL:**    |http://www.car2go.com/api/v2.0/parkingspots |
| **Method:** |GET    |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | location identifier string of the location the parking spots are searched for, e.g. "ulm", "austin". |
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |




### Request Examples ###
```

 GET http://www.car2go.com/api/v2.0/parkingspots?loc=Ulm
 
```

```

 GET http://www.car2go.com/api/v2.0/parkingspots?loc=Austin&format=json
 
```





### Response ###
The KML file defines a placemark tag for each car2go parking spot. The placemark tag defines following sub tags:
> <ul>
<blockquote><li>name - The name of the parking spot</li>
<li>description - contains the total and used capacity of the parking spot</li>
<li>point - the coordinates of the parking spot</li>
<li>extendeddata - contains the usedCapacity and the totalCapacity of the parking spot as separate attributes</li>
</ul></blockquote>



### Response Examples ###
A KML response example:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <kml xmlns:ns3="urn:oasis:names:tc:ciq:xsdschema:xAL:2.0" xmlns:ns2="http://www.w3.org/2005/Atom"
 	xmlns="http://www.opengis.net/kml/2.2">
 	<Document>
 		<description>CAR2GO Parking Lots</description>
 		<Style id="car2go">
 			<IconStyle>
 				<Icon>
 					<href>http://www.car2go.com/common/images/openapi/marker_parking.png
 					</href>
 				</Icon>
 				<hotSpot y="0.0" x="0.0" />
 			</IconStyle>
 		</Style>
 		<Style id="car2go_excluded">
 			<LineStyle>
 				<color>FF0000FF</color>
 			</LineStyle>
 		</Style>
 		<Style id="car2go_included">
 			<LineStyle>
 				<color>FF00FF00</color>
 			</LineStyle>
 		</Style>
 		<Placemark>
 			<name>Inner City Parkspot 2</name>
 			<description>Capacity (used/total): 0/3</description>
 			<styleUrl>#car2go</styleUrl>
 			<ExtendedData>
 				<Data name="usedCapacity"><value>0</value></Data>
 				<Data name="totalCapacity"><value>3</value></Data>
 			</ExtendedData>
 			<Point>
 				<coordinates>9.983611,48.398565,0</coordinates>
 			</Point>
 		</Placemark>
 	</Document>
 </kml>
 
```

A JSON response example:
> <p />
```

  {"placemarks":[{"coordinates":"[-97.750983,30.269577,0]","name":"West Ave","totalCapacity":"4","usedCapacity":"0"},{"coordinates":"[-97.74225,30.265976,0]","name":"100 East 4th Street","totalCapacity":"4","usedCapacity":"0"}]}
 
```





### TestMode ###










(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12