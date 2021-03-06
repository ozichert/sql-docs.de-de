---
title: SQL Server Audit (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- audit
helpviewer_keywords:
- SQL Server Audit
- audits [SQL Server], SQL Server Audit
ms.assetid: 0c1fca2e-f22b-4fe8-806f-c87806664f00
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8286c918c224b92e1f391931569030a7218252f1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68198423"
---
# <a name="sql-server-audit-database-engine"></a>SQL Server Audit (Datenbank-Engine)
  Die *Überwachung* einer Instanz von [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] oder einer einzelnen Datenbank umfasst die Nachverfolgung und Protokollierung von Ereignissen, die in [!INCLUDE[ssDE](../../../includes/ssde-md.md)] auftreten. Mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit können Serverüberwachungen erstellt werden, die Serverüberwachungsspezifikationen für Ereignisse auf Serverebene sowie Datenbank-Überwachungsspezifikationen für Ereignisse auf Datenbankebene beinhalten können. Überwachte Ereignisse können in die Ereignisprotokolle oder Überwachungsdateien geschrieben werden.  
  
 Es gibt mehrere Überwachungsebenen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], die von gesetzlichen oder standardspezifischen Anforderungen für die Installation abhängig sind. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit enthält die Tools und Prozesse, die Sie zum Aktivieren, Speichern und Anzeigen von Überwachungen auf verschiedenen Server- und Datenbankobjekten benötigen.  
  
 Bei Servern können Sie Überwachungsaktionsgruppen instanzweise aufzeichnen, bei Datenbanken entweder Überwachungsaktionsgruppen oder Überwachungsaktionen jeweils pro Datenbank. Das Überwachungsereignis tritt jedes Mal auf, wenn die überwachbare Aktion erkannt wird.  
  
 Alle Editionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützen Überwachungen auf Serverebene. Die Überwachung auf Datenbankebene ist auf die Editionen Enterprise, Developer und Evaluation beschränkt. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="sql-server-audit-components"></a>SQL Server Audit-Komponenten  
 Eine *Überwachung* besteht aus mehreren Elementen, die in einem einzelnen Paket für eine bestimmte Gruppe von Server- oder Datenbankaktionen zusammengefasst werden. Die Komponenten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit geben zusammen eine Ausgabe aus, die als Überwachung bezeichnet wird, ebenso wie durch die Kombination von Berichtsdefinitionen mit Grafiken und Datenelementen ein Bericht erstellt wird.  
  
 Die[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung verwendet *erweiterte Ereignisse* , um eine Überwachung zu erstellen. Weitere Informationen zu erweiterten Ereignissen finden Sie unter [Erweiterte Ereignisse](../../extended-events/extended-events.md).  
  
### <a name="sql-server-audit"></a>SQL Server Audit  
 Das *SQL Server Audit* -Objekt erfasst eine einzelne Instanz von Aktionen auf Server-oder Datenbankebene und Gruppen von Aktionen, die überwacht werden sollen. Die Überwachung wird auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanzebene ausgeführt. Es können mehrere Überwachungen pro [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz vorliegen.  
  
 Wenn Sie eine Überwachung definieren, geben Sie den Speicherort für die Ausgabe der Ergebnisse an. Dies ist das Überwachungsziel. Die Überwachung wird in einem *disabled* Zustand erstellt und überwacht Aktionen nicht automatisch. Nachdem die Überwachung aktiviert wurde, empfängt das Überwachungsziel Daten von der Überwachung.  
  
### <a name="server-audit-specification"></a>Serverüberwachungsspezifikation  
 Das *Serverüberwachungsspezifikation* -Objekt gehört zu einer Überwachung. Sie können eine Serverüberwachungsspezifikation pro Überwachung erstellen, da beide im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanzbereich erstellt werden.  
  
 Die Serverüberwachungsspezifikation listet viele Aktionsgruppen auf Serverebene auf, die von erweiterten Ereignissen ausgelöst werden. Sie können *Überwachungsaktionsgruppen* in eine Serverüberwachungsspezifikation einschließen. Überwachungsaktionsgruppen sind vorab definierte Gruppen von Aktionen, bei denen es sich um unteilbare Ereignisse handelt, die in [!INCLUDE[ssDE](../../../includes/ssde-md.md)]stattfinden. Diese Aktionen werden an die Überwachung gesendet, die sie im Ziel aufzeichnet.  
  
 Überwachungsaktionsgruppen auf Datenbankebene und Überwachungsaktionen werden im Thema [SQL Server Audit-Aktionsgruppen und -Aktionen](sql-server-audit-action-groups-and-actions.md)beschrieben.  
  
### <a name="database-audit-specification"></a>Datenbank-Überwachungsspezifikation  
 Das *Datenbank-Überwachungsspezifikation* -Objekt gehört ebenfalls zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit. Sie können eine Datenbank-Überwachungsspezifikation pro [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank und pro Überwachung erstellen.  
  
 Die Datenbank-Überwachungsspezifikation listet viele Überwachungsaktionen auf Datenbankebene auf, die von erweiterten Ereignissen ausgelöst werden. Sie können einer Datenbank-Überwachungsspezifikation Überwachungsaktionsgruppen oder Überwachungsereignisse hinzufügen. *Überwachungsereignisse* sind die unteilbaren Aktionen, die von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Engine überwacht werden können. *Überwachungsaktionsgruppen* sind vorab definierte Aktionsgruppen. Beide befinden sich im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbankbereich. Diese Aktionen werden an die Überwachung gesendet, die sie im Ziel aufzeichnet. Beziehen Sie in einer Benutzerdatenbank-Überwachungsspezifikation keine Objekte mit Serverbereich ein, wie Systemsichten.  
  
 Überwachungsaktionsgruppen auf Datenbankebene und Überwachungsaktionen werden im Thema [SQL Server Audit-Aktionsgruppen und -Aktionen](sql-server-audit-action-groups-and-actions.md)beschrieben.  
  
### <a name="target"></a>Ziel  
 Die Ergebnisse einer Überwachung werden an ein Ziel gesendet, wobei es sich um eine Datei, das Windows-Sicherheitsereignisprotokoll oder das Windows-Anwendungsereignisprotokoll handelt. Protokolle müssen regelmäßig überprüft und archiviert werden, um sicherzustellen, dass das Ziel über ausreichend Platz verfügt, um zusätzliche Datensätze anzulegen.  
  
> [!IMPORTANT]  
>  Jeder authentifizierte Benutzer kann das Windows-Anwendungsereignisprotokoll lesen und Datensätze darin schreiben. Für das Anwendungsereignisprotokoll sind niedrigere Berechtigungen als für das Windows-Sicherheitsereignisprotokoll erforderlich, daher ist es jedoch auch weniger sicher als das Windows-Sicherheitsereignisprotokoll.  
  
 Wenn Sie einen Datensatz im Windows-Sicherheitsprotokoll schreiben möchten, muss das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto der Richtlinie **Generieren von Sicherheitsüberwachungen** hinzugefügt werden. Standardmäßig sind das lokale System, der lokale Dienst und der Netzwerkdienst ein Teil dieser Richtlinie. Diese Einstellung kann mit dem Sicherheitsrichtlinien-Snap-In (secpol.msc) konfiguriert werden. Darüber hinaus muss die Sicherheitsrichtlinie **Objektzugriffsversuche überwachen** sowohl für **Erfolg** als auch für **Fehler**aktiviert sein. Diese Einstellung kann mit dem Sicherheitsrichtlinien-Snap-In (secpol.msc) konfiguriert werden. In [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] oder Windows Server 2008 können Sie die präzisetere Richtlinie zur **Anwendungs Generierung** über die Befehlszeile mit dem Überwachungs Richtlinien Programm (`AuditPol.exe)`) festlegen. Weitere Informationen zu den Schritten zum Aktivieren des Schreibens in das Windows-Sicherheitsprotokoll finden Sie unter [Schreiben von SQL-Serverüberwachungsereignissen in das Sicherheitsprotokoll](write-sql-server-audit-events-to-the-security-log.md). Weitere Informationen über das Programm Auditpol.exe finden Sie im Knowledge Base-Artikel 921469, [How to use Group Policy to configure detailed security auditing](https://support.microsoft.com/kb/921469/)(in englischer Sprache). Die Windows-Ereignisprotokolle gelten global für das Windows-Betriebssystem. Weitere Informationen zu den Windows-Ereignisprotokollen finden Sie unter [Ereignisanzeige (Übersicht)](https://go.microsoft.com/fwlink/?LinkId=101455). Wenn Sie präzisere Berechtigungen für die Überwachung benötigen, verwenden Sie das Binärdateiziel.  
  
 Um beim Speichern von Überwachungsinformationen in eine Datei Manipulationen zu verhindern, können Sie den Zugriff auf deren Speicherort auf folgende Weise einschränken:  
  
-   Das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto muss über Lese- und Schreibberechtigungen verfügen.  
  
-   Für Überwachungsadministratoren sind in der Regel Lese- und Schreibberechtigungen erforderlich. Dabei wird angenommen, dass Überwachungsadministratoren Windows-Konten für die Verwaltung von Überwachungsdateien (u. a. das Kopieren der Dateien auf andere Freigaben und das Erstellen von Sicherungen) darstellen.  
  
-   Für das Lesen von Überwachungsdateien autorisierte Überwachungsleser müssen über eine Leseberechtigung verfügen.  
  
 Selbst wenn [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Daten in eine Datei schreibt, können andere Windows-Benutzer mit entsprechender Berechtigung die Überwachungsdatei lesen. [!INCLUDE[ssDE](../../../includes/ssde-md.md)] lässt eine exklusive Sperre, die Lesevorgänge verhindert, nicht zu.  
  
 Da [!INCLUDE[ssDE](../../../includes/ssde-md.md)] auf die Datei zugreifen kann, können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen mit CONTROL SERVER-Berechtigungen über [!INCLUDE[ssDE](../../../includes/ssde-md.md)] auf Überwachungsdateien zugreifen. Um alle Benutzer aufzuzeichnen, die die Überwachungsdatei lesen, definieren Sie eine Überwachung in master.sys.fn_get_audit_file. Dadurch werden die Anmeldenamen von Benutzern mit CONTROL SERVER-Berechtigung aufgezeichnet, die über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]auf die Überwachungsdatei zugegriffen haben.  
  
 Wenn ein Überwachungsadministrator die Datei an einen anderen Ort kopiert (zur Archivierung usw.), sollten die ACLs am neuen Ort auf die folgenden Berechtigungen beschränkt werden:  
  
-   Überwachungsadministrator – Lesen/Schreiben  
  
-   Überwachungsleser – Lesen  
  
 Es wird empfohlen, Überwachungsberichte auf einer separaten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu erstellen, z.B. einer Instanz von [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)], auf die nur Überwachungsadministratoren und -leser Zugriff haben. Durch Verwenden einer separaten Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] zur Berichterstellung können Sie dazu beitragen, unautorisierte Benutzer am Zugriff auf die Überwachungsdatei zu hindern.  
  
 Zusätzlichen Schutz gegen unautorisierten Zugriff erhalten Sie, indem Sie den Ordner mit der Überwachungsdatei mit der Windows-BitLocker-Laufwerksverschlüsselung oder dem verschlüsselnden Dateisystem von Windows verschlüsseln.  
  
 Weitere Informationen zu den Überwachungsdatensätzen, die in das Ziel geschrieben werden, finden Sie unter [SQL Server Audit-Datensätze](sql-server-audit-records.md).  
  
## <a name="overview-of-using-sql-server-audit"></a>Übersicht über die Verwendung von SQL Server Audit  
 Sie können [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)] verwenden, um eine Überwachung zu definieren. Nachdem die Überwachung erstellt und aktiviert wurde, empfängt das Ziel die Einträge.  
  
 Sie können die Windows-Ereignisprotokolle mit dem Windows-Hilfsprogramm **Ereignisanzeige** lesen. Bei Dateizielen können Sie zum Lesen der Zieldatei entweder den **Protokolldatei-Viewer** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder die [fn_get_audit_file](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) -Funktion verwenden.  
  
 Im Allgemeinen wird eine Überwachung folgendermaßen erstellt und verwendet:  
  
1.  Erstellen Sie eine Überwachung, und definieren Sie das Ziel.  
  
2.  Erstellen Sie eine Serverüberwachungsspezifikation oder eine Datenbank-Überwachungsspezifikation, die der Überwachung zugeordnet wird. Aktivieren Sie die Überwachungsspezifikation.  
  
3.  Aktivieren Sie die Überwachung.  
  
4.  Lesen Sie die Überwachungsereignisse mit der Windows- **Ereignisanzeige**, dem **Protokolldatei-Viewer**oder der fn_get_audit_file-Funktion.  
  
 Weitere Informationen zur Überwachung finden Sie unter [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](create-a-server-audit-and-server-audit-specification.md) sowie [Erstellen einer Server- und Datenbank-Überwachungsspezifikation](create-a-server-audit-and-database-audit-specification.md).  
  
## <a name="considerations"></a>Überlegungen  
 Wenn während der Überwachungseinleitung ein Fehler auftritt, wird der Server nicht gestartet. In diesem Fall kann der Server gestartet werden, indem Sie in die Befehlszeile die Option **-f** eingeben.  
  
 Wenn aufgrund eines Überwachungsfehlers der Server heruntergefahren wird oder nicht startet, da für die Überwachung ON_FAILURE=SHUTDOWN festgelegt wurde, wird das Ereignis MSG_AUDIT_FORCED_SHUTDOWN in das Protokoll geschrieben. Da der Server schon beim ersten Auftreten dieser Einstellung heruntergefahren wird, wird das Ereignis nur einmal im Protokoll aufgezeichnet. Das Ereignis wird erst nach der Fehlermeldung für die Überwachung, die das Herunterfahren verursacht, geschrieben. Ein Administrator kann ein durch eine Überwachung verursachtes Herunterfahren umgehen, indem er [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem Flag **-m** im Einzelbenutzermodus startet. Wenn Sie sich im Einzelbenutzermodus anmelden, wird jede Überwachung herabgestuft, für die festgelegt wurde, dass ON_FAILURE=SHUTDOWN in dieser Sitzung als ON_FAILURE=CONTINUE ausgeführt wird. Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem Flag **-m** gestartet wird, wird die Meldung MSG_AUDIT_SHUTDOWN_BYPASSED im Fehlerprotokoll aufgezeichnet.  
  
 Weitere Informationen zu Dienststartoptionen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
### <a name="attaching-a-database-with-an-audit-defined"></a>Anfügen einer Datenbank mit einer definierten Überwachung  
 Wenn Sie eine Datenbank anfügen, für die eine Überwachungsspezifikation festgelegt wurde und die eine GUID bestimmt, die sich nicht auf dem Server befindet, entsteht eine *verwaiste* Überwachungsspezifikation. Da eine Überwachung mit einer entsprechenden GUID nicht auf der Serverinstanz vorliegt, werden keine Überwachungsereignisse aufgezeichnet. Verwenden Sie den Befehl ALTER DATABASE AUDIT SPECIFICATION, um die verwaiste Überwachungsspezifikation mit einer vorhandenen Serverüberwachung zu verbinden und somit den Fehler zu beheben. Oder verwenden Sie den Befehl CREATE SERVER AUDIT, um eine neue Serverüberwachung mit der angegebenen GUID zu erstellen.  
  
 Sie können eine Datenbank, für die eine Überwachungsspezifikation angegeben wurde, an eine andere Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anfügen, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit nicht unterstützt, z. B. [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] . Überwachungsereignisse werden jedoch nicht aufgezeichnet.  
  
### <a name="database-mirroring-and-sql-server-audit"></a>Datenbankspiegelung und SQL Server Audit  
 Eine Datenbank, für die eine Datenbank-Überwachungsspezifikation definiert wurde und für die Datenbankspiegelung verwendet wird, enthält die Datenbank-Überwachungsspezifikation. Die folgenden Elemente müssen konfiguriert werden, damit sie auf der gespiegelten SQL-Instanz ordnungsgemäß arbeitet:  
  
-   Der Spiegelserver muss über eine Überwachung mit der gleichen GUID verfügen, damit die Datenbank-Überwachungsspezifikation Überwachungsdatensätze schreiben kann. Dies kann mit dem Befehl create Audit with GUID`=`*\<GUID from Source Server Audit*> konfiguriert werden.  
  
-   Bei Binärdateizielen muss das Dienstkonto des Spiegelservers über die erforderlichen Berechtigungen für den Speicherort verfügen, an den der Überwachungspfad geschrieben wird.  
  
-   Bei Windows-Ereignisprotokollzielen muss die Sicherheitsrichtlinie für den Computer, auf dem sich der Spiegelserver befindet, den Dienstkontozugriff auf das Sicherheits- oder Anwendungsereignisprotokoll zulassen.  
  
### <a name="auditing-administrators"></a>Überwachen von Administratoren  
 Mitglieder der `sysadmin` Fixed-Server Rolle werden in jeder Datenbank als **dbo** -Benutzer identifiziert. Um die Aktionen der Administratoren zu überwachen, verfolgen Sie also die Aktionen des **dbo** -Benutzers.  
  
## <a name="creating-and-managing-audits-with-transact-sql"></a>Erstellen und Verwalten von Überwachungen mit Transact-SQL  
 Sie können DDL-Anweisungen, dynamische Verwaltungssichten und -funktionen sowie Katalogsichten verwenden, um alle Aspekte von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit zu implementieren.  
  
### <a name="data-definition-language-statements"></a>DDL-Anweisungen (Data Definition Language, Datendefinitionssprache)  
 Sie können die folgenden DDL-Anweisungen zum Erstellen, Ändern und Löschen von Überwachungsspezifikationen verwenden:  
  
|||  
|-|-|  
|[ALTER AUTHORIZATION](/sql/t-sql/statements/alter-authorization-transact-sql)|[CREATE SERVER AUDIT](/sql/t-sql/statements/create-server-audit-transact-sql)|  
|[ALTER DATABASE AUDIT SPECIFICATION](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)|[Create Server Audit Specification](/sql/t-sql/statements/create-server-audit-specification-transact-sql)|  
|[ALTER SERVER AUDIT](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)|[DROP DATABASE AUDIT SPECIFICATION](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)|  
|[ALTER SERVER AUDIT SPECIFICATION](/sql/t-sql/statements/alter-server-audit-transact-sql)|[DROP SERVER AUDIT](/sql/t-sql/statements/drop-server-audit-transact-sql)|  
|[Datenbank-Überwachungs Spezifikation erstellen](/sql/t-sql/statements/create-database-audit-specification-transact-sql)|[DROP SERVER AUDIT SPECIFICATION](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)|  
  
### <a name="dynamic-views-and-functions"></a>Dynamische Sichten und Funktionen  
 In der folgenden Tabelle werden die dynamischen Sichten und Funktion aufgelistet, die Sie für eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung verwenden können.  
  
|Dynamische Sichten und Funktionen|Beschreibung|  
|---------------------------------|-----------------|  
|[sys.dm_audit_actions](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)|Gibt eine Zeile für jede Überwachungsaktion zurück, die im Überwachungsprotokoll festgehalten werden kann, und für jede Überwachungsaktionsgruppe, die als Teil von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit konfiguriert werden kann.|  
|[sys.dm_server_audit_status](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)|Stellt Informationen über den aktuellen Status der Überwachung bereit.|  
|[sys.dm_audit_class_type_map](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)|Gibt eine Tabelle zurück, die das Feld class_type im Überwachungsprotokoll dem Feld class_desc in sys.dm_audit_actions zuordnet.|  
|[fn_get_audit_file](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)|Gibt Informationen von einer Überwachungsdatei zurück, die von einer Serverüberwachung erstellt wurde.|  
  
### <a name="catalog-views"></a>Katalogsichten  
 In der folgenden Tabelle werden die Katalogsichten aufgeführt, die Sie für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung verwenden können.  
  
|Katalogansichten|Beschreibung|  
|-------------------|-----------------|  
|[sys.database_audit_specifications](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)|Enthält Informationen über die Datenbanküberwachungsspezifikationen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz.|  
|[sys.database_audit_specification_details](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)|Enthält Informationen über die Datenbank-Überwachungsspezifikationen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz für alle Datenbanken.|  
|[sys.server_audits](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)|Enthält eine Zeile für jede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung in einer Serverinstanz.|  
|[sys.server_audit_specifications](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)|Enthält Informationen über die Serverüberwachungsspezifikationen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz.|  
|[sys.server_audit_specifications_details](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)|Enthält Informationen über Details der Serverüberwachungsspezifikation (Aktionen) in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz.|  
|[sys.server_file_audits](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)|Enthält erweiterte Informationen über den Dateiüberwachungstyp in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz.|  
  
## <a name="permissions"></a>Berechtigungen  
 Jede Funktion und jeder Befehl für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit hat eigene Berechtigungsanforderungen.  
  
 Um eine Serverüberwachung oder eine Serverüberwachungsspezifikation zu erstellen, zu ändern oder zu löschen, muss für Serverüberwachungsprinzipale die Berechtigung ALTER ANY SERVER AUDIT oder CONTROL SERVER festgelegt werden. Um eine Datenbank-Überwachungsspezifikation zu erstellen, zu ändern oder zu löschen, muss für Datenbankprinzipale die Berechtigung ALTER ANY DATABASE AUDIT, ALTER oder CONTROL in der Datenbank festgelegt werden. Zusätzlich benötigen Prinzipale die Berechtigung zum Herstellen einer Verbindung mit der Datenbank bzw. die Berechtigung ALTER ANY SERVER AUDIT oder CONTROL SERVER.  
  
 Falls nicht anders angegeben, muss ein Prinzipal zum Anzeigen der Katalogsichten über eine der folgenden Berechtigungen verfügen:  
  
-   Mitgliedschaft in der festen Server Rolle sysadmin.  
  
-   Die CONTROL SERVER-Berechtigung  
  
-   Die VIEW SERVER STATE-Berechtigung  
  
-   Die ALTER ANY AUDIT-Berechtigung  
  
-   Die View Audit State-Berechtigung (gewährt nur dem Prinzipal Zugriff auf die Katalog Sicht sys. server_audits).  
  
 Ein Prinzipal muss über die Berechtigung VIEW SERVER STATE oder ALTER ANY AUDIT verfügen, um die dynamischen Verwaltungssichten zu verwenden.  
  
 Weitere Informationen über das Gewähren von Rechten und Berechtigungen finden Sie unter [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
> [!CAUTION]  
>  Prinzipale in der Rolle sysadmin können die Überwachungskomponenten manipulieren; Prinzipale in der Rolle db_owner können Überwachungsspezifikationen in einer Datenbank bearbeiten. Die[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Überwachung überprüft, dass bei der Anmeldung, bei der eine Überwachungsspezifikation erstellt oder geändert wird, mindestens die Berechtigung ALTER ANY DATABASE AUDIT vorliegt. Es wird jedoch keine Überprüfung durchgeführt, wenn Sie eine Datenbank anfügen. Gehen Sie davon aus, dass alle Datenbank-Überwachungsspezifikationen nur so vertrauenswürdig sind wie die Prinzipale in der Rolle sysadmin oder db_owner.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](create-a-server-audit-and-server-audit-specification.md)  
  
 [Erstellen einer Server- und Datenbank-Überwachungsspezifikation](create-a-server-audit-and-database-audit-specification.md)  
  
 [Anzeigen eines SQL Server-Überwachungsprotokolls](view-a-sql-server-audit-log.md)  
  
 [Schreiben von SQL-Serverüberwachungsereignissen in das Sicherheitsprotokoll](write-sql-server-audit-events-to-the-security-log.md)  
  
## <a name="topics-closely-related-to-auditing"></a>Themen zu Überwachung  
 [Servereigenschaften &#40;Seite „Sicherheit“&#41;](../../../database-engine/configure-windows/server-properties-security-page.md)  
 Erklärt, wie die Anmeldeüberwachung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]aktiviert wird. Die Überwachungsdatensätze werden im Windows-Anwendungsprotokoll gespeichert.  
  
 [C2-Überwachungsmodus (Serverkonfigurationsoption)](../../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)  
 Erläutert den C2-Sicherheitskompatibilitäts-Überwachungsmodus in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Sicherheitsüberwachung-Ereigniskategorie &#40;SQL Server Profiler&#41;](../../../relational-databases/event-classes/security-audit-event-category-sql-server-profiler.md)  
 Erklärt die Überwachungsereignisse, die Sie in [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]verwenden können. Weitere Informationen finden Sie unter [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).  
  
 [SQL-Ablaufverfolgung](../../sql-trace/sql-trace.md)  
 Erläutert, wie Sie die SQL-Ablaufverfolgung aus Ihren Anwendungen heraus verwenden können, um Ablaufverfolgungen manuell statt mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Profiler zu erstellen.  
  
 [DDL-Trigger](../../triggers/ddl-triggers.md)  
 Erklärt, wie Sie DDL-Trigger (Data Definition Language) zum Nachverfolgen von Änderungen an den Datenbanken verwenden können.  
  
 [Microsoft TechNet: SQL Server-TechCenter: SQL Server 2005 – Sicherheit und Schutz](https://go.microsoft.com/fwlink/?LinkId=101152)  
 Stellt aktuelle Informationen zur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sicherheit bereit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Überwachungs Aktionsgruppen und-Aktionen](sql-server-audit-action-groups-and-actions.md)   
 [SQL Server Audit-Datensätze](sql-server-audit-records.md)  
  
  
