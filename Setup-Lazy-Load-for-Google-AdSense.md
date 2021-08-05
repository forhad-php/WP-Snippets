## First we need to add below script at the bottom of the page. Possibly just before the `</body>` tag.

> It's OK to use custom hook into Astra/Generatepress Theme at 'After Footer'.

```JS
<script type="text/javascript">
function downloadJSAtOnload() {
var element = document.createElement("script");
element.src = "https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js";
document.body.appendChild(element);
}
if (window.addEventListener)
window.addEventListener("load", downloadJSAtOnload, false);
else if (window.attachEvent)
window.attachEvent("onload", downloadJSAtOnload);
else window.onload = downloadJSAtOnload;
</script>
```

> This script says that, the JS src of Google ad should load after loading the current page.

## Now we create a shortcode into `functions.php` file

```PHP
function wpb_demo_shortcode() { 
	
	$frhd_gads = '<ins class="adsbygoogle" style="display:block;" data-ad-client="ca-pub-8960012494049607" data-ad-slot="1644967317" data-ad-format="auto" data-full-width-responsive="true"></ins>
	<script>
		(adsbygoogle = window.adsbygoogle || []).push({});
	</script>';

	return $frhd_gads;
}
add_shortcode('googlead', 'wpb_demo_shortcode');
```

> Add this `[googlead]` shortcode where need to show ad.
> `data-ad-client` and `data-ad-slot` values are unique for each users.


## Another situation - Lazyload only script with `data-ad-client`

```JS
<script type='text/javascript'>
var arpianLazyLoadAds = false; 
window.addEventListener("scroll", function() { 
if((document.documentElement.scrollTop != 0 && arpianLazyLoadAds === false) || 
(document.body.scrollTop != 0 && arpianLazyLoadAds === false)) { 
(function() { 
var ad = document.createElement('script'); 
ad.setAttribute('data-ad-client', 'ca-pub-xxxxxxxxxxx'); 
ad.async = true; 
ad.src = 'https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js'; 
var sc = document.getElementsByTagName('script')[0]; 
sc.parentNode.insertBefore(ad, sc); 
})(); 
arpianLazyLoadAds = true; 
} 
}, true);
</script>
```
