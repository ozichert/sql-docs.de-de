---
title: Erstellen von äußeren Joins
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 5c1a8b952d0723c4fd1c54ab2b841ed818017c9f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254308"
---
# <a name="create-outer-joins-visual-database-tools"></a>Erstellen von äußeren Joins (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In der Standardeinstellung wird vom [Abfrage- und Sicht-Designer](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) ein innerer Join zwischen Tabellen erstellt. Innere Joins entfernen die Zeilen, die nicht mit einer Zeile aus der anderen Tabelle übereinstimmen. Äußere Joins dagegen geben alle Zeilen aus mindestens einer der in der FROM-Klausel genannten Tabellen oder Sichten zurück, sofern diese Zeilen ggf. die WHERE- oder HAVING-Suchbedingungen erfüllen. Wenn Sie Datenzeilen in das Resultset einschließen möchten, die keine Übereinstimmung in der verknüpften Tabelle aufweisen, können Sie einen äußeren Join erstellen.  
  
Beim Erstellen eines äußeren Join ist die Reihenfolge relevant, in der Tabellen in der SQL-Anweisung angezeigt werden (wie im SQL-Bereich widergespiegelt). Die zuerst hinzugefügte Tabelle wird als "linke" Tabelle und die zweite hinzugefügte Tabelle als "rechte" Tabelle betrachtet. (Die tatsächliche Reihenfolge, in der die Tabellen im [Diagrammbereich](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) angezeigt werden, spielt keine Rolle.) Durch das Angeben eines linken oder rechten äußeren Joins verweisen Sie auf die Reihenfolge, in der Tabellen zur Abfrage hinzugefügt wurden, sowie auf die Reihenfolge, in der sie in der SQL-Anweisung im [SQL-Bereich](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)angezeigt werden.  
  
### <a name="to-create-an-outer-join"></a>So erstellen Sie einen äußeren Joins  
  
1.  Erstellen Sie den Joins automatisch oder manuell. Weitere Informationen finden Sie unter [Automatisches Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md) oder [Manuelles Verknüpfen von Tabellen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md).  
  
2.  Wählen Sie im Diagrammbereich die Joinlinie aus. Wählen Sie anschließend im Menü **Abfrage-Designer** die Option **Alle Zeilen von <tablename> auswählen** aus, und wählen Sie den Befehl aus, der die Tabelle enthält, deren zusätzliche Zeilen Sie einfügen möchten.  
  
    -   Wählen Sie die erste Tabelle aus, um eine linken äußeren Joins zu erstellen.  
  
    -   Wählen Sie die zweite Tabelle aus, um eine rechten äußeren Joins zu erstellen.  
  
    -   Wählen Sie beide Tabellen aus, um eine vollständigen äußeren Joins zu erstellen.  
  
Wenn Sie angeben, ändert der Abfrage- und Sicht-Designer die Joinlinie zum Anzeigen eines äußeren Joins.  
  
Außerdem ändert der Abfrage- und Sicht-Designer die SQL-Anweisung im SQL-Bereich, um die Änderung des Jointyps widerzuspiegeln, wie in der folgenden Anweisung dargestellt:  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
Da ein äußerer Join Zeilen ohne Übereinstimmungen einschließt, kann diese zum Suchen von Zeilen verwendet werden, die Fremdschlüsseleinschränkungen verletzen. Erstellen Sie hierzu einen äußeren Join, und fügen Sie anschließend eine Suchbedingung zum Suchen von Zeilen hinzu, in denen die Primärschlüsselspalte der äußersten rechten Tabelle Null ist. Mit dem folgenden äußeren Join werden z. B. Zeilen in der Tabelle `employee` gesucht, für die keine übereinstimmenden Zeilen in der Tabelle `jobs` vorhanden sind:  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Abfragen mit Joins &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
[Verknüpfen (Dialogfeld) &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-dialog-box-visual-database-tools.md)  
  
