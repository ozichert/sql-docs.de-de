---
title: Designer in Visual Database Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 773ceb4aedddd6a39df6487bd36b47b83f7fa9a9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63227040"
---
# <a name="visual-database-tool-designers"></a>Designer in Visual Database Tools
  Visual Database Tools kombiniert eine Reihe von Entwurfstools, die zur Bearbeitung von Datenquellen verwendet werden können. Sie können damit Abfragen erstellen, die Datenbankstruktur entwerfen oder ändern und Daten aktualisieren. Die Tools heißen Datenbankdiagramm-Designer, Tabellen-Designer und Abfrage- und Sicht-Designer.  
  
## <a name="properties-window"></a>Eigenschaftenfenster  
 Das Eigenschaftenfenster ist keine Eigenheit von Visual Database Tools; an dieser Stelle können Sie jedoch verschiedene Änderungen vornehmen. Hier werden die Eigenschaften des aktuell ausgewählten Elements (z. B. eine Tabelle) angezeigt. Diese Eigenschaften (vom Namen der Eigenschaften bis zur Sortierung einer Spalte) können geändert werden. Einige Eigenschaften werden im Eigenschaftenfenster angezeigt, müssen jedoch mit einem anderen Tool geändert werden.  
  
## <a name="database-diagram-designer"></a>Datenbankdiagramm-Designer  
 Im Datenbankdiagramm-Designer können Sie über ein Fenster Tabellen und Beziehungen einer Datenbank erstellen, bearbeiten und anzeigen.  
  
 Wenn Sie den Datenbankdiagramm-Designer anzeigen möchten, öffnen Sie ein vorhandenes Diagramm, oder klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Datenbankknoten, und wählen Sie **Neues Datenbankdiagramm** aus dem Dropdownmenü aus.  
  
 Sobald der Designer geöffnet ist, wird das Menü **Datenbankdiagramm** im Hauptmenü angezeigt. Dieses Menü bildet den Zugriffspunkt zu den speziellen Funktionen des Designers.  
  
> [!NOTE]  
>  Dieser Designer ist mit Microsoft SQL Server-Datenbanken verwendbar.  
>   
>  Diese Version von Visual Database Tools unterstützt Microsoft SQL Server Version 7 und ältere Versionen nicht.  
  
## <a name="table-designer"></a>Tabellen-Designer  
 Der Tabellen-Designer ist ein visuelles Tool, mit dem Sie eine einzelne Tabelle einer Microsoft SQL Server-Datenbank, mit der Sie eine Verbindung hergestellt haben, entwerfen und anzeigen können.  
  
 Der Tabellen-Designer umfasst zwei Bereiche. Im oberen Bereich wird ein Datenblatt angezeigt, wobei jede Zeile des Datenblatts eine Spalte in der Datenbank wiedergibt. Das Datenblatt zeigt die wichtigsten Attribute der einzelnen Datenbankspalten an: Spaltenname, Datentyp und Einstellung für die Zulassung von NULL-Werten.  
  
 Im unteren Bereich des Tabellen-Designers werden auf der Registerkarte Spalteneigenschaften weitere Attribute derjenigen Spalte angezeigt, die im oberen Bereich ausgewählt ist.  
  
 Im Tabellen-Designer können Sie zudem mit der rechten Maustaste auf den Datenblattabschnitt klicken, um auf Dialogfelder zuzugreifen, über die Sie Beziehungen, Einschränkungen, Indizes und Schlüssel für die Tabelle erstellen oder ändern können.  
  
 Öffnen Sie eine vorhandene Tabelle, oder klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Knoten **Tabelle** , und wählen Sie im Dropdownmenü **Neue Tabelle hinzufügen** aus, um den Tabellen-Designer anzuzeigen.  
  
 Sobald der Designer geöffnet ist, wird das Menü Tabellen-Designer im Hauptmenü angezeigt. Dieses Menü bildet den Zugriffspunkt zu den speziellen Funktionen des Designers.  
  
> [!NOTE]  
>  Dieser Designer ist mit Microsoft SQL Server-Datenbanken verwendbar.  
>   
>  Diese Version von Visual Database Tools unterstützt Microsoft SQL Server Version 7 und ältere Versionen nicht.  
  
## <a name="query-and-view-designer"></a>Abfrage- und Sicht-Designer  
 Beim Abfrage- und Sicht-Designer handelt es sich eigentlich um zwei Tools, die auf sehr ähnliche Weise funktionieren. Einige der Hauptunterschiede sind:  
  
-   Sichten werden zusammen mit der Datenbank gespeichert, während Abfragen in einem Visual Studio-Datenbankprojekt gespeichert werden.  
  
-   Der Abfrage-Designer kann mit fast jeder beliebigen Datenquelle verwendet werden, während der Sicht-Designer nur SQL Server unterstützt.  
  
-   Mit dem Abfrage-Designer können Sie SELECT-, INSERT-, UPDATE- und DELETE DML-Anweisungen entwerfen; dagegen können Sichten nur SELECT-Anweisungen enthalten.  
  
### <a name="view-designer"></a>Sicht-Designer  
 Mit dem Sicht-Designer können Sie eine vorhandene Sicht entwerfen und darstellen oder in einer Microsoft SQL Server-Datenbank, mit der eine Verbindung besteht, eine neue Sicht erstellen.  
  
 Der Sicht-Designer umfasst vier Bereiche: den Diagrammbereich, den Kriterienbereich, den SQL-Bereich und den Ergebnisbereich. Ausführlichere Informationen zu den einzelnen Bereichen finden Sie unter [Tools im Abfrage- und Sicht-Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Öffnen Sie eine vorhandene Sicht, oder klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Knoten **Sicht**, und wählen Sie im Dropdownmenü **Neue Sicht hinzufügen** aus, um den Sicht-Designer anzuzeigen.  
  
 Sobald der Designer geöffnet ist, wird das Menü **Abfrage-Designer** im Hauptmenü angezeigt. Dieses Menü bildet den Zugriffspunkt zu den speziellen Funktionen des Designers.  
  
> [!NOTE]  
>  Dieser Designer ist mit Microsoft SQL Server-Datenbanken verwendbar.  
>   
>  Diese Version von Visual Database Tools unterstützt Microsoft SQL Server Version 7 und ältere Versionen nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwerfen von Daten Bank Diagrammen &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md)   
 [Entwerfen von Tabellen &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
