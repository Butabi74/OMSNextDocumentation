[API](#api) [Parameters](#parameters) [Response](#response) [Example](#example)
# notesCorpsDispoExport
This function provides a list of unit (ministry and location) records where the contact info and/or appointed officers have changed between the specified dates.

---
## API
_Required Headers_
>Accept: application/json  
Authorization: Basic xyz...

To get all objects for a specified territory
>GET mvc/api/oms/ext/notesCorpsDispoExport/`compareDate`/`territoryId`  

To get all objects for all OMS territories
>GET mvc/api/oms/ext/notesCorpsDispoExport/`compareDate`

---
## Parameters
`compareDate` _date_  
The previous date for the basis of the comparison.  The date should be formatted yyyy-MM-dd (ie, 2016-01-01).

`territoryId` _integer_  
The ID of the requested territory.

---
## Response
>Content-Type: application/json

The response is a JSON-formmatted response that includes a success flag (true/false) and a data array containing the objects with the unit contact and appointed person info.

Status||Likely Reason
---|---|---
200|OK|
500|INTERNAL SERVER ERROR|An invalid argument was passed to the API call or the date value was not formatted correctly

---
## Example
Retrieve the list of corps contact info that has changed since 3/01/2016 for territory with ID = 55.

_Request_
>GET https://omsapi.fake.url/mvc/api/oms/ext/notesCorpsDispoExport/2016-03-01/55

_Response_  
```json
{
  "success": true,
  "data": {
    "totalCount": 99,
    "objects": [
        ...,
        {
            "action": "DELETE",
            "commandName": "Midland Division",
            "dBVersion": "4428200",
            "fax": "555-987-6543 ",
            "fkTerritory": 55,
            "id": 37,
            "locationName": "St. Louis (Maplewood), MO",
            "ministryName": "Corps Community Center",
            "officeAddress1": null,
            "officeAddress2": null,
            "officeAddress3": null,
            "officeAddress4": null,
            "officePhysicalAddress1": null,
            "officePhysicalAddress2": null,
            "officePhysicalAddress3": null,
            "officePhysicalAddress4": null,
            "officePhysicalZip": null,
            "officeZip": null,
            "personInCharge": "Captain First M. Last",
            "phone": null,
            "queryDate": "2016-08-17T00:00:00Z",
            "territoryName": "Full Territory Name"
        },
        ...
    ]
  }
}
```
