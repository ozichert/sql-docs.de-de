---
title: Implementieren von Merge-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e762c1999a4206d5277050934e82b5d5d5c59371
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82715129"
---
# <a name="implementing-merge-functionality"></a>Implementieren von MERGE-Funktionalität
  Eine Datenbank muss u. U. einen Einfüge- oder einen Updatevorgang ausführen, je nachdem, ob eine bestimmte Zeile in der Datenbank bereits vorhanden ist.  
  
 Ohne Verwendung der `MERGE`-Anweisung kann der folgende Ansatz in [!INCLUDE[tsql](../../includes/tsql-md.md)] verwendet werden:  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Eine weitere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Methode zum Implementieren eines Merge:  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 Für eine systemintern kompilierte gespeicherte Prozedur  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte.](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
