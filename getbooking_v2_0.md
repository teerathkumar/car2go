# Get booking #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides the detailed information of a recently booked vehicle for the current user. The vehicle must have been assigned to the authenticated user. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.0/booking |
| **Method:** |GET       |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | location identifier string of the user's home location, e.g. "ulm", "austin". |
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |




### Request Examples ###
```
GET https://www.car2go.com/api/v2.0/booking?loc=austin
```

```
GET https://www.car2go.com/api/v2.0/booking?loc=ulm
```





### Response ###
Booking details of the current reserved car consists of:
> <ul>
<blockquote><li>returnValue - see list of return codes below and  <a href='index.html#returnvalues'>return values</a> for more details</li>
<li>a unique booking Id</li>
<li>a reservation time: date time string, according to ISO 8601, e.g. 2010-01-21T13:05+01:00</li>
<li>a booking position: longitude and latitude of booking</li>
<li>account information: id and description of the account which will be charged</li>
<li>detailed vehicle information (optional, depends on whether a vehicles has already been assigned or not)<br>
<ul>
<li>vin unique, textual vehicle identifier</li>
<li>numberPlate number plate of vehicle, e.g. used to identify car on the streetr</li>
<li>fuel level</li>
<li>interior</li>
<li>exterior</li>
<li>position: longitude and latitude of vehicle</li>
</ul>
</li>
</ul></blockquote>



### Response Examples ###
A XML response example of reserved vehicle:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <bookingResponse xmlns="http://www.car2go.com/openapi/xmlschema">
     <returnValue>
         <code>0</code>
         <description>Operation successful.</description>
     </returnValue>
     <booking>
         <bookingId>2910</bookingId>
         <reservationTime>2010-03-29T09:00:00+01:00</reservationTime>
         <bookingposition>
             <latitude>48.423291</latitude>
             <longitude>9.939559</longitude>
             <address>Daimler Mitarbeiterparkplatz, Wilhelm-Runge-Strasse</address>
         </bookingposition>
         <account>
             <accountId>1002</accountId>
             <description>Max Mustermann1002</description>
         </account>
         <vehicle>
             <vin>WME0000000K000010</vin>
             <numberPlate>UL-C1010</numberPlate>
             <fuel>90</fuel>
             <interior>GOOD</interior>
             <exterior>GOOD</exterior>
             <position>
                 <latitude>48.42188</latitude>
                 <longitude>9.9411</longitude>
                 <address>Wilhelm-Runge-Strasse 10, 89081 Ulm</address>
             </position>
         </vehicle>
     </booking>
 </bookingResponse>
 
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
| 12       | No reserved vehicle found. |          |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12