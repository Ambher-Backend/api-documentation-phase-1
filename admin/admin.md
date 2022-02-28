## API documentation for Main Admin APIs.

> `BASE-URL` will be anything, for testing, backend team will be providing a dummy API.

---

### <u>Sign-up API</u>

```
Type: POST
Route: BASE-URL/admin/signup
```

#### Parameters:

| Param Name  | Data Type | Required |      Remarks      |
| ----------- | :-------: | :------: | :---------------: |
| name        |  String   |   true   |
| phoneNumber |  String   |   true   |
| email       |  String   |   true   |
| password    |  String   |   true   | minimum length: 8 |

##### Request(Sample)

```
{
	name: 'Admin-1',
	phoneNumber: '9412222200',
	email: 'abc@demo.com',
	password: '12345678'
}
```

##### Response(Success)

```
{
	status: 201,
	data: null,
	message: 'Admin Created'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Login API</u>

```
Type: POST
Route: BASE-URL/admin/login
```

#### Parameters:

| Param Name | Data Type | Required | Remarks |
| ---------- | :-------: | :------: | :-----: |
| email      |  String   |   true   |
| password   |  String   |   true   |

##### Request(Sample)

```
{
	email: 'abc@demo.com',
	password: '12345678'
}
```

##### Response(Success)

```
{
	status: 200,
	data: {
		_id: '<>',
		name: '<>',
		email: '<>',
		currentToken: '<>'
	},
	message: 'Admin Login Successful'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Get Admin API</u>

```
Type: GET
Route: BASE-URL/admin/adminId
```

#### Parameters:

| Param Name   | Data Type | Required |   Remarks   |
| ------------ | :-------: | :------: | :---------: |
| adminId      |  String   |   true   | in `params` |
| currentToken |  String   |   true   | in `params` |

##### Request(Sample)

```
{
	// in req.params
	adminId: '13544643g535g'
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
		_id: '<>',
		name: '<>',
		email: '<>',
		phoneNumber: '<>'
	},
	message: 'Success'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Logout API</u>

```
Type: POST
Route: BASE-URL/admin/logout
```

#### Parameters:

| Param Name   | Data Type | Required | Remarks |
| ------------ | :-------: | :------: | :-----: |
| currentToken |  String   |   true   |

##### Request(Sample)

```
{
	currentToken: '12ef3vf3v4f35v3vcv3'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Admin Logged out'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Generate Otp for a email API</u>

```
Type: POST
Route: BASE-URL/admin/new-email-otp
```

#### Parameters:

| Param Name | Data Type | Required | Remarks |
| ---------- | :-------: | :------: | :-----: |
| adminEmail |  String   |   true   |

##### Request(Sample)

```
{
	adminEmail: 'abc@demo.com'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Admin Email OTP sent successfully'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---

</br>

### <u>Verify Otp for a email API</u>

```
Type: POST
Route: BASE-URL/admin/verify-email-otp
```

#### Parameters:

| Param Name | Data Type | Required | Remarks |
| ---------- | :-------: | :------: | :-----: |
| adminEmail |  String   |   true   |
| otp        |  String   |   true   |

##### Request(Sample)

```
{
	adminEmail: 'abc@demo.com',
	otp: '123456'
}
```

##### Response(Success)

```
{
	status: 200,
	data: null,
	message: 'Admin Email OTP verified successfully'
}
```

> If any other status is received, then simply show failure and the message(response structure will be same)

---
