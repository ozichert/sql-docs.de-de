---
title: Erstellen und Ausführen von Ablaufverfolgungen mit gespeicherten Transact-SQL-Prozeduren
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3d1c5a85072bec1fc304156268680c201ad2245e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74095641"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a>Erstellen und Ausführen von Ablaufverfolgungen mit gespeicherten Transact-SQL-Prozeduren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der Ablaufverfolgungsprozess mithilfe der SQL-Ablaufverfolgung hängt davon ab, ob Sie die Ablaufverfolgung mithilfe von Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oder mithilfe gespeicherter Systemprozeduren ausführen.  
  
 Anstelle von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Systemprozeduren zum Erstellen und Ausführen von Ablaufverfolgungen verwenden. Der Ablaufverfolgungsprozess mithilfe gespeicherter Systemprozeduren sieht folgendermaßen aus:  
  
1.  Erstellen Sie eine Ablaufverfolgung mithilfe von **sp_trace_create**.  
  
2.  Fügen Sie mit **sp_trace_setevent**Ereignisse hinzu.  
  
3.  (Optional) Legen Sie mit **sp_trace_setfilter**einen Filter fest.  
  
4.  Starten Sie die Ablaufverfolgung mit **sp_trace_setstatus**.  
  
5.  Halten Sie die Ablaufverfolgung mit **sp_trace_setstatus**an.  
  
6.  Schließen Sie die Ablaufverfolgung mit **sp_trace_setstatus**.  
  
    > [!NOTE]  
    >  Beim Verwenden gespeicherter [!INCLUDE[tsql](../../includes/tsql-md.md)] -Systemprozeduren wird eine serverseitige Ablaufverfolgung erstellt. Dadurch wird sichergestellt, dass keine Ereignisse verloren gehen, sofern auf dem Datenträger Speicherplatz vorhanden ist und keine Schreibfehler auftreten. Wenn der Datenträger voll ist oder ein Datenträgerfehler auftritt, wird die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiterhin ausgeführt, aber die Ablaufverfolgung wird angehalten. Wenn **C2-Überwachungsmodus** festgelegt ist und ein Schreibfehler auftritt, wird die Ablaufverfolgung angehalten, und die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird heruntergefahren. Weitere Informationen finden zur Einstellung **C2-Überwachungsmodus** finden Sie unter [C2-Überwachungsmodus (Serverkonfigurationsoption)](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Optimieren der SQL-Ablaufverfolgung](../../relational-databases/sql-trace/optimize-sql-trace.md)|Enthält Informationen dazu, wie Sie die Auswirkungen der Ablaufverfolgung auf die Systemleistung verringern können.|  
|[Filtern einer Ablaufverfolgung](../../relational-databases/sql-trace/filter-a-trace.md)|Enthält Informationen zum Verwenden von Filtern für die Ablaufverfolgung.|  
|[Beschränken der Größe von Ablaufverfolgungsdatei und -tabelle](../../relational-databases/sql-trace/limit-trace-file-and-table-sizes.md)|Enthält Informationen dazu, wie Sie die Größe von Dateien und Tabellen, in die Ablaufverfolgungsdaten geschrieben werden, beschränken können. Beachten Sie, dass Ablaufverfolgungsinformationen nur von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in Tabellen geschrieben werden können.|  
|[Planen von Ablaufverfolgungen](../../relational-databases/sql-trace/schedule-traces.md)|Enthält Informationen zum Einstellen der Start- und Beendigungszeit für die Ablaufverfolgung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
