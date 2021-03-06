---
title: Erstellen einer Momentaufnahme eines Projekts
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.SqlProjectImportSnapshotSummaryDialog.dialog
- sql.data.tools.SqlProjectImportSnapshotDialog.dialog
ms.assetid: bed670a3-13bd-4d88-91a1-58d5b9524a97
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 40111c8807c0a0aa6162e8ad6a03d796406d5c1d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75241529"
---
# <a name="how-to-create-a-snapshot-of-a-project"></a>Gewusst wie: Erstellen einer Momentaufnahme eines Projekts

Eine **Datenschichtanwendungs-Datei** stellt eine schreibgeschützte Darstellung des Datenbankschemas zum Zeitpunkt seiner Erstellung dar. Sie wird im Grunde als Datenbankschema behandelt, aus dem Sie die Schemaobjekte zurück in ein Projekt importieren können. Sie können es auch mit dem Schema einer Datenbank oder eines Projekts vergleichen und die Datenbank bzw. das Projekt so aktualisieren, dass das in der Momentaufnahme definierte Schema widergespiegelt wird.  
  
Bei einem Benutzerfehler in einem Quellendatenbankprojekt können Sie das Quellprojekt in den Zustand zurückversetzen, in dem es zum Zeitpunkt der Momentaufnahmeerstellung vorlag. Sie können auch Momentaufnahmen in verschiedenen Phasen der Entwicklung zu Basislinienzwecken festlegen.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-create-a-snapshot"></a>So erstellen Sie eine Momentaufnahme  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie **Datenschichtanwendung (\*.dacpac)** aus.  
  
2.  SSDT versucht zuerst, das Projekt zu erstellen. Wenn kein Buildfehler auftritt, wird im **Projektmappen-Explorer** ein Ordner **Momentaufnahme** erstellt. In diesem Ordner erstellt SSDT eine DACPAC-Datei, wobei das Namensformat „<Project Name>_JJJJMMTT_HH-MM-SS.dacpac“ verwendet wird.  
  
3.  Klicken Sie mit der rechten Maustaste auf die DACPAC-Datei, und wählen Sie **Umbenennen** aus. Ändern Sie den Standarddateinamen in „TradeDev1.dacpac“.  
  
4.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Funktion **GetProductsBySupplier**, und wählen Sie **Löschen** aus, um sie aus dem Projekt zu entfernen.  
  
5.  Führen Sie die vorherigen Schritte aus, um eine neue Momentaufnahme mit dem Namen **TradeDev2.dacpac** zu erstellen.  
  
### <a name="to-import-a-snapshot"></a>So importieren Sie eine Momentaufnahme  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie im Kontextmenü **Importieren** und dann **Datenebenenanwendung (\*.dacpac)** aus.  
  
2.  Klicken Sie im Dialogfeld **Datenschichtanwendung importieren** auf **Durchsuchen**, um **TradeDev1.dacpac** als Quelle des Importvorgangs auszuwählen.  
  
    Der Abschnitt **Zielprojekt** wurde deaktiviert, da das aktuelle Projekt das Standardziel ist. Klicken Sie auf **Starten**, um den Importvorgang zu starten.  
  
3.  Klicken Sie auf der Seite **Zusammenfassung** auf **Fertig stellen**. Beachten Sie im **Projektmappen-Explorer**, dass die gelöschte Tabelle im Projekt wiederhergestellt wurde.  
  
    > [!WARNING]  
    > Mit der Importmomentaufnahme werden alle Datenbankentitäten im Momentaufnahmeschema in das Projekt importiert. Daher können nun Entitäten doppelt vorhanden sein. Alle Tabellen und Ansichten enthalten nun z. B. eine zusätzliche Kopie ihrer selbst mit dem Namen <ObjectName_1>. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die einzelnen doppelt vorhandenen Objekte, und wählen Sie **Löschen** aus, um sie aus dem Projekt zu entfernen.  
  
### <a name="to-compare-snapshots"></a>So vergleichen Sie Momentaufnahmen  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **TradeDev1.dacpac**, und wählen Sie **Schemavergleich** aus. Das Fenster **Schemavergleich** wird geöffnet.  
  
2.  Verwenden Sie die Optionen unter **Datenschichtanwendungs-Datei**, um das Quell- und Zielschema festzulegen. Legen Sie das **Quellschema** unter **Datenschichtanwendungs-Datei** auf **TradeDev1.dacpac** und das **Zielschema** auf **TradeDev2.dacpac** fest.  
  
3.  Klicken Sie auf **OK**, um den Vergleichsvorgang zu starten. Beachten Sie, dass die gelöschte Funktion als Unterschied zwischen der alten und neuen Momentaufnahme hervorgehoben wird.  
  
    Sie können die Unterschiede zu anderen Momentaufnahmen auf einfache Weise mit dem Schemavergleich auffinden. So können Sie den Fortschritt des Projekts während des Entwicklungsprozesses bestimmen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
