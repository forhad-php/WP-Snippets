```PHP
// https://wpastra.com/docs/astra-default-strings/
// Filter callback function
function example_callback( $strings ) {
    $strings['string-blog-meta-author-by'] = __( 'Writing By ', 'astra' );
    return $strings;
}
add_filter( 'astra_default_strings', 'example_callback', 10 );
```
