---
title: MSSQLSERVER_8645 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f7a039055daf8574d0c6b217c26d6f5572dd015c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62762566"
---
# <a name="mssqlserver_8645"></a>MSSQLSERVER_8645
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8645|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|MEMTIMEDOUT_ERR|  
|Meldungstext|Timeout beim Warten auf die Arbeitsspeicherressourcen für die Abfrageausführung. Führen Sie die Abfrage erneut aus.|  
  
## <a name="explanation"></a>Erklärung  
 Timeout beim Warten auf die Arbeitsspeicherressourcen für die Abfrageausführung im Ressourcenpool 'default' (257).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie keine Ressourcenkontrolle verwenden, empfehlen wir, dass Sie den gesamten Serverstatus und die Auslastung oder die Ressourcenpooleinstellungen bzw. Einstellungen für Arbeitsauslastungsgruppen überprüfen.  
  
 In der folgenden Liste werden allgemeine Schritte erläutert, die bei der Problembehandlung von Arbeitsspeicherfehlern helfen:  
  
1.  Überprüfen Sie, ob andere Anwendungen oder Dienste Arbeitsspeicher auf dem Server beanspruchen. Rekonfigurieren Sie weniger kritische Anwendungen oder Dienste, damit sie weniger Speicher beanspruchen.  
  
2.  Sammeln Sie Leistungsindikatoren für **SQL Server: Puffer-Manager** und **SQL Server: Speicher-Manager**.  
  
3.  Überprüfen Sie die folgenden SQL Server-Speicherkonfigurationsparameter:  
  
    -   **Max. Serverarbeitsspeicher**  
  
    -   **Min. Serverarbeitsspeicher**  
  
    -   **Min. Arbeitsspeicher pro Abfrage**  
  
     Achten Sie auf ungewöhnliche Einstellungen. Berichtigen Sie sie bei Bedarf. Konto für erhöhte Arbeitsspeicheranforderungen für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Die Standardeinstellungen werden unter "Festlegen von Serverkonfigurationsoptionen" in der SQL Server-Onlinedokumentation aufgeführt.  
  
4.  Verfolgen Sie die Ausgabe von DBCC MEMORYSTATUS und deren Veränderungen beim Anzeigen der Fehlermeldungen.  
  
5.  Überprüfen Sie die Arbeitsauslastung (z. B. Anzahl gleichzeitiger Sitzungen, derzeit ausgeführte Abfragen).  
  
 Durch die folgenden Aktionen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mehr Arbeitsspeicher zur Verfügung gestellt werden:  
  
-   Wenn Anwendungen außer SQL Server Ressourcen verbrauchen, sollten Sie diese Anwendungen beenden oder auf einem separaten Server ausführen. Dadurch fällt der Mangel an externem Arbeitsspeicher weg.  
  
-   Wenn Sie **Max. Serverarbeitsspeicher**  konfiguriert haben, erhöhen Sie dessen Wert.  
  
 Führen Sie die folgenden DBCC-Befehle aus, um mehrere SQL Server-Speichercaches freizugeben.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Wenn das Problem weiterhin besteht, müssen Sie weitere Untersuchungen ausführen und möglicherweise die Arbeitsauslastung reduzieren.  
  
  
