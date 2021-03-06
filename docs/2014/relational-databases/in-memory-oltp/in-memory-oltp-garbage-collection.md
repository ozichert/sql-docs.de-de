---
title: In-Memory OLTP-Garbage Collection | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a28f2401f11f20f8891dbe71537ce2240a570ed8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63158247"
---
# <a name="in-memory-oltp-garbage-collection"></a>In-Memory OLTP-Garbage Collection
  Eine Datenzeile wird als veraltet betrachtet, wenn sie durch eine nicht mehr aktive Transaktion gelöscht wurde. Eine veraltete Zeile kann durch die Garbage Collection bereinigt werden. Die Garbage Collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]weist die folgenden Merkmale auf:  
  
-   Nicht blockierend. Die Garbage Collection erfolgt über einen längeren Zeitraum und wirkt sich nur minimal auf die Arbeitsauslastung aus.  
  
-   Kooperativ. Benutzertransaktionen nehmen über den GC-Hauptthread an der Garbage Collection teil.  
  
-   Effizient. Benutzertransaktionen löschen die Verknüpfungen veralteter Zeilen aus dem verwendeten Zugriffspfad (dem Index). Dadurch wird der erforderliche Aufwand bei der endgültigen Entfernung der Zeile verringert.  
  
-   Reaktionsschnell. Hohe Arbeitsspeicherauslastung führt zu aggressiver Garbage Collection.  
  
-   Skalierbar. Nach dem Commit übernehmen Benutzertransaktionen einen Teil der Garbage Collection. Je höher die Transaktionsaktivität, umso mehr werden Verknüpfungen veralteter Zeilen von den Transaktionen entfernt.  
  
 Die Garbage Collection wird vom GC-Hauptthread gesteuert. Dieser GC-Hauptthread wird einmal pro Minute ausgeführt oder wenn die Anzahl der Transaktionen, für die ein Commit ausgeführt wurde, einen internen Schwellenwert überschreitet. Aufgaben der Garbage Collection:  
  
-   Identifizieren der Transaktionen, durch die eine Reihe von Zeilen gelöscht oder aktualisiert wurden und für die vor der ältesten aktiven Transaktion ein Commit ausgeführt wurde.  
  
-   Identifizieren von Zeilenversionen, die durch diese alten Transaktionen erstellt wurden.  
  
-   Gruppieren alter Zeilen in einer oder mehrere Einheiten von jeweils 16 Zeilen. Dadurch wird die Arbeitslast der Garbage Collection auf kleinere Einheiten verteilt.  
  
-   Verschieben dieser Arbeitseinheiten in die Warteschlange der Garbage Collection (eine für jedes Zeitplanungsmodul). Ausführliche Informationen finden Sie in den Garbage Collector-DMVs: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql) und [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).  
  
 Nachdem für eine Benutzertransaktion ein Commit ausgeführt wurde, identifiziert sie alle Elemente in der Warteschlange, die dem Zeitplanungsmodul zugeordnet sind, in dem sie ausgeführt wurde, und gibt dann den Arbeitsspeicher frei. Wenn die Garbage Collection-Warteschlange im Zeitplanungsmodul leer ist, wird nach einer nicht leeren Warteschlange im aktuellen NUMA-Knoten gesucht. Bei einer geringen Transaktionsaktivität und nicht ausreichendem Arbeitsspeicher kann der Garbage Collector-Hauptthread auf GC-Zeilen aus einer beliebigen Warteschlange zugreifen. Wenn beispielsweise nach dem Löschen einer großen Anzahl von Zeilen keine Transaktionsaktivität erfolgt und kein Engpass bei der Arbeitsspeicherverfügbarkeit besteht, werden die gelöschten Zeilen erst wieder durch die Garbage Collection bereinigt, wenn die Transaktionsaktivität fortgesetzt wird bzw. nicht mehr genügend Arbeitsspeicher zur Verfügung steht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten des Arbeitsspeichers für In-Memory-OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  
