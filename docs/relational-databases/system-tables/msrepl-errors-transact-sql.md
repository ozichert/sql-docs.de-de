---
title: MSrepl_errors (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_errors
- MSrepl_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_errors system table
ms.assetid: c6e023c1-2c32-4269-8d76-e442ea309e4b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3a44dd898b4ec4afcf161e398072edfbc3f6f815
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820076"
---
# <a name="msrepl_errors-transact-sql"></a>MSrepl_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSrepl_errors** Tabelle enthält Zeilen mit erweiterten Verteilungs-Agent und Merge-Agent Fehlerinformationen. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des Fehlers.|  
|**time**|**datetime**|Zeitpunkt des Auftretens des Fehlers.|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|Die Typ-ID der Fehlerquelle.|  
|**source_name**|**nvarchar (100)**|Der Name der Fehlerquelle.|  
|**error_code**|**sysname**|Der Fehlercode.|  
|**error_text**|**ntext**|Die Fehlermeldung.|  
|**xact_seqno**|**varbinary(16)**|Die Protokollsequenznummer der ersten Transaktion des Batches, der bei der Ausführung einen Fehler erzeugt hat. Wird nur von Verteilungs-Agents verwendet und ist die Transaktions-Protokollfolgenummer der ersten Transaktion des bei der Ausführung fehlerhaften Batches.|  
|**command_id**|**int**|Die Befehls-ID des Batches, der bei der Ausführung einen Fehler erzeugt hat. Wird nur von Verteilungs-Agents verwendet und ist die Befehls-ID des ersten Befehls des Batches, der bei der Ausführung einen Fehler erzeugt hat.|  
|**session_id**|**int**|Die ID der Agentsitzung, in der der Fehler auftrat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
