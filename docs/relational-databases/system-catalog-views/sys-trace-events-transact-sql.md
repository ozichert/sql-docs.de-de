---
title: sys. trace_events (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5bf6d23db1a6807b95e9c33f4e3bfd5f38d63982
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820905"
---
# <a name="systrace_events-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **sys. trace_events** -Katalog Sicht enthält eine Liste aller SQL-Ablauf Verfolgungs Ereignisse. Diese Ablaufverfolgungsereignisse ändern sich für eine bestimmte Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht.  
  
> **WICHTIG!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die Katalogsichten für erweiterte Ereignisse.  
  
 Weitere Informationen zu diesen Ablauf Verfolgungs Ereignissen finden Sie unter [SQL Server-Ereignis Klassenreferenz](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|Eindeutige ID des Ereignisses. Diese Spalte befindet sich auch in den Katalog Sichten **sys. trace_event_bindings** und **sys. trace_subclass_values** .|  
|**category_id**|**smallint**|Kategorie-ID des Ereignisses. Diese Spalte befindet sich auch in der Katalog Sicht **sys. trace_categories** .|  
|**name**|**nvarchar(128)**|Eindeutiger Name dieses Ereignisses. Dieser Parameter ist nicht lokalisiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. Traces &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
