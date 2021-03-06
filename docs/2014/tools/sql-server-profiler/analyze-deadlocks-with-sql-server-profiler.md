---
title: Analysieren von Deadlocks mit SQL Server Profiler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- process nodes [SQL Server Profiler]
- Profiler [SQL Server Profiler], deadlocks
- deadlocks [SQL Server], identifying cause
- resource nodes [SQL Server Profiler]
- graphs [SQL Server Profiler]
- SQL Server Profiler, deadlocks
- events [SQL Server], deadlocks
- edges [SQL Server Profiler]
ms.assetid: 72d6718f-501b-4ea6-b344-c0e653f19561
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca1882faa9c61536d1ef025058322f141beedafd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63316330"
---
# <a name="analyze-deadlocks-with-sql-server-profiler"></a>Analysieren von Deadlocks mit SQL Server Profiler
  Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um die Ursache für einen Deadlock zu identifizieren. Ein Deadlock tritt dann auf, wenn eine zyklische Abhängigkeit zwischen mindestens zwei Threads oder Prozessen für eine beliebige Gruppe von Ressourcen in SQL Server besteht. Mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie eine Ablaufverfolgung erstellen, die Deadlockereignisse zu Analysezwecken aufzeichnet, wiedergibt und anzeigt.  
  
 Um eine Ablaufverfolgung für Deadlockereignisse auszuführen, fügen Sie die **Deadlock graph** -Ereignisklasse zu einer Ablaufverfolgung hinzu. Diese Ereignisklasse füllt die **TextData** -Datenspalte in der Ablaufverfolgung mit XML-Daten zum Prozess sowie zu vom Deadlock betroffenen Objekten auf. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] kann das XML-Dokument in eine Deadlock-XML-Datei (.xdl) extrahieren, die Sie später in SQL Server Management Studio anzeigen können. Sie können [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] so konfigurieren, dass **Deadlock graph** -Ereignisse entweder in eine einzelne Datei mit allen **Deadlock graph** -Ereignissen oder in separate Dateien extrahiert werden. Das Extrahieren kann auf eine der folgenden Arten ausgeführt werden:  
  
-   Beim Konfigurieren der Ablaufverfolgung über die Registerkarte **Ereignisextraktionseinstellungen** . Beachten Sie, dass diese Registerkarte erst angezeigt wird, wenn Sie das **Deadlock graph** -Ereignis auf der Registerkarte **Ereignisauswahl** ausgewählt haben.  
  
-   Mithilfe der Option **SQL Server-Ereignisse extrahieren** im Menü **Datei**  
  
-   Einzelne Ereignisse können auch extrahiert und gespeichert werden, indem Sie mit der rechten Maustaste auf ein bestimmtes Ereignis klicken und **Ereignisdaten extrahieren**auswählen.  
  
## <a name="deadlock-graphs"></a>Deadlockdiagramme  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden Deadlock-Wartediagramme zum Beschreiben von Deadlocks. Das Deadlock-Wartediagramm enthält Prozessknoten, Ressourcenknoten und Rahmen, die die Beziehungen zwischen den Prozessen und Ressourcen darstellen. Die folgende Tabelle enthält die Definitionen der Komponenten in Wartediagrammen:  
  
 Prozessknoten  
 Ein Thread, der eine Aufgabe ausführt, beispielsweise INSERT, UPDATE oder DELETE  
  
 Ressourcenknoten  
 Ein Datenbankobjekt, beispielsweise eine Tabelle, ein Index oder eine Zeile  
  
 Microsoft Edge  
 Die Beziehung zwischen einen Prozess und einer Ressource. Ein `request`-Rahmen tritt auf, wenn ein Prozess auf eine Ressource wartet. Ein `owner`-Rahmen tritt auf, wenn eine Ressource auf einen Prozess wartet. Die Rahmenbeschreibung enthält den Sperrmodus. Beispiel: **Modus: X**.  
  
## <a name="deadlock-process-node"></a>Deadlock-Prozessknoten  
 In einem Wartediagramm enthält der Prozessknoten Informationen zum Prozess. In der folgenden Tabelle werden die Komponenten eines Prozesses erläutert.  
  
|Komponente|Definition|  
|---------------|----------------|  
|Serverprozess-ID|Serverprozessbezeichner (Server Process Identifier, SPID). Ein vom Server zugewiesener Bezeichner für den Prozess, der im Besitz der Sperre ist.|  
|Serverbatch-ID|Serverbatch-Bezeichner (Server Batch Identifier, SBID)|  
|Ausführungskontext-ID|Ausführungskontext-Bezeichner (Execution Context ID, ECID). Die Ausführungskontext-ID für einen bestimmten Thread, der einer bestimmten SPID zugeordnet ist.<br /><br /> ECID = {0,1,2,3, *...n*}, wobei 0 immer den übergeordneten Thread oder Hauptthread darstellt und {1,2,3, *...n*} die Subthreads.|  
|Deadlockpriorität|Deadlockpriorität für den Prozess. Weitere Informationen zu den möglichen Werten finden Sie unter [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql).|  
|Verwendetes Protokoll|Protokollspeicherplatz, der vom Prozess belegt wird|  
|Besitzer-ID|Transaktions-ID für die Prozesse, die Transaktionen verwenden und sich aufgrund einer Sperre gegenwärtig im Wartezustand befinden|  
|Transaktionsdeskriptor|Zeiger auf den Transaktionsdeskriptor, der den Transaktionszustand beschreibt|  
|Eingabepuffer|Eingabepuffer des aktuellen Prozesses. Er definiert den Ereignistyp und die ausgeführte Anweisung. Mögliche Werte sind:<br /><br /> **Sprache**<br /><br /> **RPC**<br /><br /> **None**|  
|-Anweisung.|Der Anweisungstyp. Mögliche Werte:<br /><br /> **NOP**<br /><br /> **SELECT**<br /><br /> **UPDATE**<br /><br /> **INSERT**<br /><br /> **DELETE**<br /><br /> **Unbekannt**|  
  
## <a name="deadlock-resource-node"></a>Deadlock-Ressourcenknoten  
 Bei einem Deadlock warten zwei Prozesse auf eine Ressource, die vom jeweils anderen Prozess beansprucht wird. In einem Deadlockdiagramm werden die Ressourcen als Ressourcenknoten angezeigt.  
  
  
