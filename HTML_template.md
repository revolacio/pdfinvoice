Only one note: if you want use external stylesheet you must specify base url.
Variable  $base contain your store base url. You must specify href with base url because pdfinvoice processing templates from catalog and admin

Example
```
<link rel="stylesheet" type="text/css" href="<?php echo $base; ?>catalog/view/theme/default/stylesheet/invoice.css" />
```