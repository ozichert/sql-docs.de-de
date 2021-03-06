---
title: Ziel-Editor für Excel (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c55b9daba7e8e1823e1ced43fc9958d4fe5892ff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66059241"
---
# <a name="excel-destination-editor-connection-manager-page"></a>Ziel-Editor für Excel (Seite Verbindungs-Manager)
  Mithilfe der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für Excel** können Sie Informationen zur Datenquelle angeben und eine Vorschau der Ergebnisse anzeigen. Das Excel-Ziel lädt Daten in ein Arbeitsblatt oder einen benannten Bereich einer [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] -Arbeitsmappe.  
  
> [!NOTE]  
>  Die `CommandTimeout` -Eigenschaft des Excel-Ziels ist nicht im **Ziel-Editor für Excel**verfügbar, kann jedoch mit dem- **Erweiterter Editor**festgelegt werden. Darüber hinaus sind bestimmte Optionen für schnelles Laden nur im Dialogfeld **Erweiterter Editor**verfügbar. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt Excel-Ziel von [Excel Custom Properties](data-flow/excel-custom-properties.md).  
  
 Weitere Informationen zum Excel-Ziel finden Sie unter [Excel Destination](data-flow/excel-destination.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Excel-Verbindungs-Manager**  
 Wählen Sie einen vorhandenen Excel-Verbindungs-Manager aus der Liste aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Excel-Verbindungs-Manager** eine neue Verbindung.  
  
 **Datenzugriffs Modus**  
 Geben Sie die Methode für die Auswahl von Daten aus der Quelle an.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|Tabelle oder Sicht|Lädt Daten aus einem Arbeitsblatt oder dem benannten Bereich einer Excel-Datenquelle.|  
|Variable für Tabellenname oder Sichtname|Geben Sie den Namen des Arbeitsblatts oder Bereichs in einer Variablen an.<br /><br /> **Verwandte Informationen:**[Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)|  
|SQL-Befehl|Lädt Daten mithilfe einer SQL-Abfrage in das Excel-Ziel.|  
  
 **Name der Excel-Tabelle**  
 Wählen Sie in der Dropdownliste das Excel-Ziel aus. Wenn die Liste leer ist, klicken Sie auf **Neu**.  
  
 **Neu**  
 Klicken Sie auf **Neu** , um das Dialogfeld **Tabelle erstellen** zu öffnen. Wenn Sie auf **OK**klicken, erstellt das Dialogfeld die Excel-Datei, auf die der **Excel-Verbindungs-Manager** zeigt.  
  
 **Vorhandene Daten anzeigen**  
 Zeigen Sie mithilfe des Dialogfelds **Vorschau der Abfrageergebnisse anzeigen** eine Vorschau der Ergebnisse an. In der Vorschau können bis zu 200 Zeilen angezeigt werden.  
  
> [!WARNING]  
>   Wenn der ausgewählte **Excel-Verbindungs-Manager** auf eine Excel-Datei zeigt, die nicht vorhanden ist, wird eine Fehlermeldung angezeigt, wenn Sie auf diese Schaltfläche klicken.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
  
### <a name="data-access-mode--table-or-view"></a>Datenzugriffsmodus = Tabelle oder Sicht  
 **Name der Excel-Tabelle**  
 Wählen Sie in der Liste der in der Datenquelle verfügbaren Objekte den Namen des Arbeitsblatts oder des benannten Bereichs aus.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Datenzugriffsmodus = Variable für Tabellenname oder Sichtname  
 **Variablenname**  
 Wählen Sie die Variable aus, die den Namen des Arbeitsblatts oder des benannten Bereichs enthält.  
  
### <a name="data-access-mode--sql-command"></a>Datenzugriffsmodus = SQL-Befehl  
 **SQL-Befehlstext**  
 Geben Sie den Text einer SQL-Abfrage ein, und erstellen Sie die Abfrage, indem Sie auf **Abfrage erstellen**klicken. Wahlweise können Sie auch nach der Datei suchen, die den Abfragetext enthält, indem Sie auf **Durchsuchen**klicken.  
  
 **Abfrage erstellen**  
 Mithilfe des Dialogfelds **Abfrage-Generator** können Sie die SQL-Abfrage visuell erstellen.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie nach der Datei suchen, die den Text der SQL-Abfrage enthält.  
  
 **Abfrage analysieren**  
 Überprüft die Syntax des Abfragetexts.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ziel-Editor für Excel &#40;Seite "Zuordnungen"&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md)   
 [Der Ziel-Editor für Excel &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md)   
 [Schleife durch Excel-Dateien und Tabellen mit einem Foreach-Schleifencontainer](control-flow/foreach-loop-container.md)  
  
  
