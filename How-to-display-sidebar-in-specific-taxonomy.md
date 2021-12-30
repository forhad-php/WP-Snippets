```PHP
/**
 * Theme: Astra
 * Location: ..\wp-content\themes\astra\single.php
 */
if ( has_tag( 'info' ) ) {

	get_sidebar();

	echo '<style>
	@media (min-width: 922px) {
		#primary {
			width: 70%;
		}
		#secondary {
			width: 30%;
		}
	}
	
	#secondary {
		margin: 4em 0 2.5em;
		word-break: break-word;
		line-height: 2;
	}
	
	@media (min-width: 993px) {
	
		#secondary {
			padding-left: 60px;
		}
	}
	</style>';
}



/**
 * Theme: GeneratePress
 * Location: functions.php
 */
function frhd_generate_custom_category_sidebar_layout( $layout ) {

 	if ( in_category( array('Blog', 'Uncategorized', 'Information') ) ) {

 	 	return 'right-sidebar';
	} else {

		return 'no-sidebar';
	}

 	// Or else, set the regular layout
 	return $layout;

}
add_filter( 'generate_sidebar_layout','frhd_generate_custom_category_sidebar_layout' );
```
