---
title: Hinzufügen, aktualisieren und Löschen von Daten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2212e7424f22ecca2619ef7215bf94b0dbb62875
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054265"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Hinzufügen, Aktualisieren und Löschen von Daten (Master Data Services)
  Sie können einem Modell in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]in einem Massenvorgang Daten hinzufügen und Datenänderungen vornehmen.  
  
 **Voraussetzungen**  
  
-   Sie müssen über die Berechtigung zum Einfügen von Daten in die Tabelle „stg.\<name>_Leaf“, „stg.\<name>_Consolidated“ bzw. „stg.\<name>_Relationship“ in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank verfügen.  
  
-   Sie müssen über Berechtigungen zum Ausführen der gespeicherten Prozedur „stg.udp_\<name>_Leaf“, „stg.udp\_\<name>_Consolidated“, oder „stg.udp\_\<name>_Relationship“ in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank verfügen.  
  
-   Das Modell darf nicht den Status **Commit wurde ausgeführt**haben.  
  
 **So können Sie Daten in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Datenbank hinzufügen, aktualisieren und löschen**  
  
1.  Bereiten Sie die Elemente für den Import in die entsprechende Stagingtabelle in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank vor, und geben Sie Werte für die Pflichtfelder an. Eine Übersicht über Stagingtabellen finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Die Tabelle für Blattelemente ist „stg.\<name>_Leaf“, wobei \<name> die entsprechende Entität bezeichnet. Weitere Informationen zu Pflichtfeldern finden Sie unter [Stagingtabelle für Blattelemente &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)  
  
    -   Die Tabelle für konsolidierte Elemente ist „stg.\<name>_Consolidated“. Weitere Informationen zu Pflichtfeldern finden Sie unter [Konsolidierte Elementstagingtabelle &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Zum Verschieben des Speicherorts von Elementen in expliziten Hierarchien wird die Tabelle „stg.\<name>_Relationship“ verwendet. Weitere Informationen zu Pflichtfeldern finden Sie unter [Stagingtabelle für Beziehungen &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Eine Übersicht über das Verschieben von Membern in expliziten Hierarchien finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Verwenden Sie den Feldwert von **ImportType** , um anzugeben, dass Sie neue Elemente erstellen, Elemente deaktivieren oder Elemente löschen. Weitere Informationen zu den Werten finden Sie unter [Stagingtabelle für Blattelemente &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) und [Konsolidierte Elementstagingtabelle &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Eine Übersicht über das Deaktivieren und Löschen von Elementen finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zur Datenbank-Engine-Instanz für Ihre [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
     Weitere Informationen finden Sie unter [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Importieren Sie Daten in die Stagingtabellen mithilfe des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import- und -Export-Assistenten.  
  
     Weitere Informationen finden Sie unter [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Laden Sie mit einer der folgenden Aktivitäten die Daten aus den Stagingtabellen in die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
    -   Führen Sie die gespeicherte Stagingprozedur aus, die der Stagingtabelle entspricht, in die Sie Daten verschieben möchten.  
  
         Eine Übersicht über gespeicherte stagingprozeduren und Stagingtabellen finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Weitere Informationen zu Parametern für gespeicherte Stagingprozeduren und ein Codebeispiel finden Sie unter [Gespeicherte Stagingprozedur &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Verwenden Sie den Funktionsbereich **Integrationsmanagement** der Masterdatenverwaltung.  
  
         Wählen Sie auf der Seite **Stagingbatches** in der Dropdownliste das Modell aus, dem Sie Daten hinzufügen möchten, und klicken Sie anschließend auf **Batches starten**. Der Status der Batchverarbeitung wird im Feld **Status** angezeigt. Weitere Informationen zu Status finden Sie unter [Importstatus &#40;Master Data Services&#41;](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Stagingbatchesseite im Master Data Manager](../../2014/master-data-services/media/mds-staging-batches.png "Stagingbatchesseite im Master Data Manager")  
  
         Der Stagingvorgang wird mit den durch die Einstellung **Staging-Batchintervall** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Zeigen Sie Fehler an, die während des Stagings aufgetreten sind. Weitere Informationen finden Sie unter [Anzeigen von Fehlern, die während des Stagingprozesses auftreten, &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md) und [stagingprozessfehlern &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Überprüfen der Daten im Hinblick auf Geschäftsregeln.  
  
     Navigieren Sie im Master Data Manager zum Funktionsbereich **Explorer** für Ihr Modell, und wenden Sie dann Geschäftsregeln zur Überprüfung Ihrer Daten an. Weitere Informationen finden Sie unter [Überprüfen von bestimmten Elementen auf Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Sie können auch eine gespeicherte Prozedur zum Überprüfen der Daten verwenden. Weitere Informationen finden Sie unter [Gespeicherte Überprüfungsprozedur &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     Wenn Sie Daten aus den Stagingtabellen laden, werden die Daten nicht automatisch im Hinblick auf Geschäftsregeln überprüft. Weitere Informationen dazu, was eine Überprüfung ist und wann sie stattfindet, finden Sie unter [Überprüfung &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
