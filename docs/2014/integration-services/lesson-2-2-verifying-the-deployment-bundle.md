---
title: 'Schritt 2: Überprüfen des Bereitstellungspakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 127044042eed7f082b6f1f7ba7ae6918232ba9ff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62891769"
---
# <a name="step-2-verifying-the-deployment-bundle"></a>Schritt 2: Überprüfen des Bereitstellungspakets
  In Lektion 1 haben Sie das Deployment Tutorial-Projekt erstellt und dem Projekt Pakete und Hilfsdateien hinzugefügt; in der vorherigen Aufgabe haben Sie ein Bereitstellungsprogramm für das Projekt erstellt.  
  
 In dieser Aufgabe überprüfen Sie den Inhalt des Bereitstellungspakets. Das Bereitstellungspaket ist der Ordner, den Sie auf den Zielcomputer kopieren und zum Installieren der Pakete verwenden. Wenn Sie den Standardwert, bin\Deployment, als Speicherort des Bereitstellungshilfsprogramms verwendet haben, entspricht das Bereitstellungspaket dem Ordner „Bin\Deployment“ im Ordner „Deployment Tutorial“ des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekts.  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>So überprüfen Sie den Inhalt des Bereitstellungspakets  
  
1.  Suchen Sie den Ordner bin\Deployment auf dem Computer.  
  
2.  Überprüfen Sie, ob die folgenden Dateien vorhanden sind:  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  Klicken Sie mit der rechten Maustaste auf Deployment Tutorial.SSISDeploymentManifest, zeigen Sie auf **Öffnen mit**, und klicken Sie anschließend auf **Internet Explorer**. Sie können die Datei auch in einem Texteditor, wie z. B. dem Editor, öffnen. Der XML-Code für die Datei sollte folgendermaßen lauten:  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  Vergewissern Sie sich, dass der `AllowConfigurationChanges` Wert des-Attributs **true** ist und `Package` der XML-Code ein-Element für jedes `MiscellaneousFile` der beiden Pakete enthält, ein-Element für jede der vier nicht `ConfigurationFile` -Paketdateien und ein-Element für jede der beiden XML-Konfigurationsdateien.  
  
5.  Beenden Sie Internet Explorer oder den Texteditor.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Installieren von Paketen](../integration-services/lesson-3-install-ssis-package.md)  
  
![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
