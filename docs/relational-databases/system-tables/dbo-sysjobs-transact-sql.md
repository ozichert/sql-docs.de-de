---
title: dbo. sysjobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8fe374a81fc88b6591da8fb0303d5ea490cccac0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806975"
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Speichert die Informationen für jeden geplanten Auftrag, der vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt werden soll. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Eindeutige ID des Auftrags.|  
|**originating_server_id**|**int**|ID des Servers, von dem der Auftrag stammt.|  
|**name**|**sysname**|Der Name des Auftrags.|  
|**wodurch**|**tinyint**|Zeigt an, ob der Auftrag für die Ausführung aktiviert ist.|  
|**Beschreibung**|**nvarchar(512)**|Die Beschreibung des Auftrags.|  
|**start_step_id**|**int**|ID des Schrittes in dem Auftrag, bei dem die Ausführung beginnen soll.|  
|**category_id**|**int**|ID der Auftragskategorie.|  
|**owner_sid**|**varbinary(85)**|Sicherheits-ID (SID, System Identification Number) des Auftragsbesitzers.|  
|**notify_level_eventlog**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen ein Benachrichtigungs Ereignis im Microsoft Windows-Anwendungsprotokoll protokolliert werden soll:<br /><br /> **0** = Nie<br /><br /> **1** = Bei erfolgreicher Ausführung des Auftrags<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_level_email**|**int**|Bitmaske, die anzeigt, unter welchen Umständen beim Abschließen eines Auftrags eine Benachrichtigungs-E-Mail gesendet werden soll.<br /><br /> **0** = Nie<br /><br /> **1** = Bei erfolgreicher Ausführung des Auftrags<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_level_netsend**|**int**|Bitmaske, die anzeigt, unter welchen Umständen beim Abschließen eines Auftrags eine Netzwerkmeldung gesendet werden soll.<br /><br /> **0** = Nie<br /><br /> **1** = Bei erfolgreicher Ausführung des Auftrags<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_level_page**|**int**|Bitmaske, die anzeigt, unter welchen Umständen beim Abschließen eines Auftrags eine Pager-Nachricht gesendet werden soll.<br /><br /> **0** = Nie<br /><br /> **1** = Bei erfolgreicher Ausführung des Auftrags<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**notify_email_operator_id**|**int**|E-Mail-Name des Operators, der benachrichtigt werden soll.|  
|**notify_netsend_operator_id**|**int**|ID des Computers oder Benutzers, die beim Senden von Netzwerkmeldungen verwendet wird.|  
|**notify_page_operator_id**|**int**|ID des Computers oder Benutzers, die beim Senden einer Pager-Nachricht verwendet wird.|  
|**delete_level**|**int**|**Bitmaske** , die anzeigt, unter welchen Umständen der Auftrag beim Abschließen eines Auftrags gelöscht werden soll:<br /><br /> **0** = Nie<br /><br /> **1** = Bei erfolgreicher Ausführung des Auftrags<br /><br /> **2** = Bei Fehlschlagen des Auftrags<br /><br /> **3** = Immer, wenn der Auftrag abgeschlossen ist (unabhängig vom Ergebnis des Auftrags)|  
|**date_created**|**datetime**|Datum, an dem der Auftrag erstellt wurde.|  
|**date_modified**|**datetime**|Datum, an dem der Auftrag zuletzt geändert wurde.|  
|**version_number**|**int**|Version des Auftrags.|  
  
  
