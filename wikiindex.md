## Templates ##

### pdf templates ###
/catalog/view/theme/default/template/pdfinvoice/

### email templates ###
/catalog/view/theme/default/template/pdfinvoice/email/

## Languages ##

pdfinvoice is shipped with default language files (english), for all other languages you can use pdfinvoice language files as default and copy them to your languages dir.

general pdfinvoice language file (pdfinvoice library):
```
/catalog/language/english/module/pdfinvoice.php
```
language used for module configuration (in admin)
```
/admin/language/english/module/pdfinvoice.php
```

pdfinvoice library use default opencart language files. For generate pdf document are used same files in both enviroments (admin and catalog)

pdfinvoice library language files are loaded in this order:
```
/catalog/language/<language>/mail/order.php
/catalog/language/<language>/checkout/checkout.php
/catalog/language/<language>/account/order.php
/catalog/language/<language>/module/pdfinvoice.php
```

Note: All files are loaded as one. If you define same language constant in multiple files, it will be overrided by last loaded language file.

Example:
/catalog/language/`<language>`/account/order.php
```
$_["title_invoice"] = "Invoice1";
```

/catalog/language/`<language>`/module/pdfinvoice.php
```
$_["title_invoice"] = "Invoice2";
```
pdfinvoice library then use last defined constant for text\_title = Invoice2