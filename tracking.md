#**Tracking Code**

####*In order for Retargeting to record the necessary events from your site, you have to insert the following javascript code right before closing the `<head>` tag.*

	<script type="text/javascript">
	(function(){
	ra_key = "your_retargeting_key";
 	ra_params = {
	    add_to_cart_button_id: 'add_to_cart_button_id',
	    price_label_id: 'price_label_id',
	};
	var ra = document.createElement("script"); ra.type ="text/javascript"; ra.async = true; ra.src = ("https:" ==
	document.location.protocol ? "https://" : "http://") + "tracking.retargeting.biz/v3/rajs/" + ra_key + ".js";
	var s = document.getElementsByTagName("script")[0]; s.parentNode.insertBefore(ra,s);})();
	</script>

##**Tracking Code** function parameters


|    **Parameter**    |    **Type**    |    **Required**    |    **Description**    |
|---|---|---|---|
|  ra_key  |  Text  |  Required  | API Key. You can get it from your Retargeting Account > Settings > Docs & API.  |
|  ra_params  |  Object  |  Optional  | An object with two parameters: add_to_cart_button_id and price_label_id.  |

	
This code is loaded asynchronous, which means it won't slow down in any mode the page load time and it will work independently from your application.