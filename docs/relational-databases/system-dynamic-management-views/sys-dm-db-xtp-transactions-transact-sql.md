---
title: sys. dm_db_xtp_transactions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_transactions
- sys.dm_db_xtp_transactions_TSQL
- dm_db_xtp_transactions
- dm_db_xtp_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_transactions dynamic management view
ms.assetid: 5c1a0a7a-e851-4b6f-8dfd-c9655fbf5a51
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d83894ed9ca328db945201c0078c1f560ee2e618
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830740"
---
# <a name="sysdm_db_xtp_transactions-transact-sql"></a>sys.dm_db_xtp_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Meldet die aktiven Transaktionen in der In-Memory-OLTP-Datenbank-Engine.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
    
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|xtp_transaction_id|**bigint**|Die interne ID für diese Transaktion im XTP-Transaktions-Manager.|  
|transaction_id|**bigint**|Die Transaktions-ID. Joins mit der Transaktions-ID in anderen transaktionsbezogenen DMVs, z. B. sys.dm_tran_active_transactions.<br /><br /> 0 nur für XTP-Transaktionen, z. B. Transaktionen, die von systemintern kompilierten gespeicherten Prozeduren gestartet werden.|  
|session_id|**smallint**|Die Sitzungs-ID der Sitzung, die diese Transaktion ausführt. Joins mit sys.dm_exec_sessions.|  
|begin_tsn|**bigint**|Transaktionsseriennummer zum Starten der Transaktion.|  
|end_tsn|**bigint**|Transaktionsseriennummer zum Beenden der Transaktion.|  
|state|**int**|Der Status der Transaktion:<br /><br /> 0=ACTIVE<br /><br /> 1=COMMITTED<br /><br /> 2=ABORTED<br /><br /> 3=VALIDATING|  
|state_desc|**nvarchar**|Die Beschreibung des Transaktionsstatus.|  
|result|**int**|Das Ergebnis dieser Transaktion. Folgende Werte sind möglich:<br /><br /> 0 - IN PROGRESS<br /><br /> 1 - SUCCESS<br /><br /> 2 - ERROR<br /><br /> 3 - COMMIT DEPENDENCY<br /><br /> 4 - VALIDATION FAILED (RR)<br /><br /> 5 - VALIDATION FAILED (SR)<br /><br /> 6 - ROLLBACK|  
|result_desc|**nvarchar**|Das Ergebnis dieser Transaktion. Folgende Werte sind möglich:<br /><br /> IN PROGRESS<br /><br /> SUCCESS<br /><br /> ERROR<br /><br /> COMMIT DEPENDENCY<br /><br /> VALIDATION FAILED (RR)<br /><br /> VALIDATION FAILED (SR)<br /><br /> ROLLBACK|  
|last_error|**int**|Nur interne Verwendung.|  
|is_speculative|**bit**|Nur interne Verwendung.|  
|is_prepared|**bit**|Nur interne Verwendung.|  
|is_delayed_durability|**bit**|Nur interne Verwendung.|  
|memory_address|**varbinary**|Nur interne Verwendung.|  
|database_address|**varbinary**|Nur interne Verwendung.|  
|thread_id|**int**|Nur interne Verwendung.|  
|read_set_row_count|**int**|Nur interne Verwendung.|  
|write_set_row_count|**int**|Nur interne Verwendung.|  
|scan_set_count|**int**|Nur interne Verwendung.|  
|savepoint_garbage_count|**int**|Nur interne Verwendung.|  
|log_bytes_required|**bigint**|Nur interne Verwendung.|  
|count_of_allocations|**int**|Nur interne Verwendung.|  
|allocated_bytes|**int**|Nur interne Verwendung.|  
|reserved_bytes|**int**|Nur interne Verwendung.|  
|commit_dependency_count|**int**|Nur interne Verwendung.|  
|commit_dependency_total_attempt_count|**int**|Nur interne Verwendung.|  
|scan_area|**int**|Nur interne Verwendung.|  
|scan_area_desc|**nvarchar**|Nur interne Verwendung.|  
|scan_location|**int**|Nur zur internen Verwendung.|  
|dependent_1_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_2_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_3_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_4_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_5_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_6_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_7_address|**varbinary(8)**|Nur interne Verwendung.|  
|dependent_8_address|**varbinary(8)**|Nur interne Verwendung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
