---
title: Auf dem Oracle-Verleger erstellte Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], objects created
ms.assetid: c58a124b-4da7-46e2-9292-af8ce9e6664b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 99e1d1f0692e5460e2c7003b0ab8dca860deca4f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63022150"
---
# <a name="objects-created-on-the-oracle-publisher"></a>Objects Created on the Oracle Publisher
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Replikation installiert Datenbankobjekte auf dem Oracle-Verleger, um die[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Änderungs Nachverfolgung und-Weiterleitung zu aktivieren (installiert keine Binärdateien auf dem Oracle-Verleger). Die folgende Tabelle enthält eine Übersicht über die Objekte, die auf dem Oracle-Verleger erstellt werden, wenn dieser auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verteiler als Verleger identifiziert wird. Die Beschreibung der Objekte dient nur zu Informationszwecken. Diese Objekte dürfen nicht geändert werden.  
  
|Objektname|Objekttyp|BESCHREIBUNG|  
|-----------------|-----------------|-----------------|  
|HREPL_ArticleNlog_V|Tabelle|Änderungsnachverfolgungstabelle mit Informationen zu Änderungen der veröffentlichten Tabelle. Eine Änderungsnachverfolgungstabelle wird für jede veröffentlichte Tabelle erstellt.|  
|HREPL_Changes|Tabelle|Tabelle, die intern vom Xactset Job zur Bestimmung der Anzahl der Änderungen verwendet wird, die auf die Zuweisung zu einem Transaktionssatz warten. Weitere Informationen zu diesem Auftrag finden Sie unter [Leistungsoptimierung für Oracle-Verleger](performance-tuning-for-oracle-publishers.md).|  
|HREPL_Distributor|Tabelle|Verteilerstatustabelle, in der die Informationen zu dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verteiler gespeichert werden, der dem Oracle-Verleger zugeordnet ist.|  
|HREPL_Event|Tabelle|Ereignistabelle, die zum Synchronisieren von Momentaufnahmen und Zeilenanzahlanforderungen verwendet wird.|  
|HREPL_Mutex|Tabelle|Tabelle, mit deren Hilfe sichergestellt wird, dass die Oracle-Paketprozedur PopulatePollTable nicht gleichzeitig vom Protokolllese-Agent und vom Datenbankauftrag ausgeführt wird.|  
|HREPL_Poll|Tabelle|Tabelle zur Identifizierung der Protokolltabelleneinträge, die mit Änderungen an veröffentlichten Tabellen verknüpft sind.|  
|HREPL_PublishedTables|Tabelle|Tabelle, die für jeden Artikel in einer Transaktionsveröffentlichung einen Eintrag enthält.|  
|HREPL_Publisher|Tabelle|Verlegerstatustabelle mit verlegerspezifischen Informationen.|  
|HREPL_SchemaFilter|Tabelle|Tabelle, die Schemas enthält, die bei der Veröffentlichung durch den Assistenten für neue Veröffentlichung nicht angezeigt werden.|  
|HREPL_XactsetCreateTimes|Tabelle|Tabelle zur Identifizierung der Erstellungszeit der einzelnen Transaktionssätze.|  
|HREPL_XactsetJob|Tabelle|Tabelle mit aktuellen Parametereinstellungen für den Xactset Job.|  
|HREPL_Pollid|Sequenz|Sequenz für das Generieren von Abruf-IDs.|  
|HREPL_Seq|Sequenz|Sequenz zum Ordnen von Änderungsbefehlen.|  
|HREPL_Stmt|Sequenz|Sequenz, die zum Generieren der Anweisungs-IDs verwendet wird.|  
|HREPL|Paket und Paketkörper|Paket mit dem Verlegersupportcode, das auf dem Verleger erstellt wird.|  
|MSSQLSERVERDISTRIBUTOR|Öffentliches Synonym|Öffentliches Synonym für die Tabelle HREPL_Distributor. Wenn Sie einen Verteiler für die Verwendung mit einem Oracle-Verleger konfigurieren und dieses Synonym bereits in der Datenbank vorhanden ist, wird es gelöscht und neu erstellt.<br /><br /> Beim Löschen des öffentlichen Synonyms und des konfigurierten Oracle-Replikationsbenutzers mit der Option CASCADE werden alle Replikationsobjekte vom Oracle-Verleger entfernt.|  
|HREPL_Len_I_J_K|Funktion|Funktion, die außerhalb des Oracle-Veröffentlichungspaketcodes definiert wird und zur Abfrage der Länge einer LONG-Spalte (beim Generieren parametrisierter Befehle für Tabellen mit veröffentlichten LONG-Spalten) verwendet wird. Eine solche Funktion wird für jede veröffentlichte Tabelle mit einer LONG-Spalte erstellt.|  
|HREPL_DropPublisher|Verfahren|Prozedur, die außerhalb des Oracle-Veröffentlichungspaketcodes definiert und zum Löschen des Oracle-Verlegers verwendet wird.|  
|HREPL_ExecuteCommand|Verfahren|Prozedur, die außerhalb des Oracle-Veröffentlichungspaketcodes definiert und zum Ausführen eines Befehls auf dem Verleger verwendet wird.|  
|HREPL_ArticleN_Trigger_Row|Trigger|Trigger, der für jede veröffentlichte Tabelle generiert und zum Nachverfolgen von Zeilenänderungen verwendet wird.|  
|HREPL_ArticleN_Trigger_Stmt|Trigger|Trigger, der für jede veröffentlichte Tabelle generiert und zum Nachverfolgen der Änderungen auf Anweisungsebene verwendet wird.|  
|HREPL_Article_I_J|Sicht|Sicht, die für jede veröffentlichte Tabelle erstellt und zum Abfragen der veröffentlichten Tabelle verwendet wird.|  
|HREPL_Log_I_J_K|Sicht|Sicht, die für jede veröffentlichte Tabelle erstellt und zum Abfragen der Änderungsnachverfolgungstabelle verwendet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md)   
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](glossary-of-terms-for-oracle-publishing.md)   
 [Veröffentlichungen mit Oracle (Übersicht)](oracle-publishing-overview.md)  
  
  
