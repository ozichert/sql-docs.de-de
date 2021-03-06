---
title: Konfigurieren von Windows-Dienstkonten und -Berechtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/28/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- startup service states [SQL Server]
- Setup [SQL Server], user accounts
- Windows permissions [SQL Server]
- modifying user accounts
- default accounts
- domains [SQL Server], user accounts
- startup accounts [SQL Server]
- system accounts [SQL Server]
- services [SQL Server], permissions
- ACL (access control list)
- local system accounts [SQL Server]
- instance-aware services [SQL Server]
- permissions [SQL Server], services
- SQL Server Agent service, user accounts
- Windows NT permissions [SQL Server]
- user accounts [SQL Server]
- identifying instance-unaware services [SQL Server]
- installing SQL Server, user accounts
- disabled startup state [SQL Server]
- user accounts [SQL Server], users
- Local Service account [SQL Server]
- SQL Server Installation Wizard
- instance-unaware services [SQL Server]
- services [SQL Server], configuring at installation
- Windows accounts [SQL Server]
- SQL Server services, user accounts
- user accounts [SQL Server], services
- MSSQLServer
- identifying instance-aware services [SQL Server]
- services [SQL Server], accounts
- access control lists
- optional accounts [SQL Server]
- service accounts [SQL Server]
- accounts [SQL Server], services
- built-in system accounts [SQL Server]
- automatic startup state
- domains [SQL Server]
- manual startup state [SQL Server]
- accounts [SQL Server], user
ms.assetid: 309b9dac-0b3a-4617-85ef-c4519ce9d014
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f74d26366e0c7c586f466b8fd227cd78ba8ab598
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83269409"
---
# <a name="configure-windows-service-accounts-and-permissions"></a>Konfigurieren von Windows-Dienstkonten und -Berechtigungen
  Jeder Dienst in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt einen Prozess oder eine Gruppe von Prozessen zum Verwalten der Authentifizierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Vorgängen mit Windows dar. In diesem Thema werden die Standardkonfiguration von Diensten in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]und die Konfigurationsoptionen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste beschrieben, die Sie während und nach der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation festlegen können.  
  
##  <a name="contents"></a><a name="Top"></a> Inhalt  
 Dieses Thema ist in folgende Abschnitte unterteilt:  
  
