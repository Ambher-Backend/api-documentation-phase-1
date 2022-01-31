## API DOCUMENTATION FOR VENDOR
>`BASE-URL` will be anything, for testing, backend team will be providing a dummy API
---
### <u>Signup API</u>

```
Type- POST
Route- BASE-URL/vendor/signup
```

#### Parameters

| Param Name  | Data Type | Required |      Remarks      |
| ----------- | :-------: | :------: | :---------------: |
| name        |  String   |   true   |
| phoneNumber |  String   |   true   |
| email       |  String   |   true   |
| password    |  String   |   true   | minimum length: 8 |
| dob         |  String   |   true   |
| Address     |  Array    |   false  | Atleast two fields must be filled|

```
Address: [
     {
       flatNo: { type: String },
       buildingNo: { type: String },
       streetName: { type: String },
       city: { type: String },
       state: { type: String },
       country: { type: String },
       zipCode: { type: String },
        lat: { type: Number },
        lon: { type: Number },
    }
       ]

```

#### Request(sample)
```
{
    
    name: kelore,
    phoneNumber: 8901929309,
    password: jekekrlkell,
    email: qwert@gmail.com,
    dob: 26/03/2003,
    address: [{flatNo: 657, buildingNo: block-a}]
    
}

```

#### Response(sample)

```
{
    status: 201,
    data: null,
    message: 'Vendor Created'
}

```

> If any other status is shown then error message has to be shown

</br>

### <u>Vendor GET API</u>

```
Type- GET
Route- BASE-URL/vendor/vendorId
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| vendorId     |  String   |   true   | in `params` |
| currentToken |  String   |   true   |  in `body`  |

##### Request(Sample)

```
{
	// in params
	vendorId: '61efde4424e70f34c8f44fbb'
},
{
	// in body
	currentToken: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MWVmZGU0NDI0...'
}
```

##### Response(Success)

```
{
	status: 200,
    data: {
        _id: "61efde4424e70f34c8f44fbb",
        name: "kelore",
        phoneNumber: "8901929309",
        email: "qwert@gmail.com",
        dob: "26/03/2003",
        address: [
            {
                _id: 61efde4424e70f34c8f44fbc,
                flatNo: 65,
                buildingNo: block-a
            }
        ]
    },
    message: "Success"
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

### <u> Vendor Login API</u>

```
Type: POST
Route: BASE-URL/vendor/login
```

#### Parameters:

| Param Name | Data Type | Required | Remarks |
| ---------- | :-------: | :------: | :-----: |
| email      |  String   |   true   |
| password   |  String   |   true   |

##### Request(Sample)

```
{
	email: "qwert@gmail.com",
    password: "jekekrlkell"
}
```

##### Response(Success)

```
{
	status: 200,
    data: {
        _id: "61efac5b7adf89327477c5eb",
        name: "kelore",
        email: "qwert@gmail.com",
        dob: "26/03/2003",
        address: [
            {
                "_id": "61efac5b7adf89327477c5ec",
                "flatNo": "657",
                "buildingNo": "block-a"
            }
        ],
        productModify: True
        currentToken: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
    },
    message: "Vendor login successfull"
}
```

>Note the status is 200 Even if vendor's credentials are correct but he/she is unverified in that case currentToken will not be present in data and product modify will be false also message: "Vendor unverified".

---

</br>

### <u>Logout API</u>

```
Type: POST
Route: BASE-URL/vendor/logout
```

#### Parameters:

| Param Name   | Data Type | Required | Remarks |
| ------------ | :-------: | :------: | :-----: |
| currentToken |  String   |   true   |

##### Request(Sample)

```
{
	currentToken: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Vendor Logged out'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Generate Otp for a email API</u>

```
Type: POST
Route: BASE-URL/vendor/new-email-otp
```

#### Parameters:

| Param Name | Data Type | Required | Remarks |
| ---------- | :-------: | :------: | :-----: |
| vendorEmail|  String   |   true   |

##### Request(Sample)

```
{
	vendorEmail: "qwert@gmail.com"
}
```
