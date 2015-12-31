# Get recent rentals #
Provides recent rentals and costs for a car2go user on each account. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details. The only supported HTTP method is GET.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.1/rentals |
| **Method:** |GET       |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |
| test     | false         | activates test mode if set to "1". See below for more details. |




### Request Examples ###
```
GET https://www.car2go.com/api/v2.1/rentals
```

```
GET https://www.car2go.com/api/v2.1/rentals?format=json
```





### Response ###
The XML file defines a rentalsResponse tag to receive all executed rentals and costs for any car2go user. The rentalsResponse tag
> defines following sub tags:
> <ul>
<blockquote><li>returnValue - see list of return codes below and <a href='index.html#returnvalues'>return values</a> for more details</li>
<p />
<li>rentals - only for successful return value, i.e. code = 0. Contains a list of all found accounts with following sub<br>
tags:<br>
<ul>
<li>driverName - name of driver for this trip</li>
<li>usageStartTime - start time of this trip</li>
<li>usageEndTime - end time of this trip</li>
<li>usageStartAddress - name of address where this trip was started</li>
<li>usageDistance - covered distance of this trip; unit given in tag unitOfLength</li>
<li>unitOfLength - unit in which distance is given; KILOMETER or MILE</li>
<li>driveDurationInMinutes - duration of this trip in minutes</li>
<li>usageAmount - overall amount of this trip; contains amountGross, amountNet, amountVat and currency</li>
<li>driveAmount - amount only for driving of this trip; contains amountGross, amountNet, amountVat and currency</li>
<li>parkAmount - amount only for parking of this trip; contains amountGross, amountNet, amountVat and currency</li>
<li>costDistance - distance of overdue; unit given in tag unitOfLength</li>
<li>costDistanceAmount - amount only for distance overdue of this trip; contains amountGross, amountNet, amountVat and currency</li>
<li>goodwillAmount - amount for any goodwill for this trip; contains amountGross, amountNet, amountVat and currency</li>
<li>minutesDiscounts - list of any minutes package which are allocated with this trip; contains amountGross, amountNet, amountVat, currency and description<br>
<li>description - name of allocated minutes package</li>
</li>
</ul>
</li>
</ul></blockquote>



### Response Examples ###
A XML response example where user has one recent rental:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <rentalsResponse xmlns="http://www.car2go.com/openapi/xmlschema">
      <returnValue>
          <code>0</code>
          <description>Operation successful.</description>
      </returnValue>
      <rentals>
          <driverName>Joe Doe</driverName>
          <usageStartTime>2014-01-08T16:34:09.320Z</usageStartTime>
          <usageEndTime>2014-01-08T16:34:09.320Z</usageEndTime>
          <usageStartAddress>Start Address 12, 12345 City</usageStartAddress>
          <usageEndAddress>Finish Address 12, 12345 City</usageEndAddress>
          <usageDistance>1</usageDistance>
          <usageAmount>
              <amountGross>16.48</amountGross>
              <amountNet>15.21</amountNet>
              <amountVat>1.27</amountVat>
              <currency>EUR</currency>
          </usageAmount>
          <driveDurationInMinutes>37</driveDurationInMinutes>
          <driveAmount>
              <amountGross>6.02</amountGross>
              <amountNet>5.89</amountNet>
              <amountVat>0.14</amountVat>
              <currency>EUR</currency>
          </driveAmount>
          <parkDurationInMinutes>8237954</parkDurationInMinutes>
          <parkAmount>
              <amountGross>3.03</amountGross>
              <amountNet>2.86</amountNet>
              <amountVat>0.17</amountVat>
              <currency>EUR</currency>
          </parkAmount>
          <costDistance>2</costDistance>
          <costDistanceAmount>
              <amountGross>1.63</amountGross>
              <amountNet>1.57</amountNet>
              <amountVat>0.06</amountVat>
              <currency>EUR</currency>
          </costDistanceAmount>
          <goodwillAmount>
              <amountGross>-1.19</amountGross>
              <amountNet>-1.00</amountNet>
              <amountVat>-0.20</amountVat>
              <currency>EUR</currency>
          </goodwillAmount>
          <unitOfLength>KILOMETER</unitOfLength>
          <minutesDiscounts>
              <amount>
                  <amountGross>6.99</amountGross>
                  <amountNet>5.89</amountNet>
                  <amountVat>1.10</amountVat>
                  <currency>EUR</currency>
              </amount>
              <description>Test Minutes</description>
          </minutesDiscounts>
      </rentals>
 </rentalsResponse>
```

> A JSON response example:
> <p />
```

 {
  "rentals": [
      {
          "costDistance": 2,
          "costDistanceAmount":
          {
              "amountGross": 1.63,
              "amountNet": 1.57,
              "amountVat": 0.06,
              "currency": "EUR"
          },
          "driveAmount":
          {
              "amountGross": 6.02,
              "amountNet": 5.89,
              "amountVat": 0.14,
              "currency": "EUR"
          },
          "driveDurationInMinutes": 37,
          "driverName": "Joe Doe",
          "goodwillAmount":
          {
              "amountGross": -1.19,
              "amountNet": -1,
              "amountVat": -0.2,
              "currency": "EUR"
          },
          "minutesDiscounts": [
          {
              "amount":
              {
                  "amountGross": 6.99,
                  "amountNet": 5.89,
                  "amountVat": 1.1,
                  "currency": "EUR"
              },
              "description": "Test Minutes"
          }],
          "parkAmount":
          {
              "amountGross": 3.03,
              "amountNet": 2.86,
              "amountVat": 0.17,
              "currency": "EUR"
          },
          "parkDurationInMinutes": 8237954,
          "unitOfLength": "KILOMETER",
          "usageAmount":
          {
              "amountGross": 16.48,
              "amountNet": 15.21,
              "amountVat": 1.27,
              "currency": "EUR"
          },
          "usageDistance": 1,
          "usageEndAddress": "Finish Address 12, 12345 City",
          "usageEndTime":
          {
              "firstDayOfWeek": 1,
              "gregorianChange": "1582-10-15",
              "lenient": true,
              "minimalDaysInFirstWeek": 1,
              "time": "2014-01-08",
              "timeInMillis": 1389198715987,
              "timeZone":
              {
                  "DSTSavings": 0,
                  "ID": "UTC",
                  "dirty": false,
                  "displayName": "Coordinated Universal Time",
                  "lastRuleInstance": null,
                  "rawOffset": 0
              }
          },
          "usageStartAddress": "Start Address 12, 12345 City",
          "usageStartTime":
          {
              "firstDayOfWeek": 1,
              "gregorianChange": "1582-10-15",
              "lenient": true,
              "minimalDaysInFirstWeek": 1,
              "time": "2014-01-08",
              "timeInMillis": 1389198715987,
              "timeZone":
              {
                  "DSTSavings": 0,
                  "ID": "UTC",
                  "dirty": false,
                  "displayName": "Coordinated Universal Time",
                  "lastRuleInstance": null,
                  "rawOffset": 0
              }
          }
      }],
      "returnValue":
      {
          "code": 0,
          "description": "Operation successful."
      }
 }
 
```





### TestMode ###
Response contains rentalsResponse containing data for all subtags for one executed rental



### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12