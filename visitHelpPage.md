#**visitHelpPage**

####*This function must be called every time a visitor visits one of the Help Pages of the site (e.g. How to order?, FAQ, How I get the products?)*

    	_ra.visitHelpPage(callback_function);
	
### *OR executing scripts automatically when the page is loaded*
	
	var _ra = _ra || {};
	
	_ra.visitHelpPageInfo = {
		"visit" : true
	}

	if (_ra.ready !== undefined) {
		_ra.visitHelpPage();
	}
	
##**visitHelpPage** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  visit  |  Bool  |  Required  |  True  |
|	callback_function 	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action's parent function executes.	|

##**visitHelpPage function examples**
----------

	var _ra = _ra || {};
	
	_ra.visitHelpPageInfo = {
		"visit" : true
	}
	
	if (_ra.ready !== undefined) {
		_ra.visitHelpPage();
	}