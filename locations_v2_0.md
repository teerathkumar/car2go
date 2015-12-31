# Get all locations #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides a list of all locations car2go is operating for like ulm or austin in either XML or JSON format.

| **Access:** |public |
|:------------|:------|
| **URL:**    |http://www.car2go.com/api/v2.0/locations |
| **Method:** |GET    |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |




### Request Examples ###
```

 GET http://www.car2go.com/api/v2.0/locations
 
```

```

 GET http://www.car2go.com/api/v2.0/locations?format=json
 
```





### Response ###
Each location consists of:
> <ul>
<blockquote><li>returnValue - see OpenApiReturnValue for more details</li>
</ul>
<ul>
<li>locationId - the unique identifier of the location</li>
<li>locationName - the name of the location</li>
</ul></blockquote>



### Response Examples ###
A XML response example:
> <p />

```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <locationResponse xmlns="http://www.car2go.com/openapi/xmlschema">
 	<returnValue>
 		<code>0</code>
 		<description>Operation successful.</description>
 	</returnValue>
 	<location>
 		<locationId>1</locationId>
 		<locationName>Ulm</locationName>
 	</location>
 	<location>
 		<locationId>2</locationId>
 		<locationName>Austin</locationName>
 	</location>
 </locationResponse>
 
```

A JSON response example:
> <p />

```

  {"location":[{"locationId":1,"locationName":"Ulm"},{"locationId":2,"locationName":"Austin"}],"returnValue":{"code":0,"description":"Operation successful."}}
 
```





### TestMode ###




### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12