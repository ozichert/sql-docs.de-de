---
title: Spalten ohne Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 685be1c7e6c43e28500dd1ee96ea6fe696ad8e20
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664632"
---
# <a name="columns-without-a-name"></a>Spalten ohne Namen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Spalten ohne Namen werden als Inlinespalten betrachtet. Beispielsweise werden namenlose Spalten für berechnete Spalten oder geschachtelte skalare Abfragen, die keinen Spaltenalias angeben, generiert. Wenn die Spalte vom Typ **xml** ist, wird der Inhalt dieser Datentypinstanz eingefügt. Anderenfalls wird der Inhalt der Spalte als Textknoten eingefügt.  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 Erstellen Sie diesen XML-Code. Standardmäßig wird im XML-Ergebnis für jede Zeile des Rowsets ein <`row`>-Element generiert. Dies entspricht dem RAW-Modus.  
  
 `<row>4</row>`  
  
 Die folgende Abfrage gibt ein Rowset mit drei Spalten zurück. Die dritte, namenlose Spalte enthält XML-Daten. Der PATH-Modus fügt eine Instanz des XML-Typs ein.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 Dies ist das Teilergebnis:  
  
```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location ...LocationID="10" ...></MI:Location>
  <MI:Location ...LocationID="20" ...></MI:Location>
  ...
</row>
```

## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
