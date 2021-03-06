---
title: Erstellen eindeutiger Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- unique indexes
- designing indexes [SQL Server], unique
- clustered indexes, unique
- indexes [SQL Server], unique
- nonclustered indexes [SQL Server], unique
- unique indexes, design guidelines
ms.assetid: 56b5982e-cb94-46c0-8fbb-772fc275354a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cf786e48e6e76ca6a16a0a50a954a2a07d3f7a66
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63162352"
---
# <a name="create-unique-indexes"></a>Erstellen eindeutiger Indizes
  In diesem Thema wird beschrieben, wie ein eindeutiger Index auf einer Tabelle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt wird. Ein eindeutiger Index garantiert, dass der Indexschlüssel keine doppelten Werte enthält und dass deshalb jede Zeile in der Tabelle in gewisser Weise eindeutig ist. Es gibt keine bedeutenden Unterschiede zwischen dem Erstellen einer UNIQUE-Einschränkung und dem Erstellen eines eindeutigen, von Einschränkungen unabhängigen Index. Die Datenüberprüfung erfolgt auf dieselbe Weise, und der Abfrageoptimierer macht keinen Unterschied zwischen einem durch eine Einschränkung erstellten eindeutigen Index und einem manuell erstellten. Das Erstellen einer UNIQUE-Einschränkung auf der Spalte verdeutlicht jedoch die Zielsetzung des Indexes. Weitere Informationen zu UNIQUE-Einschränkungen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
 Beim Erstellen eines eindeutigen Indexes können Sie eine Option aktivieren, um doppelt vorhandene Schlüssel zu ignorieren. Wenn diese Option auf **Ja** festgelegt ist und Sie versuchen, doppelte Schlüssel zu erstellen, indem Sie (mit der INSERT-Anweisung) Daten hinzufügen, die mehrere Zeilen betreffen, wird die Zeile mit dem Duplikat nicht hinzugefügt. Wenn die Option auf **Nein**festgelegt ist, schlägt die gesamte INSERT-Operation fehl, und alle Daten werden zurückgesetzt.  
  
