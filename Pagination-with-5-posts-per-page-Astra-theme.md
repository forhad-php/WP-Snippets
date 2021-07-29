```PHP
/**
 * Location: \wp-content\themes\astra\inc\class-astra-loop.php
 * Position: Before While Loop
 */
 
if ( !is_front_page() && is_home() ) {
  global $query_string;
  query_posts ('posts_per_page=5');
}
```
