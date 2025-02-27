---
title: Viewer.ShapeName property (Visio Viewer)
ms.prod: visio
api_name:
- Visio.Viewer.ShapeName
ms.assetid: cde3d4f0-5e45-1236-1d6d-227b93cdaa64
ms.date: 06/21/2019
ms.localizationpriority: medium
---


# Viewer.ShapeName property (Visio Viewer)

Gets the name of the shape at the specified index in the collection of shapes in the drawing that is open in Microsoft Visio Viewer. Read-only.


## Syntax

_expression_.**ShapeName** (_ShapeIndex_)

_expression_ An expression that returns a **[Viewer](Visio.Viewer.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
|_ShapeIndex_|Required| **Long**|The index of the shape in the collection of shapes.|

## Return value

String


## Remarks

The collection of shapes is one-based, so the index of the first shape in the collection is 1. If there are no shapes in the drawing, or if you pass the index of a nonexistent shape, the **ShapeName** property returns nothing.

The **ShapeName** property returns the local name of the shape, not its universal name.


## Example

The following code gets the names of all the shapes in the drawing that is open in Visio Viewer.

```vb
Dim intCounter As Integer

    For intCounter = 1 To Viewer1.ShapeCount

    Debug.Print Viewer1.ShapeName(intCounter)

Next intCounter
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]