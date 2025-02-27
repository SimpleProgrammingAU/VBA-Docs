---
title: Application.CurrentUser method (Access)
keywords: vbaac10.chm12538
f1_keywords:
- vbaac10.chm12538
ms.prod: access
api_name:
- Access.Application.CurrentUser
ms.assetid: 1cf7ee61-459c-1224-cfdf-a0b051eeb06e
ms.date: 02/05/2019
ms.localizationpriority: medium
---


# Application.CurrentUser method (Access)

Use the **CurrentUser** method to return the name of the current user of the database.


## Syntax

_expression_.**CurrentUser**

_expression_ A variable that represents an **[Application](Access.Application.md)** object.


## Return value

String


## Remarks

For example, use the **CurrentUser** method in a procedure that keeps track of the users who modify the database.

The **CurrentUser** method returns a string that contains the name of the current user account.

If you haven't established a security-enabled workgroup, the **CurrentUser** method returns the name of the default user account, Admin. The Admin user account gives the user full permissions to all database objects.

If you have enabled workgroup security, the **CurrentUser** method returns the name of the current user account. For user accounts other than Admin, you can specify permissions that restrict the users' access to database objects.


## Example

The following example obtains the name of the current user and displays it in a dialog box.


```vb
MsgBox "The current user is: " & CurrentUser
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
