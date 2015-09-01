**[Configuration](pdfinvoice_config.md)
  * [General](pdfinvoice_config#General.md)
  * [Invoice](pdfinvoice_config#Invoice.md)
    * [Invoice](pdfinvoice_config#Invoice.Invoice.md)
    * [Advance Invoice](pdfinvoice_config#Invoice.Advance_invoice.md)
    * [Packing slip](pdfinvoice_config#packing_slip.md)
  * [Outsourcing](pdfinvoice_config#outsourcing.md)
    * [Email](pdfinvoice_config#Oustsourcing.email.md)
  * [Custom](pdfinvoice_config#custom.md)
  * [Support](pdfinvoice_config#support.md)**


## General ##

<table valign='top'>
<tr>
<td valign='top'>
<b>Pdf files storage</b>
</td>
<td>
Specify where you want store generated pdf files. After save configuration is created in your folder .htaccess and index.html. .htaccess file is created to prevent accessing to pdf files outside of the opencart, thus if you have enabled .htaccess will be access limited. .htaccess and index.html is created in all directories except this<br>
<pre><code>/admin<br>
/download<br>
/catalog<br>
/image<br>
/system<br>
/vqmod<br>
</code></pre>
This means if you set as pdf invoice store path /download/ then will be not created .htaccess. If you create dir /download/pdf/ (for example) and use this as your store path then will be created .htaccess<br>
</td>
</tr>
<tr>
<td valign='top'><b>Customer Enable</b></td>
<td>
This allow you limit processing pdf invoice only for selected customer. All other customers will have only available download existing pdf invoice files from customer order history.<br>
This allow you testing pdfinvoice settings with one user without interact with other, for all other you can generate invoices manually after ending testing.<br>
</td>
</tr>

<tr>
<td valign='top'><b>Invoice number on checkout</b></td>
<td>Generate invoice number after confirm order by customer.</td>
</tr>

<tr>
<td valign='top'><b>Invoice number on status</b></td>
<td>
Generate invoice number if order status is same as you set.<br>
For example if you want generate invoice number on status "Complete" then will be generated invoice number when order status is changed to "Complete", this means if you edit your order and change order status to "Complete" then is created invoice number.<br>
Example for COD (cash on delivery payment module)<br>
If your customer select payment method COD and your COD has set order status "Complete" then will be created invoice number on order checkout.<br>
</td>
</tr>

<tr>
<td valign='top'><b>Don't show "Save as" dialog</b></td>
<td>
This is only helper configuration for admin users, And allow you specify how is pdf file send to you when you view it in admin order list.<br />
checked - file will be added as inline<br />
unchecked - file will be added as attachment (save as dialog)<br>
</td>

</tr>
</table>

## Invoice ##

<table>
<tr>
<td valign='top'>
<b>Template logo</b>
</td>
<td>
Image what will rendered in pdf document, This image is processed in different ways depend on your selected template type<br>
</td>
</tr>
</table>

## Invoice.Invoice ##
<table>
<tr>
<td valign='top'><b>Template</b></td>
<td>
Template what you want use for generate pdf invoice<br>
</td>
</tr>

<tr>
<td valign='top'>
<b>Create on Invoice number</b>
</td>
<td>
pdf invoice will be created after generate invoice number <a href='pdfinvoice_config#General.md'>General</a>  (Invoice number on checkout, Invoice number on status)<br>
</td>
</tr>


</table>
## Invoice.Advance invoice ##
## Invoice.Packing Slip ##

## Outsourcing ##

## Outsourcing.email ##

<table>
<tr>
<td valign='top'><b>Emails</b></td>
<td>
Where you want send outsourcing emails. Due opencart limitations of the email implementation we can not set recipient copy, thus each email is as standalone.<br>
Is allowed separate emails with comma (emails in group) and semicolon (email group)<br>
<br />
example email groups<br>
<pre><code>email1@email.com,email2@email.com;<br>
</code></pre>
<pre><code>email1@email.com;<br>
email2@email.com;<br>
</code></pre>
</td>
</tr>
<tr>
<td><b>Notify invoice delete</b></td>
<td>After delete invoice is triggered notification</td>
</tr>
<tr>
<td valign='top'><b>Operation</b></td>
<td>
Auto - notifications are executed immediatelly<br />
Manual - You must do manually in order list history.<br>
</td>
</tr>
<tr>
<td><b>Order status</b></td>
<td>Allow you select order status which generates notification</td>
</tr>
<tr>
<td valign='top'><b>Notify email template</b></td>
<td>
Select template what will be used for email<br />
Templates dir: /catalog/view/theme/default/temlate/pdfinvoice/email/<br>
</td>
</tr>
</table>
### Remarks ###
In mode manual are notification stored in same directory as generated pdf documents (see General->Pdf files storage). For each order notification is generated file `<order_id>`.ose
## Custom ##
## Support ##