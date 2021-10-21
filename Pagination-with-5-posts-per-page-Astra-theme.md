```PHP
/**
 * Location: functions.php
 */
 
function frhd_blog_page_pagination( $query ) {
	
    if ( $query->is_home() && $query->is_main_query() ) {
		
        $query->set( 'posts_per_page', 5 );
    }
}
add_action( 'pre_get_posts', 'frhd_blog_page_pagination' );
```
