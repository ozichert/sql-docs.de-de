---
title: Entpacken eines DAC-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- wizard [DAC], unpack
- data-tier application [SQL Server], unpack
- How to [DAC], unpack
- unpack DAC
ms.assetid: 697b69b3-f157-4e22-ac4e-f65c5fc2d0ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e2be902c241403ec044b3d348f90dc85327b8ad
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72909524"
---
# <a name="unpack-a-dac-package"></a>Entpacken eines DAC-Pakets
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Verwenden Sie das Dialogfeld Datenebenenanwendung entpacken, um die Skripts und die Dateien aus einem Datenebenenanwendungs-Paket (DAC) zu entzippen. Die Skripts und Dateien werden in einem Ordner abgelegt, in dem sie überprüft werden können, bevor das Paket für die Bereitstellung der DAC in einem Produktionssystem verwendet wird. Der Inhalt einer DAC kann auch mit dem Inhalt eines anderen Pakets verglichen werden, das in einen anderen Ordner entpackt wurde.  
  
1.  **Vorbereitungen:**  [Sicherheit](#Security)  
  
2.  **So entpacken Sie ein DAC-Paket mit:**  [dem Dialogfeld „Unpack Data-Tier Application Dialog“ (Datenebenenanwendung entpacken)](#UnpackDACDial), [dem Untersuchen des Inhalts eines DAC-Pakets](#ExamDACPack)  

##  <a name="security"></a><a name="Security"></a> Sicherheit  
 Das Bereitstellen eines DAC-Pakets aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche DACs können schädlichen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code ausführt oder Fehler verursacht, indem er das Schema ändert. Bevor Sie eine DAC aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, sollten Sie sie auf einer isolierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Testinstanz bereitstellen, die DAC entpacken und den Code, z. B. gespeicherte Prozeduren oder anderen benutzerdefinierten Code, untersuchen.  
  
##  <a name="unpack-data-tier-application-dialog"></a><a name="UnpackDACDial"></a> Datenebenenanwendung entpacken  
 **So entpacken Sie eine DAC-Paketdatei**  
  
-   Navigieren Sie im **Windows-Explorer**zum Speicherort einer DAC-Paketdatei (.dacpac).  
  
-   Öffnen Sie das Dialogfeld "Datenebenenanwendung entpacken" mit einer dieser beiden Methoden:  
  
    1.  Klicken Sie mit der rechten Maustaste auf die DAC-Paketdatei (.dacpac), und wählen Sie **Entpacken**aus.  
  
    2.  Doppelklicken Sie auf die DAC-Paketdatei.  
  
-   Schließen Sie die Dialogfelder ab:  
  
    -   [DAC-Paketdatei für Microsoft SQL Server entpacken](#Unpack)  
  
    -   [Nach Ordner suchen](#Browse)  
  
###  <a name="unpack-microsoft-sql-server-dac-package-file"></a><a name="Unpack"></a> DAC-Paketdatei für Microsoft SQL Server entpacken  
 Verwenden Sie diese Seite, um den Zielordner anzugeben, in dem die entpackten Dateien abgelegt werden sollen, und führen Sie dann den Entpackungsvorgang aus.  
  
 **Dateien werden in diesen Ordner entpackt:** – Geben Sie den vollständigen Pfad zum Ordner der entpackten Dateien an. Wenn der Ordner vorhanden ist und Sie den vollständigen Pfad kennen, geben Sie den Pfad im Feld ein. Klicken Sie andernfalls auf die Schaltfläche **Durchsuchen** , um zu einem Ordner zu navigieren oder einen neuen Ordner zu erstellen.  
  
 **Durchsuchen** – Öffnet die Seite **Nach Ordner suchen** , wo Sie einen Ordner auswählen können, indem Sie in der Dateihierarchie navigieren oder einen neuen Ordner erstellen.  
  
 **Entpacken** – Startet den Entpackungsvorgang.  
  
 **Abbrechen** – Schließt das Dialogfeld, ohne das DAC-Paket zu entpacken.  
  
###  <a name="browse-for-folder"></a><a name="Browse"></a> Nach Ordner suchen  
 Verwenden Sie diese Seite, um den Zielordner für den Entpackungsvorgang auszuwählen. Optional können Sie auch einen neuen Ordner erstellen.  
  
 **Ordnerliste** – Zeigt die Dateihierarchie für den Computer an. Erweitern Sie die Knoten, um zum Ordner zu navigieren, in den das DAC-Paket entpackt werden soll. Klicken Sie auf den Ordner und dann auf **OK**.  
  
 **Neuen Ordner erstellen** – Öffnet ein Dialogfeld, in dem Sie den Namen für einen neuen Ordner angeben können, der in dem Ordner erstellt werden soll, den Sie gerade in der Ordnerhierarchie ausgewählt haben.  
  
 **OK** – Legt den Ordnerpfad fest, den Sie im Feld **Dateien werden in diesen Ordner entpackt** der Seite **DAC-Paketdatei entpacken** ausgewählt haben, und wechselt wieder zu dieser Seite zurück.  
  
 **Abbrechen** – Schließt das Dialogfeld, ohne einen Ordner auszuwählen.  
  
##  <a name="examine-the-contents-of-a-dac-package"></a><a name="ExamDACPack"></a> Untersuchen des Inhalts eines DAC-Pakets  
 Nachdem Sie das Paket entpackt haben, können Sie die vom Dialogfeld **Datenebenenanwendung entpacken** erzeugten Dateien untersuchen. Das Dialogfeld erstellt die folgenden Dateien im ausgewählten Zielordner:  
  
1.  Ein Transact-SQL-Skript, das die Anweisungen zum Erstellen der in der DAC definierten Objekte enthält. Der Dateiname ist *DACName*.sql, wobei *DACName* der Name der DAC ist.  
  
2.  Alle XML-Dateien aus dem Paket.  
  
3.  Alle Dateien, die sich im Bereich für zusätzliche Dateien der DAC befinden, z. B. vor oder nach der Bereitstellung der DAC auszuführende Dateien.  
  
 Weitere Informationen finden Sie unter [Validate a DAC Package](../../relational-databases/data-tier-applications/validate-a-dac-package.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Bereitstellen einer Datenebenenanwendung](../../relational-databases/data-tier-applications/deploy-a-data-tier-application.md)   
 [Upgrade einer Datenebenenanwendung](../../relational-databases/data-tier-applications/upgrade-a-data-tier-application.md)  
  
  
