---
title: Count function (Microsoft Access SQL)
keywords: jetsql40.chm5278824
f1_keywords:
- jetsql40.chm5278824
ms.prod: access
ms.assetid: 01743d33-d7de-12b5-eb0f-eb775b0bcffd
ms.date: 09/21/2018
ms.localizationpriority: medium
---


# Count function (Microsoft Access SQL)

**Applies to:** Access 2013 | Access 2016

Calculates the number of records returned by a query.

## Syntax

**Count(** _expr_ **)**

The  _expr_ placeholder represents a string expression identifying the field that contains the data you want to count or an expression that performs a calculation using the data in the field. Operands in _expr_ can include the name of a table field or function (which can be either intrinsic or user-defined but not other SQL aggregate functions). You can count any kind of data, including text.

## Remarks

Use **Count** to count the number of records in an underlying query. For example, you could use **Count** to count the number of orders shipped to a particular country or region.

Although  _expr_ can perform a calculation on a field, **Count** simply tallies the number of records. It does not matter what values are stored in the records.

The **Count** function does not count records that have **Null** fields unless _expr_ is the asterisk (*) wildcard character. If you use an asterisk, **Count** calculates the total number of records, including those that contain **Null** fields. **Count(** * **)** is considerably faster than **Count(** [ _Column Name_ ] **)**. Do not enclose the asterisk in quotation marks (' ').

The following example calculates the number of records in the Orders table:

```sql
SELECT Count(*) 
AS TotalOrders FROM Orders;
```

If  _expr_ identifies multiple fields, the **Count** function counts a record only if at least one of the fields is not **Null**. If all of the specified fields are **Null**, the record is not counted. Separate the field names with an ampersand (&). The following example shows how you can limit the count to records in which either ShippedDate or Freight is not **Null**:

```sql
SELECT 
Count('ShippedDate & Freight') 
AS [Not Null] FROM Orders;
```

Use **Count** in a query expression. You can also use this expression in the **SQL** property of a **QueryDef** object or when creating a **Recordset** object based on an SQL query.

## Example

This example uses the Orders table to calculate the number of orders shipped to the United Kingdom.

This example calls the EnumFields procedure, which you can find in the SELECT statement example.

```vb
Sub CountX() 
 
    Dim dbs As Database, rst As Recordset 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
    
    ' Calculate the number of orders shipped  
    ' to the United Kingdom. 
    Set rst = dbs.OpenRecordset("SELECT" _ 
        & " Count (ShipCountry)" _ 
        & " AS [UK Orders] FROM Orders" _ 
        & " WHERE ShipCountry = 'UK';") 
     
    ' Populate the Recordset. 
    rst.MoveLast 
     
    ' Call EnumFields to print the contents of the  
    ' Recordset. Pass the Recordset object and desired 
    ' field width. 
    EnumFields rst, 25 
 
    dbs.Close 
 
End Sub 

```

## See also

- [Access for developers forum](https://social.msdn.microsoft.com/Forums/office/home?forum=accessdev)
- [Access help on support.office.com](https://support.office.com/search/results?query=Access)
- [Access forums on UtterAccess](https://www.utteraccess.com/forum/index.php?act=idx)
- [Access developer and VBA programming help center (FMS)](https://www.fmsinc.com/MicrosoftAccess/developer/)
- [Access posts on StackOverflow](https://stackoverflow.com/questions/tagged/ms-access)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
