# Get all accounts #
<b>car2go API v2.0 is deprecated. See <a href='index_v2_1.md'>v2.1</a> for the current car2go API version.</b>

Provides all valid accounts of a user for a given location like Ulm or Austin. Access to this function is restricted. See <a href='../oauth.html'>OAuth documentation</a> for more details. The only supported HTTP method is GET.

| **Access:** |protected |
|:------------|:---------|
| **URL:**    |https://www.car2go.com/api/v2.0/accounts |
| **Method:** |GET       |



### Parameters ###
| **Name** | **Mandatory** | **Description** |
|:---------|:--------------|:----------------|
| loc      | true          | location identifier string of the user's home location, e.g. "ulm", "austin". |
| format   | false         | defines response format. Value "json" => JSON format, otherwise xml format is used |
| callback | false         | defines JSONP (JSON with Padding) callback function used as wrapper |




### Request Examples ###
```
GET https://www.car2go.com/api/v2.0/accounts?loc=ulm&format=json
```

```
GET https://www.car2go.com/api/v2.0/accounts?loc=austin
```





### Response ###
The XML file defines a accountResponse tag to receive all valid accounts for any car2go user. The accountResponse tag
> defines following sub tags:
> <ul>
<blockquote><li>returnValue - see list of return codes below and <a href='index.html#returnvalues'>return values</a> for more details</li>
<p />
<li>account - only for successful return value, i.e. code = 0. Contains a list of all found accounts with following sub<br>
tags:<br>
<ul>
<li>accountId - the unique identifier of this account</li>
<li>description - detailed description of the account</li>
</ul>
</li>
</ul></blockquote>



### Response Examples ###
A XML response example where user has valid account:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <accountResponse xmlns="http://www.car2go.com/openapi/xmlschema">
     <returnValue>
         <code>0</code>
         <description>Operation successful.</description>
     </returnValue>
     <account>
         <accountId>58</accountId>
         <description></description>
     </account>
 </accountResponse>
 
```

A XML response example where user does not have valid account:
> <p />
```

 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <accountResponse xmlns="http://www.car2go.com/openapi/xmlschema">
     <returnValue>
         <code>3</code>
         <description>No valid accounts found.</description>
     </returnValue>
 </accountResponse>
 
```

A JSON response example:
> <p />
```

 {"returnValue":{"code":0,"description":"Operation successful."},"account":[{"accountId":994,"description":"Max Mustermann11585"}]}
 
```





### TestMode ###




### Return Codes ###
The following return codes may occur:
| **Code** | **Description** | **Note** |
|:---------|:----------------|:---------|
| 0        | Operation successful. |          |
| 1        | Location invalid. |          |
| 3        | No valid accounts found. |  The user has no valid accounts. This occurs when the user has no account and is not invited to any accounts. |






(c) 2010 car2go GmbH. All rights reserved. Generated 06.10.14 10:12