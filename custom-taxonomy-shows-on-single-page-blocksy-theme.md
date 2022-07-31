### Location: ../theme/blocksy/inc/components/hero/type-2.php

into `<header>` tag,

```PHP
<?php echo '<span class="dev-val">Developer By : ' . get_the_terms( get_the_ID(), 'Developers' )[0]->name . '</span>'; ?>
```
