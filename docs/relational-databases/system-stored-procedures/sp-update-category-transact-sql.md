---
title: sp_update_category (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_category
- sp_update_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_category
ms.assetid: 098b926a-b078-4122-a5e1-3ef54b979dd4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b0af70ae46d73a7eedde55c2fcd7e93f63be8928
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832535"
---
# <a name="sp_update_category-transact-sql"></a>sp_update_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Namen einer Kategorie.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_category  
     [@class =] 'class' ,   
     [@name =] 'old_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @class = ] 'class'`Die Klasse der zu aktualisierenden Kategorie. die *Klasse*ist vom Datentyp **varchar (8)** und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Warnung**|Aktualisiert eine Warnungskategorie.|  
|**Auftrag**|Aktualisiert eine Auftragskategorie.|  
|**KOM**|Aktualisiert eine Operatorkategorie.|  
  
`[ @name = ] 'old_name'`Der aktuelle Name der Kategorie. *old_name*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @new_name = ] 'new_name'`Der neue Name für die Kategorie. *new_name*ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_update_category** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss den Benutzern die festen Server Rolle **sysadmin** erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Auftragskategorie von `AdminJobs` in `Administrative Jobs` umbenannt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_category  
  @class = N'JOB',  
  @name = N'AdminJobs',  
  @new_name = N'Administrative Jobs' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
