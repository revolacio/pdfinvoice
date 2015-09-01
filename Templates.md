# Template comparison #

<table border='1' cellspacing='0' width='800px'>
<thead>
<th></th><th>xml</th><th>php or tpl</th><th>html</th>
</thead>

<tbody align='center'>
<tr>
<td>pdf library</td><td>fpdf</td><td>fpdf</td><td>dompdf</td>
</tr>
<tr>
<td>UTF-8 support</td><td>Yes</td><td>Yes</td><td>Poor</td>
</tr>
<tr>
<td>Pdf file size</td><td>20~30KB</td><td>20~30KB</td>
<td>~8KB without UTF-8 fonts<br />500KB-1.2MB with UTF-8 fonts</td>
</tr>
<tr>
<td>Generate pdf document duration</td><td>~30ms</td><td>~150ms</td><td>>200ms</td>
</tr>
<tr>
<td>Fonts</td>
<td><code>DejaVu Sans Condensed</code>, ...</td>
<td><code>DejaVu Sans Condensed</code>, ...</td>
<td>
<code>DejaVu Sans Condensed</code>,<br>
Times,<br>
Helvetica, ...<br>
</td>
</tr>

<tr>
<td>require knowledge</td><td><a href='XML_template_document_structure.md'>xml templates</a></td><td>php</td><td>php+html</td>
</tr>
</tbody>
</table>