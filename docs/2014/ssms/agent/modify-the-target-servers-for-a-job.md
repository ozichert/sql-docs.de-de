---
title: Ändern der Zielserver für einen Auftrag | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a97fd3892e74b16c844867f88bc7d72fedc46d20
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62720382"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job
  In diesem Thema wird beschrieben, wie Sie die Ziel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Server für- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Agent- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Aufträge [!INCLUDE[tsql](../../includes/tsql-md.md)]in mithilfe von oder ändern können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Ändern der Zielserver für einen Auftrag mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können Mitglieder der festen Serverrolle „sysadmin“ diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder einer der folgenden festen SQL Server-Agent-Datenbankrollen in der msdb-Datenbank sein:  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  SQLAgentOperatorRole  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>So ändern Sie die Zielserver für einen Auftrag  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, und erweitern Sie dann die Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Auftragseigenschaften** die Seite **Ziele**aus, und klicken Sie auf **Ziel: Lokaler Server**oder auf **Ziel: Mehrere Server**.  
  
     Wenn Sie **Ziel: Mehrere Server**auswählen, geben Sie Server an, die Ziele für den Auftrag sind, indem Sie das Kästchen links neben dem Servernamen aktivieren. Stellen Sie sicher, dass die Kästchen für die Server, die nicht Ziel für den Auftrag sind, deaktiviert sind.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>So ändern Sie die Zielserver für einen Auftrag  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird der Multiserverauftrag „Weekly Sales Backups“ dem Server SEATTLE2 zugewiesen.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 Weitere Informationen finden Sie unter [sp_add_jobserver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)  
  
  
