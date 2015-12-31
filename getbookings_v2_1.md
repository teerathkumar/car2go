# Get bookings #
Provides a list of all current bookings of a user. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.1/bookings |
| **Method:** |GET       |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |
| test     | false         | activates test mode if set to "1". See below for more details. |




### Request Examples ###
```

 GET https://www.car2go.com/api/v2.1/bookings?format=json
 
```

```

 GET https://www.car2go.com/api/v2.1/bookings
 
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
<li>engineType: CE for CombustionEngine, ED for ElectricDrive</li>
<li>charging: true/false for ElectricDrive vehicles</li>
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
             <engineType>CE</engineType>
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


> <p />
> A JSON example:
```

 {"booking":[{
    "account":{"accountId":1002,"description":"Max Mustermann1002"},
    "bookingId":2910,
    "bookingposition":{"address":"Daimler Mitarbeiterparkplatz, Wilhelm-Runge-Strasse","latitude":48.423291,"longitude":9.939559},
    "reservationTime":{"firstDayOfWeek":1,"gregorianChange":"1582-10-15","lenient":true,"minimalDaysInFirstWeek":1,"time":"2010-01-02","timeInMillis":1325501991033,"timeZone":{"DSTSavings":3600000,"ID":"Europe/Berlin","dirty":false,"displayName":"Central European Time","lastRuleInstance":{"DSTSavings":3600000,"ID":"Europe/Berlin","displayName":"Central European Time","rawOffset":3600000},"rawOffset":3600000}},
    "vehicle":{
      "engineType":"CE",
      "exterior":"GOOD",
      "fuel":90,
      "interior":"GOOD",
      "numberPlate":"UL-C1010",
      "position":{
        "address":"Wilhelm-Runge-Strasse 10, 89081 Ulm",
        "latitude":48.42188,
        "longitude":9.9411
      },
      "vin":"WME0000000K000010"}
  },{...second booking...}
  ],
  "returnValue":{
    "code":0,
    "description":"Operation successful."
  }}
 
```





### TestMode ###
Response contains two bookings, one for each test account. The first one has a vehicle assigned, the second one is scheduled in future. Note: Bookings created in test mode won't be returned.



### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |
| 3        | No valid accounts found. |  The user has no valid accounts. This occurs when the user has no account and is not invited to any accounts. |
| 4        | Not all necessary url parameters provided. |          |
| 5        | A technical error occured. |  This error can occur in case of application problems. If this error persist, please report the bug. |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12