```PHP
public function enqueue_scripts() {

		if ( $this->is_theme( 'Astra' ) ) {
			wp_enqueue_style( 'wp-handle-name-astra', PLUGIN_DIR_URL . '/css/themes/astra.css' );
		} elseif ( $this->is_theme( 'Jannah' ) ) {
			wp_enqueue_style( 'wp-handle-name-jannah', PLUGIN_DIR_URL . '/css/themes/jannah.css' );
		} elseif ( $this->is_theme( 'OceanWP' ) ) {
			wp_enqueue_style( 'wp-handle-name-salient', PLUGIN_DIR_URL . '/css/themes/oceanwp.css' );
		} elseif ( $this->is_theme( 'Salient' ) ) {
			wp_enqueue_style( 'wp-handle-name-salient', PLUGIN_DIR_URL . '/css/themes/salient.css' );
		} elseif ( $this->is_theme( 'Twenty Twenty' ) ) {
			wp_enqueue_style( 'wp-handle-name-twentytwenty', PLUGIN_DIR_URL . '/css/themes/twentytwenty.css' );
		} elseif ( $this->is_theme( 'Salient' ) ) {
			wp_enqueue_style( 'wp-handle-name-salient', PLUGIN_DIR_URL . '/css/themes/salient.css' );
		} elseif ( $this->is_theme( 'Flatsome' ) ) {
			wp_enqueue_style( 'wp-handle-name-flatsome', PLUGIN_DIR_URL . '/css/themes/flatsome.css' );
		} elseif ( $this->is_theme( 'Avada' ) ) {
			wp_enqueue_style( 'wp-handle-name-avada', PLUGIN_DIR_URL . '/css/themes/avada.css' );
		} elseif ( $this->is_theme( 'The7' ) ) {
			wp_enqueue_style( 'wp-handle-name-the7', PLUGIN_DIR_URL . '/css/themes/the7.css' );
		} elseif ( $this->is_theme( 'Betheme' ) ) {
			wp_enqueue_style( 'wp-handle-name-betheme', PLUGIN_DIR_URL . '/css/themes/betheme.css' );
		} elseif ( $this->is_theme( 'Newspaper' ) ) {
			wp_enqueue_style( 'wp-handle-name-newspaper', PLUGIN_DIR_URL . '/css/themes/newspaper.css' );
		} elseif ( $this->is_theme( 'GeneratePress' ) ) {
			wp_enqueue_style( 'wp-handle-name-generatepress', PLUGIN_DIR_URL . '/css/themes/generatepress.css' );
		}

}
```
