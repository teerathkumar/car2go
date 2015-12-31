# Create booking #
Create a new short-term booking for a user. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.1/bookings |
| **Method:** |POST      |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |
| vin      | true          | VIN of the vehicle to be booked |
| account  | true          | id of the user account which will be charged |
| test     | false         | activates test mode if set to "1". See below for more details. |




### Request Examples ###
```

 POST https://www.car2go.com/api/v2.1/bookings?vin=WME4513001K153738&account=1001
 
```





### Response ###
Similar to response provided by <a href='getbookings.html'>Get Bookings</a> though content is limited to booking created



### Response Examples ###




### TestMode ###
A successful test booking requires a valid test account and a valid vin. <br />
> Note: No real booking is created. Therefore you won't be charged for test bookings. <br />
> Furthermore the booking won't be returned by <a href='getbookings.html'>Get Bookings</a>.



### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |
| 2        | UserId invalid. |          |
| 3        | No valid accounts found. |  The user has no valid accounts. This occurs when the user has no account and is not invited to any accounts. |
| 4        | Not all necessary url parameters provided. |          |
| 5        | A technical error occured. |  This error can occur in case of application problems. If this error persist, please report the bug. |
| 6        | Invalid url parameter provided. |          |
| 7        | No valid driver license information could be found. |  This error occurs under the following circumstances: <ul> <li>the user is locked</li> <li>the user has no license data</li> <li>driver license is locked</li> <li>the user pin is locked</li> <li>the user password is locked</li> </ul> |
| 8        | The account is locked. |          |
| 9        | The vehicle can not be booked. |  This error occurs under the following circumstances: <ul> <li>the vehicle is not available (e.g. in use or already booked).</li> <li>the user has a concurrent booking.</li> <li>the maximum allowed active bookings per user have been reached.</li> </ul> |
| 10       | Vehicle invalid. |          |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12