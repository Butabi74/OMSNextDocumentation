[Description](#description) [API](#api) [Parameters](#parameters) [Response](#response) [Sample](#sample-response)
# notesCorpsDispoExport

## Description
This function provides a list of unit (ministry and location) records where the contact info and/or appointed officers have changed between the specified dates.

---
## API
To get all objects for a specified territory
>GET mvc/api/oms/ext/notesCorpsDispoExport/`compareDate`/`territoryId`

To get all OMS territories:
>GET mvc/api/oms/ext/notesCorpsDispoExport/`compareDate`

---
## Parameters
`compareDate` The previous date for the basis of the comparison.  The date should be formatted yyyy-MM-dd (ie, 2016-01-01).

`territoryId` An integer value for the requested territory.

---
## Response
The response is a JSON-formmatted response that includes a success flag (true/false) and a data array containing the objects with the unit contact and appointed person info.

---
## Sample Response
```
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
