```PHP
<script>
document.addEventListener('DOMContentLoaded', function() {
	var theSelectedPost = document.querySelector(".aaaaaaaaaaaa select");
	theSelectedPost.addEventListener('change', function handleChange(event) {
		
		var value = theSelectedPost.options[theSelectedPost.selectedIndex].value;
		document.cookie = "myJavascriptVar = " + value;
	});
}, false);
</script>
<?php
$phpVar =  $_COOKIE['myJavascriptVar'];
var_dump($phpVar);
```
