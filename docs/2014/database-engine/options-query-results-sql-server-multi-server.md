---
title: Optionen (Abfrageergebnisse-SQL Server-Multiserver) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c8b7c8a3653fd54112d4f5639832e25727ce67b5
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000770"
---
# <a name="options-query-results-sql-server-multi-server"></a>Optionen (Abfrageergebnisse > SQL Server > Multiserver)
  Wenn Sie mehrere Server gleichzeitig abfragen, können Sie mit dieser Seite die Optionen für die Anzeige von Resultsets angeben. Die Option Ergebnisse zusammenführen kombiniert die Resultsets von allen Servern zu einem einzigen Resultset. Wenn Sie Ergebnisse zusammenführen, bestimmt der erste Server, der antwortet, das Schema für das Resultset. Um die Resultsets zusammenzuführen, muss die Abfrage dieselbe Anzahl von Spalten mit denselben Spaltennamen für jeden Server zurückgeben. Wenn Sie Ergebnisse zusammenführen, wird eine Meldung für jeden Server angezeigt, der dem durch den ersten antwortenden Server festgelegten Schema nicht entspricht (Spaltenanzahl und Spaltennamen).  
  
 Wenn Sie die Ergebnisse nicht zusammenführen, wird das Resultset von jedem Server in einem eigenen Raster mit einem eigenen Schema angezeigt.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Ergebnisse zusammenführen**  
 Aktivieren Sie dieses Kontrollkästchen, um die Resultsets von mehreren Servern im selben Raster zu kombinieren.  
  
 **Servername zu den Ergebnissen hinzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um eine zusätzliche Spalte einzuschließen, die den Namen des Servers bereitstellt, der jede Zeile erstellt hat.  
  
 **Anmeldename zu den Ergebnissen hinzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um eine zusätzliche Spalte einzuschließen, die den Benutzernamen enthält, der verwendet wurde, um die Verbindung zu dem Server herzustellen, der jede Zeile bereitgestellt hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines zentralen Verwaltungs Servers und einer Server Gruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Gleichzeitiges Ausführen von Anweisungen für mehrere Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
