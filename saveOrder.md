#**saveOrder**

This function must be called whenever an order is successfully registered.

For any payment method, the function saveOrder must be called always on the Thank You page (the page where the user is informed the order was registered). If there is no Thank You page, saveOrder function must be called after the order is successfully stored in the database.

For example, for online payment method, saveOrder function must be called after the response from the payment processor is received and the answer is positive (not error or fail). In this case it means the order is successfully registered (was paid). saveOrder function must be called on the Thank You page, when all the registration process of the order is over.

	var _ra = _ra || {};
	
	_ra.saveOrderInfo = {
		"order_no": unique_order_number,
		"lastname": "buyer_last_name",
		"firstname": "buyer_first_name",
		"email": "buyer_email",
		"phone": "buyer_phone",
		"state": "buyer_state",
		"city": "buyer_city",
		"address": "buyer_address",
		"discount_code": "discount_code",
		"discount": total_discount_value,
		"shipping": shipping_value,
		"total": total_order_value
	};
		
	_ra.saveOrderProducts = [
		{
			"id": product_id,
			"quantity": product_quantity,
			"price": unit_product_price,
			"variation_code": "product_variation_code"
		},
			...
	];
		
	if( _ra.ready !== undefined ){
		_ra.saveOrder(_ra.saveOrderInfo, _ra.saveOrderProducts);
	}
	
##**saveOrder** function parameters

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  order_no  |  Number or text  |  Required  |  Unique number of the order recorded  |
|  lastname  |  Text  |  Required  |  name of the buyer |
|  firstname  |  Text  |  Required  |  buyer surname  |
|  email  |  Email  |  Required  |  buyer e-mail address  |
|  phone  |  Text  |  Required  |  phone number of the buyer  |
|  state  |  Text  |  Required  |  district address  |
|  city  |  Text  |  Required  |  city address  |
|  adress  |  Text  |  Required  |  buyer address  |
|  discount  |  Number/0  |  Required  |  the amount / value by which the total amount was reduced. Note that we are not talking about the discount value (e.g. 10%), but the money amount (e.g. 5$ discount for a 100$ order). If there is no discount applied on the order, send value 0.  |
|  discount_code  |  Text  |  Required  |  the discount code used when placing the order.  |
|  shipping  |  Text  |  Required  |  value / amount paid for the shipping (shipping fee). If there is no shipping charge, send value 0.  |
|  total  |  Text  |  Required  |  amount / total amount of payment for the order sent. Note that this the total amount the buyer actually pays, the amount obtained after applying any discount and/or shipping fee.  |

Products ordered are contained in the second parameter of the function, which is Array type. Details for each product are added in Array through an object that has the following properties: id, quantity, price, variation_code

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  products.id  |  Text  |  Required  |  product ID  |
|  products.quantity  |  Text  |  Required  |  quantity ordered  |
|  products.price  |  Text  |  Required  |   unit price of the product (per piece)  |
|  products.variation_code  |  Text  |  Required  |  variation code of sent product – for variation code format and other details see variations addToCart functions and setVariation. If the product does not have variation will send a empty string (no character string "")  |
|	callback_function 	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action's parent function executes.	|

If a visitor buys the same product, but with two different variations ( one yellow shirt and two red shirts ), they will be sent as two different objects (an object for yellow variation and one object for red variation quantity two, both objects with the same value for the property id).

##**visitHelpPage function examples**
----------

###*sending an order with all details completed*

	var _ra = _ra || {};
		
	_ra.saveOrderInfo = {
		"order_no": 25,
		"lastname": "Doe",
		"firstname": "John",
		"email": "johndoe@mail.com",
		"phone": "0700555888",
		"state": "Dambovita",
		"city": "Targoviste",
		"address": "Bd. Independentei",
		"discount": 20,
		"discount_code": "RAX204",
		"shipping": 19,
		"total": 199
	};
	_ra.saveOrderProducts = [
		{"id": 307, "quantity": 1, "price": 18, "variation_code": ""},
		{"id": 48, "quantity": 2, "price": 300, "variation_code": "R-S"},
		{"id": 48, "quantity": 1, "price": 300, "variation_code": "Y-S"},
		{"id": 50, "quantity": 1, "price": 22, "variation_code": "Y-S"}
	];
	
	if( _ra.ready !== undefined ){
		_ra.saveOrder(_ra.saveOrderInfo, _ra.saveOrderProducts);
	}