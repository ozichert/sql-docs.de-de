---
title: SQL Server, Plancache-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: a181919a40ce2e53c9fef9887f5c7ec6ff93fc5b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68130846"
---
# <a name="sql-server-plan-cache-object"></a>SQL Server, Plancache-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das **Plancache** -Objekt stellt Indikatoren bereit, mit denen überwacht werden kann, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Arbeitsspeicher zum Speichern von Objekten verwendet, z. B. gespeicherten Prozeduren, Ad-hoc-Anweisungen, vorbereiteten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen sowie Triggern. Es können mehrere Instanzen des **Plancache** -Objekts gleichzeitig überwacht werden, wobei jede Instanz einen unterschiedlichen Typ von zu überwachendem Plan darstellt.  
  
 In dieser Tabelle werden die **SQLServer:Plancache**Leistungsindikatoren beschrieben.  
  
|SQL Server, Plancache-Leistungsindikatoren|BESCHREIBUNG|  
|------------------------------------|-----------------|  
|**Cachetrefferquote**|Das Verhältnis zwischen Cachetreffern und -suchvorgängen.|  
|**Basis für Cachetrefferquote**|Nur zur internen Verwendung.| 
|**Cacheobjektzähler**|Anzahl der Cacheobjekte im Cache.|  
|**Cacheseiten**|Anzahl der von Cacheobjekten verwendeten 8-KB-Seiten.|  
|**Verwendete Cacheobjekte**|Anzahl der verwendeten Cacheobjekte.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Plancache-Instanz|BESCHREIBUNG|  
|-------------------------|-----------------|  
|**_Total**|Informationen zu allen Typen von Cacheinstanzen.|  
|**Sql-Pläne**|Abfragepläne, die von einer Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage, einschließlich automatisch parametrisierten Abfragen, oder durch [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen generiert wurden, die mit **sp_prepare** oder **sp_cursorprepare**vorbereitet wurden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert die Pläne für Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen für die spätere Wiederverwendung zwischen, wenn die identische [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung später ausgeführt wird. Vom Benutzer parametrisierte Abfragen (selbst wenn sie nicht ausdrücklich vorbereitet sind) werden ebenfalls mit Prepared SQL Plans überwacht.|  
|**Objektpläne**|Abfragepläne, die durch Erstellen von gespeicherten Prozeduren, Funktionen oder Triggern generiert wurden.|  
|**Gebundene Strukturen**|Normalisierte Strukturen für Sichten, Regeln, berechnete Spalten und CHECK-Einschränkungen.|  
|**Erweiterte gespeicherte Prozeduren**|Kataloginformationen für erweiterte Prozeduren.|  
|**Temporäre Tabellen & Tabellenvariablen**|Cacheinformationen zu temporären Tabellen und Tabellenvariablen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [SQL Server, Puffer-Manager-Objekt](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
