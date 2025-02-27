---
title: CellRange.Column property (Publisher)
keywords: vbapb10.chm5177346
f1_keywords:
- vbapb10.chm5177346
ms.prod: publisher
api_name:
- Publisher.CellRange.Column
ms.assetid: 77925e68-c8ff-9732-32c4-4f082eb3fd1c
ms.date: 06/06/2019
ms.localizationpriority: medium
---


# CellRange.Column property (Publisher)

Returns a **Long** that represents the table column containing the specified cell. Read-only.


## Syntax

_expression_.**Column**

_expression_ A variable that represents a **[CellRange](Publisher.CellRange.md)** object.


## Example

This example adds a page to the active publication, creates a table on that new page, and diagonally splits all cells in even-numbered columns.

```vb
Sub CreateNewTable() 
 
 Dim pgeNew As Page 
 Dim shpTable As Shape 
 Dim tblNew As Table 
 Dim celTable As Cell 
 Dim rowTable As Row 
 
 'Creates a new document with a five-row by five-column table 
 Set pgeNew = ActiveDocument.Pages.Add(Count:=1, After:=1) 
 Set shpTable = pgeNew.Shapes.AddTable(NumRows:=5, NumColumns:=5, _ 
 Left:=72, Top:=72, Width:=468, Height:=100) 
 Set tblNew = shpTable.Table 
 
 'Inserts a diagonal split into all cells in even-numbered columns 
 For Each rowTable In tblNew.Rows 
 For Each celTable In rowTable.Cells 
 If celTable.Column Mod 2 = 0 Then 
 celTable.Diagonal = pbTableCellDiagonalUp 
 End If 
 Next celTable 
 Next rowTable 
 
End Sub
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]