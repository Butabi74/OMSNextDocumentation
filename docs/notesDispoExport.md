### [TOC](../README.md) | [Request](#request) | [Parameters](#parameters) | [Response](#response) | [Returns](#returns) | [Example](#example)  

# notesDispoExport
This function provides a list of officer records whose appointments have changed between the specified dates including officers who have been commissioned (new appointment), transferred (end one appointment and start another), and retired/case closed/PTG (end appointment).  Data includes basic person, officer, appointment, and contact info.

---
## Request
_Required Headers_
>Accept: application/json  
Authorization: Basic xyz...

To get all objects for a specified territory
>GET mvc/api/oms/ext/notesDispoExport/`compareDate`/`territoryId`

To get all objects for all OMS territories
>GET mvc/api/oms/ext/notesDispoExport/`compareDate`

---
## Parameters
`compareDate` _date_  
The previous date for the basis of the comparison.  The date should be formatted yyyy-MM-dd (ie, 2016-01-01).

`territoryId` _integer_  
The ID of the requested territory.

---
## Response
>Content-Type: application/json

The response is a JSON-formmatted response that includes a success flag (true/false) and a data array containing the objects with the officer, appointment, and contact info.

Status Code|Likely Reason
---|---
200 OK|
500 INTERNAL SERVER ERROR|An invalid argument was passed to the API call or the date value was not formatted correctly

---
## Returns
An array of objects with the following fields to note:

* **action** This is either UPDATE or DELETE for all objects.  UPDATE indicates the person or position was changed because a new appointment was created or an existing appointment was changed.  DELETE indicates the position or person are no longer associated by an appointment record. 
* **id** This is just a unique field for the result set and is NOT guaranteed to be the same value for each call.
* **fkPerson** The unique person ID within the system.  This will be consistent across all calls to the API.
* **fkPosition** The unique unit (positon) ID within the system.  This will be consistent across all calls to the API.
* **fkAppointment** The unique appointment ID within the system.  This will be consistent across all calls to the API.

There are other fields than the ones listed here, but these warranted further explanation regarding their use for the end user.  Please see the [example](#example) below for the full list of returned fields.

---
## Example
Retrieve the list of persons and positions that have had updated appointments since 3/01/2016 for territory with ID = 55.

_Request_
>GET mvc/api/oms/ext/notesDispoExport/2016-03-01/55

_Response_
```json
{
    "success": true,
    "data": {
        "totalCount": 1008,
        "objects": [
            ...,
            {
                "action": "UPDATE",
                "altAddress1": null,
                "altAddress2": null,
                "altAddress3": null,
                "altAddress4": null,
                "altCountryCode": null,
                "altZip": null,
                "appointmentEndDate": null,
                "appointmentIsInCharge": false,
                "appointmentIsPrimary": "Y",
                "appointmentStartDate": "2016-06-29T00:00:00Z",
                "cellPhone": "555-123-4567",
                "cellPhoneNote": "",
                "commandName": "Northern Division",
                "commissionDate": "2015-06-14T00:00:00Z",
                "dBVersion": "4428200",
                "firstName": "ThisIsMy-FirstName",
                "fkAppointment": 663230,
                "fkCommand": 15603,
                "fkEntity": 190276,
                "fkPerson": 190276,
                "fkPosition": 16982,
                "fkShortcut": null,
                "fkSpouse": null,
                "fkTerritory": 55,
                "gloryDate": null,
                "groupDispoOrder": 4,
                "groupName": "Division Corps",
                "homeAddress1": null,
                "homeAddress2": null,
                "homeAddress3": null,
                "homeAddress4": null,
                "homeCountryCode": null,
                "homeDivision": "",
                "homeEMail": null,
                "homePhone": null,
                "homePhoneNote": null,
                "homeZip": null,
                "id": 6,
                "imagePath": "PathToImage-190276-doHVR8UXyX.jpg",
                "juniorSoldierDate": null,
                "lastName": "ThisIsMy-LastName",
                "locationDispoOrder": 17,
                "locationName": "Minneapolis (Central), MN",
                "mailPhone": null,
                "mailPhoneNote": null,
                "maritalStatus": "Single",
                "middleName": "",
                "ministryDispoOrder": 1,
                "ministryName": "Corps Community Center",
                "modifiedDate": "2016-07-13T15:59:11Z",
                "namePrefix": "",
                "nameSuffix": "",
                "nickName": "",
                "officeAddress1": null,
                "officeAddress2": null,
                "officeAddress3": null,
                "officeAddress4": null,
                "officeCountryCode": null,
                "officeEMail": "any.address@example.com",
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
                "originalCorps": "Milwaukee (Citadel), WI",
                "otherPhone": null,
                "otherPhoneNote": null,
                "personType": "Officer",
                "positionDispoOrder": 1,
                "positionIsOverseas": "N",
                "positionTitle": "Corps Officer",
                "queryDate": "2016-08-17T00:00:00Z",
                "rank": "Lieutenant",
                "rankName": "Lieutenant",
                "retirementDate": null,
                "seniorSoldierDate": "1995-07-01T00:00:00Z",
                "serviceDate": "2015-06-14T00:00:00Z",
                "session": "Heralds of Grace",
                "sex": "F",
                "spouseFirstName": null,
                "spouseLastName": null,
                "spouseMiddleName": null,
                "spouseNamePrefix": null,
                "spouseNameSuffix": null,
                "spouseNickName": null,
                "spouseRank": null,
                "territoryName": "Full Territory Name Here"
            },
            ...
        ]
    }
}
```
