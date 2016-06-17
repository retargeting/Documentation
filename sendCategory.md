#**sendCategory**

####*This function must be called when a visitor goes to a category page. In this case, the category page is the page that displays the category details and the list of subcategories belonging to the first or the page that lists the products of a certain category.*

	var _ra = _ra || {};
	
	_ra.sendCategoryInfo = {
		"id": category_id,
		"name" : "category_name",
		"parent": parent_category_id,
		"category_breadcrumb": [
			{
					"id": parent_category_id,
					"name": "parent_category_name",
					"parent": parent_of_parent_category_id
				},
				...
			]
		}

	if (_ra.ready !== undefined) {
		_ra.sendCategory(_ra.sendCategoryInfo);
	}

##**sendBrand** function parameters


|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  id  |  Number or text  |  Required  |  The category identifier.  |
|	name	|	Text	|	Required	|	The category name	|
|	parent	|	Number, text, false	|	Required	|	ID of parent category. If there isn’t any parent category, send false value.	|
|	category_breadcrumb	|	Array	|	Required	|	Array containing all the parent categories of the category to which the product belongs (in this array you must not add the product category). If the category does not have a parent category (category.parent is set false), send an empty array. Each parent category is sent as object and contains the following properties: id, name, parent.	|
|	category_breadcrumb.id	|	Number or text	|	Required	|	Category id	|
|	category_breadcrumb.name	|	Text	|	Required	|	Category Name	|
|	category_breadcrumb.parent	|	Number, text, false	|	Required	|	Id of parent category. If there isn’t any parent category, send false value.	|
|	callback_function	|	Function	|	Optional	|	With this parameter you can define a function that runs itself after the action’s parent function executes	|


##**senCategory function examples**
----------

### *sending a category without parent*
	
	var _ra = _ra || {};
	
	_ra.sendCategoryInfo = {
		"id": 20,
		"name": "Shoes",
		"parent": false,
		"category_breadcrumb": [] 
	};
	
	if (_ra.ready !== undefined) {
		_ra.sendCategory(_ra.sendCategoryInfo);
	}
	
### *sending a category with one subcategory level*
	
	var _ra = _ra || {};
	
	_ra.sendCategoryInfo = {
		"id": 21,
		"name": "Sneakers",
		"parent": 20,
		"category_breadcrumb": [
			{"id": 20, "name": "Shoes", "parent": false}
		]
	};
	
	if (_ra.ready !== undefined) {
		_ra.sendCategory(_ra.sendCategoryInfo);
	}
	
### *sending a category with two subcategory level*
	
	var _ra = _ra || {};
	
	_ra.sendCategoryInfo = {
		"id": 22,
		"name": "Sport sneakers",
		"parent": 21,
		"category_breadcrumb": [
			{"id": 21, "name": "Sneakers", "parent": 20},
			{"id": 20, "name": "Shoes", "parent": false}
		]
	}
	
	if (_ra.ready !== undefined) {
		_ra.sendCategory(_ra.sendCategoryInfo);
	}
	