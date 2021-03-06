---
title: Measures (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27ec8f99-e9ef-44c9-a83f-f7c88e128ad3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1ca545e081826f1b81117e377f370136a7b4998
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067009"
---
# <a name="measures-ssas-tabular"></a>Measures (SSAS – tabellarisch)
  In tabellarischen Modellen ist ein Measure eine Berechnung, die mit einer DAX-Formel für die Verwendung in einem Berichtserstellungsclient erstellt wird. Measures werden auf Grundlage von Feldern, Filtern oder eines Slicers ausgewertet, die der Benutzer in der Clientanwendung zur Berichtserstellung auswählt.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_understanding)  
  
-   [Definieren von Measures mit dem Measureraster](#bkmk_def_mg)  
  
-   [Eigenschaften von Measures](#bkmk_properties)  
  
-   [Verwenden eines Measures in einem KPI](#bkmk_KPI)  
  
-   [Verwandte Aufgaben](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a>Davon  
 Measures können auf Standardaggregationsfunktionen basieren, z. B. AVERAGE, COUNT oder SUM, oder Sie können mit DAX eigene Formeln definieren. Zusätzlich zur Formel verfügt jedes Measure über Eigenschaften, die vom Measuredatentyp definiert werden, z. B. Name, Tabellendetails, Format und Dezimalstellen.  
  
 Nachdem Measures in einem Modell definiert wurden, kann der Benutzer sie einem Bericht oder einer PivotTable hinzufügen. Abhängig von den Perspektiven und Rollen werden Measures mit ihrer zugeordneten Tabelle in der Feldliste angezeigt. Dort stehen sie allen Benutzern des Modells zur Verfügung. Measures werden üblicherweise in Faktentabellen erstellt; sie können jedoch auch unabhängig von der Tabelle sein, der sie zugeordnet sind.  
  
 Es ist wichtig, die wesentlichen Unterschiede zwischen einer berechneten Spalte und einem Measure zu verstehen. In einer berechneten Spalte ergibt eine Formel einen Wert für jede Zeile in der Spalte. In einer FactSales-Tabelle berechnet eine berechnete Spalte mit dem Namen TotalProfit anhand der folgenden Formel z. B. den Gesamtgewinn (eine Zeile pro Verkauf) für jede Zeile in der FactSales-Tabelle:  
  
```  
=[SalesAmount] - [TotalCost] - [ReturnAmount]  
```  
  
 Die berechnete TotalProfit-Spalte kann anschließend wie jede andere Spalte in einem Berichterstellungsclient verwendet werden.  
  
 Auf der anderen Seite ergibt ein Measure einen Wert auf der Grundlage einer Benutzerauswahl; ein in einer PivotTable oder einem Bericht festgelegter Filterkontext. Ein Measure in der FactSales-Tabelle wird z. B. anhand der folgenden Formel erstellt:  
  
```  
Sum of TotalProfit: =SUM([TotalProfit])  
```  
  
 Ein Sales Analyst, der mit Excel arbeitet, möchte den Gesamtgewinn für eine Produktkategorie ermitteln. Jede Produktkategorie umfasst mehrere Produkte. Der Sales Analyst wählt die ProductCategoryName-Spalte aus und fügt sie dem Filterfenster Zeilenbezeichnungen einer PivotTable hinzu. Daraufhin wird in der PivotTable für jede Produktkategorie eine Zeile angezeigt. Anschließend wählt der Benutzer das Measure Summe TotalProfit aus. Ein Measure wird standardmäßig dem Filterfenster Werte hinzugefügt. Durch das Measure wird der Gesamtgewinn berechnet, und die Ergebnisse pro Produktkategorie werden angezeigt. Anschließend kann der Sales Analyst den summierten Gesamtgewinn für jede Produktkategorie mithilfe eines Slicers weiter filtern. Beispielsweise kann er CalendarYear als Slicer hinzufügen, um den Gesamtgewinn pro Produktkategorie nach Jahr aufzuschlüsseln.  
  
|ProductCategoryName|Summe TotalProfit|  
|-------------------------|------------------------|  
|Audio|$2,731,061,308.69|  
|Cameras and Camcorders|$620,623,675.75|  
|Computers|$392,999,044.59|  
|Tv and Video|$946,989,702.51|  
|**Grand Total**|**$4,691,673,731.53**|  
  
##  <a name="defining-measures-by-using-the-measure-grid"></a><a name="bkmk_def_mg"></a>Definieren von Measures mit dem measureraster  
 Measures werden zur Entwurfszeit mithilfe des Measurerasters im Modell-Designer erstellt. Jede Tabelle verfügt über ein Measureraster. Standardmäßig wird das Measureraster unter jeder Tabelle im Modell-Designer angezeigt. Sie können auch festlegen, das Measureraster für eine bestimmte Tabelle nicht anzuzeigen. Zum Umschalten der Anzeige des measurerasters einer Tabelle klicken Sie auf das Menü **Tabelle** und dann auf measureraster **anzeigen**.  
  
 Im Measureraster können Sie wie folgt Measures erstellen:  
  
-   Klicken Sie auf eine leere Zelle im Measureraster, und geben Sie dann in der Bearbeitungsleiste eine DAX-Formel ein. Wenn Sie die Formelerstellung mit EINGABE abschließen, wird das Measure in der Zelle des Measurerasters angezeigt.  
  
-   Erstellen Sie ein Measure mithilfe einer Standardaggregationsfunktion, indem Sie auf eine Spalte, auf der Symbolleiste auf die Schaltfläche AutoSumme (∑) und dann auf eine Standardaggregationsfunktion klicken. Standardaggregationen: Summe, Mittelwert, Anzahl, DistinctCount, Max, Min. Measures, die mithilfe der Schaltfläche AutoSumme erstellt wurden, werden im Measureraster immer direkt unterhalb der Spalte angezeigt.  
  
 Bei Verwendung von AutoSumme wird der Name des Measures standardmäßig durch den Namen der zugeordneten Spalte definiert, auf den ein Doppelpunkt und dann die Formel folgt. Der Name kann auf der Bearbeitungsleiste oder in der Einstellung der Eigenschaft **Measurename** im Eigenschaftenfenster geändert werden. Wenn Sie ein Measure mithilfe einer benutzerdefinierten Formel erstellen, können Sie einen Namen in der Bearbeitungsleiste eingeben, auf den ein Doppelpunkt und dann die Formel folgt. Alternativ können Sie einen Namen in der Einstellung der Eigenschaft **Measurename** im Eigenschaftenfenster eingeben.  
  
 Die Namen von Measures müssen mit Bedacht ausgewählt werden. Der Measurename wird mit der zugeordneten Tabelle in der Feldliste des Berichterstellungsclients angezeigt. Ein KPI wird ebenfalls nach dem Basismeasure benannt. Ein Measure darf nicht den gleichen Namen wie eine Spalte in einer beliebigen Tabelle des Modells haben.  
  
> [!TIP]  
>  Sie können Measures aus mehreren Tabellen in einer Tabelle gruppieren, indem Sie eine leere Tabelle erstellen, in die Sie entweder Measures verschieben oder in der Sie neue Measures erstellen. Wenn Sie auf Spalten in anderen Tabellen verweisen, sollten Sie bedenken, dass Sie die Tabellennamen möglicherweise in DAX-Formeln aufnehmen müssen.  
  
 Wenn für das Modell Perspektiven definiert wurden, werden in diese Perspektiven nicht automatisch Measures eingefügt. Sie müssen einer Perspektive Measures manuell mithilfe des Dialogfelds Perspektiven hinzufügen. Weitere Informationen finden Sie unter [Perspektiven &#40;SSAS – tabellarisch&#41;](perspectives-ssas-tabular.md).  
  
##  <a name="measure-properties"></a><a name="bkmk_properties"></a>Measure-Eigenschaften  
 Jedes Measure verfügt über Eigenschaften, durch die es definiert wird. Measureeigenschaften können zusammen mit den Eigenschaften der zugeordneten Spalte im Eigenschaftenfenster bearbeitet werden. Measures verfügen über die folgenden Eigenschaften:  
  
|Eigenschaft|Standardeinstellung|Beschreibung|  
|--------------|---------------------|-----------------|  
|**Beschreibung**|Leer|Die Beschreibung der Maßeinheit. Die Beschreibung wird nicht mit dem Measure in einem Berichterstellungsclient angezeigt.|  
|**Ges**|Wird automatisch durch den Datentyp der Spalte bestimmt, auf die im Formelausdruck verwiesen wird.|Das Format des Measures. Beispielsweise Währung oder Prozentsatz.|  
|**Formel**|Die Formel, die bei der Erstellung des Measures in die Bearbeitungsleiste eingefügt wurde.|Die Formel des Measures.|  
|**Measurename**|Bei Verwendung von AutoSumme ist der Measurename gefolgt von einem Doppelpunkt dem Spaltennamen vorangestellt. Wenn eine benutzerdefinierte Formel eingegeben wird, geben Sie einen Namen gefolgt von einem Doppelpunkt und dann die Formel ein.|Der Name des Measures, so wie er in der Feldliste des Berichterstellungsclients angezeigt wird.|  
  
##  <a name="using-a-measure-in-a-kpi"></a><a name="bkmk_KPI"></a>Verwenden eines Measures in einem KPI  
 Ein KPI (Key Performance Indicator) wird durch einen *Basiswert* definiert, der wiederum durch ein Measure festgelegt wird, und mit einem *Zielwert* verglichen, der ebenfalls durch ein Measure oder durch einen absoluten Wert definiert wird. Ein KPI umfasst außerdem den *Status*. Damit wird berechnet, wo der Basiswert zwischen den Schwellenwerten für den Zielwert ausgewertet wird. Das Ergebnis wird in einem grafischen Format angezeigt. KPIs werden oft von Geschäftsleuten verwendet, um Trends in wichtigen Geschäftsmetriken aufzudecken.  
  
 Jedes Measure kann als Basismeasure eines KPIs verwendet werden. Klicken Sie mit der rechten Maustaste auf ein Measure und anschließend auf **KPI erstellen**, um einen KPI im Measureraster zu erstellen. Das Dialogfeld Key Performance Indicator wird dort angezeigt, wo Sie anschließend einen Zielwert (definiert durch ein Measure oder einen absoluten Wert) angeben und Statusschwellenwerte und einen Grafiktyp definieren können. Weitere Informationen finden Sie unter [KPIs &#40;SSAS – tabellarisch&#41;](kpis-ssas-tabular.md), um die Anzeige des Measurerasters für eine Tabelle einzuschalten.  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> Verwandte Aufgaben  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen und Verwalten von Measures &#40;SSAS – tabellarisch&#41;](measures-ssas-tabular.md)|Beschreibt, wie Measures mithilfe des Measurerasters im Modell-Designer erstellt und verwaltet werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [KPIs &#40;tabellarischen SSAS-&#41;](kpis-ssas-tabular.md)   
 [Erstellen und Verwalten von KPIs &#40;tabellarischen SSAS-&#41;](create-and-manage-kpis-ssas-tabular.md)   
 [Berechnete Spalten &#40;SSAS – tabellarisch&#41;](ssas-calculated-columns.md)  
  
  
