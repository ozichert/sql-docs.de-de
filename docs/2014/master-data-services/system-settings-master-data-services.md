---
title: Systemeinstellungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, system settings
- system settings [Master Data Services]
ms.assetid: 83075cdf-f059-4646-8ba2-19be8202f130
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a411290435a10e351c05e9dd1350bde597dbe449
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289248"
---
# <a name="system-settings-master-data-services"></a>Systemeinstellungen (Master Data Services)
  Sie können für alle Webanwendungen und Webdienste, die einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank zugeordnet sind, Systemeinstellungen konfigurieren.  
  
 Viele dieser Einstellungen können im [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] auf der Seite **Datenbank** konfiguriert werden. Andere können in der Tabelle Systemeinstellungen (mdm.tblSystemSetting) in der Datenbank [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] konfiguriert werden.  
  
 Die Einstellungen lassen sich folgendermaßen kategorisieren:  
  
-   [Allgemeine Einstellungen](#General)  
  
-   [Versionsverwaltungseinstellungen](#Versions)  
  
-   [Stagingeinstellungen](#Staging)  
  
-   [Explorer-Einstellungen](#Explorer)  
  
-   [Einstellungen für Add-In für Excel](#xls)  
  
-   [Geschäftsregel Einstellungen](#BusinessRules)  
  
-   [Benachrichtigungseinstellungen](#Notifications)  
  
-   [Sicherheitseinstellungen](#Security)  
  
-   [Nicht verwendet](#NotUsed)  
  
##  <a name="general-settings"></a><a name="General"></a>Allgemeine Einstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Timeout für Datenbankverbindung**|**DatabaseConnectionTimeOut**|Die Anzahl von Sekunden, während der die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auf die Herstellung einer Verbindung wartet. Wenn die Verbindung innerhalb dieser Zeit nicht hergestellt wird, wird sie abgebrochen, und es wird ein Fehler zurückgegeben. Der Standardwert ist **60** Sekunden (1 Minute).|  
|**Timeout für Datenbankbefehl**|**DatabaseCommandTimeOut**|Die Anzahl von Sekunden, während der die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank auf den Abschluss eines Befehls wartet. Wenn der Befehl innerhalb dieser Zeit nicht abgeschlossen wird, wird er abgebrochen, und es wird ein Fehler zurückgegeben. Der Standardwert ist **3600** Sekunden (60 Minuten).|  
|**Webdiensttimeout**|**Server Timeout (**|Die Anzahl von Sekunden, während der ASP.NET auf den Abschluss einer [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Seitenanforderung wartet. Wenn die Anforderung innerhalb dieser Zeit nicht abgeschlossen wird, wird die Anforderung abgebrochen und ein Fehler zurückgegeben. Der Standardwert ist **120000** Sekunden (2.000 Minuten).|  
|**Clienttimeout**|**ClientTimeOut**|Die Anzahl von Sekunden ohne Aktivität, nach der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zur Startseite zurückkehrt. Der Standardwert ist **300** Sekunden (5 Minuten).|  
|**Anzahl der Zeilen pro Batch.**|**RowsPerBatch**|Die Anzahl von Datensätzen, die vom Webdienst in den einzelnen Batches abgerufen werden sollen. Der Standardwert ist **50**.|  
||**ApplicationName**|Der Text, der in Ereignisprotokollen angezeigt wird. Der Standardwert ist **MDM**.|  
||**SiteTitle**|Der Text, der in der Titelleiste des [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webbrowsers angezeigt wird. Der Standardwert ist **Master Data Manager**.|  
  
##  <a name="version-management-settings"></a><a name="Versions"></a>Versions Verwaltungs Einstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Nur Versionen kopieren, für die ein Commit ausgeführt wurde**|**CopyOnlyCommittedVersion**|Gibt in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]an, ob Benutzer nur Modellversionen mit dem Status **Commit wurde ausgeführt**oder Versionen mit einem beliebigen anderen Status kopieren können. Der Standardwert ist **Ja** oder **1**. Er gibt an, dass Benutzer nur Versionen mit dem Status **Commit wurde ausgeführt** kopieren können. Wenn Sie den Wert in **Nein** oder **2** ändern, können Benutzer alle Versionen kopieren.|  
  
 Weitere Informationen finden Sie unter [Versionen &#40;Master Data Services&#41;](versions-master-data-services.md).  
  
##  <a name="staging-settings"></a><a name="Staging"></a> Stagingeinstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Protokollieren aller Stagingtransaktionen**|**StagingTransactionLogging**|Gilt nur für SQL Server 2008 R2. Legt fest, ob Transaktionen beim Laden von Stagingdatensätzen in die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank protokolliert werden. Der Standardwert ist **Aus** oder **2**. Ändern Sie den Wert in **Ein** oder **1** , um die Protokollierung zu aktivieren.|  
|**Staging-Batchintervall**|**StagingBatchInterval**|Gibt im Funktionsbereich [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Integration Management** functional area, the number of seconds after you select **Start Batches** that your batch is processed. Der Standardwert ist **60** Sekunden (1 Minute).|  
  
 Weitere Informationen finden Sie unter [Datenimport &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="explorer-settings"></a><a name="Explorer"></a> Explorereinstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Die Standardanzahl der Elemente in der Hierarchie.**|**HierarchyChildNodeLimit**|Gibt im Funktionsbereich -[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** an, wie viele Elemente maximal in den einzelnen Hierarchieknoten angezeigt werden, bevor **...Weitere...** angezeigt wird. Sie können auf **...Weitere...** klicken, um die nächste Gruppe von Elementen anzuzeigen. Der Standardwert ist **50**.|  
|**Standardmäßig Namen in Hierarchie anzeigen**|**ShowNamesInHierarchy**|Legt im Funktionsbereich -[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** die Standardeinstellung fest, die bei der Anzeige von Hierarchien ausgewählt wird.<br /><br /> Der Standardwert ist **Yes** oder **1**. Er gibt an, dass Name und Code der einzelnen Elemente angezeigt werden. Ändern Sie den Wert in **No** oder **2** , wenn Sie nur den Code anzeigen möchten.|  
|**Anzahl domänenbasierter Attribute in Liste**|**DBAListRowLimit**|Gibt an, wie viele Attribute in einer Liste im Funktionsbereich des [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Internet** angezeigt werden, wenn Sie auf einen domänenbasierten Attributwert im Raster doppelklicken. Der Standardwert ist **50**. Wenn mehr als 50 Elemente vorhanden sind, wird stattdessen ein durchsuchbares Dialogfeld angezeigt.|  
||**GridFilterDefaultFuzzySimilarityLevel**|Gibt im Funktionsbereich [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the level of similarity used when using the **Matches** filter criteria. Der Standardwert ist **0,3**. Legen Sie als Wert eine Zahl in der Nähe von **1** fest, um ein Ergebnis zurückzugeben, das den Suchkriterien besser entspricht. Eine exakte Übereinstimmung erhalten Sie, wenn Sie den Wert auf **1** festlegen.|  
  
##  <a name="add-in-for-excel-settings"></a><a name="xls"></a>Add-in für Excel-Einstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|Anzeigen von Add-In für Excel-Text auf Websitehomepage|ShowAddInText|Zeigt auf der Startseite von [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] einen Link an, damit Benutzer das [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]herunterladen können.|  
|Add-In für Excel-Installationspfad auf Websitehomepage|AddInURL|Dies ist auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Homepage, wenn der Link zum [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] angezeigt wird, der Speicherort, zu dem die Benutzer nach Anklicken des Links geführt werden.|  
  
##  <a name="business-rule-settings"></a><a name="BusinessRules"></a> Geschäftsregeleinstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Zahl, mit der neue Geschäftsregeln inkrementiert werden**|**BusinessRuleDefaultPriorityIncrement**|Im Funktionsbereich [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Systemverwaltung** die Zahl, mit der die Priorität der einzelnen neuen Geschäftsregeln inkrementiert wird. Der Standardwert ist **10**.|  
|**Anzahl von Elementen zur Anwendung von Geschäftsregeln.**|**BusinessRuleRealtimeMemberCount**|Gibt im Funktionsbereich  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** an, auf wie viele Elemente im Raster Geschäftsregeln angewendet werden sollen. In [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]die maximale Anzahl von Elementen im aktiven Arbeitsblatt, auf die Geschäftsregeln angewendet werden sollen. Der Standardwert ist **10000**.|  
  
 Weitere Informationen finden Sie unter [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md).  
  
##  <a name="notification-settings"></a><a name="Notifications"></a>Benachrichtigungseinstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
|**Master Data Manager-URL für Benachrichtigungen**|**MDMRootURL**|Gibt die URL für die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung an, die im Link in E-Mail-Benachrichtigungen verwendet wird, z.B. http://constoso/mds.|  
|**Benachrichtigungs-E-Mail-Intervall**|**NotificationInterval**|Die Häufigkeit in Sekunden, in der E-Mail-Benachrichtigungen gesendet werden. Der Standardwert ist **120** Sekunden (2 Minuten).|  
|**Anzahl von Benachrichtigungen in einer einzelnen E-Mail**|**NotificationsPerEmail**|Die maximale Anzahl von Problemen bei der Überprüfung, die in einer Benachrichtigungs-E-Mail aufgeführt werden. Weitere Probleme (sofern vorhanden) werden nicht in die E-Mail aufgenommen, sind aber im [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]verfügbar.|  
|**E-Mail-Standardformat**|**EmailFormat**|Das Format für alle E-Mail-Benachrichtigungen. Der Standardwert ist **HTML** oder **1**. Die Datenbankeinstellung **2** steht für **Text**.<br /><br /> Hinweis: Sie können das Format für einen einzelnen Benutzer in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]überschreiben, indem Sie das **E-Mail-Format** auf der Registerkarte **Allgemein** des Benutzers ändern und speichern.|  
|**Regulärer Ausdruck für E-Mail-Adresse**|**EmailRegExPattern**|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Im Funktionsbereich **Benutzer-und Gruppenberechtigungen** der reguläre Ausdruck, mit dem die e-Mail-Adresse überprüft wird, die auf der Registerkarte **Allgemein** eines Benutzers eingegeben wurde. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre](https://go.microsoft.com/fwlink/?LinkId=164401) Ausdrücke in der MSDN Library.|  
|**Datenbank-E-Mail Konto**|**EmailProfilePrincipalAccount**|Zeigt das Datenbank-E-Mail-Konto an, das für das Senden von E-Mail-Benachrichtigungen verwendet werden soll. Das Standardprofil lautet **mds_email_user**.|  
|**Datenbank-E-Mail Profil**|**DatabaseMailProfile**|Das zu verwendende Datenbank-E-Mail-Profil beim Senden von E-Mail-Benachrichtigungen. Für diese Einstellung gibt es keinen Standardwert.|  
||**ValidationIssueHTML**|Der Text der E-Mail-Benutzer ist im HTML-Format, wenn keine Überprüfung für eine Geschäftsregel besteht.|  
||**ValidationIssueText**|Das Nur-Text-Format besteht aus einem Text für E-Mail-Benutzer, wenn keine Überprüfung einer Geschäftsregel besteht.|  
||**VersionStatusChangeText**|Im Nur-Text-Format kommt der Text der E-Mail-Benutzer herein, wenn sich der Status einer Version ändert. Nur Benutzer mit der Berechtigung **Aktualisieren** für das gesamte Modell erhalten diese E-Mail.|  
||**VersionStatusChangeHTML**|Im HTML-Format kommt der Text für E-Mail-Benutzer herein, wenn sich der Status einer Version ändert. Nur Benutzer mit der Berechtigung **Aktualisieren** für das gesamte Modell erhalten diese E-Mail.|  
  
 Weitere Informationen finden Sie unter [Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md).  
  
##  <a name="security-settings"></a><a name="Security"></a>Sicherheitseinstellungen  
  
|Einstellung des Konfigurations-Managers|Systemeinstellung|BESCHREIBUNG|  
|-----------------------------------|--------------------|-----------------|  
||**SecurityMemberProcessInterval**|Gibt im Funktionsbereich [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Benutzer- und Gruppenberechtigungen** an, mit welcher Häufigkeit (in Sekunden) Benutzer- und Gruppenberechtigungen angewendet werden, die auf der Registerkarte **Hierarchieelemente** festlegt sind. Der Standardwert ist **3600** Sekunden (60 Minuten).|  
  
 Weitere Informationen finden Sie unter [Sofortiges Anwenden von Elementberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="not-used"></a><a name="NotUsed"></a>Nicht verwendet  
 Die folgenden Einstellungen in der Tabelle Systemeinstellungen werden nicht verwendet.  
  
-   **SecurityMode**  
  
-   **MDSHubName**  
  
-   **ApplicationLogging**  
  
-   **ReportServer**  
  
-   **ReportDirectory**  
  
-   **BusinessRuleEngineIterationLimit**  
  
-   **BusinessRuleExtensibility**  
  
-   **AttributeExplorerMarkAllActionMemberCount**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
