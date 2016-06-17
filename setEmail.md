#**setEmail**

####*This function needs to be called each time a guest register, logs in or completes the email address in a form from the website (e.g. Contact or Newsletter Form).*

	_ra.setEmail({
		"email": "email_address",
		"name": "full_name",
		"phone": "phone_number",
		"city": "city_name",
		"sex": sex_code
	}, callback_function);
	
### *OR executing scripts automatically when the page is loaded*
	
	var _ra = _ra || {};
	
	_ra.setEmailInfo = {
		"email": "email_address",
		"name": "full_name",
		"phone": "phone_number",
		"city": "city_name",
		"sex": sex_code
	};
	
	if (_ra.ready !== undefined) {
		_ra.setEmail(_ra.setEmailInfo)
	}

##**setEmail** function parameters


|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  email  |  Email  |  Required  |  Guest email address.  |
|	name	|	Text	|	Optional	|	Guest name.	|
|	phone	|	Text	|	Optional	|	Guest phone number.	|
|	city	|	Text	|	Optional	|	Guest town.	|
|	sex	|	Text	|	Optional	|	This parameter is numeric and has two possible values: 0 - woman and 1 - man	|
|	callback_function	|	Function	|	Optional	| With this parameter you can define a function that runs itself after the action's parent function executes. |

##**setEmail function examples**
----------

### *function call with all complete parameters and callback function*
	
	_ra.setEmail({
		"email": "johndoe@mail.com",
		"name": "John Doe",
		"phone": "0777222000",
		"city": "Targoviste",
		"sex": 1
	}, function() {
		console.log("setEmail informations have been sent");
	});
	
### *function call only with mandatory*
	
	_ra.setEmail({
		"email": "johndoe@mail.com"
	});
	