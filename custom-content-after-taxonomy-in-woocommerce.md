```PHP
// Add term page
add_action( 'product_cat_add_form_fields', 'wpm_taxonomy_add_new_meta_field', 10, 2 );
 
function wpm_taxonomy_add_new_meta_field() {
  // this will add the custom meta field to the add new term page
  ?>
  <div class="form-field">
    <label for="term_meta[custom_term_meta]"><?php _e( 'Details', 'wpm' ); ?></label>
    <textarea name="term_meta[custom_term_meta]" id="term_meta[custom_term_meta]" rows="5" cols="40"></textarea>
    <p class="description"><?php _e( 'Detailed category info to appear below the product list','wpm' ); ?></p>
  </div>
  <?php
}
 
// Edit term page
add_action( 'product_cat_edit_form_fields', 'wpm_taxonomy_edit_meta_field', 10, 2 );
 
function wpm_taxonomy_edit_meta_field($term) {
 
  // put the term ID into a variable
  $t_id = $term->term_id;
 
  // retrieve the existing value(s) for this meta field. This returns an array
  $term_meta = get_option( "taxonomy_$t_id" );
  $content = $term_meta['custom_term_meta'] ? wp_kses_post( $term_meta['custom_term_meta'] ) : '';
  $settings = array( 'textarea_name' => 'term_meta[custom_term_meta]' );
  ?>
  <tr class="form-field">
  <th scope="row" valign="top"><label for="term_meta[custom_term_meta]"><?php _e( 'Details', 'wpm' ); ?></label></th>
    <td>
      <?php wp_editor( $content, 'product_cat_details', $settings ); ?>
      <p class="description"><?php _e( 'Detailed category info to appear below the product list','wpm' ); ?></p>
    </td>
  </tr>
<?php
}
 
// Save extra taxonomy fields callback function
add_action( 'edited_product_cat', 'save_taxonomy_custom_meta', 10, 2 );  
add_action( 'create_product_cat', 'save_taxonomy_custom_meta', 10, 2 );
 
function save_taxonomy_custom_meta( $term_id ) {
  if ( isset( $_POST['term_meta'] ) ) {
    $t_id = $term_id;
    $term_meta = get_option( "taxonomy_$t_id" );
    $cat_keys = array_keys( $_POST['term_meta'] );
    foreach ( $cat_keys as $key ) {
      if ( isset ( $_POST['term_meta'][$key] ) ) {
        $term_meta[$key] = wp_kses_post( stripslashes($_POST['term_meta'][$key]) );
      }
    }
    // Save the option array.
    update_option( "taxonomy_$t_id", $term_meta );
  }
}
 
// Display details on product category archive pages
add_action( 'woocommerce_after_shop_loop', 'wpm_product_cat_archive_add_meta' );
 
function wpm_product_cat_archive_add_meta() {
  $t_id = get_queried_object()->term_id;
  $term_meta = get_option( "taxonomy_$t_id" );
  $term_meta_content = $term_meta['custom_term_meta'];
  if ( $term_meta_content != '' ) {
    echo '<div class="woo-sc-box normal rounded full">';
      echo apply_filters( 'the_content', $term_meta_content );
    echo '</div>';
  }
}
```
