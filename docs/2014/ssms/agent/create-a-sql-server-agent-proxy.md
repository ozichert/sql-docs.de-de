---
title: Erstellen eines Proxys für den SQL Server-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfaba668e4f2328610656db6a61f01960814bff0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68189506"
---
# <a name="create-a-sql-server-agent-proxy"></a>Erstellen eines Proxys für den SQL Server-Agent
  In diesem Thema wird beschrieben, wie SQL Server-Agent-Proxys in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt werden.  
  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxykonto definiert einen Sicherheitskontext, in dem ein Auftragsschritt ausgeführt werden kann. Jeder Proxy entspricht einem Satz Sicherheitsanmeldeinformationen. Um Berechtigungen für einen bestimmten Auftragsschritt festzulegen, erstellen Sie ein Proxykonto mit den erforderlichen Berechtigungen für ein Subsystem des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents und weisen dann dieses Proxykonto dem Auftragsschritt zu.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie einen Proxy für den SQL Server-Agent mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie müssen, falls keine Anmeldeinformationen vorhanden sind, Anmeldeinformationen erstellen, bevor Sie ein Proxykonto erstellen.  
  
-   Von[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Proxys werden Anmeldeinformationen zum Speichern von Informationen zu Windows-Benutzerkonten verwendet. Der in der Anmeldeinformation angegebene Benutzer muss über eine Berechtigung des Typs "Anmelden als Stapelverarbeitungsauftrag" auf dem Computer verfügen, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird der Subsystemzugriff für einen Proxy überprüft und der Zugriff auf den Proxy jedes Mal dann gewährt, wenn der Auftragsschritt ausgeführt wird. Wenn der Proxyzugriff auf das Subsystem nicht mehr länger möglich ist, erzeugt der Auftragsschritt einen Fehler. Ansonsten wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die Identität des Benutzers angenommen, der im Proxy angegeben ist und von dem der Auftragsschritt ausgeführt wird.  
  
-   Die Berechtigungen für den Benutzer werden nicht durch das Erstellen eines Proxys geändert, der in den Anmeldeinformationen für den Proxy angegeben ist. Sie können beispielsweise einen Proxy für einen Benutzer erstellen, der keine Verbindungsberechtigung für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hat. In diesem Fall kann von Auftragsschritten, die diesen Proxy verwenden, keine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt werden.  
  
-   Wenn die Anmeldung für den Benutzer Zugriffsrecht auf den Proxy hat, oder der Benutzer zu einer Rolle mit Zugriffsrechten auf den Proxy gehört, kann der Benutzer den Proxy in einem Auftragsschritt verwenden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
  
-   Nur Mitglieder der festen Serverrolle **sysadmin** haben die Berechtigung zum Erstellen, Ändern oder Löschen von Proxykonten. Benutzer, die nicht Mitglieder der festen Serverrolle **sysadmin** sind, müssen zur Verwendung von Proxys einer der folgenden festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents in der **msdb** -Datenbank hinzugefügt werden: **SQLAgentUserRole**, **SQLAgentReaderRole**oder **SQLAgentOperatorRole**.  
  
-   Erfordert die `ALTER ANY CREDENTIAL`-Berechtigung, wenn für den Proxy zusätzlich eine Anmeldeinformation erstellt wird.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>So erstellen Sie einen Proxy für den SQL Server-Agent  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, auf dem Sie ein Proxy auf dem SQL Server-Agent erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Proxys** , und wählen Sie dann **Neuer Proxy**aus.  
  
4.  Geben Sie in das Dialogfeld **Neues Proxykonto** auf der Seite **Allgemein** den Namen des neuen Proxykontos in das Feld **Proxyname** ein.  
  
5.  Geben Sie im Feld **Anmeldeinformationsname** den Namen der Sicherheitsanmeldeinformationen ein, die vom Proxykonto verwendet werden.  
  
6.  Geben Sie im Feld **Beschreibung** eine Beschreibung für das Proxykonto ein.  
  
7.  Wählen Sie unter **Folgenden Subsystemen gegenüber aktiv**das bzw. die entsprechenden Subsysteme für diesen Proxy aus.  
  
8.  Auf der Seite **Prinzipale** können Sie Anmeldenamen oder Rollen hinzufügen oder entfernen, um den Zugriff auf das Proxykonto zu erteilen oder zu entziehen.  
  
9. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>So erstellen Sie einen Proxy für den SQL Server-Agent  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter:  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [sp_add_proxy &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [sp_grant_proxy_to_subsystem &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
