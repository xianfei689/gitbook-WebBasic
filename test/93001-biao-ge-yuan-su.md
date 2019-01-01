# 表格元素 {#表格元素}

## table {#table}

Table 元素用来生成表格。表格拥有行、列。

## caption {#caption}

Caption 元素为表格元素添加标题或者说明信息，caption应该包含在table元素中。

```php
<caption>
<p>表1.</p>
<p>表格说明文字。</p>
</caption>
```

## tbody {#tbody}

Tbody 元素用来标记表格主体。

## thead {#thead}

thead 元素用来标记表格的表头。

## tfoot {#tfoot}

Tfoot 元素用来标记表格的脚部，通常都是合计之类的信息。

## tr {#tr}

Tr 元素用来标记表格的行。

## td {#td}

Td 元素用来标记表格的单元格。

## th {#th}

Th 元素表示表头的单元格。

```php
<table>
   <caption>表格说明文字</caption>
 <thead>
  <tr> <th> ID <th> Measurement <th> Average <th> Maximum
 <tbody>
  <tr> <td> <th scope=rowgroup> Cats <td> <td>
  <tr> <td> 93 <th scope=row> Legs <td> 3.5 <td> 4
  <tr> <td> 10 <th scope=row> Tails <td> 1 <td> 1
 </tbody>
 <tbody>
  <tr> <td> <th scope=rowgroup> English speakers <td> <td>
  <tr> <td> 32 <th scope=row> Legs <td> 2.67 <td> 4
  <tr> <td> 35 <th scope=row> Tails <td> 0.33 <td> 1
 </tbody>
</table>
```



