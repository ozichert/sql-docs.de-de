---
title: Verwalten von Dateien mit Codierung
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 67106a11e7a42f6167c0d08df99917ed057f11f5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75251880"
---
# <a name="manage-files-with-encoding"></a>Verwalten von Dateien mit Codierung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Um die Anzeige von Code in einer bestimmten Sprache und auf einer bestimmten Plattform zu vereinfachen, können Sie einer Datei eine bestimmte Zeichencodierung zuordnen.  
  
## <a name="opening-files"></a>Öffnen von Dateien  
Sie können zum Bearbeiten der Datei einen Editor Ihrer Wahl verwenden.  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a>So öffnen Sie eine Datei mit einem bestimmten Editor  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Wählen Sie im Dialogfeld **Datei öffnen** den Dateinamen aus.  
  
3.  Klicken Sie auf den Pfeil neben der Schaltfläche **Öffnen** , und klicken Sie dann im angezeigten Menü auf**Öffnen mit** .  
  
4.  Wählen Sie in der Liste **Wählen Sie das zu öffnende Programm aus** einen Editor aus, und klicken Sie dann auf **Öffnen**. Wählen Sie zum Öffnen einer Datei mit einer bestimmten Codierung einen Editor mit Codierungsunterstützung aus, z. B. den SQL-Abfrage-Editor mit Codierung oder den XML-Editor mit Codierung.  
  
## <a name="saving-files"></a>Speichern von Dateien  
Sie können Code auch mit Unicode-Codierung oder einer anderen Codepage speichern, um verschiedene Sprachen zu unterstützen, z. B. Westeuropäisch oder Osteuropäisch. Sie können einer Datei eine bestimmte Zeichencodierung zuordnen, um die Anzeige von Code in dieser Sprache zu vereinfachen, sowie einen Zeilenendentyp zur Unterstützung eines bestimmten Betriebssystems. Darüber hinaus können einige Zeichen in Dateinamen nur gespeichert werden, wenn sie mit Unicode-Codierung gespeichert werden.  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a>So speichern Sie eine Datei mit einer anderen Codierung oder einem anderen Zeilenendentyp  
  
1.  Zeigen Sie im Menü **Datei** auf **Speichern <filename> unter**.  
  
2.  Erweitern Sie im Dialogfeld **Datei speichern unter** die Schaltfläche **Speichern** , und klicken Sie dann auf **Mit Codierung speichern**.  
  
3.  Wählen Sie im Dialogfeld **Erweiterte Speicheroptionen** in der Liste **Codierung** die gewünschte Codierung aus.  
  
4.  Wählen Sie in der Liste **Zeilenenden**den gewünschten Zeilenendentyp aus.  
  
    > [!NOTE]  
    > Wenn Sie die Datei mit Unicode-Codierung speichern, muss die Datei in [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual SourceSafe als Binärdatei eingecheckt werden, da Visual SourceSafe keine Unterstützung für das Zusammenführen, Vergleichen und Anzeigen von Unterschieden zwischen Dateien bietet, die mit Unicode-Codierung gespeichert werden.  
  
Wenn Sie mit Visual SourceSafe Dateien mit ANSI-, UTF8- oder Unicode-Codierung speichern, beachten Sie die folgenden Einschränkungen:  
  
-   Bei ANSI-Dateien sind nur Zeichen zulässig, die in der aktuellen Codepage unterstützt werden, wodurch die internationale Verwendung eingeschränkt ist.  
  
-   Bei Unicode-Dateien können die Funktionen zum freigegebenen Auschecken, Überprüfen von Unterschieden oder Zusammenführen nicht verwendet werden, da sie als Binärdateien behandelt werden. Sie können dieses Format in internationalen Dateien verwenden.  
  
-   UTF8-Dateien funktionieren nicht sicher mit Visual SourceSafe, da Änderungen, die für Editoren von UTF8-Dateien Probleme verursachen, beim Einchecken, Auschecken, Überprüfen von Unterschieden und Zusammenführen vorgenommen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Dateien zum Verwalten von Projektmappen und Projekten](../../ssms/solution/files-that-manage-solutions-and-projects.md)  
[Zuordnen von Dateierweiterungen zu einem Code-Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
