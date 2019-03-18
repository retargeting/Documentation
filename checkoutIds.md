#**checkoutIds**

####*This function must be called every time a visitor reaches the page where he can add the discount code - checkout page.*

    var _ra = _ra || {};
    
	_ra.checkoutIdsInfo = [product_id, product_id, ...];
	
	if (_ra.ready !== undefined) {
		_ra.checkoutIds(_ra.checkoutIdsInfo);
	}
	
##**checkoutIds** function parameters

This function takes as a parameter an array containing all the IDs of the products that the visitor intends to purchase (ID`s of all products from the shopping cart).

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  product_id  |  Number or text  |  Required  |  The product id .  |


##**checkoutIds function examples**

	var _ra = _ra || {};
	
	_ra.checkoutIdsInfo = [100, 110, 200];
	
	if (_ra.ready !== undefined) {
	  _ra.checkoutIds(_ra.checkoutIdsInfo);
	}
