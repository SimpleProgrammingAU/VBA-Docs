---
title: ListBox.Controls property (Access)
keywords: vbaac10.chm11214
f1_keywords:
- vbaac10.chm11214
ms.prod: access
api_name:
- Access.ListBox.Controls
ms.assetid: 16356c09-4509-c774-1fd6-9ba5b330eaa5
ms.date: 02/21/2019
ms.localizationpriority: medium
---


# ListBox.Controls property (Access)

Returns the **Controls** collection of a form, subform, report, or section. Read-only **Controls**.


## Syntax

_expression_.**Controls**

_expression_ A variable that represents a **[ListBox](Access.ListBox.md)** object.


## Remarks

Use the **Controls** property to refer to one of the controls on a form, subform, report, or section within or attached to another control. For example, the first code syntax returns the number of controls located on Form1. The second references the name of a property within a control.

```vb
Forms("Form1").Controls.Count 
 
Forms("Form1").Controls("Textbox1").Properties(5).Name
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]