-   [Durch SQL Server installierte Dienste](#Service_Details)  
  
-   [Dienst Eigenschaften und-Konfiguration](#Serv_Prop)  
  
    -   [Standarddienstkonten](#Default_Accts)  
  
        -   [Ändern von Konto Eigenschaften](#Changing_Accounts)  
  
    -   [In Windows 7 und Windows Server 2008 R2 verfügbare neue Kontotypen](#New_Accounts)  
  
    -   [Automatischer Start](#Auto_Start)  
  
    -   [Konfigurieren von Diensten während der unbeaufsichtigten Installation](#Configure_services)  
  
    -   [Firewallport](#Firewall)  
  
-   [Dienst Berechtigungen](#Serv_Perm)  
  
    -   [Dienstkonfiguration und Zugriffssteuerung](#Serv_SID)  
  
    -   [Windows-Berechtigungen und Rechte](#Windows)  
  
    -   [SQL Server pro-Dienst-SIDs oder lokalen Windows-Gruppen gewährte Datei System Berechtigungen](#Reviewing_ACLs)  
  
    -   [Anderen Windows-Benutzerkonten oder -Gruppen gewährte Dateisystemberechtigung](#File_System_Other)  
  
    -   [Auf ungewöhnliche Speicherorte auf einem Datenträger bezogene Dateisystemberechtigungen](#Unusual_Locations)  
  
    -   [Überprüfen zusätzlicher Aspekte](#Review_additional_considerations)  
  
    -   [Registrierungsberechtigungen](#Registry)  
  
    -   [WMI](#WMI)  
  
    -   [Named Pipes](#Pipes)  
  
-   [Bereitstellung](#Provisioning)  
  
    -   [Bereitstellung der Datenbank-Engine](#DE_Prov)  
  
        -   [Windows-Prinzipale](#Win_Principals)  
  
        -   [sa-Konto](#sa)  
  
        -   [Pro-Dienst-SID-Anmeldung für SQL Server und Berechtigungen](#Logins)  
  
        -   [SQL Server-Agent-Anmeldung und Berechtigungen](#Agent)  
  
        -   [HADRON- und SQL-Failoverclusterinstanz und Berechtigungen](#Hadron)  
  
        -   [SQL Writer und Berechtigungen](#Writer)  
  
        -   [SQL WMI und Berechtigungen](#SQLWMI)  
  
    -   [SSAS-Bereitstellung](#SSAS)  
  
    -   [SSRS-Bereitstellung](#SSRS)  
  
-   [Aktualisieren von früheren Versionen](#Upgrade)  
  
-   [Gers](#Appendix)  
  
    -   [Beschreibung von Dienstkonten](#Serv_Accts)  
  
    -   [Identifizieren von instanzabhängigen und nicht instanzabhängigen Diensten](#Identify_instance_aware_and_unaware)  
  
    -   [Lokalisierte Dienstnamen](#Localized_service_names)  
  
##  <a name="services-installed-by-ssnoversion"></a><a name="Service_Details"></a> Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Je nach den Komponenten, die Sie installieren möchten, werden beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup die folgenden Dienste installiert:  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankdienste** – Der Dienst für das relationale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]. Die ausführbare Datei ist „\<MSSQLPATH>\MSSQL\Binn\sqlservr.exe“.  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent** – Führt Aufträge aus, überwacht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], löst Warnungen aus und ermöglicht die Automatisierung bestimmter Verwaltungsaufgaben. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ist vorhanden, aber in Instanzen von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]deaktiviert. Die ausführbare Datei ist „\<MSSQLPATH>\MSSQL\Binn\sqlagent.exe“.  
  
-   **[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]**-Bietet OLAP-Funktionen (Online Analytical Processing) und Data Mining Funktionen für Business Intelligence-Anwendungen. Die ausführbare Datei ist „\<MSSQLPATH>\OLAP\Bin\msmdsrv.exe“.  
  
-   **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**-Dient zum Verwalten, ausführen, erstellen, planen und übermittelt von Berichten. Die ausführbare Datei ist „\<MSSQLPATH>\Reporting Services\ReportServer\Bin\ReportingServicesService.exe“.  
  
-   **[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]**: Bietet Verwaltungs Unterstützung für das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Speichern und Ausführen von Paketen. Der Pfad der ausführbaren Datei ist " \< mssqlpath> \120\dz\binn\msdtssrvr.exe".  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser** – Der Namensauflösungsdienst, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungsinformationen für Clientcomputer bereitstellt. Der Pfad der ausführbaren Datei lautet „c:\Programme (x86)\Microsoft SQL Server\90\Shared\sqlbrowser.exe“.  
  
-   **Volltextsuche** – Erstellt schnell Volltextindizes für den Inhalt und die Eigenschaften von strukturierten und semistrukturierten Daten, um eine Dokumentfilterung und Wörtertrennung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu bereitzustellen.  
  
-   **SQL Writer** – Ermöglicht das Ausführen von Sicherungs- und Wiederherstellungsanwendungen im Framework des Volumeschattenkopie-Diensts (Volume Shadow Copy Service; VSS).  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Controller** – Stellt eine koordinierte Wiedergabe der Ablaufverfolgung auf mehreren Distributed Replay-Clientcomputern bereit.  
  
-   **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Client** – Mindestens ein Distributed Replay-Clientcomputer, der mit einem Distributed Replay-Controller zusammenarbeitet, um gleichzeitige Arbeitsauslastungen für eine [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz zu simulieren.  
  
##  <a name="service-properties-and-configuration"></a><a name="Serv_Prop"></a> Diensteigenschaften und -konfiguration  
 Als Startkonten zum Starten und Ausführen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können [Domänenbenutzerkonten](#Domain_User), [lokale Benutzerkonten](#Local_User), [verwaltete Dienstkonten](#MSA), [virtuelle Konten](#VA_Desc)oder [integrierte Systemkonten](#Local_Service)verwendet werden. Zum Starten und Ausführen muss für jeden Dienst in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während der Installation ein Startkonto konfiguriert werden.  
  
 In diesem Abschnitt werden die Konten beschrieben, die zum Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten konfiguriert werden können. Des Weiteren werden die beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup verwendeten Standardwerte, das Konzept der Pro-Dienst-SIDs, die Startoptionen und die Konfiguration der Firewall erläutert.  
  
-   [Standarddienstkonten](#Default_Accts)  
  
-   [Automatischer Start](#Auto_Start)  
  
-   [Konfigurieren des Starttyps für den Dienst](#Configure_services)  
  
-   [Firewallport](#Firewall)  
  
###  <a name="default-service-accounts"></a><a name="Default_Accts"></a> Standarddienstkonten  
 Die folgende Tabelle enthält die beim Setup bei der Installation aller Komponenten verwendeten Standarddienstkonten. Die aufgeführten Standardkonten sind die empfohlenen Konten, sofern nicht anders angegeben.  
  
 **Eigenständiger Server oder Domänencontroller**  
  
|Komponente|[!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]|Windows 7 und [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2 oder höher|  
|---------------|------------------------------------|----------------------------------------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)<sup>*</sup>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc) <sup>*</sup>|  
|[!INCLUDE[ssAS](../../includes/ssas-md.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc) <sup>*</sup>|  
|[!INCLUDE[ssIS](../../includes/ssis-md.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc) <sup>*</sup>|  
|[!INCLUDE[ssRS](../../includes/ssrs.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)<sup>*</sup>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)<sup>*</sup>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)<sup>*</sup>|  
|FD-Startprogramm (Volltextsuche)|[LOKALER DIENST](#Local_Service)|[Virtuelles Konto](#VA_Desc)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser|[LOKALER DIENST](#Local_Service)|[LOKALER DIENST](#Local_Service)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer|[LOKALES SYSTEM](#Local_System)|[LOKALES SYSTEM](#Local_System)|  
  
 <sup>*</sup>Wenn Ressourcen außerhalb des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computers benötigt werden, [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt die Verwendung eines verwalteten Dienst Kontos (Managed Service Account, MSA), das mit den erforderlichen Mindestberechtigungen konfiguriert ist.  
  
 **SQL Server-Failoverclusterinstanz**  
  
|Komponente|[!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]|[!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2|  
|---------------|------------------------------------|---------------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)]|Keine. Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent|Keine. Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|  
|[!INCLUDE[ssAS](../../includes/ssas-md.md)]|Keine. Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|Geben Sie ein [Domänenbenutzerkonto](#Domain_User) an.|  
|[!INCLUDE[ssIS](../../includes/ssis-md.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)|  
|[!INCLUDE[ssRS](../../includes/ssrs.md)]|[NETZWERKDIENST](#Network_Service)|[Virtuelles Konto](#VA_Desc)|  
|FD-Startprogramm (Volltextsuche)|[LOKALER DIENST](#Local_Service)|[Virtuelles Konto](#VA_Desc)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser|[LOKALER DIENST](#Local_Service)|[LOKALER DIENST](#Local_Service)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer|[LOKALES SYSTEM](#Local_System)|[LOKALES SYSTEM](#Local_System)|  
  
####  <a name="changing-account-properties"></a><a name="Changing_Accounts"></a> Ändern von Kontoeigenschaften  
  
> [!IMPORTANT]
>  -   Verwenden Sie immer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools, z. B. den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um das von den [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] - oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensten verwendete Konto oder das Kennwort für das Konto zu ändern. Zusätzlich zum Ändern des Kontonamens können Sie mithilfe vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager weitere Konfigurationen vornehmen wie z. B. das Update der lokalen Windows-Sicherheitsspeicherung, die den Diensthauptschlüssel für [!INCLUDE[ssDE](../../includes/ssde-md.md)]schützt. Mit anderen Tools, z. B. dem Windows-Dienstkontroll-Manager, kann der Kontoname geändert werden, es können jedoch nicht alle erforderlichen Einstellungen vorgenommen werden.  
> -   Verwenden Sie für in einer SharePoint-Farm bereitgestellte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen immer die SharePoint-Zentraladministration, um die Serverkonten für [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] -Anwendungen und [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]zu ändern. Bei Verwendung der Zentraladministration werden zugehörige Einstellungen und Berechtigungen für die Verwendung der neuen Kontoinformationen aktualisiert.  
> -   Verwenden Sie zum Ändern der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Optionen das Reporting Services-Konfigurationstool.  
  
###  <a name="new-account-types-available-with-windows-7-and-windows-server-2008-r2"></a><a name="New_Accounts"></a>In Windows 7 und Windows Server 2008 R2 verfügbare neue Konto Typen  
 In Windows 7 und Windows Server 2008 R2 sind zwei neue Dienstkontotypen verfügbar: verwaltete Dienstkonten (MSA) und virtuelle Konten. Verwaltete Dienstkonten und virtuelle Konten sollen für wichtige Anwendungen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ihre eigenen Konten zur Verfügung stellen, sodass ein Administrator den Dienstprinzipalnamen (Service Principal Name, SPN) und die Anmeldedaten für diese Konten nicht mehr manuell verwalten muss. Diese Konten vereinfachen erheblich die langfristige Verwaltung von Dienstkontobenutzern, Kennwörtern und SPNs.  
  
-   <a name="MSA"></a> **Verwaltete Dienstkonten**  
  
     Bei einem verwalteten Dienstkonto (MSA) handelt es sich um eine vom Domänencontroller erstellte und verwaltete Art von Domänenkonto. Es wird einem Computer mit einem Mitglied für die Ausführung eines Diensts zugewiesen. Das Kennwort wird automatisch vom Domänencontroller verwaltet. Sie können sich nicht mithilfe eines MSA an einem Computer anmelden, aber ein Computer kann mithilfe eines MSA einen Windows-Dienst starten. Ein MSA kann Dienstprinzipalnamen (SPN) bei Active Directory registrieren. Ein MSA wird mit einem **$** -Suffix bezeichnet, z.B. **DOMÄNE\KONTONAME$** . Wenn Sie ein MSA angeben, lassen Sie das Kennwort leer. Da ein MSA einem einzelnen Computer zugewiesen ist, kann es nicht für verschiedene Knoten eines Windows-Clusters verwendet werden.  
  
    > [!NOTE]  
    >  Das MSA muss in Active Directory vom Domänenadministrator erstellt werden, bevor es beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste verwendet werden kann.  
    
-  <a name="GMSA"></a> **Gruppenverwaltete Dienstkonten**  
  
     Ein gruppenverwaltetes Dienstkonto ist ein MSA für mehrere Server. Windows verwaltet ein Dienstkonto für Dienste, die auf einer Gruppe von Servern ausgeführt werden. Active Directory aktualisiert das Kennwort des gruppenverwalteten Dienstkontos automatisch, ohne Dienste neu zu starten. Sie können SQL Server Services für die Verwendung eines Gruppen verwalteten Dienst Konto Prinzipals konfigurieren. Ab SQL Server 2014 unterstützt SQL Server Gruppen verwaltete Dienst Konten für eigenständige Instanzen.  
  
    Sie benötigen Windows Server 2012 R2 oder höher als Betriebssystem, um ein gruppenverwaltetes Dienstkonto für SQL Server 2014 oder höher zu verwenden. Server mit Windows Server 2012 R2 erfordern [KB 2998082](https://support.microsoft.com/kb/2998082) , damit die Dienste sich ohne Unterbrechung nach einer Änderung des Kennworts direkt anmelden können.  
  
    Weitere Informationen finden Sie unter [Gruppenverwaltete Dienstkonten: Übersicht](https://technet.microsoft.com/library/hh831782.aspx).  
      
    > [!NOTE]  
    >  Das gruppenverwaltete Dienstkonto muss im Active Directory vom Domänenadministrator erstellt werden, bevor es beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste verwendet werden kann. 
  
-   <a name="VA_Desc"></a>**Virtuelle Konten**  
  
     Bei virtuellen Konten (beginnend mit Windows Server 2008 R2 und Windows 7) handelt es sich um *verwaltete lokale Konten* , die die folgenden Funktionen zur Vereinfachung der Dienstverwaltung bereitstellen. Das virtuelle Konto wird automatisch verwaltet und kann auf das Netzwerk in einer Domänenumgebung zugreifen. Wenn während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setups der Standardwert für die Dienstkonten verwendet wird, wird ein virtuelles Konto mit dem Instanznamen als Dienstnamen im Format **NT-DIENST\\** _\<DIENSTNAME>_ verwendet. Als virtuelle Konten ausgeführte Dienste greifen auf Netzwerkressourcen mithilfe der Anmeldeinformationen des Computerkontos im Format _<Domänenname>_ **\\** _<Computername>_ **$** zu.  Wenn Sie zum Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein virtuelles Konto angeben, lassen Sie das Kennwort leer. Wenn das virtuelle Konto den Dienstprinzipalnamen (SPN) nicht registriert, registrieren Sie den SPN manuell. Weitere Informationen zum manuellen Registrieren eines SPNs finden Sie unter [Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](register-a-service-principal-name-for-kerberos-connections.md#Manual).  
  
    > [!NOTE]  
    >  Virtuelle Konten können nicht für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz verwendet werden, da das virtuelle Konto nicht dieselbe SID auf allen Knoten des Clusters besäße.  
  
     In der folgenden Tabelle sind Beispiele für virtuelle Kontonamen aufgeführt:  
  
    |Dienst|Name des virtuellen Kontos|  
    |-------------|--------------------------|  
    |Standardinstanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensts|**NT SERVICE\MSSQLSERVER**|  
    |Benannte Instanz eines [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensts mit dem Namen **PAYROLL**|**NT SERVICE\MSSQL$PAYROLL**|  
    |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf der Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|**NT SERVICE\SQLSERVERAGENT**|  
    |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Namen **PAYROLL**|**NT SERVICE\SQLAGENT$PAYROLL**|  
  
 Weitere Informationen zu verwalteten Dienstkonten und virtuellen Konten finden Sie im Abschnitt **Managed service account and virtual account concepts** (Konzepte verwalteter Dienstkonten und virtueller Konten) in der [Service Accounts Step-by-Step Guide](https://technet.microsoft.com/library/dd548356\(WS.10\).aspx) (Schritt-für-Schritt-Anleitung für Dienstkonten) und den [Managed Service Accounts Frequently Asked Questions (FAQ)](https://technet.microsoft.com/library/ff641729\(WS.10\).aspx)(Häufig gestellten Fragen (FAQ) zu verwalteten Dienstkonten).  
  
 **Sicherheitshinweis:** [!INCLUDE[ssNoteLowRights](../../includes/ssnotelowrights-md.md)] Verwenden Sie möglichst ein [verwaltetes Dienstkonto](#MSA) oder ein [virtuelles Konto](#VA_Desc). Wenn die Verwendung von verwalteten Dienstkonten und virtuellen Konten nicht möglich ist, verwenden Sie ein bestimmtes Benutzerkonto oder Domänenkonto mit niedrigen Berechtigungen anstelle eines freigegebenen Kontos für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste. Verwenden Sie separate Konten für andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste. Gewähren Sie dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto oder den Dienstgruppen keine zusätzlichen Berechtigungen. Berechtigungen werden durch Gruppenmitgliedschaft oder direkt für eine Dienst-SID gewährt, sofern eine Dienst-SID unterstützt wird.  
  
###  <a name="automatic-startup"></a><a name="Auto_Start"></a>Automatischer Start  
 Neben Benutzerkonten verfügt jeder Dienst über drei mögliche Startstatuswerte, die von den Benutzern gesteuert werden können:  
  
-   **Deaktiviert** Der Dienst ist installiert, wird jedoch zurzeit nicht ausgeführt.  
  
-   **Manuell** – Der Dienst ist installiert, wird jedoch nur gestartet, wenn ein anderer Dienst oder eine andere Anwendung seine Funktionalität benötigt.  
  
-   **Automatisch** Der Dienst wird vom Betriebssystem automatisch gestartet.  
  
 Der Startstatus wird während des Setups ausgewählt. Beim installieren einer benannten Instanz sollte für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst der automatische Start festgelegt werden.  
  
###  <a name="configuring-services-during-unattended-installation"></a><a name="Configure_services"></a>Konfigurieren von Diensten während der unbeaufsichtigten Installation  
 In der folgenden Tabelle sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste dargestellt, die während der Installation konfiguriert werden können. Für unbeaufsichtigte Installationen können Sie die Schalter in einer Konfigurationsdatei oder an einer Eingabeaufforderung verwenden.  
  
|Name des SQL Server-Diensts|Switches für unbeaufsichtigte Installationen<sup>1</sup>|  
|-----------------------------|-------------------------------------------------------|  
|MSSQLSERVER|SQLSVCACCOUNT, SQLSVCPASSWORD, SQLSVCSTARTUPTYPE|  
|SQLServerAgent<sup>2</sup>|AGTSVCACCOUNT, AGTSVCPASSWORD, AGTSVCSTARTUPTYPE|  
|MSSQLServerOLAPService|ASSVCACCOUNT, ASSVCPASSWORD, ASSVCSTARTUPTYPE|  
|ReportServer|RSSVCACCOUNT, RSSVCPASSWORD, RSSVCSTARTUPTYPE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|ISSVCACCOUNT, ISSVCPASSWORD, ISSVCSTARTUPTYPE|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller|DRU_CTLR, CTLRSVCACCOUNT, CTLRSVCPASSWORD, CTLRSTARTUPTYPE, CTLRUSERS|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client|DRU_CLT, CLTSVCACCOUNT, CLTSVCPASSWORD, CLTSTARTUPTYPE, CLTCTLRNAME, CLTWORKINGDIR, CLTRESULTDIR|  
  
 <sup>1</sup> Weitere Informationen und eine Beispiel Syntax für unbeaufsichtigte Installationen finden Sie unter [Installieren von SQL Server 2014 von der Eingabeaufforderung](../install-windows/install-sql-server-from-the-command-prompt.md).  
  
 <sup>2</sup> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ist auf Instanzen von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] und [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] mit Advanced Services deaktiviert.  
  
###  <a name="firewall-port"></a><a name="Firewall"></a> Firewallport  
 Bei der Erstinstallation kann in den meisten Fällen mithilfe von Tools wie [!INCLUDE[ssDE](../../includes/ssde-md.md)] , die auf demselben Computer wie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] installiert sind, eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt werden. Vom[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup werden keine Ports in der Windows-Firewall geöffnet. Verbindungen von anderen Computern sind möglicherweise nicht möglich, bis [!INCLUDE[ssDE](../../includes/ssde-md.md)] für das Warten auf einen TCP-Port konfiguriert und der entsprechende Port in der Windows-Firewall für Verbindungen geöffnet wird. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="service-permissions"></a><a name="Serv_Perm"></a> Dienstberechtigungen  
 In diesem Abschnitt werden die Berechtigungen beschrieben, die beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup für die Pro-Dienst-SIDs der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste konfiguriert werden.  
  
-   [Dienstkonfiguration und Zugriffssteuerung](#Serv_SID)  
  
-   [Windows-Berechtigungen und Rechte](#Windows)  
  
-   [Pro-Dienst-SIDs für SQL Server oder lokalen Windows-Gruppen gewährte Dateisystemberechtigungen](#Reviewing_ACLs)  
  
-   [Anderen Windows-Benutzerkonten oder -Gruppen gewährte Dateisystemberechtigungen](#File_System_Other)  
  
-   [Auf ungewöhnliche Speicherorte auf einem Datenträger bezogene Dateisystemberechtigungen](#Unusual_Locations)  
  
-   [Überprüfen zusätzlicher Aspekte](#Review_additional_considerations)  
  
-   [Registrierungsberechtigungen](#Registry)  
  
-   [WMI](#WMI)  
  
-   [Named Pipes](#Pipes)  
  
###  <a name="service-configuration-and-access-control"></a><a name="Serv_SID"></a> Dienstkonfiguration und Zugriffssteuerung  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktiviert die Pro-Dienst-SID für alle seine Dienste, um Dienstisolierung und tiefgreifende Vorbeugungsmaßnahmen zu ermöglichen. Die Pro-Dienst-SID ergibt sich aus dem Dienstnamen und ist für diesen Dienst eindeutig. Ein möglicher Dienst-SID-Name für den [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Dienst wäre **NT Service\MSSQL$** _\<Instanzname>_ . Die Dienstisolierung ermöglicht den Zugriff auf bestimmte Objekte, ohne dass hierzu ein Konto mit umfangreichen Berechtigungen verwendet oder die Sicherheit des Objekts gefährdet werden muss. Durch die Verwendung eines Zugriffssteuerungseintrags mit einer Dienst-SID kann ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst den Zugriff auf die eigenen Ressourcen einschränken.  
  
> [!NOTE]  
>  Unter Windows 7 und [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2 (und höher) kann die Pro-Dienst-SID das virtuelle vom Dienst verwendete Konto sein.  
  
 Für die meisten Komponenten wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die ACL direkt für das Pro-Dienst-Konto konfiguriert, sodass das Dienstkonto geändert werden kann, ohne den Prozess für Ressourcen-ACLs zu wiederholen.  
  
 Bei der Installation von [!INCLUDE[ssAS](../../includes/ssas-md.md)]wird eine Pro-Dienst-SID für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienst erstellt. Eine lokale Windows-Gruppe wird im Format **SQLServerMSASBenutzer$** _Computername_ **$** _Instanzname_erstellt. Der Pro-Dienst-SID **NT SERVICE\MSSQLServerOLAPService** wird die Mitgliedschaft in der lokalen Windows-Gruppe gewährt, und die lokale Windows-Gruppe erhält die entsprechenden Berechtigungen in der ACL. Wird das für das Starten des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Diensts verwendete Konto geändert, müssen vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager einige Windows-Berechtigungen (wie das Recht zum Anmelden als Dienst) geändert werden. Die der lokalen Windows-Gruppe zugewiesenen Berechtigungen stehen ohne Update weiterhin zur Verfügung, da die Pro-Dienst-SID nicht verändert wurde. Diese Methode ermöglicht die Umbenennung des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Diensts während der Upgrades.  
  
 Während der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup lokale Windows-Gruppen für den [!INCLUDE[ssAS](../../includes/ssas-md.md)] - und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser-Dienst erstellt. Für diese Dienste wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die ACL für die lokalen Windows-Gruppen konfiguriert.  
  
 Je nach Dienstkonfiguration wird das Dienstkonto für einen Dienst oder eine Dienst-SID während der Installation oder eines Upgrades als Element der Dienstgruppe hinzugefügt.  
  
###  <a name="windows-privileges-and-rights"></a><a name="Windows"></a> Windows-Berechtigungen und Rechte  
 Für das zum Starten eines Diensts zugewiesene Konto ist die **Berechtigung zum Starten, Beenden und Anhalten** für den Dienst erforderlich. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupprogramm weist diese automatisch zu.  Installieren Sie zuerst Remoteserver-Verwaltungstools (Remote Server Administration Tools, RSAT). Siehe [Remoteserver-Verwaltungstools für Windows 7](https://www.microsoft.com/download/details.aspx?id=7887).  
  
 Die folgende Tabelle enthält Berechtigungen, die beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten verwendeten Pro-Dienst-SIDs oder lokalen Windows-Gruppen erforderlich sind.  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst|Vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup gewährte Berechtigungen|  
|---------------------------------------|------------------------------------------------------------|  
|**[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]:**<br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz: **NT SERVICE\MSSQLSERVER**. Benannte Instanz: **NT SERVICE\MSSQL$** Instanzname.)|**Als Dienst anmelden** (SeServiceLogonRight)<br /><br /> **Token auf Prozessebene ersetzen** (SeAssignPrimaryTokenPrivilege)<br /><br /> **Traversierungsüberprüfung umgehen** (SeChangeNotifyPrivilege)<br /><br /> **Speicherkontingente für einen Prozess anpassen** (SeIncreaseQuotaPrivilege)<br /><br /> Berechtigung zum Starten von SQL Writer<br /><br /> Berechtigung zum Lesen des Ereignisprotokolldiensts<br /><br /> Berechtigung zum Lesen des Remoteprozeduraufruf-Diensts|  
|** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:** <sup>1</sup><br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz: **NT Service\SQLSERVERAGENT**. Benannte Instanz: **NT Service\SQLAGENT$** _Instanzname_.)|**Als Dienst anmelden** (SeServiceLogonRight)<br /><br /> **Token auf Prozessebene ersetzen** (SeAssignPrimaryTokenPrivilege)<br /><br /> **Traversierungsüberprüfung umgehen** (SeChangeNotifyPrivilege)<br /><br /> **Speicherkontingente für einen Prozess anpassen** (SeIncreaseQuotaPrivilege)|  
|**[!INCLUDE[ssAS](../../includes/ssas-md.md)]:**<br /><br /> (Einer lokalen Windows-Gruppe werden alle Rechte gewährt. Standardinstanz: **SQLServerMSASUser$** _Computername_ **$MSSQLSERVER**. Benannte Instanz: **SQLServerMSASUser$** _Computername_ **$** _Instanzname_. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Instanz: **SQLServerMSASUser$** _Computername_ **$** _PowerPivot_.)|**Als Dienst anmelden** (SeServiceLogonRight)<br /><br /> Nur für tabellarisch:<br /><br /> **Arbeitssatz eines Prozesses vergrößern** (SeIncreaseWorkingSetPrivilege)<br /><br /> **Speicherkontingente für einen Prozess anpassen** (SeIncreaseQuotaSizePrivilege)<br /><br /> **Sperren von Seiten im Speicher** (SeLockMemoryPrivilege): Dies ist nur erforderlich, wenn die Auslagerung vollständig ausgeschaltet wird.<br /><br /> Nur für Failoverclusterinstallationen:<br /><br /> **Anheben der Zeitplanungspriorität** (SeIncreaseBasePriorityPrivilege)|  
|**[!INCLUDE[ssRS](../../includes/ssrs.md)]:**<br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz: **NT SERVICE\ReportServer**. Benannte Instanz: **NT- \\ $ Dienst**_instanceName_.)|**Als Dienst anmelden** (SeServiceLogonRight)|  
|**[!INCLUDE[ssIS](../../includes/ssis-md.md)]:**<br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz und benannte Instanz: **NT SERVICE\MsDtsServer120**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verfügt über keinen separaten Prozess für eine benannte Instanz.)|**Als Dienst anmelden** (SeServiceLogonRight)<br /><br /> Berechtigung zum Schreiben in das Anwendungsereignisprotokoll<br /><br /> **Traversierungsüberprüfung umgehen** (SeChangeNotifyPrivilege)<br /><br /> **Annehmen der Clientidentität nach Authentifizierung** (SeImpersonatePrivilege)|  
|**Volltextsuche:**<br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz: **NT Service\MSSQLFDLauncher**. Benannte Instanz: **NT Service\ MSSQLFDLauncher$** _Instanzname_.)|**Als Dienst anmelden** (SeServiceLogonRight)<br /><br /> **Speicherkontingente für einen Prozess anpassen** (SeIncreaseQuotaPrivilege)<br /><br /> **Traversierungsüberprüfung umgehen** (SeChangeNotifyPrivilege)|  
|**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser:**<br /><br /> (Einer lokalen Windows-Gruppe werden alle Rechte gewährt. Standardinstanz oder benannte Instanz: **SQLServer2005SQLBrowserUser** _$Computername_. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser verfügt über keinen separaten Prozess für eine benannte Instanz.)|**Als Dienst anmelden** (SeServiceLogonRight)|  
|**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer:**<br /><br /> (Der Pro-Dienst-SID werden alle Rechte gewährt. Standardinstanz oder benannte Instanz: **NT Service\SQLWriter**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer verfügt über keinen separaten Prozess für eine benannte Instanz.)|Der SQLWriter-Dienst wird unter dem lokalen Systemkonto ausgeführt, das über alle erforderlichen Berechtigungen verfügt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup überprüft oder erteilt keine Berechtigungen für diesen Dienst.|  
|**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller:**|**Als Dienst anmelden** (SeServiceLogonRight)|  
|**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client:**|**Als Dienst anmelden** (SeServiceLogonRight)|  
  
 <sup>1</sup> Der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst ist auf Instanzen von deaktiviert [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
###  <a name="file-system-permissions-granted-to-sql-server-per-service-sids-or-local-windows-groups"></a><a name="Reviewing_ACLs"></a> Pro-Dienst-SIDs für SQL Server oder lokalen Windows-Gruppen gewährte Dateisystemberechtigungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonten müssen über einen Zugriff auf Ressourcen verfügen. Zugriffssteuerungslisten (Access Control Lists, ACLs) werden für die Pro-Dienst-SID oder die lokale Windows-Gruppe festgelegt.  
  
> [!IMPORTANT]  
>  Für Failovercluster-Installationen müssen Ressourcen für freigegebene Datenträger auf eine Zugriffssteuerungsliste für ein lokales Konto festgelegt werden.  
  
 In der folgenden Tabelle werden die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup festgelegten Zugriffssteuerungslisten aufgeführt.  
  
|Dienstkonto für|Dateien und Ordner|Zugriff|  
|-------------------------|-----------------------|------------|  
|MSSQLServer|Instid\MSSQL\backup|Vollzugriff|  
||Instid\MSSQL\binn|Lesen, Ausführen|  
||Instid\MSSQL\data|Vollzugriff|  
||Instid\MSSQL\FTData|Vollzugriff|  
||Instid\MSSQL\Install|Lesen, Ausführen|  
||Instid\MSSQL\Log|Vollzugriff|  
||Instid\MSSQL\Repldata|Vollzugriff|  
||120\shared|Lesen, Ausführen|  
||Instid\MSSQL\Template-Daten (nur[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] )|Lesen|  
|SQLServerAgent<sup>1</sup>|Instid\MSSQL\binn|Vollzugriff|  
||Instid\MSSQL\binn|Vollzugriff|  
||Instid\MSSQL\Log|Lesen, Schreiben, Löschen, Ausführen|  
||120\com|Lesen, Ausführen|  
||120\shared|Lesen, Ausführen|  
||120\shared\Errordumps|Lesen, Schreiben|  
||ServerName\EventLog|Vollzugriff|  
|FTS|Instid\MSSQL\FTData|Vollzugriff|  
||Instid\MSSQL\FTRef|Lesen, Ausführen|  
||120\shared|Lesen, Ausführen|  
||120\shared\Errordumps|Lesen, Schreiben|  
||Instid\MSSQL\Install|Lesen, Ausführen|  
||Instid\MSSQL\jobs|Lesen, Schreiben|  
|MSSQLServerOLAPService|120\shared\ASConfig|Vollzugriff|  
||Instid\OLAP|Lesen, Ausführen|  
||Instid\Olap\Data|Vollzugriff|  
||Instid\Olap\Log|Lesen, Schreiben|  
||Instid\OLAP\Backup|Lesen, Schreiben|  
||Instid\OLAP\Temp|Lesen, Schreiben|  
||120\shared\Errordumps|Lesen, Schreiben|  
|ReportServer|Instid\Reporting Services\Log Files|Lesen, Schreiben, Löschen|  
||Instid\Reporting Services\ReportServer|Lesen, Ausführen|  
||Instid\Reporting Services\ReportServer\global.asax|Vollzugriff|  
||Instid\Reporting Services\ReportServer\rsreportserver.config|Lesen|  
||Instid\Reporting Services\reportManager|Lesen, Ausführen|  
||Instid\Reporting Services\RSTempfiles|Lesen, Schreiben, Ausführen, Löschen|  
||120\shared|Lesen, Ausführen|  
||120\shared\Errordumps|Lesen, Schreiben|  
|MSDTSServer100|120\dts\binn\MsDtsSrvr.ini.xml|Lesen|  
||120\dts\binn|Lesen, Ausführen|  
||120\shared|Lesen, Ausführen|  
||120\shared\Errordumps|Lesen, Schreiben|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser|120\shared\ASConfig|Lesen|  
||120\shared|Lesen, Ausführen|  
||120\shared\Errordumps|Lesen, Schreiben|  
|SQLWriter|N/V (wird als lokales System ausgeführt)||  
|Benutzer|Instid\MSSQL\binn|Lesen, Ausführen|  
||Instid\Reporting Services\ReportServer|Lesen, Ausführen, Ordnerinhalt auflisten|  
||Instid\Reporting Services\ReportServer\global.asax|Lesen|  
||Instid\Reporting Services\reportManager|Lesen, Ausführen|  
||Instid\Reporting Services\ReportManager\pages|Lesen|  
||Instid\Reporting Services\ReportManager\Styles|Lesen|  
||120\dts|Lesen, Ausführen|  
||120\tools|Lesen, Ausführen|  
||100\tools|Lesen, Ausführen|  
||90\tools|Lesen, Ausführen|  
||80\tools|Lesen, Ausführen|  
||120\sdk|Lesen|  
||Microsoft SQL Server\120\Setup Bootstrap|Lesen, Ausführen|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller|\<ToolsDir>\DReplayController\Log\ (leeres Verzeichnis)|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\DReplayController.exe|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\resources\|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\\{alle DLLs}|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\DReplayController.config|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\IRTemplate.tdf|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayController\IRDefinition.xml|Lesen, Ausführen, Ordnerinhalt auflisten|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client|\<ToolsDir>\DReplayClient\Log\|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\DReplayClient.exe|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\resources\|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\ (alle DLLs)|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\DReplayClient.config|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\IRTemplate.tdf|Lesen, Ausführen, Ordnerinhalt auflisten|  
||\<ToolsDir>\DReplayClient\IRDefinition.xml|Lesen, Ausführen, Ordnerinhalt auflisten|  
  
 <sup>1</sup> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ist auf Instanzen von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] und [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] mit Advanced Services deaktiviert.  
  
 Wenn Datenbankdateien an einem benutzerdefinierten Ort gespeichert werden, muss Pro-Dienst-SID-Zugriff auf diesen Ort gewährt sein. Weitere Informationen zum Gewähren von Dateisystemberechtigungen an einen pro-Dienst-SID finden Sie unter [Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff](configure-file-system-permissions-for-database-engine-access.md).  
  
###  <a name="file-system-permissions-granted-to-other-windows-user-accounts-or-groups"></a><a name="File_System_Other"></a> Anderen Windows-Benutzerkonten oder -Gruppen gewährte Dateisystemberechtigungen  
 Einige Zugriffssteuerungsberechtigungen müssen u. U. für integrierte Konten oder andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonten erteilt werden. In der folgenden Tabelle werden weitere vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup festgelegte Zugriffssteuerungslisten aufgeführt.  
  
|Anfordernde Komponente|Konto|Resource|Berechtigungen|  
|--------------------------|-------------|--------------|-----------------|  
|MSSQLServer|Leistungsprotokollbenutzer|Instid\MSSQL\binn|Ordnerinhalt auflisten|  
||Systemmonitorbenutzer|Instid\MSSQL\binn|Ordnerinhalt auflisten|  
||Leistungsprotokollbenutzer, Systemmonitorbenutzer|\WINNT\system32\sqlctr120.dll|Lesen, Ausführen|  
||Nur Administrator|\\\\.\root\microsoft\sqlserver\serverevents \\<sql_instance_name><sup>1</sup>|Vollzugriff|  
||Administratoren, System|\tools\binn\schemas\sqlserver\2004\07\showplan|Vollzugriff|  
||Benutzer|\tools\binn\schemas\sqlserver\2004\07\showplan|Lesen, Ausführen|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Berichtsserverkonto des Windows-Diensts|*\<Installationsverzeichnis>* \Reporting Services\LogFiles|Delete<br /><br /> READ_CONTROL<br /><br /> SYNCHRONIZE<br /><br /> FILE_GENERIC_READ<br /><br /> FILE_GENERIC_WRITE<br /><br /> FILE_READ_DATA<br /><br /> FILE_WRITE_DATA<br /><br /> FILE_APPEND_DATA<br /><br /> FILE_READ_EA<br /><br /> FILE_WRITE_EA<br /><br /> FILE_READ_ATTRIBUTES<br /><br /> FILE_WRITE_ATTRIBUTES|  
||Berichts Server-Windows-Dienst Konto, jeder|* \< Installieren Sie>* \Reporting Services\ReportManager, * \< Installieren Sie>* \Reporting services\reportmanager\pages \\ \* . \* , * \< install>* \Reporting services\reportmanager\styles \\ \* . \* , * \< install>* \Reporting Services\ReportManager\ webctrl_client \ 1_0 \\ *.\*|Lesen, Ausführen|  
||Berichtsserverkonto des Windows-Diensts|*\<Installationsverzeichnis>* \Reporting Services\ReportServer|Lesen|  
||Berichtsserverkonto des Windows-Diensts|*\<Installationsverzeichnis>* \Reporting Services\ReportServer\global.asax|Vollständig|  
||Jeder|*\<Installationsverzeichnis>* \Reporting Services\ReportServer\global.asax|READ_CONTROL<br /><br /> FILE_READ_DATA<br /><br /> FILE_READ_EA<br /><br /> FILE_READ_ATTRIBUTES|  
||Konto für Berichts Server-Windows-Dienste|*\<install>* \Reporting Services\ReportServer\rsreportserver.config|Delete<br /><br /> READ_CONTROL<br /><br /> SYNCHRONIZE<br /><br /> FILE_GENERIC_READ<br /><br /> FILE_GENERIC_WRITE<br /><br /> FILE_READ_DATA<br /><br /> FILE_WRITE_DATA<br /><br /> FILE_APPEND_DATA<br /><br /> FILE_READ_EA<br /><br /> FILE_WRITE_EA<br /><br /> FILE_READ_ATTRIBUTES<br /><br /> FILE_WRITE_ATTRIBUTES|  
||Jeder|Berichtsserverschlüssel (Instid-Struktur)|Wert abfragen<br /><br /> Unterschlüssel auflisten<br /><br /> Benachrichtigen<br /><br /> Lesezugriff|  
||Terminaldienstebenutzer|Berichtsserverschlüssel (Instid-Struktur)|Wert abfragen<br /><br /> Wert festlegen<br /><br /> Unterschlüssel erstellen<br /><br /> Unterschlüssel auflisten<br /><br /> Benachrichtigen<br /><br /> Löschen<br /><br /> Lesezugriff|  
||Hauptbenutzer|Berichtsserverschlüssel (Instid-Struktur)|Wert abfragen<br /><br /> Wert festlegen<br /><br /> Unterschlüssel erstellen<br /><br /> Unterschlüssel auflisten<br /><br /> Benachrichtigen<br /><br /> Löschen<br /><br /> Lesezugriff|  
  
 <sup>1</sup> Dies ist der Namespace des WMI-Anbieters.  
  
###  <a name="file-system-permissions-related-to-unusual-disk-locations"></a><a name="Unusual_Locations"></a> Auf ungewöhnliche Speicherorte auf einem Datenträger bezogene Dateisystemberechtigungen  
 Das Standardlaufwerk für Speicherorte zur Installation von tempdb-Datenbanken oder Benutzerdatenbanken ist **systemdrive**, normalerweise das Laufwerk C.  
  
 **Nicht standardmäßiges Laufwerk**  
  
 Bei der Installation auf einem lokalen Laufwerk, bei dem es sich nicht um das Standardlaufwerk handelt, muss die Pro-Dienst-SID Zugriff auf den Speicherort besitzen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup stellt den erforderlichen Zugriff bereit.  
  
 **Netzwerkfreigabe**  
  
 Wenn Datenbanken in einer Netzwerkfreigabe installiert werden, muss das Dienstkonto Zugriff auf den Dateispeicherort der Benutzer- und tempdb-Datenbanken haben. Das[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup kann keinen Zugriff auf eine Netzwerkfreigabe bereitstellen. Der Benutzer muss vor dem Ausführen des Setups Zugriff auf einen tempdb-Speicherort für das Dienstkonto bereitstellen. Der Benutzer muss vor dem Erstellen der Datenbank Zugriff auf den Speicherort der Benutzerdatenbank bereitstellen.  
  
> [!NOTE]  
>  Virtuelle Konten können nicht gegenüber einem Remotestandort authentifiziert werden. Alle virtuellen Konten verwenden die Berechtigung des Computerkontos. Geben Sie das Computerkonto im Format _<Domänenname>_ **\\** _<Computername>_ **$** an.  
  
###  <a name="reviewing-additional-considerations"></a><a name="Review_additional_considerations"></a> Überprüfen zusätzlicher Aspekte  
 In der folgenden Tabelle werden die Berechtigungen angezeigt, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste erforderlich sind, damit sie zusätzliche Funktionen bereitstellen:  
  
|Dienst/Anwendung|Funktionalität|Erforderliche Berechtigung|  
|--------------------------|-------------------|-------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)|Schreiben in einen Mailslot mithilfe von xp_sendmail.|Netzwerkschreibberechtigungen.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)|Ausführen von xp_cmdshell für einen Benutzer, der kein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administrator ist.|Einsetzen als Teil des Betriebssystems und Ersetzen von Token auf Prozessebene.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent (MSSQLSERVER)|Verwenden der Funktion für den automatischen Neustart.|Muss ein Mitglied der lokalen Gruppe Administratoren sein.|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber|Optimiert Datenbanken für eine optimale Abfrageleistung.|Bei der ersten Verwendung muss ein Benutzer mit Anmeldeinformationen als Systemadministrator die Anwendung initialisieren. Nach der Initialisierung können dbo-Benutzer mithilfe des Optimierungsratgebers für [!INCLUDE[ssDE](../../includes/ssde-md.md)] nur diejenigen Tabellen optimieren, die sie besitzen. Weitere Informationen finden Sie unter "Initialisieren des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgebers" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.|  
  
> [!IMPORTANT]  
>  Aktivieren Sie vor dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Upgrade die Windows-Authentifizierung für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, und überprüfen Sie die erforderliche Standardkonfiguration: Das Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts muss Mitglied der sysadmin-Gruppe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sein.  
  
###  <a name="registry-permissions"></a><a name="Registry"></a> Registrierungsberechtigungen  
 Die Registrierungsstruktur für instanzabhängige Komponenten wird unter **HKLM\Software\Microsoft\Microsoft SQL Server\\** _<Instanz-ID>_ erstellt. Beispiel:  
  
-   **HKLM\Software\Microsoft\Microsoft SQL Server\MSSQL12.MyInstance**  
  
-   **HKLM\Software\Microsoft\Microsoft SQL Server\MSASSQL12.MyInstance**  
  
-   **HKLM\Software\Microsoft\Microsoft SQL Server\MSSQL.120**  
  
 Die Registrierung verwaltet auch eine Zuordnung der Instanz-ID zum Instanznamen. Die Zuordnung der Instanz-ID zum Instanznamen wird folgendermaßen verwaltet:  
  
-   **[HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\Instance Names\SQL] "InstanceName"="MSSQL12"**  
  
-   **[HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\Instance Names\OLAP] "InstanceName"="MSASSQL12"**  
  
-   **[HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft SQL Server\Instance Names\RS] "InstanceName"="MSRSSQL12"**  
  
###  <a name="wmi"></a><a name="WMI"></a> WMI  
 Windows-Verwaltungsinstrumentation (WMI) muss eine Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]herstellen können. Dazu wird die Pro-Dienst-SID des Windows-WMI-Anbieters (**NT SERVICE\winmgmt**) in [!INCLUDE[ssDE](../../includes/ssde-md.md)]bereitgestellt.  
  
 Der SQL-WMI-Anbieter erfordert die folgenden Berechtigungen:  
  
-   Mitgliedschaft in der festen Datenbankrolle **db_ddladmin** oder **db_owner** in der msdb-Datenbank  
  
-   **CREATE DDL EVENT NOTIFICATION** -Berechtigung auf dem Server  
  
-   **CREATE TRACE EVENT NOTIFICATION** -Berechtigung für [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   **VIEW ANY DATABASE** -Berechtigung auf Serverebene  
  
     Das[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup erstellt einen SQL-WMI-Namespace und gewährt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst-SID die Leseberechtigung.  
  
###  <a name="named-pipes"></a><a name="Pipes"></a> Named Pipes  
 Bei allen Installationen stellt das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup über das Shared Memory-Protokoll Zugriff auf [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bereit. Dabei handelt es sich um eine Named Pipe.  
  
##  <a name="provisioning"></a><a name="Provisioning"></a> Bereitstellung  
 In diesem Abschnitt wird beschrieben, wie Konten in den verschiedenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten bereitgestellt werden.  
  
-   [Bereitstellung der Datenbank-Engine](#DE_Prov)  
  
    -   [Windows-Prinzipale](#Win_Principals)  
  
    -   [sa-Konto](#sa)  
  
    -   [Pro-Dienst-SID-Anmeldung für SQL Server und Berechtigungen](#Logins)  
  
    -   [SQL Server-Agent-Anmeldung und Berechtigungen](#Agent)  
  
    -   [HADRON- und SQL-Failoverclusterinstanz und Berechtigungen](#Hadron)  
  
    -   [SQL Writer und Berechtigungen](#Writer)  
  
    -   [SQL WMI und Berechtigungen](#SQLWMI)  
  
-   [SSAS-Bereitstellung](#SSAS)  
  
-   [SSRS-Bereitstellung](#SSRS)  
  
###  <a name="database-engine-provisioning"></a><a name="DE_Prov"></a> Bereitstellung des Datenbankmoduls  
 Die folgenden Konten werden als Anmeldungen in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]hinzugefügt.  
  
####  <a name="windows-principals"></a><a name="Win_Principals"></a> Windows-Prinzipale  
 Während des Setups wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup mindestens ein Benutzerkonto gefordert, das als Mitglied der festen Serverrolle **sysadmin** genannt werden soll.  
  
####  <a name="sa-account"></a><a name="sa"></a> sa-Konto  
 Das **sa** -Konto ist immer als [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Anmeldung vorhanden und ist Mitglied der festen Serverrolle **sysadmin** . Wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] nur mit der Windows-Authentifizierung installiert wird, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung also nicht aktiviert ist, ist die **sa** -Anmeldung zwar vorhanden, aber deaktiviert. Weitere Informationen zum Aktivieren des **sa** -Kontos finden Sie unter [Ändern des Serverauthentifizierungsmodus](change-server-authentication-mode.md).  
  
####  <a name="sql-server-per-service-sid-login-and-privileges"></a><a name="Logins"></a> Pro-Dienst-SID-Anmeldung für SQL Server und Berechtigungen  
 Die Pro-Dienst-SID des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensts wird als [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Anmeldung bereitgestellt. Die Pro-Dienst-SID-Anmeldung ist Mitglied der festen Serverrolle **sysadmin** .  
  
####  <a name="sql-server-agent-login-and-privileges"></a><a name="Agent"></a> SQL Server-Agent-Anmeldung und Berechtigungen  
 Die Pro-Dienst-SID des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts wird als [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Anmeldung bereitgestellt. Die Pro-Dienst-SID-Anmeldung ist Mitglied der festen Serverrolle **sysadmin** .  
  
####  <a name="sshadrc-and-sql-failover-cluster-instance-and-privileges"></a><a name="Hadron"></a> [!INCLUDE[ssHADRc](../../includes/sshadrc-md.md)]- und SQL-Failoverclusterinstanz und -Berechtigungen  
 Bei der Installation des [!INCLUDE[ssDE](../../includes/ssde-md.md)] s als [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] - oder SQL-Failoverclusterinstanz (SQL FCI), wird **LOCAL SYSTEM** im [!INCLUDE[ssDE](../../includes/ssde-md.md)]bereitgestellt. Die **LOCAL SYSTEM** -Anmeldung erhält die Berechtigungen **ALTER ANY AVAILABILITY GROUP** (für [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]) und die **VIEW SERVER STATE** (für SQL FCI).  
  
####  <a name="sql-writer-and-privileges"></a><a name="Writer"></a> SQL Writer und Berechtigungen  
 Die Pro-Dienst-SID des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VSS Writer-Diensts wird als [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Anmeldung bereitgestellt. Die Pro-Dienst-SID-Anmeldung ist Mitglied der festen Serverrolle **sysadmin** .  
  
####  <a name="sql-wmi-and-privileges"></a><a name="SQLWMI"></a> SQL WMI und Berechtigungen  
 Das[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup stellt das Konto **NT SERVICE\Winmgmt** als [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Anmeldung bereit und fügt es der festen Serverrolle **sysadmin** hinzu.  
  
#### <a name="ssrs-provisioning"></a>SSRS-Bereitstellung  
 Das während des Setups angegebene Konto wird als Mitglied der Datenbankrolle **RSExecRole** bereitgestellt. Weitere Informationen finden Sie unter [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
###  <a name="ssas-provisioning"></a><a name="SSAS"></a> SSAS-Bereitstellung  
 [!INCLUDE[ssAS](../../includes/ssas-md.md)] -Dienstkontoanforderungen unterscheiden sich je nach Bereitstellung des Servers. Bei der Installation von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]fordert das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup die Konfiguration des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Diensts zur Ausführung unter einem Domänenkonto. Domänenkonten sind erforderlich, um die in SharePoint integrierte Funktion für verwaltete Konten zu unterstützen. Aus diesem Grund wird beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup kein Standarddienstkonto, z. B. ein virtuelles Konto, für die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation bereitgestellt. Weitere Informationen zur Bereitstellung von PowerPivot für SharePoint, finden Sie unter [Konfigurieren von Power Pivot-Dienstkonten](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts).  
  
 Für alle anderen eigenständigen [!INCLUDE[ssAS](../../includes/ssas-md.md)] -Installationen können Sie den Dienst zur Ausführung unter einem Domänenkonto, integriertem Systemkonto, verwaltetem Konto oder virtuellem Konto bereitstellen. Weitere Informationen zur Bereitstellung von Konten finden Sie unter [Konfigurieren von Dienstkonten &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/instances/configure-service-accounts-analysis-services).  
  
 Für gruppierte Installationen müssen Sie ein Domänenkonto oder integriertes Systemkonto angeben. Weder verwaltete noch virtuelle Konten werden für [!INCLUDE[ssAS](../../includes/ssas-md.md)] -Failovercluster unterstützt.  
  
 Für alle [!INCLUDE[ssAS](../../includes/ssas-md.md)] -Installationen ist die Angabe eines Systemadministrators der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz erforderlich. Administratorberechtigungen werden in der Analysis Services-Rolle **Server** bereitgestellt.  
  
###  <a name="ssrs-provisioning"></a><a name="SSRS"></a> SSRS-Bereitstellung  
 Das während des Setups angegebene Konto wird in [!INCLUDE[ssDE](../../includes/ssde-md.md)] als Mitglied der Datenbankrolle **RSExecRole** bereitgestellt. Weitere Informationen finden Sie unter [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
##  <a name="upgrading-from-previous-versions"></a><a name="Upgrade"></a> Aktualisieren von früheren Versionen  
 In diesem Abschnitt werden die während eines Upgrades von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vorgenommenen Änderungen beschrieben.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erfordert [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2 SP1, Windows Server 2012, Windows 8.0, Windows Server 2012 R2 oder Windows 8.1. Bei jeder früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die unter einer niedrigeren Betriebssystemversion ausgeführt wird, muss zunächst das Betriebssystem aktualisiert werden, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wird.  
  
-   Während des Upgrades von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup folgendermaßen konfiguriert:  
  
    -   [!INCLUDE[ssDE](../../includes/ssde-md.md)] wird mit dem Sicherheitskontext der Pro-Dienst-SID ausgeführt. Der Pro-Dienst-SID wird Zugriff auf die Dateiordner der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz (z. B. DATA) und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Registrierungsschlüssel gewährt.  
  
    -   Die Pro-Dienst-SID vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] wird im [!INCLUDE[ssDE](../../includes/ssde-md.md)] als Mitglied der festen Serverrolle **sysadmin** bereitgestellt.  
  
    -   Der Pro-Dienst-SID wird zu den lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Windows-Gruppen hinzugefügt, es sei denn, bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] handelt es sich um eine Failoverclusterinstanz.  
  
    -   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressourcen werden weiterhin in den lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Windows-Gruppen bereitgestellt.  
  
    -   Die lokale Windows-Gruppe für Dienste wird von **SQLServer2005MSSQLUser$** _<Computername>_ **$** _<Instanzname>_ in **SQLServerMSSQLUser$** _<Computername>_ **$** _<Instanzname>_ umbenannt. Die Dateipfade für migrierte Datenbanken besitzen Zugriffssteuerungseinträge (Access Control Entries, ACE) für die lokalen Windows-Gruppen. Die Dateipfade für neue Datenbanken besitzen ACEs für die Pro-Dienst-SID.  
  
-   Während des Upgrades von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] werden beim [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup die ACEs für die Pro-Dienst-SID von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] beibehalten.  
  
-   Für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstanz wird der für den Dienst konfigurierte ACE für das Domänenkonto beibehalten.  
  
##  <a name="appendix"></a><a name="Appendix"></a> Anhang  
 Dieser Abschnitt enthält weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten.  
  
-   [Beschreibung von Dienstkonten](#Serv_Accts)  
  
-   [Identifizieren von instanzabhängigen und nicht instanzabhängigen Diensten](#Identify_instance_aware_and_unaware)  
  
-   [Lokalisierte Dienstnamen](#Localized_service_names)  
  
###  <a name="description-of-service-accounts"></a><a name="Serv_Accts"></a> Beschreibung von Dienstkonten  
 Beim Dienstkonto handelt es sich um das Konto, das für das Starten eines Windows-Dienst verwendet wird, wie z. B. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
####  <a name="accounts-available-with-any-operating-system"></a><a name="Any_OS"></a> Mit einem beliebigen Betriebssystem verfügbare Konten  
 Neben den zuvor beschriebenen neuen [MSAs](#MSA) und [virtuellen Konten](#VA_Desc) können folgende Konten verwendet werden:  
  
 <a name="Domain_User"></a> **Domänenbenutzerkonto**  
  
 Wenn der Dienst mit Netzwerkdiensten interagieren und auf Domänenressourcen wie Dateifreigaben zugreifen muss oder verknüpfte Serververbindungen mit anderen Computern mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet, kann ein Domänenkonto mit minimalen Rechten verwendet werden. Viele Server-zu-Server-Aktivitäten können nur mit einem Domänenbenutzerkonto ausgeführt werden. Dieses Konto sollte in Ihrer Umgebung von der Domänenverwaltung vorab erstellt werden.  
  
> [!NOTE]  
>  Wenn Sie die Anwendung zur Verwendung eines Domänenkontos konfigurieren, können Sie zwar die Berechtigungen für die Anwendung isolieren, müssen aber Kennwörter manuell verwalten oder eine benutzerdefinierte Lösung für die Verwaltung dieser Kennwörter erstellen. Viele Serveranwendungen erhöhen die Sicherheit mithilfe dieser Strategie, aber diese Strategie erfordert zusätzliche Verwaltung und Komplexität. Bei diesem Bereitstellungen wenden Dienstadministratoren viel Zeit für Wartungstasks wie die Verwaltung von Dienstkennwörtern und Dienstprinzipalnamen (SPNs) auf, die für die Kerberos-Authentifizierung erforderlich sind. Außerdem können diese Wartungstasks den Dienst stören.  
  
 <a name="Local_User"></a> **Lokale Benutzerkonten**  
  
 Wenn der Computer nicht Teil einer Domäne ist, empfiehlt sich ein lokales Benutzerkonto ohne die Berechtigungen eines Windows-Administrators.  
  
 <a name="Local_Service"></a> **Lokales Dienstkonto**  
  
 Das lokale Dienstkonto ist ein integriertes Konto, das dieselben Zugriffsrechte für Ressourcen und Objekte besitzt wie die Mitglieder der Gruppe Benutzer. Durch diesen beschränkten Zugriff wird das System bei Gefährdung einzelner Dienste oder Prozesse geschützt. Dienste, die unter dem lokalen Dienstkonto ausgeführt werden, greifen als NULL-Sitzung ohne Anmeldeinformationen auf Netzwerkressourcen zu. Beachten Sie, dass das lokale Dienstkonto nicht für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unterstützt wird. Der lokale Dienst wird nicht als das Konto unterstützt, unter dem diese Dienste ausgeführt werden, da es sich um einen freigegebenen Dienst handelt und alle anderen Dienste, die unter dem lokalen Dienst ausgeführt werden, Systemadministratorzugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hätten. Der tatsächliche Name des Kontos lautet **NT AUTHORITY\LOCAL SERVICE**.  
  
 <a name="Network_Service"></a> **Netzwerkdienstkonto**  
  
 Das Netzwerkdienstkonto ist ein integriertes Konto, das mehr Zugriffsrechte für Ressourcen und Objekte besitzt als die Mitglieder der Gruppe „Benutzer“. Dienste, die unter dem Netzwerkdienstkonto ausgeführt werden, greifen mithilfe der Anmeldeinformationen des Computerkontos im Format _<Domänenname>_ **\\** _<Computername>_ **$** auf Netzwerkressourcen zu. Der tatsächliche Name des Kontos lautet **NT AUTHORITY\NETWORK SERVICE**.  
  
 <a name="Local_System"></a> **Lokales Systemkonto**  
  
 Das lokale Systemkonto ist ein integriertes Konto mit sehr hohen Privilegien. Es besitzt umfangreiche Berechtigungen auf dem lokalen System und repräsentiert den Computer im Netzwerk. Der tatsächliche Name des Kontos lautet **NT AUTHORITY\SYSTEM**.  
  
###  <a name="identifying-instance-aware-and-instance-unaware-services"></a><a name="Identify_instance_aware_and_unaware"></a> Identifizieren von instanzabhängigen und nicht instanzabhängigen Diensten  
 Instanzabhängige Dienste werden mit einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verknüpft und haben eine eigene Registrierungsstruktur. Sie können mehrere Kopien von instanzabhängigen Diensten installieren, indem Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup für die einzelnen Komponenten oder Dienste ausführen. Nicht instanzabhängige Dienste werden für alle installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen freigegeben. Sie sind nicht mit einer bestimmten Instanz verknüpft, werden nur einmal installiert und können nicht parallel installiert werden.  
  
 Instanzabhängige Dienste in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfassen Folgendes:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
     Beachten Sie, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf Instanzen von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] und [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services deaktiviert ist.  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <sup>1</sup>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Volltextsuche  
  
 Nicht instanzabhängige Dienste in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfassen Folgendes:  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser  
  
-   SQL Writer  
  
 <sup>1</sup> Analysis Services im integrierten SharePoint-Modus wird als einzelne, benannte Instanz als ' Power Pivot ' ausgeführt. Der Instanzname ist unveränderlich. Sie können keinen anderen Namen angeben. Sie können nur eine Instanz von Analysis Services installieren, die auf jedem physischen Server als 'PowerPivot' ausgeführt wird.  
  
###  <a name="localized-service-names"></a><a name="Localized_service_names"></a> Lokalisierte Dienstnamen  
 In der folgenden Tabelle werden Dienstnamen aufgeführt, die in lokalisierten Versionen von Windows angezeigt werden.  
  
|Sprache|Name für lokalen Dienst|Name für Netzwerkdienst|Name für lokales System|Name für Administratorgruppe|  
|--------------|----------------------------|------------------------------|---------------------------|--------------------------|  
|Englisch<br /><br /> Chinesisch (vereinfacht)<br /><br /> Chinesisch (traditionell)<br /><br /> Koreanisch<br /><br /> Japanisch|NT AUTHORITY\LOCAL SERVICE|NT AUTHORITY\NETWORK SERVICE|NT AUTHORITY\SYSTEM|BUILTIN\Administrators|  
|Deutsch|NT-AUTORITÄT\LOKALER DIENST|NT-AUTORITÄT\NETZWERKDIENST|NT-AUTORITÄT\SYSTEM|VORDEFINIERT\Administratoren|  
|Französisch|AUTORITE NT\SERVICE LOCAL|AUTORITE NT\SERVICE RÉSEAU|AUTORITE NT\SYSTEM|BUILTIN\Administrators|  
|Italienisch|NT AUTHORITY\SERVIZIO LOCALE|NT AUTHORITY\SERVIZIO DI RETE|NT AUTHORITY\SYSTEM|BUILTIN\Administrators|  
|Spanisch|NT AUTHORITY\SERVICIO LOC|NT AUTHORITY\SERVICIO DE RED|NT AUTHORITY\SYSTEM|BUILTIN\Administradores|  
|Russisch|NT AUTHORITY\LOCAL SERVICE|NT AUTHORITY\NETWORK SERVICE|NT AUTHORITY\SYSTEM|BUILTIN\Администраторы|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
 [Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
 [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
