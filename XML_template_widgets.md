# XML Template widgets #
Widgets are methods called in renderer. Method selection is done by _**method**_ attribute in  **widget**.

### Supported widgets ###

<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th align='center'>method</th>
<th>description</th>
</tr>
</thead>
<tbody align='left'>

<tr>
<td align='center'>text</td>
<td>Render template text</td>
</tr>

<tr>
<td align='center'>lang</td>
<td>Render template language constant</td>
</tr>
<tr>
<td align='center'>merge</td>
<td>Render template multiple types text,lang,data as one string</td>
</tr>
<tr>
<td align='center'>image</td>
<td>Render image</td>
</tr>
<tr>
<td align='center'>data</td>
<td>Render string from data variable</td>
</tr>
<tr>
<td align='center'>label</td>
<td>Render pair</td>
</tr>
<tr>
<td align='center'>custom_text</td>
<td>Render custom_text variable</td>
</tr>
<tr>
<td align='center'>table</td>
<td>Render array variable as table</td>
</tr>

</tbody>
</table>

## text ##

**Description:**
one param for  string what you want render

Example
```
<widget method="text">
   <param>test string</param>
</widget>
```

Output
```
test string
```

## lang ##

**Description:** one param for  language constant what you want render, constant is searched in lang array if is not found then is rendered param value

Example
```
<widget method="lang">
   <param>text_invoice</param>
</widget>
```

Output (success)
```
Invoice
```

Output (invalid lang constant)
```
text_invoice
```

## merge ##
**Description:**
Allow you merge multiple parameters to one string and render it. Each parameter can have different type (source)

Param attributes
<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>type</td>
<td>data,text,lang</td>
<td>
data - lookup in data array<br />
text - param value is used value<br />
lang - lookup in lang array for lang value<br />
</td>
</tr>
</tbody>
</table>

Example
```
<widget method="merge">
   <param type="data">payment_firstname</param>
   <param type="text"> </param>
   <param type="data">payment_lastname</param>
</widget>
```

Output
```
firstname lastname
```

## image ##

**Description:**
Render image specified with parameter value, value is key in data array in which is stored full path to image.
In param we need specify height or width, ratio is then computed from known values. If you specify both values (height and width) then is nothing computed and is used dimension what you forced. Dimensions are in document units, Default is mm, thus if you specify image width 20 is rendered image with width 20 mm

Param attributes
<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>width</td>
<td>document unit</td>
<td></td>
</tr>
<tr>
<td>height</td>
<td>document unit</td>
<td></td>
</tr>
</tbody>
</table>

**Note:**
currently is image not resized, if use image with size 1MB and you set width to 20 then is image rendered with your width, but is whole encoded to pdf document, thus you will get (~20 KB (pdf document) + 1 MB (image size)) = pdf document size

Example
```
<widget method="image">
   <param width="20">template_logo</param>
</widget>
```

## data ##

**Description:**
Render string from data array key, param value is key in data array

Example
```
<widget method="data">
   <param>store_name</param>
</widget>
```

Output
```
Your store
```

## label ##
**Description:**
Render two values as label and value. Require two parameters, each specify from where will be value used


Param attributes
<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>width</td>
<td>document unit</td>
<td>width="0" mean autosize and width will be automatically set to string width<br>
if both parameters are without width attribute then is calculated width for each param 50% of  client area</td>
</tr>
<tr>
<td>data</td>
<td>data,lang,text</td>
<td>
data - lookup in data array<br />
text - param value is used value<br />
lang - lookup in lang array for lang value<br />
</td>
</tr>

<tr>
<td>skip</td>
<td>whatever</td>
<td>is checked only presence of the attribute and is accepted with data="data". This allow you ignore widget label (line is skiped) if data value is empty</td>
</tr>

</tbody>
</table>

Example
```
<widget method="label">
   <param data="lang">text_date_added</param>
   <param data="data">date_added<param>
</widget>
```

Output
```
Order date:     16/02/2014
```

## custom\_text ##

**Description:**
You can use it with or without param tags. Using without tags is meant to render all custom text in widget. Or you can specify `<param>group_name</param>` what you want render. This allow you have multiple custom texts based group name

Note: all custom\_text which not have group name is added to default group named 'defafult'

Example (all custom\_text strings)
```
<widget method="custom_text"> </widget>
```

Example (by group)
```
<widget method="custom_text">
   <param>my_group_first</param>
   <param>default</param>
</widget>
```

This render text from group my\_group\_first and text without group name

## table ##

**Description:**
Render table from key which contains array.<br />
Using two types tags for describe table `<header>` and `<param>`
header tag specify table header column and must be assigned to `<param>` value name


widget attributes
<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>data</td>
<td>data array key</td>
<td>data array key containing array of the values what we want use</td>
</tr>
</tbody>
</table>

header attributes
<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>column</td>
<td>value of the <code>&lt;param&gt;</code></td>
<td>Define header column and assign it to data column</td>
</tr>
</tbody>
</table>

option attribute (accepted only for column name)

<table cellpadding='2' width='500' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th align='left'>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>margin-left</td>
<td>document unit</td>
<td></td>
</tr>
</tbody>
</table>


Example (render order products)
```
<widget method="table" data="products">
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="name">column_name</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="model">column_model</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="quantity">column_quantity</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="tax">column_tax</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="price_tax_exclude">column_price</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="30" column="total_tax_include" text-align="R">column_total</header>
   <param border-width="0.2" border-color="#cddddd">name</param>
   <param border-width="0.2" border-color="#cddddd">model</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C">quantity</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C">tax</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C" width="20">price_tax_exclude</param>
   <param border-width="0.2" border-color="#cddddd" text-align="R">total_tax_include</param>
</widget>

```

Output
![https://pdfinvoice.googlecode.com/git/examp_product_table.png](https://pdfinvoice.googlecode.com/git/examp_product_table.png)

Example (order totals)
```
<widget method="table" data="totals">
   <param text-align="R" border-width="0.2" border-color="#cddddd">title</param>
   <param text-align="R" width="30" border-width="0.2" border-color="#cddddd">text</param>
</widget>
```

Output
![https://pdfinvoice.googlecode.com/git/example_totals.png](https://pdfinvoice.googlecode.com/git/example_totals.png)


Example (render product table with product options)
```
<widget method="table" data="products">
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" column="name">column_name</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="40" column="model">column_model</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="20" text-align="C" column="quantity">column_quantity</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="20" text-align="C" column="tax">column_tax</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="20" text-align="C" column="price_tax_exclude">column_price</header>
   <header border-width="0.2" border-color="#cddddd" background-color="#e7efef" width="30" column="total_tax_include" text-align="R">column_total</header>
   <param border-width="0.2" border-color="#cddddd">name</param>
   <param border-width="0.2" border-color="#cddddd">model</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C">quantity</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C">tax</param>
   <param border-width="0.2" border-color="#cddddd" text-align="C" width="20">price_tax_exclude</param>
   <param border-width="0.2" border-color="#cddddd" text-align="R">total_tax_include</param>
   <option font-size="8" margin-left="5"></option>
</widget>

```

Output
![https://pdfinvoice.googlecode.com/git/example_product_table_with_option.png](https://pdfinvoice.googlecode.com/git/example_product_table_with_option.png)