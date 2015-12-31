# Get the operating area #
Provides a list of all zones forming the car2go operating area for a given location like ulm or austin in KML format.
KML is a file format used to display geographic data in an Earth browser such as Google Earth, Google Maps, and Google Maps for mobile. More information about KML can be found here: <a href='http://code.google.com/intl/de/apis/kml/documentation/kmlreference.html'>KML Reference at code.google.com</a>


| **Access:** |public |
|:------------|:------|
| **URL:**    |http://www.car2go.com/api/v2.1/operationareas |
| **Method:** |GET    |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | Location identifier string of the user's home location, e.g. "ulm", "austin". |
| oauth\_consumer\_key | true          | Your assigned oauth consumer key |
| format   | false         | Defines response format. Value "json" => JSON format, otherwise XML format is used. |
| callback | false         | Defines JSONP (JSON with Padding) callback function used as wrapper. |
| test     | false         | Has currently no effect. |




### Request Examples ###
```
GET http://www.car2go.com/api/v2.1/operationareas?oauth_consumer_key=consumerkey&loc=ulm
```

```
GET http://www.car2go.com/api/v2.1/operationareas?oauth_consumer_key=consumerkey&loc=ulm&format=json
```





### Response ###
The response is provided as KML file which defines a placemark tag for each zone contained in the operating area.
> The placemark has a name and is styled according to its zoneType:
> <ul>
<blockquote><li>included - zones included in the operating area</li>
<li>excluded - zones excluded from the operating area (no parking allowed)</li>
<li>parking - zone is a dedicated car2go parking spot</li>
</ul></blockquote>



### Response Examples ###
```

 <kml xmlns:ns3="urn:oasis:names:tc:ciq:xsdschema:xAL:2.0" xmlns:ns2="http://www.w3.org/2005/Atom"
 	xmlns="http://www.opengis.net/kml/2.2">
 	<Document>
 		<description>CAR2GO Operation Area</description>
 		<Style id="car2go_excluded">
 			<LineStyle>
 				<color>FF0000FF
 				</color>
 			</LineStyle>
 		</Style>
 		<Style id="car2go_included">
 			<LineStyle>
 				<color>FF00DD00
 				</color>
 			</LineStyle>
 		</Style>
 		<Style id="car2go_parking_spot">
 			<LineStyle>
 				<color>FFEE0000
 				</color>
 			</LineStyle>
 		</Style>
 		<Placemark>
 			<name>a zone</name>
 			<styleUrl>#car2go_excluded</styleUrl>*
 		    <ExtendedData>
 		        <Data name="zoneType">
 		            <value>excluded</value>
 		        </Data>
 		    </ExtendedData>
 			<LineString>
 				<coordinates>10.02739,48.458917,0 10.02739,48.468917,0 10.041390000000002,48.468917,0 10.041390000000002,48.458917,0</coordinates>
 		</LineString>
 		</Placemark>
 	</Document>
 </kml>
 
```

A JSON response example:
> <p />
```

 {"placemarks":[{"coordinates":[10.02739,48.458916,0,10.02739,48.468918,0],"name":"a zone","zoneType":"excluded"}]}
 
```





### TestMode ###




### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12