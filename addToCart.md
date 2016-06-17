#**addToCart**

####*This function must be called every time a product is added to cart.*
####*If you redirect to another page (e.g. the checkout page) right after the user added the product to cart, the add to cart must be set in the function of the callback function, right after the data has been sent to Retargeting (see the examples of the addToCart function).*
####*If add to cart is possible in other pages too, other than in the product details page, you must first call the sendProduct function (for the product that will be added to cart) right before you call the addToCart function (see the examples of the addToCart function).*
####*In the following paragraphs of the addToCart function, we will talk about "variations" of the products. Variation of a product is the product properties group the user has to choose when he is willing to add a product to cart: color, size, capacity, etc. For example, an online fashion store can set a system based on color and size variations: "Y-32" (yellow color and size 32), "R-XS" (red color and size XS), "M" (size M) etc.*

	_ra.addToCart(product_id, {
		"code": "var_code",
		"details": {
			"var_code_option": {
				"category_name": "var_code_option_category_name",
				"category": "var_code_option_category_unique_token",
				"value": "var_code_option_value_name"
			},
			...
		}
	}, callback_function);
	
### *OR executing scripts automatically when the page is loaded*
	
	var _ra = _ra || {};
	
	_ra.addToCartInfo = {
		"product_id": product_id,
		"variation": {
			"code": "var_code",
			"details": {
				"var_code_option": {
					"category_name": "var_code_option_category_name",
					"category": "var_code_option_category_unique_token",
					"value": "var_code_option_value_name"
				},
				...
			}
		}
	};
	
	if (_ra.ready !== undefined) {
		_ra.addToCart(_ra.addToCartInfo.product_id, _ra.addToCartInfo.variation);
	}
	
##**addToCart** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The product id .  |
|	variation	|	Object / False	|	Required	|	object with details about chosen variation details for the product added to cart. If the product does not have variation send false value. The object containing the details of the chosen variation has the following properties: code, details	|
|	variation.code	|	Text	|	Required	|	The product name	|
|	variation.details	|	Object	|	Required	|	The product name	|
|	variation.details.variation_code_option.category_name	|	Text	|	Required	|	 object that contains details about each variation option. Object details contains properties with the name of the property codes variation, and each property is an object containing the following properties: category_name, category, value	|
|	variation.details.variation_code_option.category	|	Text	|	Required	|	Unique token or unique id of the category to which it belongs variation_code_option property code	|
|	variation.details.variation_code_option.value	|	Text	|	Required	|	Full name of the variation_code_option property code	|
|	callback_function 	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action's parent function executes.	|

##**addToCart function examples**
----------

#### *send add to cart event of a product without variation adding to cart is in the product page (it was originally called sendProduct method)*	
	_ra.addToCart(50, false, function() {
		console.log("the informations have been sent");
	});
	
#### *send add to cart event of a product with variation if adding to cart is in the product page (it was originally called sendProduct method)  and redirect after add to cart.  for example will use the method of site for add product to cart function site_add_to_cart(id, variation) function of the site add to cart will be called after being sent data to retargeting, because it is assumed that this has as effect after adding to cart redirect to checkout page.*
	
	_ra.addToCart(52, {
		"code": "Y-32",
		"details": {
			"Y": {
				"category_name": "Color",
				"category": "color",
				"value": "Yellow"
			},
			"32": {
				"category_name": "Size",
				"category": "size",
				"value": "32"
			}
		}
	}, function() {
		site_add_to_cart(52, "Y-32");
	});
	
#### *send add to cart event for a product without variation, with redirect after adding to cart to checkout page, and adding is made from the product listing page without reaching the page with details of the product (function sendProduct is not initially called) have used the same add to cart function from site site_add_cart(id, variation)*
	
	_ra.sendProduct({
		"id": 100,
		"name": "Black leather gloves", 
		"url": "http://site.com/accessories/Black-leather-gloves",
		"img": "http://site.com/public/ products-photos/Black-leather-gloves.jpg", 
		"price": 125, 
		"promo": 0, 
		"brand": false,
		"category": {
			"id": 80,
			"name": "Accessories",
			"parent": false
		},
		"category_breadcrumb": []
	}, function(){
		_ra.addToCart(100, false, function() {
			site_add_to_cart(100, false);
		});
	});