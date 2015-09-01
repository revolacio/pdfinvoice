# XML tags #

## Basic example ##
```
<?xml version="1.0" encoding="UTF-8"?>
<pdfinvoicedocument>
    <meta>
        <renderer>1.0</renderer>
    </meta>

    <document>
        <meta>
            <page>A4</page>
            <width></width>
            <height></height>
            <orientation>P</orientation>
            <unit>mm</unit>
            <title data="lang">text_invoice</title>
            <subject data="data">invoice_number</subject>
            <author data="data">store_name</author>
            <font default="10">
                <name>dejavu</name>
                <style></style>
                <file>DejaVuSansCondensed.ttf</file>
            </font>
        </meta>
        <row type="content">
           <layout>
              <column>
                 <widget method="text">
                    <param>test string</param>
                 </widget>
              </column>
           </layout>
        </row>
    </document>
</pdfinvoicedocument>
```

## pdfinvoicedocument.meta.renderer ##

<table>
<thead>
<tr>
<th>Values</th>
</tr>
</thead>
<tbody>
<tr>
<td>1.0</td>
</tr>
</tbody>
</table>


## pdfinvoicedocument.document.meta.page ##

<table>
<thead>
<tr>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>A4</td>
<td>width 210,height 297</td>
</tr>
</tbody>
</table>

## pdfinvoicedocument.document.meta.page ##


<table>
<thead>
<tr>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>P</td>
<td>Portrait</td>
</tr>

<tr>
<td>L</td>
<td>Landscape</td>
</tr>
</tbody>
</table>

## pdfinvoicedocument.document.meta.unit ##



<table>
<thead>
<tr>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>mm</td>
<td>document unit in milimeters</td>
</tr>
</tbody>
</table>

## pdfinvoicedocument.document.meta.title ##

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>data</td>
<td>data,lang,text</td>
<td>specify which array will be used as source</td>
</tr>
</tbody>
</table>

Example
```
<title data="lang">text_invoice</title>
```

## pdfinvoicedocument.document.meta.subject ##

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>data</td>
<td>data,lang,text</td>
<td>specify which array will be used as source</td>
</tr>
</tbody>
</table>

Example
```
<subject data="data">invoice_number</subject>
```


## pdfinvoicedocument.document.meta.font ##

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Values</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>default</td>
<td>font size value</td>
<td>Set font as default for document with size specified by value</td>
</tr>
</tbody>
</table>

<table border='1'>
<thead>
<tr>
<th>Element</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>name</td>
<td>Font name included from file</td>
<td>Select font name name which is stored in font file</td>
</tr>
<tr>
<td>style</td>
<td>Font style</td>
<td>Select font style, with no value = regular, B = bold, I = italic, BI or IB = bold italic.<br>
See fpdf::AddFont</td>
</tr>
<tr>
<td>file</td>
<td>Font filename</td>
<td>which is in fpdf/font/unifont directory</td>
</tr>

</tbody>
</table>


Example
```
<font default="10">
   <name>dejavu</name>
   <style></style>
   <file>DejaVuSansCondensed.ttf</file>
</font>
```

## row ##

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>type</td>
<td>content,footer</td>
<td>Specifying type of row, each new page render first footer and then content rows</td>
</tr>
<tr>
<td>page</td>
<td>0,1,2...</td>
<td>If row type is footer then you can specify on which page you want use this row. 0 means first page because is zero based index, if this attribute is not specified, then will be footer row rendered on each new page</td>
</tr>
</tbody>
</table>

rows are rendered vertically thus if row height is more than as remain page size, is row rendered on new page (except table widgets - allow content page wrap)

## layout ##

allow you render vertically inside row

## column ##

columns are rendered horizontally, inside layout element

## widget ##

widget's are rendered vertically and are used for render data

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Values</th>
<th align='left'>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>method</td>
<td><a href='XML_template_widgets.md'>See widgets</a></td>
<td>Specify what and how you want render</td>
</tr>
</tbody>
</table>

### General attributes ###

<table cellpadding='2' width='600' border='1' cellspacing='0'>
<thead>
<tr>
<th>Attribute</th>
<th>row</th>
<th>layout</th>
<th>column</th>
<th>widget</th>
</tr>
</thead>
<tbody align='center'>
<tr>
<td>width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>height</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>margin-left</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>margin-top</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>margin-rigth</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>margin-bottom</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>


<tr>
<td>padding-left</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>padding-top</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>padding-rigth</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>padding-bottom</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>background-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>




<tr>
<td>border-height</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-left-width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-top-width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>border-rigth-width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>

<tr>
<td>border-bottom-width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>


<tr>
<td>border-left-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>


<tr>
<td>border-top-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-rigth-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-bottom-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>border-top-width</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>font-size</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>font-style</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>
<tr>
<td>font-color</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
</tr>




</tbody>
</table>