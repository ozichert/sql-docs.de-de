---
title: Implementieren der SQL Server-Agent-Sicherheit
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2110e84464fae3f71495d40527ca7b189b072005
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242331"
---
# <a name="implement-sql-server-agent-security"></a>Implementieren der SQL Server-Agent-Sicherheit
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ermöglicht dem Datenbankadministrator, jeden Auftragsschritt in einem Sicherheitskontext auszuführen, dem lediglich die Berechtigungen erteilt wurden, die zum Durchführen dieses Auftragsschritts erforderlich sind, wie von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxy festgelegt. Um Berechtigungen für einen bestimmten Auftragsschritt festzulegen, erstellen Sie einen Proxy mit den erforderlichen Berechtigungen und weisen dann diesen Proxy dem Auftragsschritt zu. Ein Proxy kann für mehrere Auftragsschritte angegeben werden. Für Auftragsschritte, für die dieselben Berechtigungen erforderlich sind, verwenden Sie denselben Proxy.  
  
Im folgenden Abschnitt wird erläutert, welche Datenbankrolle Sie Benutzern erteilen müssen, damit sie Aufträge mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents erstellen oder ausführen können.  
  
## <a name="granting-access-to-sql-server-agent"></a>Erteilen des Zugriffs auf den SQL Server-Agent  
Um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zu verwenden, müssen die Benutzer Mitglied mindestens einer der folgenden festen Datenbankrollen sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Diese Rollen werden in der **msdb** -Datenbank gespeichert. Standardmäßig ist kein Benutzer Mitglied dieser Datenbankrollen. Die Mitgliedschaft in diesen Rollen muss explizit erteilt werden. Benutzer, die Mitglieder der festen Serverrolle **sysadmin** sind, haben vollen Zugriff auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und müssen nicht Mitglied dieser festen Datenbankrollen sein, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent verwenden zu können. Wenn ein Benutzer nicht Mitglied einer dieser Datenbankrollen oder der **sysadmin** -Rolle ist, steht ihm der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten nicht zur Verfügung, wenn er mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]herstellt.  
  
Die Mitglieder dieser Datenbankrollen können Aufträge anzeigen und ausführen, deren Besitzer sie sind, und Auftragsschritte erstellen, die als bereits vorhandenes Proxykonto ausgeführt werden. Weitere Informationen zu den einzelnen Berechtigungen, die jeder dieser festen Rollen zugeordnet sind, finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Die Mitglieder der festen Serverrolle **sysadmin** haben die Berechtigung zum Erstellen, Ändern und Löschen von Proxykonten. Die Mitglieder der **sysadmin** -Rolle haben die Berechtigung zum Erstellen von Auftragsschritten, die keinen Proxy angeben, sondern stattdessen als das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto ausgeführt werden, bei dem es sich um das Konto handelt, das zum Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verwendet wird.  
  
## <a name="guidelines"></a>Richtlinien  
Befolgen Sie diese Richtlinien, um die Sicherheit Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Implementierung zu verbessern:  
  
-   Erstellen Sie dedizierte Benutzerkonten speziell für Proxys, und verwenden Sie diese Proxybenutzerkonten nur zum Ausführen von Auftragsschritten.  
  
-   Erteilen Sie die erforderlichen Berechtigungen lediglich den Proxybenutzerkonten. Erteilen Sie lediglich die Berechtigungen, die zum Ausführen der Auftragsschritte erforderlich sind, die einem bestimmten Proxykonto zugewiesen sind.  
  
-   Führen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst nicht unter einem Microsoft Windows-Konto aus, das Mitglied der Windows-Gruppe **Administratoren** ist.  
  
-   Proxys sind nur so sicher wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationenspeicher.  
  
-   Wenn Benutzerschreibvorgänge in das NT-Ereignisprotokoll schreiben können, können sie Warnungen über den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auslösen.  
  
-   Geben Sie das NT-Adminkonto nicht als Dienst- oder Proxykonto an.  
  
-   Hinweis: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent können gegenseitig auf ihre Ressourcen zugreifen. Die beiden Dienste verwenden einen einzelnen Prozessraum, und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent fungiert mit der Rolle "sysadmin" auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst.  
  
-   Wenn für ein TSX ein MSX eingetragen wird, erhält die MSX-Rolle "sysadmins" die vollständige Kontrolle über die TSX-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   ACE ist eine Erweiterung und kann sich nicht selbst aufrufen. ACE wird von der „Chainer ScenarioEngine.exe“ (auch als bekannt als „Microsoft.SqlServer.Chainer.Setup.exe“) oder einem anderen Hostprozess aufgerufen.  
  
-   ACE hängt von den folgenden Konfigurations-DLL-Elementen ab, die sich im Besitz von SSDP befinden, da diese DLL-APIs von ACE aufgerufen werden:  
  
    -   **SCO:** Microsoft.SqlServer.Configuration.Sco.dll, einschließlich neuer SCO-Überprüfungen für virtuelle Konten  
  
    -   **Cluster:** Microsoft.SqlServer.Configuration.Cluster.dll  
  
    -   **SFC:** Microsoft.SqlServer.Configuration.SqlConfigBase.dll  
  
    -   **Erweiterung:** Microsoft.SqlServer.Configuration.ConfigExtension.dll  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwenden vordefinierter Rollen](../../reporting-services/security/role-definitions-predefined-roles.md)  
[sp_addrolemember (Transact-SQL)](https://msdn.microsoft.com/a583c087-bdb3-46d2-b9e5-3921b3e6d10b)  
[sp_droprolemember (Transact-SQL)](https://msdn.microsoft.com/c2f19ab1-e742-4d56-ba8e-8ffd40cf4925)  
[Sicherheit und Schutz (Datenbank-Engine)](https://msdn.microsoft.com/dfb39d16-722a-4734-94bb-98e61e014ee7)  
  
