---
title: Implementieren eines Geschäftslogikhandlers für einen Mergeartikel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 659bba7156ccc1c3a60bef38a51fd983554e4ead
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721205"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a>Implementieren eines Geschäftslogikhandlers für einen Mergeartikel
  In diesem Thema wird beschrieben, wie ein Geschäftslogikhandler für einen Mergeartikel mit Replikationsprogrammierung oder Replikationsverwaltungsobjekten (RMO) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] implementiert wird.  
  
 Der <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> -Namespace implementiert eine Schnittstelle, mit der Sie eine komplexe Geschäftslogik zum Verarbeiten von Ereignissen schreiben können, die während der Synchronisierung der Mergereplikation eintreten. Die Methoden im Geschäftslogikhandler können vom Replikationsvorgang für jede geänderte Zeile aufgerufen werden, die während der Synchronisierung repliziert wird.  
  
 Der allgemeine Vorgang zum Implementieren eines Geschäftslogikhandlers ist Folgender:  
  
1.  Erstellen Sie die Geschäftslogikhandler-Assembly.  
  
2.  Registrieren Sie die Assembly beim Verteiler.  
  
3.  Stellen Sie die Assembly auf dem Server bereit, auf dem der Merge-Agent ausgeführt wird. Für ein Pullabonnement wird der Agent auf dem Abonnenten ausgeführt, und für ein Pushabonnement wird der Agent auf dem Verteiler ausgeführt. Wenn Sie die Websynchronisierung verwenden, wird der Agent auf dem Webserver ausgeführt.  
  
4.  Erstellen Sie einen Artikel, der den Geschäftslogikhandler verwendet, oder ändern Sie einen vorhandenen Artikel so, dass er den Geschäftslogikhandler verwendet.  
  
 Der von Ihnen angegebene Geschäftslogikhandler wird für jede Zeile ausgeführt, die synchronisiert wird. Eine komplexe Logik und Aufrufe anderer Anwendungen oder Netzwerkdienste können sich auf die Leistung auswirken. Weitere Informationen zu Geschäftslogikhandlern finden Sie unter [Ausführen der Geschäftslogik während der Mergesynchronisierung](merge/execute-business-logic-during-merge-synchronization.md).  
  
 **In diesem Thema**  
  
