```PHP
/**
 * Show SKU on single product pages.
 */
add_action( 'woocommerce_single_product_summary', 'doggietoys_show_sku', 5 );
function doggietoys_show_sku(){
    global $product;
    echo 'SKU: ' . $product->get_sku();
}
```
