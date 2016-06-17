#Product Feed
In order for Retargeting to display only products available in stock you need to create a XML feed that returns some informations about products.

	<products>
	        <product>
	            <id>product_id</id>
	            <price>product_price</price>
	            <promo>product_promotional_price</promo>
	            <inventory>
	                <variations>1</variations>
	                <stock>
	                    <variation>
	                        <code>variation-code-1</code>
	                        <stock>1</stock>        
	                    <variation>    
	                    <variation>
	                        <code>variation-code-2</code>
	                        <stock>0</stock>        
	                    <variation>
	                    ...
	                </stock>
	            </inventory>
	        </product>
	    </products>

##Feed file fields

**products**: a block with products

**product**: a block of product information

**id**: product id

**stock**: 0 - not in stock, 1 - is in stock.

**price**: product price. If the product is on promotion (is reduced) then this parameter receives the price before the reduction (old price).

**promo**: promotional price (new price) of the product. When the product has no discount, send the value 0.

##Feed file examples

*In order to make the file smaller it is not necessary to send products with no stock*  
	
    <products>
        <product>
            <id>75</id>
            <price>28.99</price>
            <promo>19.99</promo>
            <inventory>
                <variations>1</variations>
                <stock>
                    <variation>
                        <code>42-M</code>
                        <stock>1</stock>        
                    <variation>    
                    <variation>
                        <code>42-S</code>
                        <stock>0</stock>        
                    <variation>
                </stock>
            </inventory>
        </product>
        <product>
            <id>28</id>
            <price>135.99</price>
            <promo>0</promo>
            <inventory>
                <variations>0</variations>
                <stock>1</stock>
            </inventory>
        </product>
    </products>