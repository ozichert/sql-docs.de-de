---
title: Anzeigen und Ändern der Eigenschaften von Pushabonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5dc55cc688f4e40d188492636c3653556f88b1c6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68212017"
---
# <a name="view-and-modify-push-subscription-properties"></a>Anzeigen und Ändern der Eigenschaften von Pushabonnements
  In diesem Thema wird beschrieben, wie die Eigenschaften von Pushabonnements in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) angezeigt und geändert werden.  
  
 **In diesem Thema**  
  
-   **So können Sie Eigenschaften von Pushabonnements anzeigen und ändern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Sie können die Eigenschaften von Pushabonnements vom Verleger an den folgenden Stellen anzeigen und ändern:  
  
-   Im Dialogfeld **Abonnementeigenschaften – \<Verleger>: \<Verlegerdatenbank>** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   Auf der Registerkarte **Alle Abonnements** , verfügbar im Replikationsmonitor. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a>So zeigen Sie Eigenschaften von Pushabonnement in Management Studio an und ändern Sie die Eigenschaften  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Erweitern Sie die entsprechende Veröffentlichung, klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a>So zeigen Sie Eigenschaften von Pushabonnement im Replikationsmonitor an und ändern Sie die Eigenschaften  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Pushabonnements können geändert und auf ihre Eigenschaften kann mithilfe gespeicherter Replikationsprozeduren programmgesteuert zugegriffen werden. Welche gespeicherten Prozeduren verwendet werden, hängt vom Typ der Veröffentlichung ab, zu der das Abonnement gehört.  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften eines Pushabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung an  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)aus. Geben **@publication**Sie **@subscriber**, und den Wert **all** für an **@article**.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)aus, und geben Sie **@subscriber**.  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>So ändern Sie die Eigenschaften eines Pushabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)aus, und geben Sie **@subscriber** sowie Parameter für die zu ändernden Abonnenteneigenschaften an.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)aus. Geben **@publication**Sie **@subscriber**, **@destination_db**,, den Wert **all** für **@article**, die zu ändernde Abonnement Eigenschaft **@property**als und den neuen Wert als **@value**. Dadurch werden die Sicherheitseinstellungen für das Pushabonnement geändert.  
  
3.  (Optional) Um die Paketeigenschaften der Data Transformation Services (Datentransformationsdienste, DTS) zu ändern, führen Sie [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) auf dem Abonnenten für die Abonnementdatenbank aus. Geben Sie die ID des Verteilungs-Agent Auftrags für **@jobid** und die folgenden DTS-Paket Eigenschaften an:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Dadurch werden die DTS-Paketeigenschaften eines Abonnements geändert.  
  
    > [!NOTE]  
    >  Die Auftrag-ID erhalten Sie, wenn Sie [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)ausführen.  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a>So zeigen Sie die Eigenschaften eines Pushabonnements für eine Mergeveröffentlichung an  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)aus. Geben **@publication** Sie **@subscriber**und an.  
  
2.  Führen Sie auf dem Verleger [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)aus, und geben Sie **@subscriber**verfügbar ist.  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a>So ändern Sie die Eigenschaften eines Pushabonnements für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)aus. Geben **@publication**Sie **@subscriber**, **@subscriber_db**,, die zu ändernde Abonnement **@property**Eigenschaft als und den neuen Wert **@value**als.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a>Beispiel (Transact-SQL)  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Die RMO-Klassen, mit denen Sie die Eigenschaften von Pushabonnements anzeigen oder ändern, hängen vom Typ der Veröffentlichung ab, für die das Pushabonnement abonniert wird.  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften eines Pushabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung an oder ändern sie  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransSubscription>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>und <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> fest.  
  
4.  Legen Sie <xref:Microsoft.SqlServer.Management.Common.ServerConnection> aus Schritt 1 für die Einstellung der <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 3 falsch definiert, oder das Abonnement ist nicht vorhanden.  
  
6.  (Optional) Zum Ändern der Eigenschaften legen Sie einen neuen Wert für eine der <xref:Microsoft.SqlServer.Replication.TransSubscription> -Eigenschaften fest, die definiert werden können, und rufen Sie dann die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> -Methode auf.  
  
7.  (Optional) Um die neuen Einstellungen anzuzeigen, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> -Methode auf, um die Eigenschaften für das Abonnement erneut zu laden.  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a>So zeigen Sie die Eigenschaften eines Pushabonnements für eine Mergeveröffentlichung an oder ändern sie  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeSubscription>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>und <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> fest.  
  
4.  Legen Sie <xref:Microsoft.SqlServer.Management.Common.ServerConnection> aus Schritt 1 für die Einstellung der <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 3 falsch definiert, oder das Abonnement ist nicht vorhanden.  
  
6.  (Optional) Zum Ändern der Eigenschaften legen Sie einen neuen Wert für eine der <xref:Microsoft.SqlServer.Replication.MergeSubscription> -Eigenschaften fest, die definiert werden können, und rufen Sie dann die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> -Methode auf.  
  
7.  (Optional) Um die neuen Einstellungen anzuzeigen, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> -Methode auf, um die Eigenschaften für das Abonnement erneut zu laden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikations](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Bewährte Sicherheitsmethoden für die Replikation](security/replication-security-best-practices.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
