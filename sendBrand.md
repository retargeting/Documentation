#**sendBrand**

####*This function must be called every time a visitor goes to the producer/brand page. In this case, the brand page is the page where the brand details are listed, or the page that lists the products belonging to that brand.*

    var _ra = _ra || {};
    
    _ra.sendBrandInfo = {
		"id": brand_id,
		"name": "brand_name"
	};

	if (_ra.ready !== undefined) {
	_ra.sendBrand(_ra.sendBrandInfo);
	}

##**sendBrand** function parameters


|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The brand item identifier.  |
|	name	|	Text	|	Required	|	The brand name	|


----------

##**sendBrand function examples**
----------

### *sending a product without discount, with brand, belonging to a category without parent*
	
	var _ra = _ra || {};

	_ra.sendBrandInfo = {
		"id": 50,
		"name": "Lee Cooper"
	};
	
	if (_ra.ready !== undefined) {
		_ra.sendBrand(_ra.sendBrandInfo);
	}
	