> [!NOTE]  
>  Sie können keinen eindeutigen Index für eine einzelne Spalte erstellen, wenn mehr als eine Zeile der Spalte NULL enthält. Ebenso können Sie keinen eindeutigen Index für mehrere Spalten erstellen, wenn die Spaltenkombination in mehreren Zeilen NULL enthält. Diese werden beim Indizieren als doppelt vorhandene Werte betrachtet.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Vorteile eines eindeutigen Indexes](#Benefits)  
  
     [Typische Implementierungen](#Implementations)  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie einen eindeutigen Index auf einer Tabelle mithilfe von:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="benefits-of-a-unique-index"></a><a name="Benefits"></a> Vorteile eines eindeutigen Indexes  
  
-   Eindeutige Indizes für mehrere Spalten stellen sicher, dass jede Kombination der Werte in der indizierten Spalte eindeutig ist. Wenn z. B. ein eindeutiger Index für eine Kombination der Spalten **LastName**, **FirstName**und **MiddleName** erstellt wird, können keine zwei Zeilen in der Tabelle dieselbe Kombination der Werte in diesen Spalten aufweisen.  
  
-   Unter der Voraussetzung, dass die Daten in jeder Spalte eindeutig sind, können Sie einen eindeutigen gruppierten Index und mehrere eindeutige nicht gruppierte Indizes in derselben Tabelle erstellen.  
  
-   Eindeutige Indizes sichern die Datenintegrität der definierten Spalten.  
  
-   Eindeutige Indizes stellen weitere hilfreiche Informationen für den Abfrageoptimierer bereit, der effizientere Ausführungspläne erstellen kann.  
  
###  <a name="typical-implementations"></a><a name="Implementations"></a> Typische Implementierungen  
 Eindeutige Indizes werden auf folgende Weise implementiert:  
  
-   **PRIMARY KEY- oder UNIQUE-Einschränkung**  
  
     Wenn Sie eine PRIMARY KEY-Einschränkung erstellen, wird automatisch ein eindeutiger gruppierter Index für die Spalte(n) erstellt, wenn noch kein gruppierter Index für die Tabelle vorhanden ist und Sie keinen eindeutigen nicht gruppierten Index angeben. Die Primärschlüsselspalte darf keine NULL-Werte zulassen.  
  
     Wenn Sie eine UNIQUE-Einschränkung erstellen, wird ein eindeutiger nicht gruppierter Index erstellt, um standardmäßig eine UNIQUE-Einschränkung zu erzwingen. Sie können einen eindeutigen gruppierten Index angeben, wenn noch kein gruppierter Index für die Tabelle vorhanden ist.  
  
     Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md) und [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
-   **Index unabhängig von einer Einschränkung**  
  
     Es können mehrere eindeutige nicht gruppierte Indizes für eine Tabelle definiert werden.  
  
     Weitere Informationen finden Sie unter [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
-   **Indizierte Sicht**  
  
     Zum Erstellen einer indizierten Sicht wird ein eindeutiger gruppierter Index für mindestens eine Spalte der Sicht definiert. Diese Sicht wird ausgeführt und das Resultset auf der Blattebene des Indexes gespeichert, so wie auch Tabellendaten in einem gruppierten Index gespeichert werden. Weitere Informationen finden Sie unter [Erstellen von indizierten Sichten](../views/views.md).  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Ein eindeutiger Index, die UNIQUE-Einschränkung oder die PRIMARY KEY-Einschränkung kann nicht erstellt werden, wenn in den Daten doppelte Schlüsselwerte vorhanden sind.  
  
-   Ein eindeutiger, nicht gruppierter Index kann eingeschlossene Nichtschlüsselspalten enthalten. Weitere Informationen finden Sie unter [Create Indexes with Included Columns](create-indexes-with-included-columns.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung in der Tabelle oder Sicht. Der Benutzer muss ein Mitglied der festen Serverrolle **sysadmin** bzw. der festen Datenbankrollen **db_ddladmin** und **db_owner** sein.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-unique-index-by-using-the-table-designer"></a>So erstellen Sie einen eindeutigen Index mit dem Tabellen-Designer  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, für die Sie einen eindeutigen Index erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Tabellen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Tabelle, in der Sie einen eindeutigen Index erstellen möchten, und wählen Sie **Entwurf**aus.  
  
4.  Wählen Sie im Menü **Tabellen-Designer** **Indizes/Schlüssel**aus.  
  
5.  Klicken Sie im Dialogfeld **Indizes/Schlüssel** auf **Hinzufügen**.  
  
6.  Wählen Sie im Textfeld **Ausgewählter Primärschlüssel/eindeutiger Schlüssel oder Index** den neuen Index aus.  
  
7.  Wählen Sie im Hauptraster unter **(Allgemein)** **Typ** aus, und wählen Sie dann **Index** aus der Liste aus.  
  
8.  Wählen Sie **Spalten** aus, und klicken Sie dann auf die Auslassungspunkte **(...)** .  
  
9. Wählen Sie im Dialogfeld **Indexspalten** unter **Spaltenname**die Spalten aus, die Sie indizieren möchten. Sie können bis zu 16 Spalten auswählen. Um optimale Ergebnisse zu gewährleisten, sollten Sie für jeden Index höchstens zwei Spalten auswählen. Für jede ausgewählte Spalte können Sie festlegen, ob die darin enthaltenen Werte über den Index in aufsteigender oder absteigender Reihenfolge geordnet werden.  
  
10. Wenn alle Spalten für den Index ausgewählt sind, klicken Sie auf **OK**.  
  
11. Wählen Sie im Raster unter **(Allgemein)** **Ist eindeutig** aus, und wählen Sie anschließend **Ja** aus der Liste aus.  
  
12. Optional: wählen Sie im Hauptraster unter **Tabellen-Designer** **Doppelte Schlüssel ignorieren** aus, und wählen Sie dann **Ja** aus der Liste aus. Auf diese Weise ignorieren Sie Versuche, Daten hinzuzufügen, die im eindeutigen Index einen doppelten Schlüssel erstellen würden.  
  
13. Klicken Sie auf **Schließen**.  
  
14. Klicken Sie im Menü **Datei** auf **Save**_table_name_speichern.  
  
#### <a name="create-a-unique-index-by-using-object-explorer"></a>Erstellen eines eindeutigen Indexes mit dem Objekt-Explorer  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, für die Sie einen eindeutigen Index erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Tabellen** .  
  
3.  Erweitern Sie die Tabelle, für die Sie einen eindeutigen Index erstellen möchten.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Indizes**, zeigen Sie auf **Neuer Index**, und wählen Sie **Nicht gruppierter Index...** aus.  
  
5.  Geben Sie in das Dialogfeld **Neuer Index** auf der Seite **Allgemein** den Namen des neuen Indexes in das Feld **Indexname** ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Eindeutig** .  
  
7.  Klicken Sie unter **Indexschlüsselspalten** auf **Hinzufügen…** .  
  
8.  Aktivieren Sie im Dialogfeld **Spalten auswählen aus**_table_name_ die Kontrollkästchen der Tabellenspalten, die dem eindeutigen Index hinzugefügt werden sollen.  
  
9. Klicken Sie auf **OK**.  
  
10. Klicken Sie im Dialogfeld **Neuer Index** auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-unique-index-on-a-table"></a>So erstellen Sie einen eindeutigen Index auf einer Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named AK_UnitMeasure_Name and delete it if found  
    IF EXISTS (SELECT name from sys.indexes  
               WHERE name = N'AK_UnitMeasure_Name')   
       DROP INDEX AK_UnitMeasure_Name ON Production.UnitMeasure;   
    GO  
    -- Create a unique index called AK_UnitMeasure_Name  
    -- on the Production.UnitMeasure table using the Name column.  
    CREATE UNIQUE INDEX AK_UnitMeasure_Name   
       ON Production.UnitMeasure (Name);   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
  
