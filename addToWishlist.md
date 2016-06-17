#**addToWishlist**

####*This function must be called every time a product is added to a wishlist. If add to wishlist can be done in other page than in the product details page (the sendProduct function is not being called), proceed the same as in addToCart function (see the examples from addToCart function).*

    _ra.addToWishlist(product_id, callback_function);
	
### *OR executing scripts automatically when the page is loaded*
	
	var _ra = _ra || {};
	
	_ra.addToWishlistInfo = {
		"product_id" : product_id
	};
	
	if (_ra.ready !== undefined) {
		_ra.addToWishlist(_ra.addToWishlistInfo.product_id);
	}
	
##**addToWishlist** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The product id .  |
|	callback_function 	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action's parent function executes.	|

##**addToWishlist function examples**
----------

### *sending the addToWishlist event with callback function*
	
	_ra.addToWishlist(100, function() {
		console.log("the informations have been sent");
	});
	
### *sending the addToWishlist event with no callback function*
	
	_ra.addToWishlist(100);