---
title: Reduzieren von Zeilengruppen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- group collapsing [SQL Server]
- collapsing rows
- row collapsing [SQL Server]
ms.assetid: 7338dad0-965d-44ba-8c1a-b993acb7156d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7f6cbc6b4150f2f951befcb70c1b09108de3b51
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62670483"
---
# <a name="collapse-groups-of-rows-visual-database-tools"></a>Reduzieren von Zeilengruppen (Visual Database Tools)
  Sie können ein Abfrageergebnis erstellen, in dem jede Ergebniszeile einer kompletten Zeilengruppe aus den ursprünglichen Daten entspricht. Beim Reduzieren von Zeilengruppen sind folgende Punkte zu beachten:  
  
-   **Sie können doppelte Zeilen entfernen.** Einige Abfragen erstellen Resultsets mit mehreren identischen Zeilen. Sie können z.B. ein Resultset erstellen, in dem jede Zeile den Namen der Stadt und des Lands bzw. der Region für eine Stadt angibt, in der Autoren ansässig sind. Wenn jedoch mehrere Autoren in einer Stadt ansässig sind, werden mehrere identische Zeilen ausgegeben. Hierfür kann folgende SQL-Anweisung formuliert werden:  
  
    ```  
    SELECT city, state  
    FROM authors  
    ```  
  
     Das von der oben stehenden Abfrage generierte Resultset ist nicht sehr sinnvoll. Wenn in einer Stadt vier Autoren ansässig sind, enthält das Resultset vier identische Zeilen. Da das Resultset nur Spalten für die Stadt und das Land bzw. die Region enthält, können die identischen Zeilen nicht voneinander unterschieden werden. Ein Verfahren zur Vermeidung solcher doppelten Zeilen ist das Einbinden zusätzlicher Spalten, durch die die Zeilen eindeutig werden. Wenn Sie z. B. die Namen der Autoren aufnehmen, ergeben sich eindeutige Zeilen (vorausgesetzt, dass nicht mehrere Autoren mit demselben Namen in einer Stadt leben). Hierfür kann folgende SQL-Anweisung formuliert werden:  
  
    ```  
    SELECT city, state, fname, minit, lname  
    FROM authors  
  
    ```  
  
     Diese Abfrage umgeht zwar das Problem, löst es jedoch nicht. Das Resultset enthält keine Duplikate, es handelt sich aber auch nicht mehr um ein Resultset, das Aussagen zu Städten liefert. Um sowohl die Duplikate im ursprünglichen Resultset zu entfernen als auch Informationen über Städte zu erhalten, können Sie eine Abfrage erstellen, die ausschließlich eindeutige Zeilen zurückgibt. Hierfür kann folgende SQL-Anweisung formuliert werden:  
  
    ```  
    SELECT DISTINCT city, state  
    FROM authors  
  
    ```  
  
     Ausführliche Informationen zum Ausschließen von Duplikaten finden Sie unter [Ausschließen doppelter Zeilen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
-   **Sie können Berechnungen für Zeilengruppen durchführen.** Das heißt, Sie können Informationen in Zeilengruppen zusammenfassen. Sie können z. B. ein Resultset erstellen, in dem jede Zeile die Stadt, das Land bzw. die Region für die Stadt sowie einen in dieser Stadt ansässigen Autoren enthält sowie zusätzlich die Anzahl der in dieser Stadt lebenden Autoren. Hierfür kann folgende SQL-Anweisung formuliert werden:  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
  
    ```  
  
     Ausführliche Informationen zum Berechnen von Gruppen von Zeilen finden Sie unter [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) und [Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).  
  
-   **Sie können Auswahlkriterien verwenden, um Gruppen von Zeilen aufzunehmen.** Sie können z. B. ein Resultset erstellen, in dem jede Zeile eine Stadt enthält, in der mehrere Autoren ansässig sind, außerdem das Land bzw. die Region für diese Stadt und zusätzlich die Anzahl der in dieser Stadt ansässigen Autoren. Hierfür kann folgende SQL-Anweisung formuliert werden:  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    HAVING COUNT(*) > 1  
  
    ```  
  
     Ausführliche Informationen zum Anwenden von Auswahlkriterien auf Zeilengruppen finden Sie unter [Angeben von Bedingungen für Gruppen &#40;Visual Database Tools&#41;](specify-conditions-for-groups-visual-database-tools.md) und [Verwenden von HAVING- und WHERE-Klauseln in derselben Abfrage &#40;Visual Database Tools&#41;](use-having-and-where-clauses-in-the-same-query-visual-database-tools.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
