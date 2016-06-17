#**Tracking Code**

####*In order for Retargeting to record the necessary events from your site, you have to insert the following javascript code right before closing the `<head>` tag.*

	<script type="text/javascript">
	(function(){
	var ra = document.createElement("script"); ra.type ="text/javascript"; ra.async = true; ra.src = ("https:" ==
	document.location.protocol ? "https://" : "http://") + "retargeting-data.eu/" +
	document.location.hostname.replace("www.","") + "/ra.js"; var s =
	document.getElementsByTagName("script")[0]; s.parentNode.insertBefore(ra,s);})();
	</script>
	
This code is loaded asynchronous, which means it won't slow down in any mode the page load time and it will work independently from your application.