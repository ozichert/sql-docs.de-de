---
title: Zulassen, dass Nichtadministratoren den Replikationsmonitor verwenden
description: Erfahren Sie, wie Sie Nichtadministratoren den Zugriff auf den Replikationsmonitor in SQL Server Management Studio (SSMS) erteilen.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: f0451d8fcd55cc3d33616452109a5e5ff95081e0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287742"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Zulassen, dass Nichtadministratoren den Replikationsmonitor verwenden
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Nicht-Administratoren ermöglicht wird, den Replikationsmonitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]zu verwenden. Der Replikationsmonitor kann von Benutzern verwendet werden, die Mitglieder der folgenden Rollen sind:  
  
-   Feste Serverrolle **sysadmin** .  
  
     Diese Benutzer können die Replikation überwachen und haben den vollen Zugriff in Bezug auf Änderungen der Replikationseigenschaften, wie beispielsweise Zeitpläne für Agents, Agentprofile usw.  
  
-   Datenbankrolle **replmonitor** in der Verteilungsdatenbank.  
  
     Diese Benutzer können die Replikation überwachen, aber keine Replikationseigenschaften ändern.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So ermöglichen Sie Nichtadministratoren die Verwendung des Replikationsmonitors mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Um zuzulassen, dass Nichtadministratoren den Replikationsmonitor verwenden, muss ein Mitglied der festen Serverrolle **sysadmin** den Benutzer der Verteilungsdatenbank hinzufügen und diesen Benutzer der Rolle **replmonitor** zuweisen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>So lassen Sie zu, dass Nichtadministratoren den Replikationsmonitor verwenden  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie **Datenbanken**und **Systemdatenbanken**, und erweitern Sie die Verteilungsdatenbank (standardmäßig als **distribution** bezeichnet).  
  
3.  Erweitern Sie **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Benutzer**, und klicken Sie dann auf **Neuer Benutzer**.  
  
4.  Geben Sie einen Benutzernamen und ein Kennwort für den Benutzer ein.  
  
5.  Wählen Sie ein Standardschema für **replmonitor**aus.  
  
6.  Aktivieren Sie das Kontrollkästchen **replmonitor** im Raster **Mitglied in Datenbankrollen** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>So fügen Sie der festen Datenbankrolle "replmonitor" einen Benutzer hinzu  
  
1.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_helpuser &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)aus. Wenn der Benutzer nicht unter **UserName** im Resultset aufgeführt wird, muss diesem Benutzer mithilfe der [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)-Anweisung der Zugriff auf die Verteilungsdatenbank erteilt werden.  
  
2.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) unter Angabe des Werts **replmonitor** für den `@rolename`-Parameter aus. Wenn der Benutzer unter **MemberName** im Resultset aufgeführt wird, gehört der Benutzer bereits zu der Rolle.  
  
3.  Wenn der Benutzer nicht zur Rolle **replmonitor** gehört, führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_addrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) aus. Geben Sie einen **replmonitor**-Wert für `@rolename` und den Namen des Datenbankbenutzers oder den Windows-Anmeldenamen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] an, der für `@membername` hinzugefügt wird.  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>So entfernen Sie einen Benutzer aus der festen Datenbankrolle "replmonitor"  
  
1.  Führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) aus, und geben Sie den Wert **replmonitor** für `@rolename` an, um zu überprüfen, ob der Benutzer zur Rolle **replmonitor** gehört. Wenn der Benutzer unter **MemberName** im Resultset nicht aufgeführt wird, gehört der Benutzer aktuell nicht zu der Rolle.  
  
2.  Wenn der Benutzer zur Rolle **replmonitor** gehört, führen Sie auf dem Verteiler für die Verteilungsdatenbank [sp_droprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) aus. Geben Sie einen **replmonitor**-Wert für `@rolename` und den Namen des Datenbankbenutzers oder den Windows-Anmeldenamen an, der für `@membername` entfernt wird. 
  
  
