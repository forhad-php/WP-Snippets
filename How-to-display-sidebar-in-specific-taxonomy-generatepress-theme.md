```PHP
	<?php
	/**
	 * Sidebar shows on specific taxonomy.
   * Location : /wp-content/themes/generatepress/single.php
	 */
	$layout = generate_get_block_editor_sidebar_layout();

	if ( has_tag( 'info' ) && 'no-sidebar' === $layout ) : ?>

	<style>
	.separate-containers .inside-left-sidebar,
	.separate-containers .inside-right-sidebar {
		margin-left: 20px;
	}
    #content {
        display: flex;
    }
	.site-content .content-area {
		width: 70%;
	}
	.is-right-sidebar {
		width: 30%;
	}
	</style>
	
	<div id="right-sidebar" <?php generate_do_element_classes( 'right_sidebar' ); ?>>
		<div class="inside-right-sidebar">
			<?php
			/**
			 * generate_before_right_sidebar_content hook.
			 *
			 * @since 0.1
			 */
			do_action( 'generate_before_right_sidebar_content' );

			if ( ! dynamic_sidebar( 'sidebar-1' ) ) {
				generate_do_default_sidebar_widgets( 'right-sidebar' );
			}

			/**
			 * generate_after_right_sidebar_content hook.
			 *
			 * @since 0.1
			 */
			do_action( 'generate_after_right_sidebar_content' );
			?>
		</div>
	</div>
	<?php endif; ?>
```
