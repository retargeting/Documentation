#**addToCart**

####*This function must be called every time a product is added to cart.*
####*If you redirect to another page (e.g. the checkout page) right after the user added the product to cart, the add to cart must be set in the function of the callback function, right after the data has been sent to Retargeting (see the examples of the addToCart function).*
####*If add to cart is possible in other pages too, other than in the product details page, you must first call the sendProduct function (for the product that will be added to cart) right before you call the addToCart function (see the examples of the addToCart function).*
####*In the following paragraphs of the addToCart function, we will talk about "variations" of the products. Variation of a product is the product properties group the user has to choose when he is willing to add a product to cart: color, size, capacity, etc. For example, an online fashion store can set a system based on color and size variations: "Y-32" (yellow color and size 32), "R-XS" (red color and size XS), "M" (size M) etc.*

    _ra.addToCart(product_id, quantity, {
        "code": "var_code",
        "stock": stock,
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
        "quantity": product_quantity, 
        "variation": {
            "code": "var_code",
            "stock": stock,
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
        _ra.addToCart(
            _ra.addToCartInfo.product_id,
            _ra.addToCartInfo.quantity,
            _ra.addToCartInfo.variation
        );
    }
	
##**addToCart** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The ID of the product.  |
|  quantity  |  Number or text  |  Required  |  Product quantity.  |
|	variation	|	Object / False	|	Required	|	object with details about chosen variation details for the product added to cart. If the product does not have variation send false value. The object containing the details of the chosen variation has the following properties: code, details	|
|	variation.code	|	Text	|	Required	|	unique combination of properties that form the variation of product, separated by simple line (-). It is mandatory to use a simple dash (-) to separate the options of variation.	|
|	variation.stock	|	Bool	|	Required	|	false - out of stock, true - in stock	|
|	variation.details	|	Object	|	Required	|	The product name	|
|	variation.details.variation_code_option.category_name	|	Text	|	Required	|	 object that contains details about each variation option. Object details contains properties with the name of the property codes variation, and each property is an object containing the following properties: category_name, category, value	|
|	variation.details.variation_code_option.category	|	Text	|	Required	|	Unique token or unique id of the category to which it belongs variation_code_option property code	|
|	variation.details.variation_code_option.value	|	Text	|	Required	|	Full name of the variation_code_option property code	|
|	callback_function 	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action's parent function executes.	|

##**addToCart function examples**
----------

#### *send add to cart event for a product without variation adding to cart is done in the product page*	
	_ra.addToCart(50, 1, false, function() {
        console.log("the informations have been sent");
    });
	
#### *executing scripts automatically when the page is loaded.*
	
	_ra.addToCartInfo = {
        "product_id": 133,
        "quantity": 1,
        "variation": {
            "code": "42-B",
            "stock": true,
            "details": {
                "42": {
                    "category_name": "Size",
                    "category": "size",
                    "value": "42"
                },
                "B": {
                    "category_name": "Color",
                    "category": "color",
                    "value": "Black"
                }
            }
        }
    };
	
    if (_ra.ready !== undefined) {
        _ra.addToCart(
            _ra.addToCartInfo.product_id,
            _ra.addToCartInfo.quantity,
            _ra.addToCartInfo.variation
        );
    }	
