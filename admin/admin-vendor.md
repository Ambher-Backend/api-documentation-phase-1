## API documentation for Admin-Vendor APIs.

> `BASE-URL` will be anything, for testing, backend team will be providing a dummy API.

### <u>Verify Vendor</u>

```
Type: POST
Route: BASE-URL/admin/verify-vendor
```

#### Parameters:

| Param Name   | Data Type | Required | Remarks |
| ------------ | :-------: | :------: | :-----: |
| vendorId     |  String   |   true   |
| currentToken |  String   |   true   |

##### Request(Sample)

```
{
	vendorId: '8rf34hv89hg48hg34',
	currentToken: '12345634fg34b5b4'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Vendor Account Verified By Admin Successfully'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>List Vendors</u>

```
Type: POST
Route: BASE-URL/admin/vendors
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
		isVerifiedByAdmin: <true or false>,
		isBlocked: <true or false>,
		address: {
			city: "Nagpur",
			state: "UP",
		}
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
					address: "",
					reviews: "",
					rating: "",
					totalOrders: "",
					totalProducts: "",
					isVerified: <true or false>,
					isVerifiedByAdmin: <true or false>,
					isBlocked: <true or false>
				},
				{
					_id: "2",
					profilePictureUrl: "",
					name: "",
					phoneNumber: "",
					email: "",
					address: "",
					reviews: "",
					rating: "",
					totalOrders: "",
					totalProducts: "",
					isVerified: <true or false>,
					isVerifiedByAdmin: <true or false>,
					isBlocked: <true or false>
				},
				{
					_id: "3",
					profilePictureUrl: "",
					name: "",
					phoneNumber: "",
					email: "",
					address: "",
					reviews: "",
					rating: "",
					totalOrders: "",
					totalProducts: "",
					isVerified: <true or false>,
					isVerifiedByAdmin: <true or false>,
					isBlocked: <true or false>
				},
			]
		},
		{
			page: 2,
			objectArray: [
				{
					_id: "4",
					profilePictureUrl: "",
					name: "",
					phoneNumber: "",
					email: "",
					address: "",
					reviews: "",
					rating: "",
					totalOrders: "",
					totalProducts: "",
					isVerified: <true or false>,
					isVerifiedByAdmin: <true or false>,
					isBlocked: <true or false>
				},
				{
					_id: "5",
					profilePictureUrl: "",
					name: "",
					phoneNumber: "",
					email: "",
					address: "",
					reviews: "",
					rating: "",
					totalOrders: "",
					totalProducts: "",
					isVerified: <true or false>,
					isVerifiedByAdmin: <true or false>,
					isBlocked: <true or false>
				},
			]
		}
	]
	message: 'Vendor List'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Vendor Details</u>

```
Type: GET
Route: BASE-URL/admin/vendor-details/vendorId
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| vendorId     |  String   |   true   | in `params` |
| currentToken |  String   |   true   | in `params` |

##### Request(Sample)

```
{
	// in req.params
	vendorId: '13544643g535g',
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
		totalOrders: "",
		totalProducts: "",
		rating: "",
		isVerifiedByAdmin: <true or false>,
		isVerified: <true or false>,
		isBlocked: <true or false>,
		blockedReason: ""; // only if isBlocked is true
		blockedBy: ""; // only if isBlocked is true
		blockedByEmail: ""; // only if isBlocked is true
		verifiedByEmail: ""; only if isVerifiedByAdmin is true
		verifiedByName: ""; only if isVerifiedByAdmin is true
	},
	message: 'Vendor Details'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Vendor Orders</u>

```
Type: GET
Route: BASE-URL/admin/vendor-details/orders
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| vendorId     |  String   |   true   | in `params` |
| currentToken |  String   |   true   | in `params` |

##### Request(Sample)

```
{
	vendorId: '13544643g535g',
	currentToken: "121d223",
},
```

##### Response(Success)

```
{
	status: 200,
	data: {
		page: 1,
		objectArray: [
			{
				_id: "1",
				vendorName: "hello",
				productName: "hello",
				status: "Hello",
				totalPrice: 11322.1231
			},
			{
				_id: "2",
				vendorName: "hello",
				productName: "hello",
				status: "Hello",
				totalPrice: 11322.1231
			},
		],
	}
	message: 'Vendor Orders'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---
