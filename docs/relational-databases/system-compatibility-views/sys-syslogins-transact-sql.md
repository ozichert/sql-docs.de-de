---
title: sys. syslogins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5745d3f98741d4a414c7bb69d8f9865258d47e34
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020010"
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Anmeldekonto.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis zur [aktuellen Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary(85)**|Sicherheits-ID.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**mit "up"**|**datetime**|Datum, an dem der Anmeldename hinzugefügt wurde.|  
|**Update Date**|**datetime**|Datum, an dem der Anmeldename aktualisiert wurde.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Anmeldename des Benutzers.|  
|**dbname**|**sysname**|Name der Standarddatenbank des Benutzers beim Herstellen einer Verbindung.|  
|**password**|**nvarchar(128)**|Gibt NULL zurück.|  
|**Kurse**|**sysname**|Standardsprache des Benutzers.|  
|**denylogin**|**int**|1 = Anmeldename ist ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzer oder eine Windows-Gruppe, dem bzw. der der Zugriff verweigert wurde.|  
|**hasaccess**|**int**|1 = Dem Anmeldenamen wurde der Zugriff auf den Server erteilt.|  
|**isntname**|**int**|1 = Anmeldename ist ein Windows-Benutzer oder eine Windows-Gruppe.<br /><br /> 0 = Anmeldename ist ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename.|  
|**isntgroup**|**int**|1 = Anmeldename ist eine Windows-Gruppe.|  
|**isntuser**|**int**|1 = Anmeldename ist ein Windows-Benutzer.|  
|**Serverrollen**|**int**|1 = Der Anmeldename ist ein Mitglied der **sysadmin** -Serverrolle.|  
|**securityadmin**|**int**|1 = Der Anmeldename ist ein Mitglied der **securityadmin** -Serverrolle.|  
|**serveradmin**|**int**|1 = Der Anmeldename ist ein Mitglied der **serveradmin** -Serverrolle.|  
|**setupadmin**|**int**|1 = Der Anmeldename ist ein Mitglied der **setupadmin** -Serverrolle.|  
|**processadmin**|**int**|1 = Der Anmeldename ist ein Mitglied der **processadmin** -Serverrolle.|  
|**diskadmin**|**int**|1 = Der Anmeldename ist ein Mitglied der **diskadmin** -Serverrolle.|  
|**dbcreator**|**int**|1 = Der Anmeldename ist ein Mitglied der **dbcreator** -Serverrolle.|  
|**bulkadmin**|**int**|1 = Der Anmeldename ist ein Mitglied der festen Serverrolle **bulkadmin** .|  
|**LoginName**|**nvarchar(128)**|Anmeldename des Benutzers. Dieser Parameter wird aus Gründen der Abwärtskompatibilität bereitgestellt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
