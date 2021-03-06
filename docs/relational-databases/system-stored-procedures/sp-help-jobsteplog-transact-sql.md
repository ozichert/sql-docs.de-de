---
title: sp_help_jobsteplog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 522672192ab955ced5987184ed2f6ea2812a431a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827554"
---
# <a name="sp_help_jobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Metadaten zu einem bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Auftrags Schritt Protokoll des-Agents zurück. **sp_help_jobsteplog** gibt das tatsächliche Protokoll nicht zurück.  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] 'job_id'`Die ID des Auftrags, für den Auftrags Schritt-Protokollinformationen zurückgegeben werden sollen. *job_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @step_id = ] step_id`Die ID des Auftrags Schritts. Wenn diese nicht angegeben wird, sind alle Schritte im Auftrag eingeschlossen. *step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @step_name = ] 'step_name'`Der Name des Schritts im Auftrag. *step_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Eindeutiger Bezeichner des Auftrags.|  
|**job_name**|**sysname**|Der Name des Auftrags.|  
|**step_id**|**int**|Bezeichner des Schritts innerhalb des Auftrags. Wenn der Schritt beispielsweise der erste Schritt des Auftrags ist, ist sein *step_id* 1.|  
|**step_name**|**sysname**|Name des Auftragsschritts.|  
|**step_uid**|**uniqueidentifier**|Eindeutiger Bezeichner des Schritts (systemgeneriert) im Auftrag.|  
|**date_created**|**datetime**|Datum, an dem der Schritt erstellt wurde.|  
|**date_modified**|**datetime**|Datum, an dem der Schritt zuletzt geändert wurde.|  
|**log_size**|**float**|Größe des Auftragsschrittprotokolls in MB.|  
|**angezeigt**|**nvarchar(max)**|Ausgabe des Auftragsschrittprotokolls.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_jobsteplog** in der **msdb** -Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder von **SQLAgentUserRole** können nur die Metadaten des Auftrags Schritt Protokolls für Auftrags Schritte anzeigen, die Sie besitzen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. Gibt Auftragsschritt-Protokollinformationen für alle Schritte in einem bestimmten Auftrag zurück  
 Im folgenden Beispiel werden alle Auftragsschrittinformationen für den Auftrag namens `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. Zurückgeben von Auftragsschritt-Protokollinformationen zu einem bestimmten Auftragsschritt  
 Im folgenden Beispiel werden Auftragsschrittinformationen zum ersten Auftragsschritt des Auftrags namens `Weekly Sales Data Backup` zurückgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
