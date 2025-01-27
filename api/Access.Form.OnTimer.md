---
title: Form.OnTimer property (Access)
keywords: vbaac10.chm13461
f1_keywords:
- vbaac10.chm13461
ms.prod: access
api_name:
- Access.Form.OnTimer
ms.assetid: a7df5020-5163-967b-b59a-0fd8f6fe7a54
ms.date: 03/14/2019
ms.localizationpriority: medium
---


# Form.OnTimer property (Access)

Sets or returns the value of the **On Timer** box in the Properties window of a form. Read/write **String**.


## Syntax

_expression_.**OnTimer**

_expression_ A variable that represents a **[Form](Access.Form.md)** object.


## Remarks

This property is helpful for programmatically changing the action that Microsoft Access takes when an event is triggered. For example, between event calls you may want to change an expression's parameters, or switch from an event procedure to an expression or macro, depending on the circumstances under which the event was triggered. 

The **Timer** event occurs for a form at regular intervals as specified by the form's **TimerInterval** property.

The **OnTimer** value will be one of the following, depending on the selection chosen in the Choose Builder window (accessed by choosing the **Build** button next to the **On Timer** box in the form's Properties window):

- If you choose Expression Builder, the value will be =_expression_, where _expression_ is the expression from the Expression Builder window.
    
- If you choose Macro Builder, the value is the name of the macro. 
    
- If you choose Code Builder, the value will be [Event Procedure]. 
    
If the **On Timer** box is blank, the property value is an empty string.


## Example

The following example prints the value of the **OnTimer** property in the Immediate window for the **Order Entry** form.

```vb
Debug.Print Forms("Order Entry").OnTimer
```



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]