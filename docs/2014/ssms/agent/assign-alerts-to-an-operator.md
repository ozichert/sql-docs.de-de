---
title: Zuweisen von Warnungen zu einem Operator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 905114d0190a7d1e8441e98249664c985a433988
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62473211"
---
# <a name="assign-alerts-to-an-operator"></a>Assign Alerts to an Operator
  In diesem Thema wird beschrieben, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie-Agent-Warnungen zu Operatoren zugewiesen werden, damit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] diese in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)]von oder Benachrichtigungen über Aufträge empfangen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So weisen Sie einem Operator Warnungen zu mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] kann das gesamte Warnungssystem auf einfache Weise über eine grafische Oberfläche verwaltet werden. Für die Konfiguration einer Warnungsinfrastruktur sollte [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verwendet werden.  
  
-   Zum Senden einer Benachrichtigung als Reaktion auf eine Warnung müssen Sie zunächst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent für das Senden von E-Mail konfigurieren. Weitere Informationen finden Sie unter [configure SQL Server-Agent Mail to use Datenbank-E-Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
-   Wenn beim Senden einer E-Mail- oder Pagerbenachrichtigung ein Fehler auftritt, wird der Fehler im Fehlerprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts aufgezeichnet.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können Operatoren Warnungen zuweisen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-assign-alerts-to-an-operator"></a>So weisen Sie einem Operator Warnungen zu  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, der den Operator enthält, dem Sie die Warnung zuweisen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um den Ordner **Operatoren** zu erweitern.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Operator, dem Sie eine Warnung zuweisen möchten, wählen Sie **Eigenschaften**aus, und wählen Sie die Seite **Benachrichtigungen** aus.  
  
5.  Wählen Sie im Dialogfeld _operator_name_**Eigenschaften** unter **Seite auswählen**die Option **Benachrichtigungen**aus.  
  
6.  Wählen Sie unter **Benachrichtigungen an diesen Benutzer anzeigen von**die Option **Warnung** aus, um eine Liste der Warnungen anzuzeigen, die an diesen Operator gesendet wurden, oder wählen Sie **Aufträge** aus, um eine Liste der Aufträge anzuzeigen, von denen Benachrichtigungen an diesen Operator gesendet werden. Aktivieren Sie mindestens eines der folgenden Kontrollkästchen, um die Benachrichtigungsmethode für jede Benachrichtigung zu definieren: **E-Mail**, **Pager**oder **NET SEND**.  
  
7.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-assign-alerts-to-an-operator"></a>So weisen Sie einem Operator Warnungen zu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_add_notification &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
  
