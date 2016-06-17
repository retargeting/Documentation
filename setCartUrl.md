#**setCartUrl**

####*This function saves the url of shopcart page. If you do not use this function, the url of shopcart page is taken when the checkoutIds functions is called.*

	var _ra = _ra || {};

    _ra.setCartUrlInfo = {
        "url": "shopcart_page_url"
    };
    
    if (_ra.ready !== undefined) {
        _ra.setCartUrl(_ra.setCartUrlInfo.url);
    }
	
##**setCartUrl** function parameters

The function has only one parameter.

|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  url  |  URL  |  Required  |  url of shopcart page  |


##**setCartUrl function examples**

    var _ra = _ra || {};
    
    _ra.setCartUrlInfo = {
        "url": "http://site.com/shopcart-page"
    };
    
    if (_ra.ready !== undefined) {
        _ra.setCartUrl(_ra.setCartUrlInfo.url);
    }