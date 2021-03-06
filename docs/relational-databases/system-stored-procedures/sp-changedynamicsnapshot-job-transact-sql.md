---
title: sp_changedynamicsnapshot_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedynamicsnapshot_job
- sp_changedynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_changedynamicsnapshot_job
ms.assetid: ea0dacd2-a5fd-42f4-88dd-7d289b0ae017
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67aeb7243b52ef4675b9effea27d3c81c1078538
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829621"
---
# <a name="sp_changedynamicsnapshot_job-transact-sql"></a>sp_changedynamicsnapshot_job (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert den Agentauftrag, der die Momentaufnahme für ein Abonnement einer Veröffentlichung mit einem parametrisierten Zeilenfilter generiert. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changedynamicsnapshot_job [ @publication = ] 'publication'  
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
    [ , [ @frequency_type = ] frequency_type ]   
    [ , [ @frequency_interval = ] frequency_interval ]   
    [ , [ @frequency_subday = ] frequency_subday ]   
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]   
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]   
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]   
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Der Name des Momentaufnahme Auftrags, der geändert wird. *dynamic_snapshot_jobname*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert N '% '. Wenn *dynamic_snapshot_jobid* angegeben ist, müssen Sie den Standardwert für *dynamic_snapshot_jobname*verwenden.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Die ID des Momentaufnahme Auftrags, der geändert wird. *dynamic_snapshot_jobid* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL. Wenn *dynamic_snapshot_jobname*angegeben ist, müssen Sie den Standardwert für *dynamic_snapshot_jobid*verwenden.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Agent geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|On-Demand-Streaming|  
|**4**|Täglich|  
|**8**|Wöchentlich|  
|**Uhr**|Monatlich|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
|NULL (Standard)||  
  
`[ @frequency_interval = ] frequency_interval`Die Tage, an denen der Agent ausgeführt wird. *frequency_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Sonntag|  
|**2**|Montag|  
|**3**|Tuesday|  
|**4**|Wednesday|  
|**5**|Thursday|  
|**6**|Freitag|  
|**7**|Samstag|  
|**8**|Tag|  
|**9**|Wochentage|  
|**10**|Wochenendtage|  
|NULL (Standard)||  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4**|Minute|  
|**8**|Stunde|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum, an dem die Merge-Agent ausgeführt wird. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|First (Erster)|  
|**2**|Sekunde|  
|**4**|Dritter|  
|**8**|Vierter|  
|**Uhr**|Last (Letzter)|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Merge-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Merge-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der die Merge-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der die Merge-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @job_login = ] 'job_login'`Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Momentaufnahmen-Agent ausgeführt wird, wenn die Momentaufnahme für ein Abonnement mithilfe eines parametrisierten Zeilen Filters erzeugt wird. *job_login* ist vom Datentyp **nvarchar (257)** und hat den Standardwert NULL.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem die Momentaufnahmen-Agent ausgeführt wird, wenn die Momentaufnahme für ein Abonnement mithilfe eines parametrisierten Zeilen Filters erzeugt wird. *job_password* ist vom Datentyp **nvarchar (257)** und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changedynamicsnapshot_job** wird bei der Mergereplikation für Veröffentlichungen mit parametrisierten Zeilen filtern verwendet.  
  
 Nach dem Ändern des Anmeldenamens oder Kennworts eines Agents müssen Sie den Agent beenden und neu starten, damit die Änderungen in Kraft treten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changedynamicsnapshot_job**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Replikations Sicherheitseinstellungen](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Momentaufnahmen für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
  
