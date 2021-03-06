---
title: Berechnete Spalten (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e1011278-556d-4984-b01d-a37f8a33b304
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9a93fffba5c34d26cdb0305b0f6a97369e51b3e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67284893"
---
# <a name="calculated-columns-ssas-tabular"></a>Berechnete Spalten (SSAS – tabellarisch)
  Mithilfe berechneter Spalten in tabellarischen Modellen können Sie dem Modell neue Daten hinzufügen. Anstatt Werte in die Spalte einfügen oder importieren zu müssen, erstellen Sie eine DAX-Formel, die die Zeilen Ebenen Werte der Spalte definiert. Die berechnete Spalte kann wie jede andere Spalte in einem Bericht, einer PivotTable oder einem PivotChart verwendet werden.  
  
> [!NOTE]  
>  Berechnete Spalten werden für tabellarische Modelle im DirectQuery-Modus nicht unterstützt. Weitere Informationen finden Sie unter [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](directquery-mode-ssas-tabular.md).  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_understanding)  
  
-   [Benennen einer berechneten Spalte](#bkmk_naming)  
  
-   [Leistung berechneter Spalten](#bkmk_perf)  
  
-   [Verwandte Aufgaben](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a>Davon  
 Formeln in berechneten Spalten sind mit Formeln in Excel vergleichbar. Anders als in Excel können Sie jedoch für verschiedene Zeilen einer Tabelle keine unterschiedlichen Formeln erstellen. Stattdessen wird die DAX-Formel automatisch auf die gesamte Spalte angewendet.  
  
 Enthält eine Spalte eine Formel, wird für jede Zeile der entsprechende Wert berechnet. Die Ergebnisse werden für die Spalte berechnet, wenn Sie eine gültige Formel eingeben. Spaltenwerte werden dann bei Bedarf neu berechnet, z. B. wenn die zugrunde liegenden Daten aktualisiert werden.  
  
 Sie können berechnete Spalten erstellen, die auf Measures und anderen berechneten Spalten basieren. Sie können z. B. eine berechnete Spalte erstellen, um eine Zahl aus einer Textzeichenfolge zu extrahieren und diese Zahl dann in einer anderen berechneten Spalte zu verwenden.  
  
 Eine berechnete Spalte basiert auf Daten, die bereits in einer vorhandenen Tabelle enthalten sind oder die mit einer DAX-Formel erstellt wurden. Sie können beispielsweise Werte verketten, Additionen ausführen, Teilzeichenfolgen extrahieren oder Werte in anderen Feldern vergleichen. Das Modell muss mindestens über eine Tabelle verfügen, um eine berechnete Spalte hinzufügen zu können.  
  
 In diesem Beispiel wird eine einfache Formel in einer berechneten Spalte veranschaulicht:  
  
```  
=EOMONTH([StartDate],0])  
  
```  
  
 Mit dieser Formel wird der Monat aus der Spalte "StartDate" extrahiert. Anschließend wird für jede Zeile in der Tabelle der Wert für das Monatsende berechnet. Der zweite Parameter gibt die Anzahl der Monate vor oder nach dem Monat in "StartDate" an. In diesem Fall entspricht 0 dem gleichen Monat. Wenn der Wert in der Spalte "StartDate" z. B. "01.06.2001" beträgt, beträgt der Wert in der berechneten Spalte "30.06.2001".  
  
##  <a name="naming-a-calculated-column"></a><a name="bkmk_naming"></a>Benennen einer berechneten Spalte  
 Neue berechnete Spalten werden standardmäßig rechts neben anderen Spalten in einer Tabelle hinzugefügt, und die Spalten werden standardmäßig und automatisch **CalculatedColumn1**, **CalculatedColumn2**usw. genannt. Sie können auch mit der rechten Maustaste auf eine Spalte und dann auf Spalte einfügen klicken, um zwischen zwei vorhandenen Spalten eine neue Spalte zu erstellen. Sie können Spalten innerhalb der gleichen Tabelle durch Klicken und Ziehen neu anordnen und Spalten umbenennen, nachdem sie erstellt wurden. Folgende Einschränkungen beim Ändern von berechneten Spalten sollten jedoch beachtet werden:  
  
-   Jeder Spaltenname muss innerhalb einer Tabelle eindeutig sein.  
  
-   Vermeiden Sie Namen, die bereits für Measures innerhalb desselben Modells verwendet wurden. Obwohl es möglich ist, dass ein Measure und eine berechnete Spalte den gleichen Namen haben, kann es bei nicht eindeutigen Namen zu Berechnungsfehlern kommen. Um bei Bezugnahme auf eine Spalte den versehentlichen Aufruf eines Measures zu vermeiden, verwenden Sie immer einen vollqualifizierten Spaltenverweis.  
  
-   Wenn Sie eine berechnete Spalte umbenennen, müssen alle Formeln, die von der Spalte abhängig sind, manuell aktualisiert werden. Außer wenn Sie sich im manuellen Updatemodus befinden, werden die Formelergebnisse automatisch aktualisiert. Dieser Vorgang nimmt möglicherweise etwas Zeit in Anspruch.  
  
-   Einige Zeichen können innerhalb von Spaltennamen nicht verwendet werden. Weitere Informationen finden Sie unter „Benennungsanforderungen“ in der [DAX-Syntaxspezifikation für PowerPivot](/dax/dax-syntax-reference).  
  
##  <a name="performance-of-calculated-columns"></a><a name="bkmk_perf"></a>Leistung berechneter Spalten  
 Die Formel für eine berechnete Spalte kann ressourcenintensiver als die für ein Measure verwendete Formel sein. Ein Grund hierfür ist, dass das Ergebnis für eine berechnete Spalte immer für jede Zeile in einer Tabelle berechnet wird, wohingegen ein Measure nur für die vom Filter definierten Zellen berechnet wird, die in einem Bericht, in der PivotTable oder im PivotChart verwendet werden. Zum Beispiel enthält eine Tabelle mit einer Million Zeilen immer eine berechnete Spalte mit einer Million Ergebnissen, was sich entsprechend auf die Leistung auswirkt. Eine PivotTable filtert Daten jedoch im Allgemeinen, indem eine Zeilen- und Spaltenüberschrift angewendet wird. Daher wird ein Measure nur für die Teilmenge der Daten in jeder Zelle der PivotTable berechnet.  
  
 Eine Formel weist Abhängigkeiten für die Objekte auf, auf die in der Formel verwiesen wird, z. B. andere Spalten oder Ausdrücke, die Werte auswerten. Eine berechnete Spalte, die auf einer anderen Spalte basiert, oder eine Berechnung, die einen Ausdruck mit einem Spaltenverweis enthält, kann beispielsweise erst ausgewertet werden, wenn die andere Spalte ausgewertet wurde. Standardmäßig ist die automatische Aktualisierung in Arbeitsmappen aktiviert, daher können diese Abhängigkeiten die Leistung beeinträchtigen, während Werte und Formeln aktualisiert werden.  
  
 Beachten Sie beim Erstellen von berechneten Spalten die folgenden Richtlinien, um Leistungsprobleme zu vermeiden:  
  
-   Anstatt eine einzelne Formel zu erstellen, die viele komplexe Abhängigkeiten enthält, sollten Sie die Formeln in Schritten erstellen und die jeweiligen Ergebnisse in Spalten speichern, damit Sie die Ergebnisse überprüfen und die Leistung bewerten können.  
  
-   Das Ändern der Daten erfordert oft, dass berechnete Spalten neu berechnet werden. Sie können dies verhindern, indem Sie den Neuberechnungsmodus auf manuell festlegen. Enthält die berechnete Spalte jedoch falsche Werte, wird die Spalte ausgegraut, bis Sie eine Aktualisierung vornehmen und die Daten neu berechnen.  
  
-   Wenn Sie Beziehungen zwischen Tabellen ändern oder löschen, werden die Formeln, die Spalten in diesen Tabellen verwenden, möglicherweise ungültig.  
  
-   Wenn Sie eine Formel erstellen, die eine Ring- oder auf sich selbst verweisende Abhängigkeit enthält, tritt ein Fehler auf.  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> Verwandte Aufgaben  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen einer berechneten Spalte &#40;SSAS – tabellarisch&#41;](ssas-calculated-columns-create-a-calculated-column.md)|In den Tasks in diesem Thema wird beschrieben, wie einer Tabelle eine neue berechnete Spalte hinzugefügt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Spalten &#40;tabellarischen SSAS-&#41;](tables-and-columns-ssas-tabular.md)   
 [Measures &#40;tabellarischen SSAS-&#41;](measures-ssas-tabular.md)   
 [Berechnungen &#40;SSAS – tabellarisch&#41;](calculations-ssas-tabular.md)  
  
  
