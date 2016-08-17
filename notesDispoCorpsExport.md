[Description](#description) [API](#api) [Parameters](#parameters) [Response](#response) [Sample](#sample-response)
# notesDispoExport

## Description
This function provides a list of officer records whose appointments have changed between the specified dates including officers who have been commissioned (new appointment), transferred (end one appointment and start another), and retired/case closed/PTG (end appointment).  Data includes basic person, officer, appointment, and contact info.

---
## API
To get all objects for a specified territory
>GET mvc/api/oms/ext/notesDispoExport/`compareDate`/`territoryId`

To get all OMS territories:
>GET mvc/api/oms/ext/notesDispoExport/`compareDate`
---
## Parameters
`compareDate` The previous date for the basis of the comparison.  The date should be formatted yyyy-MM-dd (ie, 2016-01-01).

`territoryId` An integer value for the requested territory.

---
## Response
The response is a JSON-formmatted response that includes a success flag (true/false) and a data array containing the objects with the officer, appointment, and contact info.

*Notes*
* **action** This is either UPDATE or DELETE for all objects.  UPDATE indicates the person or position was changed because a new appointment was created or an existing appointment was changed.  DELETE indicates the position or person are no longer associated by an appointment record. 
* **id** This is just a unique field for the result set and is NOT guaranteed to be the same value for each call.
* **fkPerson** The unique person ID within the system.  This will be consistent across all calls to the API.
* **fkPosition** The unique unit (positon) ID within the system.  This will be consistent across all calls to the API.
* **fkAppointment** The unique appointment ID within the system.  This will be consistent across all calls to the API.

---
## Sample Response
```
{
    "success": true,
    "data": {
        "totalCount": 1008,
        "objects": [
            {
                "action": "UPDATE",
                "altAddress1": null,
                "altAddress2": null,
                "altAddress3": null,
                "altAddress4": null,
                "altCountryCode": null,
                "altZip": null,
                "appointmentEndDate": null,
                "appointmentIsInCharge": null,
                "appointmentIsPrimary": "Y",
                "appointmentStartDate": null,
                "cellPhone": null,
                "cellPhoneNote": null,
                "commandName": null,
                "commissionDate": null,
                "dBVersion": "4428200",
                "firstName": "Christopher",
                "fkAppointment": null,
                "fkCommand": null,
                "fkEntity": 170299,
                "fkPerson": 170299,
                "fkPosition": null,
                "fkShortcut": null,
                "fkSpouse": null,
                "fkTerritory": 55,
                "gloryDate": null,
                "groupDispoOrder": null,
                "groupName": null,
                "homeAddress1": null,
                "homeAddress2": null,
                "homeAddress3": null,
                "homeAddress4": null,
                "homeCountryCode": null,
                "homeDivision": null,
                "homeEMail": null,
                "homePhone": null,
                "homePhoneNote": null,
                "homeZip": null,
                "id": 1,
                "imagePath": null,
                "juniorSoldierDate": null,
                "lastName": "Selvage",
                "locationDispoOrder": null,
                "locationName": null,
                "mailPhone": null,
                "mailPhoneNote": null,
                "maritalStatus": "Unknown",
                "middleName": "",
                "ministryDispoOrder": null,
                "ministryName": null,
                "modifiedDate": "2016-03-07T19:04:23Z",
                "namePrefix": "",
                "nameSuffix": "",
                "nickName": "",
                "officeAddress1": null,
                "officeAddress2": null,
                "officeAddress3": null,
                "officeAddress4": null,
                "officeCountryCode": null,
                "officeEMail": null,
                "officeFax": null,
                "officeFaxNote": null,
                "officeOther": null,
                "officeOtherNote": null,
                "officePhone": null,
                "officePhoneNote": null,
                "officePhysicalAddress1": null,
                "officePhysicalAddress2": null,
                "officePhysicalAddress3": null,
                "officePhysicalAddress4": null,
                "officePhysicalCountryCode": null,
                "officePhysicalZip": null,
                "officeZip": null,
                "originalCorps": null,
                "otherPhone": null,
                "otherPhoneNote": null,
                "personType": "Relative",
                "positionDispoOrder": null,
                "positionIsOverseas": null,
                "positionTitle": null,
                "queryDate": "2016-08-17T00:00:00Z",
                "rank": null,
                "rankName": null,
                "retirementDate": null,
                "seniorSoldierDate": null,
                "serviceDate": null,
                "session": null,
                "sex": "M",
                "spouseFirstName": null,
                "spouseLastName": null,
                "spouseMiddleName": null,
                "spouseNamePrefix": null,
                "spouseNameSuffix": null,
                "spouseNickName": null,
                "spouseRank": null,
                "territoryName": "USA Central Territory"
            },
            ...
        ]
    }
}
```
