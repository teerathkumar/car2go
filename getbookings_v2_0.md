# Get bookings #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides a list of all current bookings of a user. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.0/bookings |
| **Method:** |GET       |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | location identifier string of the user's home location, e.g. "ulm", "austin". |
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |




### Request Examples ###
```

 GET https://www.car2go.com/api/v2.0/bookings?loc=ulm&format=json
 
```

```

 GET https://www.car2go.com/api/v2.0/bookings?loc=austin
 
```





### Response ###
Each booking consists of
> <ul>
<blockquote><li>returnValue - see list of return codes below and <a href='index.html#returnvalues'>return values</a> for more details</li>
<li>a unique booking Id</li>
<li>a reservation time: date time string, according to ISO 8601, e.g. 2010-01-21T13:05+01:00</li>
<li>a booking position: longitude and latitude of booking</li>
<li>account information: id and description of the account which will be charged</li>
<li>and vehicle information (optional, depends on whether a vehicles has already been assigned or not)</li>
</ul>
<p />
Vehicle information consists of<br>
<ul>
<li>vin unique, textual vehicle identifier</li>
<li>numberPlate number plate of vehicle, e.g. used to identify car on the street</li>
<li>fuel level</li>
<li>interior</li>
<li>exterior</li>
<li>position: longitude and latitude of vehicle</li>
</ul></blockquote>



### Response Examples ###
A XML response example:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <bookingResponse xmlns="http://www.car2go.com/openapi/xmlschema">
     <returnValue>
         <code>0</code>
         <description>Operation successful.</description>
     </returnValue>
     <booking>
         <bookingId>4321</bookingId>
         <reservationTime>2001-12-31T12:00:00+01:00</reservationTime>
         <bookingposition>
             <latitude>48.4008</latitude>
             <longitude>9.9596</longitude>
             <address>Blaubeurer Strasse 128, 89077 Ulm</address>
         </bookingposition>
         <account>
             <accountId>5678</accountId>
             <description>Max Mustermann</description>
         </account>
         <vehicle>
             <vin>WME4513001K154451</vin>
             <numberPlate>UL-C5713</numberPlate>
             <fuel>90</fuel>
             <interior>GOOD</interior>
             <exterior>GOOD</exterior>
             <position>
                 <latitude>48.4008</latitude>
                 <longitude>9.9596</longitude>
                 <address>Blaubeurer Strasse 128, 89077 Ulm</address>
             </position>
         </vehicle>
     </booking>
     <booking>
         <bookingId>4321</bookingId>
         <reservationTime>2001-12-31T13:00:00+01:00</reservationTime>
         <bookingposition>
             <latitude>48.1048</latitude>
             <longitude>8.1591</longitude>
             <address>Lange Strasse 67, 82828 Grossstadt</address>
         </bookingposition>
         <account>
             <accountId>5678</accountId>
             <description>Max Mustermann</description>
         </account>
     </booking>
 </bookingResponse>
 
```

A JSON response example:
> <p />
```

 {"returnValue":{"code":0,"description":"Operation successful."},"booking":[]}
 
```





### TestMode ###




### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |
| 1        | Location invalid. |          |
| 3        | No valid accounts found. |  The user has no valid accounts. This occurs when the user has no account and is not invited to any accounts. |
| 4        | Not all necessary url parameters provided. |          |
| 5        | A technical error occured. |  This error can occur in case of application problems. If this error persist, please report the bug. |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12