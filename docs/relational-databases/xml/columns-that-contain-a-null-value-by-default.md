---
title: Spalten, die standardmäßig einen NULL-Wert enthalten | Microsoft-Dokumentation
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7672d59b2355c0733a5e26da6217fbabf729c6a
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664698"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Spalten, die standardmäßig einen NULL-Wert enthalten

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

In der Standardeinstellung wird ein NULL-Wert in einer Spalte der Abwesenheit des Attributs, Knotens oder Elements zugeordnet. Dieses Standardverhalten kann mithilfe des Schlüsselwortausdrucks ELEMENTS XSINIL außer Kraft gesetzt werden. Dieser Ausdruck fordert elementzentriertes XML an. Das bedeutet, dass NULL-Werte in den zurückgegebenen Ergebnissen explizit angegeben werden. Diese Elemente weisen keinen Wert auf.

Der ELEMENTS XSINIL-Ausdruck ist im folgenden Transact-SQL SELECT-Beispiel dargestellt.

```sql
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
  AND  E.EmployeeID=1
FOR XML PATH, ELEMENTS XSINIL;
```  
  
 Im Folgenden wird das Ergebnis gezeigt. Beachten Sie, dass das <`Middle`>-Element abwesend sein wird, wenn XSINIL nicht angegeben wird.  
  
```xml
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
