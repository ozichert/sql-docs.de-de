---
title: Erweiterte Objektauswahl (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 390ef0c2-107c-4443-9495-80f35f22d168
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2e00eece4d8a3064806b401975aa299e76518f3f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68061206"
---
# <a name="advanced-object-selection--mysqltosql"></a>Erweiterte Objektauswahl (MySqlToSql)
Im Dialogfeld Erweiterter **Objekt Abschnitt** können Sie Datenbankobjekte filtern, indem Sie Zeichen folgen und Teil Zeichenfolgen im Objektnamen verwenden. Wählen Sie anschließend diese Objekte aus, oder deaktivieren Sie diese. SSMA führt Konvertierungs-und Migrations Vorgänge für ausgewählte Objekte aus.  
  
Um auf dieses Dialogfeld zuzugreifen, klicken Sie mit der rechten Maustaste in einen metadatenexplorer, und wählen Sie dann **Erweiterte Objektauswahl**aus.  
  
Wenn Sie das Dialogfeld zum ersten Mal öffnen, klicken Sie auf **Unterkategorien Elemente anzeigen** , um alle Objekte anzuzeigen, die Metadaten in das Projekt geladen haben. Sie können dann Zeichen folgen eingeben, um die Elemente zu filtern. Geben Sie z. b. die Zeichenfolge "Company" ein, um alle Elemente anzuzeigen, deren Namen diese Zeichenfolge enthalten.  
  
Bevor Sie dieses Dialogfeld verwenden, möchten Sie möglicherweise erzwingen, dass SSMA alle Metadaten lädt, indem Sie entweder Schemas oder das Projekt speichern.  
  
## <a name="options"></a>Optionen  
**Alle Elemente überprüfen**  
Fügt ein Häkchen neben allen Elementen hinzu. Diese Elemente werden sofort im metadatenexplorer ausgewählt.  
  
**Alle Elemente deaktivieren**  
Entfernt das Häkchen neben alle Elemente. Diese Elemente werden sofort im metadatenexplorer gelöscht.  
  
**Listen Ansichtsmodus**  
Zeigt gefilterte Elemente in einer Liste an.  
  
**Tabellen Ansichtsmodus**  
Zeigt gefilterte Elemente in einer Tabelle an.  
  
**Nur geladene Elemente werden angezeigt.**  
Schaltet die Anzeige von Kategorien oder Elementen um. Wenn diese Schaltfläche ausgewählt ist, zeigt SSMA alle Elemente an, die mit den Filterkriterien übereinstimmen, und diejenigen, die zuvor geladen wurden. Wenn diese Schaltfläche nicht ausgewählt ist, zeigt SSMA die Kategorieordner an.  
  
**Filter**  
Geben Sie die Zeichenfolge ein, die Sie zum Filtern von Elementen verwenden möchten. Wenn Sie z. b. alle verfügbaren Elemente suchen möchten, die die Zeichenfolge "ID" im Elementnamen enthalten, geben Sie die Zeichenfolge "ID" in das **Filter** Feld ein.  
  
Wenn die Elemente den Filterkriterien entsprechen, werden die Kategorien oder Elemente angezeigt, wenn Sie die Zeichenfolge eingeben. Um die übereinstimmenden Elemente anzuzeigen, empfiehlt es sich, auf die Schaltfläche **nur angezeigte Elemente** zu klicken.  
  
**Filter löschen**  
Löscht das **Filter** Feld.  
  
