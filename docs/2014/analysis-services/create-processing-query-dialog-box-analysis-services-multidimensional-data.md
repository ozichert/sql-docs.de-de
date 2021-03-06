---
title: Verarbeitungs Abfrage erstellen (Dialog Feld) (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.createprocessingquerydialog.f1
ms.assetid: c133d624-f35e-486e-be9f-ceafd906f168
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 225f5d757ee6b1d1da5c57b457d599fe4bb42d6c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086767"
---
# <a name="create-processing-query-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Verarbeitungsabfrage erstellen' (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie das Dialogfeld **Verarbeitungsabfrage erstellen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um im Dialogfeld **Speicheroptionen** auf der Registerkarte **Benachrichtigungen** eine Verarbeitungsabfrage zu erstellen. Eine Verarbeitungsabfrage ist eine Abfrage, durch die ein Rowset mit den Änderungen zurückgegeben wird, die an einer mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verknüpften Tabelle seit der letzten für die Tabelle ausgeführten Abfrage vorgenommen wurden. Mithilfe der Verarbeitungsabfrage wird der mehrdimensionale OLAP-Zwischenspeicher (MOLAP) für das Objekt inkrementell aktualisiert. Durch Analysis Services wird eine andere, als Abrufabfrage bezeichnete Abfrage verwendet, mit der eine mit einem Objekt verknüpfte Tabelle abgefragt wird, um festzustellen, ob die Tabelle sich geändert hat. Wenn der MOLAP-Zwischenspeicher für das Objekt vollständig aktualisiert wird, erübrigen sich Verarbeitungsabfragen.  
  
 Normalerweise ist die Verarbeitungsabfrage parametrisiert, und aktuell werden zwei Parameter unterstützt:  
  
-   Der durch die Abrufabfrage während des vorherigen geplanten Abrufvorgangs zurückgegebene einzelne Wert.  
  
-   Der durch die Abrufabfrage während des aktuellen geplanten Abrufvorgangs zurückgegebene einzelne Wert.  
  
 Die in der folgenden Tabelle aufgeführten Abfragen können beispielsweise zum inkrementellen Aktualisieren der Customer-Dimension im Adventure Works DW-Beispielprojekt von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet werden.  
  
|Abfragetyp|Abfrageanweisung|  
|----------------|---------------------|  
|Abrufabfrage|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|Verarbeitungsabfrage|`SELECT`<br /><br /> `*`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`<br /><br /> `WHERE`<br /><br /> `(CustomerKey > COALESCE (@Param1, - 1))`<br /><br /> `AND (CustomerKey <= @Param2)`|  
  
 Weitere Informationen zu inkrementellen Updates für geplante Abrufbenachrichtigungen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
 Um das Dialogfeld **Verarbeitungsabfrage erstellen** anzuzeigen, klicken Sie in der Spalte **Verarbeitungsabfrage** des Rasters für die Option **Geplantes Abrufen** auf der Registerkarte **Benachrichtigungen** des Dialogfelds **Speicheroptionen** auf **...**. Weitere Informationen zur Registerkarte **Benachrichtigungen** des Dialogfelds **Speicheroptionen** finden Sie unter [Benachrichtigungen &#40;Dialogfeld „Speicheroptionen“&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).  
  
 Bei der eingegebenen Abfrage muss es sich um einen gültigen Abfragebefehl für den zugrunde liegenden Anbieter handeln. Die Abfrage wird mit dem zugrunde liegenden Anbieter zur Überprüfung vorbereitet und dient der Identifizierung der zurückgegebenen Spalten. Das Dialogfeld kann in zwei Sichten dargestellt werden:  
  
-   Visual Database Tools (VDT)-Abfrage-Generator  
  
     In der Sicht VDT-Abfrage-Generator steht allen Benutzern eine Gruppe von Benutzeroberflächentools zur visuellen Erstellung und für den Test von SQL-Abfragen zur Verfügung.  
  
-   Standardabfrage-Generator  
  
     Erfahreneren Benutzern steht mit dem Standardabfrage-Generator für die Erstellung und den Test von SQL-Abfragen eine einfachere Benutzeroberfläche mit direkterem Zugriff zur Verfügung.  
  
## <a name="options"></a>Optionen  
 **Data Source**  
 Gibt die Datenquelle für die Abfrage an.  
  
 **Abfragedefinition**  
 Durch die Abfragedefinition werden eine Symbolleiste und Bereiche bereitgestellt, die der ausgewählten Sicht entsprechend zum Definieren der Abfrage verwendet werden.  
  
 **Suchfeld**  
 Mithilfe der Symbolleiste können Sie Datasets verwalten, Bereiche zur Anzeige auswählen und unterschiedliche Abfragefunktionen steuern.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Zum Standardabfrage-Generator wechseln**|Wählen Sie diese Option aus, um nur die Optionen anzuzeigen, die in der Sicht des Standardabfrage-Generators verfügbar sind. Es werden nur die folgenden Optionen angezeigt:<br /><br /> **SQL-Bereich**<br /><br /> **Ergebnisbereich**<br /><br /> **Symbolleiste**, nur mit den Schaltflächen **Zum VDT-Abfrage-Generator wechseln** und **Ausführen**<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Zum VDT-Abfrage-Generator wechseln**|Wählen Sie diese Option aus, um alle Optionen anzuzeigen, die in der Sicht VDT-Abfrage-Generator (Visual Database Tools) verfügbar sind.<br /><br /> Hinweis: Die Option ist nur verfügbar, wenn **Zum Standardabfrage-Generator wechseln** ausgewählt ist.|  
|**Diagrammbereich ein-/ausblenden**|Blendet den **Diagramm**Bereich ein oder aus.<br /><br /> **Hinweis** Diese Option wird nur angezeigt **, wenn zu VDT wechseln Abfrage-Generator** ausgewählt ist.|  
|**Rasterbereich ein-/ausblenden**|Blendet den **Raster**Bereich ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**SQL-Bereich ein-/ausblenden**|Blendet den **SQL-Bereich**ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Ergebnisbereich ein-/ausblenden**|Blendet den **Ergebnisbereich**ein oder aus.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Ausführen**|Führt die Abfrage aus. Ergebnisse werden im **Ergebnisbereich**angezeigt.|  
|**SQL überprüfen**|Überprüft die SQL-Anweisung in der Abfrage.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Aufsteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in aufsteigender Reihenfolge.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Absteigend sortieren**|Sortiert die Ausgabezeilen der ausgewählten Spalte im **Rasterbereich**in absteigender Reihenfolge.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Filter entfernen**|Entfernt die Sortierkriterien ggf. für die ausgewählte Zeile im **Rasterbereich**.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**GROUP BY verwenden**|Fügt der Abfrage die Gruppierungsfunktionalität hinzu.<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
|**Tabelle hinzufügen**|Zeigt das Dialogfeld **Tabelle hinzufügen** an, in dem der Abfrage eine neue Tabelle oder Sicht hinzugefügt werden kann. Weitere Informationen zum Dialogfeld **Tabelle hinzufügen** finden Sie unter [Tabelle hinzufügen &#40;Dialogfeld, Analysis Services – Mehrdimensionale Daten&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Hinweis: Diese Option wird nur angezeigt, wenn **Zum VDT-Abfrage-Generator wechseln** ausgewählt ist.|  
  
 **Diagrammbereich**  
 Zeigt die Objekte an, auf die durch die Abfrage als Diagramm verwiesen wird. Das Diagramm zeigt die in der Abfrage enthaltenen Tabellen sowie die Art, wie diese miteinander verknüpft sind. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben einer Spalte in einer Tabelle, um die entsprechende Spalte der Abfrageausgabe hinzuzufügen bzw. sie daraus zu entfernen.  
  
 Wenn Sie der Abfrage Tabellen hinzufügen, werden im Dialogfeld auf der Grundlage der Schlüssel in der Tabelle Joins zwischen Tabellen erstellt. Um einen Join hinzuzufügen, ziehen Sie ein Feld aus einer Tabelle auf ein Feld in einer anderen Tabelle. Sie können den Join verwalten, indem Sie mit der rechten Maustaste auf den Join klicken.  
  
 Klicken Sie mit der rechten Maustaste auf den Bereich **Diagramm** , um Tabellen hinzuzufügen oder zu entfernen, alle Tabellen auszuwählen oder Bereiche ein- oder auszublenden.  
  
> [!NOTE]  
>   Die Inhalte von **Diagrammbereich**, **Rasterbereich**und **SQL-Bereich** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
> [!IMPORTANT]  
>  Das Ändern von Abfragetypen wird in dem Dialogfeld nicht unterstützt.  
  
 **Rasterbereich**  
 Zeigt die Objekte an, auf die durch die Abfrage in einem Raster verwiesen wird. In diesem Bereich können Sie der Abfrage Spalten hinzufügen oder Spalten aus der Abfrage entfernen sowie die Einstellungen für die einzelnen Spalten ändern.  
  
> [!NOTE]  
>   Die Inhalte von **Diagrammbereich**, **Rasterbereich**und **SQL-Bereich** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
 **SQL-Bereich**  
 Zeigt die Abfrage als SQL-Anweisung an. Geben Sie die entsprechenden Werte ein, um die SQL-Anweisung für die Abfrage zu ändern.  
  
> [!NOTE]  
>   Die Inhalte von **Diagrammbereich**, **Rasterbereich**und **SQL-Bereich** werden synchronisiert, sodass sich Änderungen in einem Bereich sofort auch auf die anderen beiden Bereiche auswirken.  
  
 **Ergebnisbereich**  
 Zeigt die Ergebnisse der Abfrage an, wenn Sie im Bereich **Symbolleiste** auf **Ausführen** klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
