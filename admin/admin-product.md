## API documentation for Admin-Product APIs.

> `BASE-URL` will be anything, for testing, backend team will be providing a dummy API.

### <u>Verify Product</u>

```
Type: POST
Route: BASE-URL/admin/verify-product
```

#### Parameters:

| Param Name   | Data Type | Required | Remarks |
| ------------ | :-------: | :------: | :-----: |
| productId    |  String   |   true   |
| currentToken |  String   |   true   |

##### Request(Sample)

```
{
	productId: '8rf34hv89hg48hg34',
	currentToken: '12345634fg34b5b4'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Product Verified By Admin Successfully'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>List Products</u>

```
Type: POST
Route: BASE-URL/admin/products
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
    isVerifiedByAdmin: <true or false>,
    isBlocked: <true or false>,
    pincode: [
      '1234',
      '1234',
    ]
  },
  currentToken: '14ef34g35g'
}
```

##### Response(Success)

```
{
  status: 200,
  data: [{
    page: 1,
    objectArray: [{
      _id: '',
      displayPicture: '',
      name: '',
      shopName: '',
      orders: '',
      details: [{
        size: '',
        colors: ['', '', '']
      }],
      rating: ''
    }]
  }],
  message: 'Product List'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Product Details</u>

```
Type: GET
Route: BASE-URL/admin/product-details/productId
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| productId    |  String   |   true   | in `params` |
| currentToken |  String   |   true   | in `params` |

##### Request(Sample)

```
{
	// in req.params
	productId: '13544643g535g',
	currentToken: '12ef3vf3v4f35v3vcv3'
}
```

##### Response(Success)

```
{
  status: 200,
  data: {
    _id: '',
    profilePictureUrl: '',
    name: '',
    shopName: '',
    reviews: '',
    details: [{
      size: '',
      colors: ['', '', '']
    }],
    rating: '',
    isVerifiedByAdmin: <true or false>,
    isBlocked: <true or false>,
    blockedReason: '', // only if is isBlocked is true
    blockedBy: '', // only if is isBlocked is true
    blockedByEmail: '', // only if is isBlocked is true
    verifiedByEmail: '', // only if is isVerifiedByAdmin is true
    verifiedByName: '', // only if is isVerifiedByAdmin is true
  }
  message: 'Product Details'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Product Orders</u>

```
Type: GET
Route: BASE-URL/admin/product-details/orders
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| productId    |  String   |   true   | in `params` |
| currentToken |  String   |   true   | in `params` |

##### Request(Sample)

```
{
	productId: '13544643g535g',
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
	message: 'Product Orders'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---
