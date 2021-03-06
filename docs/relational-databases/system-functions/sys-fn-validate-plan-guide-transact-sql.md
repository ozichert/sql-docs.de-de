---
title: sys. fn_validate_plan_guide (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_validate_plan_guide
- sys.fn_validate_plan_guide_TSQL
- fn_validate_plan_guide
- fn_validate_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_validate_plan_guide function
- sys.fn_validate_plan_guide function
ms.assetid: 3af8b47a-936d-4411-91d1-d2d16dda5623
author: rothja
ms.author: jroth
ms.openlocfilehash: a76835272ed86faeab807f97f6e8801985062733
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68059195"
---
# <a name="sysfn_validate_plan_guide-transact-sql"></a>sys.fn_validate_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft die Gültigkeit der angegebenen Planhinweisliste. Die sys.fn_validate_plan_guide-Funktion gibt die erste Fehlermeldung zurück, die beim Anwenden der Planhinweisliste auf ihre Abfrage gefunden wird. Ein leeres Rowset wird zurückgegeben, wenn die Planhinweisliste gültig ist. Planhinweislisten können ungültig werden, nachdem Änderungen am physischen Entwurf der Datenbank vorgenommen wurden. Wenn beispielsweise eine Planhinweisliste einen bestimmten Index angibt, und dieser Index anschließend gelöscht wird, kann die Abfrage die Planhinweisliste nicht länger verwenden.  
  
 Durch Überprüfen der Gültigkeit einer Planhinweisliste können Sie feststellen, ob die Planhinweisliste ohne Änderungen durch den Optimierer verwendet werden kann. Auf der Basis der Ergebnisse der Funktion können Sie entscheiden, dass die Planhinweisliste gelöscht wird und die Abfrage neu optimiert wird, oder Sie können den Datenbankentwurf ändern, indem Sie beispielsweise den in der Planhinweisliste angegebenen Index neu erstellen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.fn_validate_plan_guide ( plan_guide_id )  
```  
  
## <a name="arguments"></a>Argumente  
 *plan_guide_id*  
 Die ID der Planhinweisliste, wie sie in der [sys.plan_guides](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md) -Katalogsicht angegeben ist. *plan_guide_id* ist vom Datentyp **int** und besitzt keinen Standardwert.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|msgnum|**int**|ID der Fehlermeldung.|  
|severity|**tinyint**|Schweregrad des Fehlers, der zwischen 1 und 25 liegen kann.|  
|state|**smallint**|Statusnummer des Fehlers, welche die Stelle im Code angibt, an der der Fehler aufgetreten ist.|  
|message|**nvarchar (2048)**|Meldungstext des Fehlers.|  
  
## <a name="permissions"></a>Berechtigungen  
 Für Planhinweislisten mit dem Bereich OBJECT ist die VIEW DEFINITION- oder die ALTER-Berechtigung für das Objekt erforderlich, auf das verwiesen wird, ebenso wie Berechtigungen zur Kompilierung der Abfrage oder des Batches, die in der Planhinweisliste bereitgestellt werden. Wenn ein Batch z. B. SELECT-Anweisungen enthält, sind SELECT-Berechtigungen für die Objekte erforderlich, auf die verwiesen wird.  
  
 Für Planhinweislisten mit dem Bereich SQL oder TEMPLATE ist die ALTER-Berechtigung für die Datenbank erforderlich, ebenso wie Berechtigungen zur Kompilierung der Abfrage oder des Batches, die in der Planhinweisliste bereitgestellt werden. Wenn ein Batch z. B. SELECT-Anweisungen enthält, sind SELECT-Berechtigungen für die Objekte erforderlich, auf die verwiesen wird.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-validating-all-plan-guides-in-a-database"></a>A. Überprüfen aller Planhinweislisten in einer Datenbank  
 Im folgenden Beispiel wird die Gültigkeit aller Planhinweislisten in der aktuellen Datenbank überprüft. Wenn ein leeres Resultset zurückgegeben wird, sind alle Planhinweislisten gültig.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT plan_guide_id, msgnum, severity, state, message  
FROM sys.plan_guides  
CROSS APPLY fn_validate_plan_guide(plan_guide_id);  
GO  
```  
  
### <a name="b-testing-plan-guide-validation-before-implementing-a-change-to-the-database"></a>B. Testen der Gültigkeitsüberprüfung der Planhinweislisten vor dem Implementieren von Änderungen an der Datenbank  
 Im folgenden Beispiel wird eine explizite Transaktion verwendet, um einen Index zu löschen. Die Funktion `sys.fn_validate_plan_guide` -Funktion wird ausgeführt, um zu bestimmen, ob durch diese Aktion Planhinweislisten in der Datenbank ungültig gemacht werden. Auf der Basis der Ergebnisse der Funktion wird entweder ein Commit der `DROP INDEX` -Anweisung oder ein Rollback der Transaktion ausgeführt, sodass der Index nicht gelöscht wird.  
  
```sql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DROP INDEX IX_SalesOrderHeader_CustomerID ON Sales.SalesOrderHeader;  
-- Check for invalid plan guides.  
IF EXISTS (SELECT plan_guide_id, msgnum, severity, state, message  
           FROM sys.plan_guides  
           CROSS APPLY sys.fn_validate_plan_guide(plan_guide_id))  
    ROLLBACK TRANSACTION;  
ELSE  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Hinweis Listen](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
