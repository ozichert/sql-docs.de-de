---
title: sp_unbindrule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 54c5c0f9bfa6bc64a79e0f4dcde72c09b2a281fb
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82809381"
---
# <a name="sp_unbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt die Bindung einer Regel an eine Spalte oder einen Aliasdatentyp in der aktuellen Datenbank auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Es wird empfohlen, stattdessen mithilfe des Default-Schlüssel Worts in den [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) -oder [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) -Anweisungen Standarddefinitionen zu erstellen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'object_name'`Der Name der Tabelle und Spalte oder der Alias Datentyp, von dem die Regel nicht gebunden ist. *object_name* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht zuerst, zweiteilige Bezeichner für Spaltennamen aufzulösen, und versucht dann, zweiteilige Bezeichner für Aliasdatentypen aufzulösen. Beim Aufheben der Bindung einer Regel an einen Aliasdatentyp wird auch die Bindung für alle Spalten des betreffenden Datentyps, die dieselbe Regel aufweisen, aufgehoben. Spalten dieses Datentyps mit Regeln, die direkt an diese gebunden sind, sind nicht betroffen.  
  
> [!NOTE]  
>  *object_name* können eckige Klammern **[]** als Begrenzungs Bezeichner enthalten. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'`Wird nur beim Aufheben der Bindung einer Regel an einen Alias Datentyp verwendet. *futureonly_flag* ist vom Datentyp **varchar (15)** und hat den Standardwert NULL. Wenn *futureonly_flag* **futureonly**ist, verlieren vorhandene Spalten dieses Datentyps die angegebene Regel nicht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie sich den Text der Regel anzeigen lassen möchten, können Sie **sp_helptext** mit dem Regelnamen als Parameter ausführen.  
  
 Wenn eine Regel nicht gebunden wird, werden die Informationen über die Bindung aus der **sys. Columns** -Tabelle entfernt, wenn die Regel an eine Spalte gebunden wurde, und aus der **sys. types** -Tabelle, wenn die Regel an einen Alias Datentyp gebunden wurde.  
  
 Beim Aufheben der Bindung einer Regel an einen Aliasdatentyp wird auch die Bindung an alle Spalten mit diesem Aliasdatentyp aufgehoben. Die Regel kann auch weiterhin an Spalten gebunden werden, deren Datentypen später durch die ALTER COLUMN-Klausel einer ALTER TABLE-Anweisung geändert wurden. Sie müssen die Bindung der Regel an diese Spalten mithilfe von **sp_unbindrule** und angeben des Spaltennamens explizit aufheben.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Aufheben der Bindung einer Regel an eine Tabellenspalte ist die ALTER-Berechtigung für die Tabelle erforderlich. Zum Aufheben der Bindung einer Regel an einen Aliasdatentyp ist die CONTROL-Berechtigung für den Typ oder die ALTER-Berechtigung für das Schema erforderlich, zu dem der Typ gehört.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-unbinding-a-rule-from-a-column"></a>A. Aufheben der Bindung einer Regel an eine Spalte  
 Das folgende Beispiel hebt die Bindung der Regel an die `startdate`-Spalte einer `employees`-Tabelle auf.  
  
```  
EXEC sp_unbindrule 'employees.startdate';  
```  
  
### <a name="b-unbinding-a-rule-from-an-alias-data-type"></a>B. Aufheben der Bindung einer Regel an einen Aliasdatentyp  
 Das folgende Beispiel hebt die Bindung der Regel an den `ssn`-Aliasdatentyp auf. Die Bindungen der Regel an vorhandene und zukünftige Spalten dieses Typs werden aufgehoben.  
  
```  
EXEC sp_unbindrule ssn;  
```  
  
### <a name="c-using-futureonly_flag"></a>C. Verwenden von futureonly_flag  
 Das folgende Beispiel hebt die Bindung der Regel an den `ssn`-Aliasdatentyp auf, ohne dass vorhandene `ssn`-Spalten davon beeinflusst werden.  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D: Verwenden von Begrenzungs Bezeichnerzeichen  
 Im folgenden Beispiel wird die Verwendung von Begrenzungs bezeichnerbezeichnerzeichen im *object_name* -Parameter gezeigt.  
  
```  
CREATE TABLE [t.4] (c1 int); -- Notice the period as part of the table   
-- name.  
GO  
CREATE RULE rule2 AS @value > 100;  
GO  
EXEC sp_bindrule rule2, '[t.4].c1' -- The object contains two   
-- periods; the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
GO  
EXEC sp_unbindrule '[t.4].c1';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [Drop Rule &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
