#**sendProduct**

####*This function must be called every time a visitor clicks on a product details page.*

    var _ra = _ra || {};
    
	_ra.sendProductInfo = {
		"id": product_id,
		"name": "product_name",
		"url": "product_url",
		"img": "product_main_image_src",
		"price": product_price,
		"promo": product_promotional_price,
		"stock": stock,
		"brand": {
			"id": brand_id,
			"name": "brand_name",
		},
		"category": {
			"id": category_id,
			"name": "category_name",
			"parent": parent_category_id
		},
		"category_breadcrumb": [
			{
				"id": parent_category_id,
				"name": "parent_category_name",
				"parent": parent_of_parent_category_id
			},
			...
		]
	};
	
	if (_ra.ready !== undefined) {
		_ra.sendProduct(_ra.sendProductInfo);
	}

##**sendProduct** function parameters


|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The product item identifier, ie. itemcode. It should identify to the sold product, but not necessarily some specific variant of the product. Must be unique in your site.  |
|	name	|	Text	|	Required	|	The product name	|
|	url	|	URL	|	Required	|	Complete URL of the item. Must start with http:// or https://.	|
|	img	|	URL	|	Required	|	Complete URL of an image of the item.	|
|	price	|	Number or text	|	Required	|	Current product price. If the product is on promotion (price is reduced) then this parameter gets the value of the price before promotion was applied to the product (old price).	|
|	promo	|	Number or text	|	Optional	|	Promotional price (new price). When the product isn’t on promotion (no reduced price), send value 0.	|
|	stock	|	Bool (0/1)	|	Required	|	Stock of the product.For product in stock send value 1. When the product isn’t on stock send value 0.	|
|	brand	|	Object	|	Required	|	Details about product brand. If the product does not belong to any brand, send false value. The object containing brand details, has the following properties: id, name.	|
|	brand.id	|	Number or text	|	Required	|	The brand item identifier.	|
|	brand.name	|	Text	|	Required	|	Brand name	|
|	category	|	Object	|	Required	|	An object that contain details about products category. The object should contain the following properties: id, name, parent	|
|	category.id	|	Number or text	|	Required	|	The category identifier	|
|	category.name	|	Text	|	Required	|	Category name	|
|	category.parent	|	Number, text, false	|	Required	|	Id of parent category. If there isn’t any parent category, send false value.	|
|	category_breadcrumb	|	Array	|	Required	|	Array containing all the parent categories of the category to which the product belongs (in this array you must not add the product category). If the category does not have a parent category (category.parent is set false), send an empty array. Each parent category is sent as object and contains the following properties: id, name, parent.	|
|	category_breadcrumb.id	|	Number or text	|	Required	|	Category id	|
|	category_breadcrumb.name	|	Text	|	Required	|	Category Name	|
|	category_breadcrumb.parent	|	Number, text, false	|	Required	|	Id of parent category. If there isn’t any parent category, send false value.	|
|	callback_function	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action’s parent function executes	|


----------

##**sendProduct function examples**
----------

### *sending a product without discount, with brand, belonging to a category without parent*
	
	var _ra = _ra || {};
	
	_ra.sendProductInfo = {
		"id": 100,
		"name": "Black leather gloves",
		"url": "http://site.com/accessories/black-leather-gloves",
		"img": "http://site.com/public/product-images/black-leather-gloves.jpg", 
		"price": 125,
		"promo": 0,
		"stock": 1,
		"brand": {
			"id": 22,
			"name": "Brand name",
		},
		"category": {
			"id": 80,
			"name": "Accessories",
			"parent": false
		},
		"category_breadcrumb": []
	}
	
	if (_ra.ready !== undefined) {
		_ra.sendProduct(_ra.sendProductInfo);
	}
	
### *sending a product without discount, with brand, belonging to a category without parent*
	

	_ra.sendProductInfo = {
		"id": 75,
		"name": "Sport sneakers red",
		"url": "http://site.com/shoes/sneakers/sport-sneakers/sport-sneakers-red", 
	  	"img": "http://site.com/public/product-images/sport-sneakers-red.jpg", 
	  	"price": 420,
		"promo": 380,
		"stock": 1,
		"brand": false,
		"category": {
			"id": 22,
			"name": "Sport sneakers", 
			"parent": 21
		},
		"category_breadcrumb": [
			{"id": 21, "name": "Sneakers", "parent": 20},
			{"id": 20, "name": "Shoes", "parent": false}
		]
	};
	
	if (_ra.ready !== undefined) {
		_ra.sendProduct(_ra.sendProductInfo);
	}