```PHP
<?php
/**
 * Location ..\wp-content\themes\astra\single.php
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
?>
