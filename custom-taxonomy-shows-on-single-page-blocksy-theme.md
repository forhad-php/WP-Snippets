### Location: ../theme/blocksy/inc/components/hero/type-2.php

into `<header>` tag,

```PHP
<?php
$taxonomy_dev_name = get_the_terms( get_the_ID(), 'Developers' )[0]->name;
$taxonomy_dev_id = get_the_terms( get_the_ID(), 'Developers' )[0]->term_id;
echo '<span class="dev-val">Developer By : <a href="' . esc_url( get_term_link( $taxonomy_dev_id ) ) . '"' . esc_html( $taxonomy_dev_name ) . '</a></span>';
?>
```
