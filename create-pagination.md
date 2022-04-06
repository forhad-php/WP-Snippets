# Simple Way
```PHP
$frhd_big = 999999999; // Need an unlikely integer.
echo '<div class="frhd__paginate">';
$frhd_arg = array(
  'base'      => str_replace( $frhd_big, '%#%', esc_url( get_pagenum_link( $frhd_big ) ) ),
  'format'    => '?paged=%#%',
  'current'   => max( 1, get_query_var( 'paged' ) ),
  'total'     => $frhd_post_query->max_num_pages,
  'prev_text' => __( '«' ),
  'next_text' => __( '»' ),
);
echo wp_kses_post( paginate_links( $frhd_arg ) );
echo '</div>'; // frhd_paginate.
var_dump( $frhd_arg );
```

# Another way__
```PHP
/**
 * Builds the base url.
 *
 * @param string $permalink_structure Premalink Structure.
 * @param string $base Base.
 * @since 1.14.9
 */
function build_base_url( $permalink_structure, $base ) {
  // Check to see if we are using pretty permalinks.
  if ( ! empty( $permalink_structure ) ) {

    if ( strrpos( $base, 'paged-' ) ) {
      $base = substr_replace( $base, '', strrpos( $base, 'paged-' ), strlen( $base ) );
    }

    // Remove query string from base URL since paginate_links() adds it automatically.
    // This should also fix the WPML pagination issue that was added since 1.10.2.
    if ( count( $_GET ) > 0 ) { // phpcs:ignore WordPress.Security.NonceVerification.Recommended
      $base = strtok( $base, '?' );
    }

    // Add trailing slash when necessary.
    if ( '/' === substr( $permalink_structure, -1 ) ) {
      $base = trailingslashit( $base );
    } else {
      $base = untrailingslashit( $base );
    }
  } else {
    $url_params = wp_parse_url( $base, PHP_URL_QUERY );

    if ( empty( $url_params ) ) {
      $base = trailingslashit( $base );
    }
  }

  return $base;
}
/**
 * Returns the Paged Format.
 *
 * @param string $permalink_structure Premalink Structure.
 * @param string $base Base.
 * @since 1.14.9
 */
function paged_format( $permalink_structure, $base ) {

  $page_prefix = empty( $permalink_structure ) ? 'paged' : 'page';

  if ( ! empty( $permalink_structure ) ) {
    $format  = substr( $base, -1 ) !== '/' ? '/' : '';
    $format .= $page_prefix . '/';
    $format .= '%#%';
    $format .= substr( $permalink_structure, -1 ) === '/' ? '/' : '';
  } elseif ( empty( $permalink_structure ) || is_search() ) {
    $parse_url = wp_parse_url( $base, PHP_URL_QUERY );
    $format    = empty( $parse_url ) ? '?' : '&';
    $format   .= $page_prefix . '=%#%';
  }

  return $format;
}
/**
 * Gives the paged Query var.
 *
 * @param Object $frhd_post_query Query.
 * @return int $frhd_paged Paged Query var.
 * @since 1.14.9
 */
function get_paged( $frhd_post_query ) {

  global $frhd_paged;

  // Check the 'paged' query var.
  $frhd_paged_qv = $frhd_post_query->get( 'paged' );

  if ( is_numeric( $frhd_paged_qv ) ) {
    return $frhd_paged_qv;
  }

  // Check the 'page' query var.
  $page_qv = $frhd_post_query->get( 'page' );

  if ( is_numeric( $page_qv ) ) {
    return $page_qv;
  }

  // Check the $frhd_paged global?
  if ( is_numeric( $frhd_paged ) ) {
    return $frhd_paged;
  }

  return 0;
}
$permalink_structure = get_option( 'permalink_structure' );
$base                = untrailingslashit( wp_specialchars_decode( get_pagenum_link() ) );
$base                = build_base_url( $permalink_structure, $base );
$format              = paged_format( $permalink_structure, $base );
$frhd_paged          = get_paged( $frhd_post_query );
$page_limit          = min( 10, $frhd_post_query->max_num_pages ); // 10 = page limit.
$page_limit          = isset( $page_limit ) ? $page_limit : 6; // 6 = post per page.

$links = paginate_links(
  array(
    'base'      => $base . '%_%',
    'format'    => $format,
    'current'   => ( ! $frhd_paged ) ? 1 : $frhd_paged,
    'total'     => $page_limit,
    'type'      => 'array',
    'mid_size'  => 4,
    'end_size'  => 4,
    'prev_text' => '<<',
    'next_text' => '>>',
  )
);

if ( isset( $links ) ) {

  echo wp_kses_post( implode( PHP_EOL, $links ) );
}
```
