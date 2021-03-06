---
title: sys. database_query_store_options (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 752b8780b810f20e2fb71f2a5b8c55fad044981c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828189"
---
# <a name="sysdatabase_query_store_options-transact-sql"></a>sys. database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt die Abfragespeicher Optionen für diese Datenbank zurück.  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] .
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Gibt den gewünschten Betriebsmodus Abfragespeicher an, der explizit vom Benutzer festgelegt wird.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|Textbeschreibung des gewünschten Betriebsmodus Abfragespeicher:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Gibt den Betriebsmodus Abfragespeicher an. Neben der Liste der für den Benutzer erforderlichen gewünschten Zustände kann der tatsächliche Zustand einen Fehlerstatus aufweisen.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = Fehler|  
|**actual_state_desc**|**nvarchar(60)**|Textbeschreibung des tatsächlichen Betriebsmodus Abfragespeicher.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERROR<br /><br /> Es gibt Situationen, in denen sich der tatsächliche Zustand vom gewünschten Zustand unterscheidet:<br />-Wenn die Datenbank auf den schreibgeschützten Modus festgelegt ist oder Abfragespeicher Größe das konfigurierte Kontingent überschreitet, können Abfragespeicher im schreibgeschützten Modus ausgeführt werden, auch wenn der Benutzer Lese-/Schreibzugriff festgelegt hat.<br />In extremen Szenarien kann Abfragespeicher aufgrund interner Fehler einen Fehlerzustand eingeben. In diesem Fall können Abfragespeicher für SQL 2017 und höher wieder hergestellt werden, indem die `sp_query_store_consistency_check` gespeicherte Prozedur in der betroffenen Datenbank ausgeführt wird. Wenn `sp_query_store_consistency_check` die Ausführung von nicht 2016 funktioniert, müssen Sie die Daten durch Ausführen von löschen.`ALTER DATABASE [YourDatabaseName] SET QUERY_STORE CLEAR ALL;`|  
|**readonly_reason**|**int**|Wenn die **desired_state_desc** READ_WRITE und die **actual_state_desc** READ_ONLY ist, gibt **readonly_reason** eine Bitmap zurück, um anzugeben, warum sich die Abfragespeicher im schreibgeschützten Modus befindet.<br /><br /> **1** -Datenbank befindet sich im schreibgeschützten Modus<br /><br /> **2** : die Datenbank befindet sich im Einzelbenutzermodus.<br /><br /> **4** -Datenbank befindet sich im Notfallmodus<br /><br /> **8** -Database ist ein sekundäres Replikat (gilt für Always on und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] georeplikation). Dieser Wert kann nur für **lesbare** sekundäre Replikate wirksam beobachtet werden.<br /><br /> **65536** -die Abfragespeicher hat die von der MAX_STORAGE_SIZE_MB-Option festgelegte Größenbeschränkung erreicht.<br /><br /> **131072** -die Anzahl der unterschiedlichen Anweisungen in Abfragespeicher hat das interne Arbeitsspeicher Limit erreicht. Entfernen Sie nicht benötigte Abfragen, oder führen Sie ein Upgrade auf eine höhere Dienst Ebene durch, um die Übertragung von Abfragespeicher in den Lese-/Schreibmodus zu ermöglichen<br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /><br /> **262144** -die Größe der in-Memory-Elemente, die auf den Datenträger warten müssen, hat das interne Arbeitsspeicher Limit erreicht. Abfragespeicher werden vorübergehend im schreibgeschützten Modus ausgeführt, bis die in-Memory-Elemente auf dem Datenträger gespeichert werden. <br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /><br /> **524288** -die Datenträger Größenbeschränkung wurde von der Datenbank erreicht. Abfragespeicher ist ein Teil der Benutzerdatenbank, d. h., wenn für eine Datenbank kein Speicherplatz mehr verfügbar ist, bedeutet dies, dass Abfragespeicher nicht mehr mehr anwachsen kann.<br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <br /> <br /> Informationen zum zurück wechseln des Abfragespeicher Betriebsmodus in den Lese-/Schreibmodus finden Sie im Abschnitt **Abfragespeicher Überprüfen der kontinuierlichen Erfassung von Abfrage Daten** [durch den Abfragespeicher](../../relational-databases/performance/best-practice-with-the-query-store.md#Verify).|  
|**current_storage_size_mb**|**bigint**|Größe des Abfragespeicher auf dem Datenträger in Megabyte.|  
|**flush_interval_seconds**|**bigint**|Der Zeitraum für die reguläre Leerung von Abfragespeicher Daten auf den Datenträger (in Sekunden). Der Standardwert ist **900** (15 min.).<br /><br /> Ändern Sie mithilfe der- `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` Anweisung.|  
|**interval_length_minutes**|**bigint**|Das Statistik-Aggregations Intervall in Minuten. Beliebige Werte sind nicht zulässig. Verwenden Sie eine der folgenden Aktionen: 1, 5, 10, 15, 30, 60 und 1440 Minuten. Der Standardwert ist **60** Minuten.|  
|**max_storage_size_mb**|**bigint**|Maximale Datenträger Größe für die Abfragespeicher in Megabyte (MB). Der Standardwert ist **100** MB.<br />Der Standardwert für die [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition ist 1 GB, und bei [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition beträgt der Standardwert 10 MB.<br /><br /> Ändern Sie mithilfe der- `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` Anweisung.|  
|**stale_query_threshold_days**|**bigint**|Anzahl von Tagen, in denen Abfragen ohne Richtlinien Einstellungen in Abfragespeicher aufbewahrt werden. Der Standardwert ist **30**. Legen Sie auf 0 fest, um die Aufbewahrungs Richtlinie zu deaktivieren.<br />Für die Basic-Edition von [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ist der Standardwert 7 Tage.<br /><br /> Ändern Sie mithilfe der- `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` Anweisung.|  
|**max_plans_per_query**|**bigint**|Begrenzt die maximale Anzahl gespeicherter Pläne. Der Standardwert ist **200**. Wenn der Höchstwert erreicht ist, beendet Abfragespeicher die Erfassung neuer Pläne für diese Abfrage. Wenn Sie auf 0 festlegen, wird die Einschränkung in Bezug auf die Anzahl der aufgezeichneten Pläne entfernt.<br /><br /> Ändern Sie mithilfe der- `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` Anweisung.|  
|**query_capture_mode**|**smallint**|Der derzeit aktive Abfrage Erfassungs Modus:<br /><br /> **1** = alle-alle Abfragen werden erfasst. Dies ist der Standard Konfigurations Wert für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher).<br /><br /> 2 = Automatische Erfassung relevanter Abfragen basierend auf der Ausführungs Anzahl und dem Ressourcenverbrauch. Dies ist der Standardkonfigurationswert für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = keine-beendet die Erfassung neuer Abfragen. Der Abfragedatenspeicher sammelt weiterhin Statistiken zur Kompilierung und Runtime für Abfragen, die bereits erfasst wurden. Verwenden Sie diese Konfiguration vorsichtig, da Sie möglicherweise die Erfassung wichtiger Abfragen übersehen.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Textbeschreibung des tatsächlichen Aufzeichnungsmodus Abfragespeicher:<br /><br /> Alle (Standardeinstellung für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] )<br /><br /> **Auto** (Standardeinstellung für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] )<br /><br /> Keine|  
|**size_based_cleanup_mode**|**smallint**|Steuert, ob die Bereinigung automatisch aktiviert wird, wenn sich die Gesamtmenge der Daten der maximalen Größe nähert:<br /><br /> 0 = die nicht auf Größen basierende Bereinigung wird nicht automatisch aktiviert.<br /><br /> **1** = die automatische Größen basierte Bereinigung wird automatisch aktiviert, wenn die Größe auf dem Datenträger **90 Prozent** der *max_storage_size_mb*erreicht. Dies ist der Standardkonfigurationswert.<br /><br />Ein auf der Größe basierendes Cleanup entfernt die am wenigsten aufwendigen und die ältesten Abfragen. Sie wird beendet, wenn ungefähr **80 Prozent** der *max_storage_size_mb* erreicht werden.|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|Textbeschreibung des tatsächlichen Größen basierten Bereinigungs Modus Abfragespeicher:<br /><br /> OFF <br /> **Auto** (Standard)|  
|**wait_stats_capture_mode**|**smallint**|Steuert, ob Abfragespeicher die Erfassung von warte Statistiken durchführt: <br /><br /> 0 = OFF <br /> **1** = on<br /> **Gilt für**:  [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] und höher.|
|**wait_stats_capture_mode_desc**|**nvarchar(60)**|Textbeschreibung des tatsächlichen Erfassungs Modus für warte Statistiken: <br /><br /> OFF <br /> **On** (Standard)<br /> **Gilt für**:  [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] und höher.| 
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. query_context_settings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys. query_store_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys. query_store_query &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys. query_store_query_text &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys. query_store_runtime_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys. query_store_runtime_stats_interval &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
