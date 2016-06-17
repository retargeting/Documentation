#**likeFacebook**

####*This function must be called every time a visitor gives LIKE for a product in its details page.*

	_ra.likeFacebook(product_id, callback_function);

	
##**likeFacebook** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  the ID of the liked product.  |
|	callback_function	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action’s parent function executes	|

##**likeFacebook function examples**

####*sending like product event with callback function*
			
	_ra.likeFacebook(100, function() {
		console.log("the informations have been sent");
	});
	
####*sending like product event with no callback function*
	
	_ra.likeFacebook(100);
	