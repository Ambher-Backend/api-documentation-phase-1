## API documentation for the customer APIs.
> `BASE-URL` will be anything, for testing, backend team will be providing a dummy API.


***
### <u>Sign-up API</u>
```
Type: POST
Route: BASE-URL/customer/signup
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| name |String|true
| phoneNumber | String |true
| email | String |true
| password | String |true |minimum length: 8
| dob | String |true


##### Request(Sample)
```
{
	name: 'Customer-1',
	phoneNumber: '9412222200',
	email: 'abc@demo.com',
	password: '12345678',
    	dob: '04-12-2001'
}
```

##### Response(Success)
```
{
	status: 201,
	data: null,
	message: 'Customer Created'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Login API</u>
```
Type: POST
Route: BASE-URL/customer/login
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| email | String |true
| password | String |true

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
	message: 'Customer Login Successful'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Get Customer API</u>
```
Type: GET
Route: BASE-URL/admin/:adminId
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
|customerId | String | true | in `params`
|currentToken | String | true | in `body`

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
		_id: '<>',
		name: '<>',
		email: '<>',
		phoneNumber: '<>',
        	dob: '<>'
	},
	message: 'Success'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Logout API</u>
```
Type: POST
Route: BASE-URL/customer/logout
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| currentToken |String|true

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
	message: 'Customer Logged out'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Generate Otp for a email API</u>
```
Type: POST
Route: BASE-URL/customer/new-email-otp
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| customerEmail | String |true

##### Request(Sample)
```
{
	customerEmail: 'abc@demo.com'
}
```

##### Response(Success)
```
{
	status: 200,
	data: null,
	message: 'Customer Email OTP sent successfully'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Verify Otp for a email API</u>
```
Type: POST
Route: BASE-URL/customer/verify-email-otp
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| customerEmail | String |true
| otp | String |true

##### Request(Sample)
```
{
	customerEmail: 'abc@demo.com',
	otp: '123456'
}
```

##### Response(Success)
```
{
	status: 400,
	data: null,
	message: 'Customer Email OTP verified successfully'
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
</br>

### <u>Create dummy Customer</u>
```
Type: POST
Route: BASE-URL/customer/create-dummy-data
```
#### Parameters:

| Param Name    | Data Type     | Required      | Remarks       |
| ------------- |:-------------:|:-------------:|:-------------:|
| internalAuthKey | String |true
| currentToken | String |true
| deleteExisting | Boolean |true
| total | Number |true



##### Request(Sample)
```
{
    internalAuthKey: 'dummyKey',
    currentToken: '12345634fg34b5b4',
    deleteExisting: true,
    total: 10

}
```

##### Response(Success)
```
{
	status: 201,
	data: null,
	message: `All documents from collection || Customer || deleted on "Sun Jan 30 2022 23:27:56 GMT+0530 (India Standard Time)" by 'Admin'`
}
```
> If any other status is received, then simply show failure and the message(response structure will be same)
***
