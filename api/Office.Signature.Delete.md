---
title: Signature.Delete method (Office)
keywords: vbaof11.chm248006
f1_keywords:
- vbaof11.chm248006
ms.prod: office
api_name:
- Office.Signature.Delete
ms.assetid: c75a2200-081a-7f5c-ae02-ab7be845c003
ms.date: 01/24/2019
ms.localizationpriority: medium
---


# Signature.Delete method (Office)

Deletes the **Signature** object from the collection.


## Syntax

_expression_.**Delete**

_expression_ Required. A variable that represents a **[Signature](Office.Signature.md)** object.


## Remarks

For the **Scripts** collection, using the **Delete** method removes all scripts from the specified Microsoft Word document, Microsoft Excel worksheet, or Microsoft PowerPoint slide. 

A script anchor is represented by a shape in the host application. Therefore, the **Shape** object associated with each script anchor of type **msoScriptAnchor** is deleted from the **Shapes** collection in Excel and PowerPoint and from the **InlineShapes** and **Shapes** collections in Word.


## See also

- [Signature object members](overview/Library-Reference/signature-members-office.md)



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]