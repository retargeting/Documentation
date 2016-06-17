#**clickImage**

####*This function must be called every time a visitor opens the main image of the product in the product detail page.*

	_ra.clickImage(product_id, callback_function);

###*OR executing scripts automatically when the page is loaded*

	var _ra = _ra || {};
	
	_ra.clickImageInfo = {
		"product_id" : product_id
	};
	
	if (_ra.ready !== undefined) {
		_ra.clickImage(_ra.clickImageInfo.product_id);
	}
	
##**clickImage** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  product id the picture belongs to.  |
|	callback_function	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action’s parent function executes	|



##**clickImage function examples**

####*sending click on the image event with callback function*
	
	_ra.clickImage(100, function() {
		console.log("the informations have been sent");
	});
	
####*sending click on the image event with no callback function*
	
	_ra.clickImage(100);
	