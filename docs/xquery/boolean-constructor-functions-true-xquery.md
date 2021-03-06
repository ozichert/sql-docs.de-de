---
title: true-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 56f2dde1899340f036024253405379e094de59a6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68039044"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Boolesche Konstruktorfunktionen – true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den xs:boolean-Wert True zurück. Dieser entspricht `xs:boolean("1")`.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Verwenden der XQuery Boolean-Funktion true()  
 Im folgenden Beispiel wird eine nicht typisierte **XML** -Variable abgefragt. Der Ausdruck in der **value ()** -Methode gibt den booleschen Wert **true ()** zurück, wenn "AAA" der Attribut Wert ist. Die **value ()** -Methode des **XML** -Datentyps konvertiert den booleschen Wert in ein Bit und gibt ihn zurück.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 Im folgenden Beispiel wird die Abfrage für eine typisierte **XML** -Spalte angegeben. Der `if` Ausdruck überprüft den typisierten booleschen Wert des <`ROOT`> Elements und gibt entsprechend das konstruierte XML zurück. Das Beispiel führt die folgenden Aktionen aus:  
  
-   Erstellt eine XML-Schema Auflistung, die die `ROOT` <> Element des xs: Boolean-Typs definiert.  
  
-   Erstellt eine Tabelle mit einer typisierten **XML** -Spalte, indem die XML-Schema Auflistung verwendet wird.  
  
-   Speichert eine XML-Instanz in der Spalte und fragt sie ab.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Boolesche Konstruktorfunktionen &#40;XQuery-&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
