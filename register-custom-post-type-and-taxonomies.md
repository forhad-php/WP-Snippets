```PHP
/**
 * Generate Custom Post Type & Taxonomy.
 */
// Creating a Apps Custom Post Type
function frhd_cpt_init() {

	$labels = array(
		'name'                  => _x( 'Apps', 'Post type general name', 'app' ),
		'singular_name'         => _x( 'App', 'Post type singular name', 'app' ),
		'menu_name'             => _x( 'Apps', 'Admin Menu text', 'app' ),
		'name_admin_bar'        => _x( 'App', 'Add New on Toolbar', 'app' ),
		'add_new'               => __( 'Add New', 'app' ),
		'add_new_item'          => __( 'Add New app', 'app' ),
		'new_item'              => __( 'New app', 'app' ),
		'edit_item'             => __( 'Edit app', 'app' ),
		'view_item'             => __( 'View app', 'app' ),
		'all_items'             => __( 'All apps', 'app' ),
		'search_items'          => __( 'Search apps', 'app' ),
		'parent_item_colon'     => __( 'Parent apps:', 'app' ),
		'not_found'             => __( 'No apps found.', 'app' ),
		'not_found_in_trash'    => __( 'No apps found in Trash.', 'app' ),
		'featured_image'        => _x( 'App Cover Image', 'Overrides the “Featured Image” phrase for this post type. Added in 4.3', 'app' ),
		'set_featured_image'    => _x( 'Set cover image', 'Overrides the “Set featured image” phrase for this post type. Added in 4.3', 'app' ),
		'remove_featured_image' => _x( 'Remove cover image', 'Overrides the “Remove featured image” phrase for this post type. Added in 4.3', 'app' ),
		'use_featured_image'    => _x( 'Use as cover image', 'Overrides the “Use as featured image” phrase for this post type. Added in 4.3', 'app' ),
		'archives'              => _x( 'App archives', 'The post type archive label used in nav menus. Default “Post Archives”. Added in 4.4', 'app' ),
		'insert_into_item'      => _x( 'Insert into app', 'Overrides the “Insert into post”/”Insert into page” phrase (used when inserting media into a post). Added in 4.4', 'app' ),
		'uploaded_to_this_item' => _x( 'Uploaded to this app', 'Overrides the “Uploaded to this post”/”Uploaded to this page” phrase (used when viewing media attached to a post). Added in 4.4', 'app' ),
		'filter_items_list'     => _x( 'Filter apps list', 'Screen reader text for the filter links heading on the post type listing screen. Default “Filter posts list”/”Filter pages list”. Added in 4.4', 'app' ),
		'items_list_navigation' => _x( 'Apps list navigation', 'Screen reader text for the pagination heading on the post type listing screen. Default “Posts list navigation”/”Pages list navigation”. Added in 4.4', 'app' ),
		'items_list'            => _x( 'Apps list', 'Screen reader text for the items list heading on the post type listing screen. Default “Posts list”/”Pages list”. Added in 4.4', 'app' ),
	);
	$args   = array(
		'labels'             => $labels,
		'description'        => 'App custom post type.',
		'public'             => true,
		'publicly_queryable' => true,
		'show_ui'            => true,
		'show_in_menu'       => true,
		'query_var'          => true,
		'rewrite'            => array( 'slug' => 'app' ),
		'capability_type'    => 'post',
		'has_archive'        => true,
		'hierarchical'       => false,
		'menu_position'      => 5,
		'supports'           => array( 'title', 'editor', 'author', 'thumbnail' ),
		'taxonomies'         => array( 'category', 'post_tag' ),
		'show_in_rest'       => true,
	);

	register_post_type( 'Apps', $args );
}
add_action( 'init', 'frhd_cpt_init' );

// Let us create Taxonomy for Custom Post Type
add_action( 'init', 'frhd_create_custom_taxonomy', 0 );

// create a custom taxonomy name it "Developer" for your posts
function frhd_create_custom_taxonomy() {

	$labels = array(
		'name'              => _x( 'Developers', 'taxonomy general name' ),
		'singular_name'     => _x( 'Developer', 'taxonomy singular name' ),
		'search_items'      => __( 'Search Developers' ),
		'all_items'         => __( 'All Developers' ),
		'parent_item'       => __( 'Parent Developer' ),
		'parent_item_colon' => __( 'Parent Developer:' ),
		'edit_item'         => __( 'Edit Developer' ),
		'update_item'       => __( 'Update Developer' ),
		'add_new_item'      => __( 'Add New Developer' ),
		'new_item_name'     => __( 'New Developer Name' ),
		'menu_name'         => __( 'Developers' ),
	);

	register_taxonomy(
		'developers',
		array( 'apps' ),
		array(
			'hierarchical'      => true,
			'labels'            => $labels,
			'show_ui'           => true,
			'show_admin_column' => true,
			'query_var'         => true,
			'rewrite'           => array( 'slug' => 'developers' ),
		)
	);
}

/**
 * If a new post of custom post type says ↓
 * Oops! That page can’t be found..
 * Use this function once and then comment out again to deactivate.
 *
 * @return void
 */
// function frhd_custom_flush_rules() {

// 	flush_rewrite_rules();
// }
// add_action( 'after_theme_switch', 'frhd_custom_flush_rules' );
```
