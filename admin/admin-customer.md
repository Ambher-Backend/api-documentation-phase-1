## API documentation for Admin-Customer APIs.

> `BASE-URL` will be anything, for testing, backend team will be providing a dummy API.

### <u>List Customers</u>

```
Type: POST
Route: BASE-URL/admin/customers
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| filter       |  Object   |   true   | default: {} |
| currentToken |  String   |   true   |

##### Request(Sample)

```
{
  filter: {
    // all keys are optional
    query: "Vendor Name",
    isVerified: <true or false>
    isBlocked: <true or false>,
  },
	currentToken: '12345634fg34b5b4'
}
```

##### Response(Success)

```
{
	status: 200,
	data: [
    {
      page: 1,
      objectArray: [
        {
          _id: "1",
          profilePictureUrl: "",
          name: "",
          phoneNumber: "",
          email: "",
          reviews: "",
          totalOrders: ""
        },
        {
          _id: "2",
          profilePictureUrl: "",
          name: "",
          phoneNumber: "",
          email: "",
          reviews: "",
          totalOrders: ""
        }
      ]
    },
    {
      page: 2,
      objectArray: [
        {
          _id: "3",
          profilePictureUrl: "",
          name: "",
          phoneNumber: "",
          email: "",
          reviews: "",
          totalOrders: ""
        },
        {
          _id: "4",
          profilePictureUrl: "",
          name: "",
          phoneNumber: "",
          email: "",
          reviews: "",
          totalOrders: ""
        }
      ]
    }
	]
	message: 'Customer List'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Customer Details</u>

```
Type: GET
Route: BASE-URL/admin/customer-details/customerId
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| customerId   |  String   |   true   | in `params` |
| currentToken |  String   |   true   |  in `body`  |

##### Request(Sample)

```
{
	// in req.params
	customerId: '13544643g535g'
},
{
	// in req.body
	currentToken: '12ef3vf3v4f35v3vcv3'
}
```

##### Response(Success)

```
{
	status: 200,
	data: {
		_id: "",
		profilePictureUrl: "",
		name: "",
		phoneNumber: "",
		email: "",
		address: "",
		reviews: "",
		totalOrders: "",
		isVerified: <true or false>,
		isBlocked: <true or false>,
		blockedReason: ""; // only if isBlocked is true
		blockedBy: ""; // only if isBlocked is true
		blockedByEmail: ""; // only if isBlocked is true
	},
	message: 'Customer Details'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Customer Search</u>

```
Type: GET
Route: BASE-URL/admin/customer-search/:customerEmail
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| customerEmail|  String   |   true   | in `params` |
| currentToken |  String   |   true   |  in `body`  |

##### Request(Sample)

```
{
	// in req.params
	customerEmail: 'qwert@gmail.com'
},
{
	// in req.body
	currentToken: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MjFjY2UzMDIzZmFjYzJiZ...'
}
```

##### Response(Success)

```
{
	status: 200,
	data: {
		_id: "",
		profilePictureUrl: "",
		name: "",
		phoneNumber: "",
		email: "",
		reviews: "",
		Orders: "",
		isVerified: <true or false>,
		isBlocked: <true or false>,
		blockedReason: ""; // only if isBlocked is true
		blockedBy: ""; // only if isBlocked is true
		blockedByEmail: ""; // only if isBlocked is true
	},
	message: 'Customer fetched'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same). Possible error status are; 400 and 500 and in case of error data part in the message will be null.

---