-   **So implementieren Sie einen Geschäftslogikhandler für einen Mergeartikel mit:**  
  
     [Replikations Programmierung](#ReplProg)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-replication-programming"></a><a name="ReplProg"></a> Verwenden der Replikationsprogrammierung  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a>So erstellen Sie einen Geschäftslogikhandler und stellen ihn bereit  
  
1.  Erstellen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio ein neues Projekt für die .NET-Assembly mit dem Code, der den Geschäftslogikhandler implementiert.  
  
2.  Fügen Sie Verweise auf das Projekt für die folgenden Namespaces hinzu.  
  
    |Assemblyverweis|Speicherort|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (Standardinstallation)|  
    |<xref:System.Data>|GAC (Komponente von .NET Framework)|  
    |<xref:System.Data.Common>|GAC (Komponente von .NET Framework)|  
  
3.  Fügen Sie eine Klasse hinzu, die die <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Klasse überschreibt.  
  
4.  Implementieren Sie die <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> -Eigenschaft, um die Typen von Änderungen anzugeben, die verarbeitet werden.  
  
5.  Überschreiben Sie mindestens eine der folgenden Methoden der <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Klasse:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> &ndash; wird aufgerufen, wenn während der Synchronisierung ein Commit für eine Datenänderung ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> &ndash; wird aufgerufen, wenn beim Hochladen oder Herunterladen einer DELETE-Anweisung ein Fehler auftritt.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> &ndash; wird aufgerufen, wenn DELETE-Anweisungen hochgeladen oder heruntergeladen werden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> &ndash; wird aufgerufen, wenn beim Hochladen oder Herunterladen einer INSERT-Anweisung ein Fehler auftritt.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> &ndash; wird aufgerufen, wenn INSERT-Anweisungen hochgeladen oder heruntergeladen werden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> &ndash; wird aufgerufen, wenn in Konflikt stehende UPDATE-Anweisungen auf dem Verleger und dem Abonnenten auftreten.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> &ndash; wird aufgerufen, wenn UPDATE-Anweisungen mit DELETE-Anweisungen auf dem Verleger und dem Abonnenten in Konflikt stehen.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> &ndash; wird aufgerufen, wenn beim Hochladen oder Herunterladen einer UPDATE-Anweisung ein Fehler auftritt.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> &ndash; wird aufgerufen, wenn UPDATE-Anweisungen hochgeladen oder heruntergeladen werden.  
  
6.  Erstellen Sie das Projekt, um die Geschäftslogikhandler-Assembly zu erstellen.  
  
7.  Stellen Sie die Assembly in dem Verzeichnis mit der ausführbaren Datei für den Merge-Agent (replmerg.exe) bereit (bei der Standardinstallation ist dies [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM), oder installieren Sie sie im globalen Assemblycache (GAC) von .NET. Installieren Sie die Assembly nur dann im GAC, wenn andere Anwendungen als der Merge-Agent auf die Assembly zugreifen müssen. Die Assembly kann mit dem im .NET Framework SDK bereitgestellten Global Assembly Cache-Tool (**Gacutil.exe** ) im GAC installiert werden.  
  
    > [!NOTE]  
    >  Auf jedem Server, auf dem der Merge-Agent ausgeführt wird, muss ein Geschäftslogikhandler bereitgestellt werden. Dazu gehört auch der IIS-Server, der die Datei replisapi.dll hostet, wenn die Websynchronisierung verwendet wird.  
  
#### <a name="to-register-a-business-logic-handler"></a>So registrieren Sie einen Geschäftslogikhandler  
  
1.  Führen Sie auf dem Verleger [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) aus, um zu prüfen, ob die Assembly noch nicht als Geschäftslogikhandler registriert wurde.  
  
2.  Führen Sie auf dem Verteiler [sp_registercustomresolver &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)aus, und geben Sie einen anzeigen Amen für den **@article_resolver**Geschäftslogik Handler für `true` , **@is_dotnet_assembly**den Wert für, den Namen der **@dotnet_assembly_name**Assembly für und den voll qualifizierten Namen der Klasse an, die für <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name**überschreibt.  
  
    > [!NOTE]  
    >  Wenn die Assembly nicht im gleichen Verzeichnis wie die ausführbare Datei Merge-Agent bereitgestellt wird, im gleichen Verzeichnis wie die Anwendung, die die Merge-Agent synchron startet, oder im globalen Assemblycache (GAC), müssen Sie den vollständigen Pfad mit dem Assemblynamen für **@dotnet_assembly_name**angeben. Wenn Sie die Websynchronisierung verwenden, müssen Sie den Speicherort der Assembly auf dem Webserver angeben.  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a>So verwenden Sie einen Geschäftslogikhandler mit einem neuen Tabellenartikel  
  
1.  Führen Sie [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) aus, um einen Artikel zu definieren. Geben Sie dabei den Anzeigenamen des Geschäftslogikhandlers für **@article_resolver** an. Weitere Informationen finden Sie unter [Definieren eines Artikels](publish/define-an-article.md).  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a>So verwenden Sie einen Geschäftslogikhandler mit einem bestehenden Tabellenartikel  
  
1.  Führen Sie [sp_changemergearticle &#40;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)-&#41;**@publication**aus **@article**, und geben Sie,, **@property**den Wert **article_resolver** für und den anzeigen amen des Geschäftslogik **@value**Handlers für an.  
  
###  <a name="examples-replication-programming"></a><a name="TsqlExample"></a>Beispiele (Replikations Programmierung)  
 In diesem Beispiel wird ein Geschäftslogikhandler gezeigt, der ein Überwachungsprotokoll erstellt.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 Das folgende Beispiel registriert eine Geschäftslogikhandler-Assembly auf dem Verteiler und ändert einen bestehenden Mergeartikel so, dass diese benutzerdefinierte Geschäftslogik verwendet wird.  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../snippets/tsql/SQL15/replication/howto/tsql/registerblh_10.sql#sp_registerblh_10)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
#### <a name="to-create-a-business-logic-handler"></a>So erstellen Sie einen Geschäftslogikhandler  
  
1.  Erstellen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio ein neues Projekt für die .NET-Assembly mit dem Code, der den Geschäftslogikhandler implementiert.  
  
2.  Fügen Sie Verweise auf das Projekt für die folgenden Namespaces hinzu.  
  
    |Assemblyverweis|Speicherort|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (Standardinstallation)|  
    |<xref:System.Data>|GAC (Komponente von .NET Framework)|  
    |<xref:System.Data.Common>|GAC (Komponente von .NET Framework)|  
  
3.  Fügen Sie eine Klasse hinzu, die die <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Klasse überschreibt.  
  
4.  Implementieren Sie die <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> -Eigenschaft, um die Typen von Änderungen anzugeben, die verarbeitet werden.  
  
5.  Überschreiben Sie mindestens eine der folgenden Methoden der <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Klasse:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> &ndash; wird aufgerufen, wenn während der Synchronisierung ein Commit für eine Datenänderung ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> &ndash; wird aufgerufen, wenn ein Fehler auftritt, während eine DELETE-Anweisung hochgeladen oder heruntergeladen wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> &ndash; wird aufgerufen, wenn DELETE-Anweisungen hochgeladen oder heruntergeladen werden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> &ndash; wird aufgerufen, wenn ein Fehler auftritt, während eine INSERT-Anweisung hochgeladen oder heruntergeladen wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> &ndash; wird aufgerufen, wenn INSERT-Anweisungen hochgeladen oder heruntergeladen werden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> &ndash; wird aufgerufen, wenn in Konflikt stehende UPDATE-Anweisungen auf dem Verleger und dem Abonnenten auftreten.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> &ndash; wird aufgerufen, wenn UPDATE-Anweisungen mit DELETE-Anweisungen auf dem Verleger und dem Abonnenten in Konflikt stehen.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> &ndash; wird aufgerufen, wenn ein Fehler auftritt, während eine UPDATE-Anweisung hochgeladen oder heruntergeladen wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> &ndash; wird aufgerufen, wenn UPDATE-Anweisungen hochgeladen oder heruntergeladen werden.  
  
    > [!NOTE]  
    >  Alle Artikelkonflikte, die nicht explizit von Ihrem benutzerdefinierten Geschäftslogikhandler verarbeitet werden, werden vom Standardkonfliktlöser für den Artikel bearbeitet.  
  
6.  Erstellen Sie das Projekt, um die Geschäftslogikhandler-Assembly zu erstellen.  
  
#### <a name="to-register-a-business-logic-handler"></a>So registrieren Sie einen Geschäftslogikhandler  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Klasse. Übergeben Sie <xref:Microsoft.SqlServer.Management.Common.ServerConnection> von Schritt 1.  
  
3.  Rufen Sie <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> auf, und überprüfen Sie das zurückgegebene <xref:System.Collections.ArrayList> -Objekt, um sicherzustellen, dass die Assembly noch nicht als Geschäftslogikhandler registriert wurde.  
  
4.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler>-Klasse. Geben Sie die folgenden Eigenschaften an:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> &ndash; der Name der .NET-Assembly. Sie müssen den vollständigen Pfad mit dem Assemblynamen angeben, falls die Assembly nicht im gleichen Verzeichnis wie die ausführbare Datei für den Merge-Agent, im gleichen Verzeichnis wie die Anwendung, mit der der Merge-Agent synchron gestartet wird, oder im GAC bereitgestellt wird. Sie müssen den vollständigen Pfad mit dem Assemblynamen angeben, wenn Sie einen Geschäftslogikhandler mit der Websynchronisierung verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> &ndash; der vollqualifizierte Name der Klasse, die <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> überschreibt und den Geschäftslogikhandler implementiert.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> &ndash; ein Anzeigename, den Sie beim Zugriff auf den Geschäftslogikhandler verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> &ndash; der Wert `true`.  
  
#### <a name="to-deploy-a-business-logic-handler"></a>So stellen Sie einen Geschäftslogikhandler bereit  
  
1.  Stellen Sie die Assembly auf dem Server, auf dem der Merge-Agent ausgeführt wird, in dem Dateispeicherort bereit, der angegeben wurde, als der Geschäftslogikhandler beim Verteiler registriert wurde. Für ein Pullabonnement wird der Agent auf dem Abonnenten ausgeführt, und für ein Pushabonnement wird der Agent auf dem Verteiler ausgeführt. Wenn Sie die Websynchronisierung verwenden, wird der Agent auf dem Webserver ausgeführt. Wenn der vollständige Pfad beim Registrieren des Geschäftslogikhandlers nicht zusammen mit dem Assemblynamen angegeben wurde, stellen Sie die Assembly im gleichen Verzeichnis wie die ausführbare Datei für den Merge-Agent, im gleichen Verzeichnis wie die Anwendung, mit der der Merge-Agent synchron gestartet wird, bereit. Sie können die Assembly im GAC installieren, wenn es mehrere Anwendungen gibt, die die gleiche Assembly verwenden.  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a>So verwenden Sie einen Geschäftslogikhandler mit einem neuen Tabellenartikel  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeArticle>-Klasse. Legen Sie die folgenden Eigenschaften fest:  
  
    -   Den Namen des Artikels für <xref:Microsoft.SqlServer.Replication.Article.Name%2A>  
  
    -   Den Namen der Veröffentlichung für <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>  
  
    -   Den Namen der Veröffentlichungsdatenbank für <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.  
  
    -   Den Anzeigenamen des Geschäftslogikhandlers (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) für <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Article.Create%2A> -Methode auf. Weitere Informationen finden Sie unter [Definieren eines Artikels](publish/define-an-article.md).  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a>So verwenden Sie einen Geschäftslogikhandler mit einem bestehenden Tabellenartikel  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeArticle>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>und <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> fest.  
  
4.  Legen Sie die Verbindung aus Schritt 1 für die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder die Artikeleigenschaften in Schritt 3 falsch definiert, oder der Artikel ist nicht vorhanden. Weitere Informationen finden Sie unter [View and Modify Article Properties](publish/view-and-modify-article-properties.md).  
  
6.  Legen Sie den Anzeigenamen des Geschäftslogikhandlers für <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>fest. Dies ist der Wert der <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> -Eigenschaft, die beim Registrieren des Geschäftslogikhandlers angegeben wird.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a>Beispiele (RMO)  
 Dieses Beispiel zeigt einen Geschäftslogikhandler, der Informationen über Einfüge-, Update- und Löschvorgänge auf dem Abonnenten protokolliert.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 In diesem Beispiel wird ein Geschäftslogikhandler beim Verteiler registriert.  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 In diesem Beispiel wird ein vorhandener Artikel geändert, um den Geschäftslogikhandler zu verwenden.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren eines benutzerdefinierten Konflikt Lösers für einen Mergeartikel](implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [Debuggen eines Geschäftslogik Handlers &#40;Replikations Programmierung&#41;](debug-a-business-logic-handler-replication-programming.md)   
 [Bewährte Sicherheitsmethoden für die Replikation](security/replication-security-best-practices.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)  
  
  
