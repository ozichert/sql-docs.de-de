---
title: Erstellen von CHECK-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table constraints [SQL Server]
- attaching check constraints
- columns [SQL Server], constraints
- constraints [SQL Server], check
- CHECK constraints, attaching
ms.assetid: b8756304-9454-4d39-996a-64516831b7df
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a27b4bf288d6b1e436ba43fc9c1002d03cd9eaf4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62736200"
---
# <a name="create-check-constraints"></a>Erstellen von CHECK-Einschränkungen
  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in einer Tabelle eine CHECK-Einschränkung erstellen, um die Datenwerte anzugeben, die in einer oder mehreren Spalten in [!INCLUDE[tsql](../../includes/tsql-md.md)] akzeptiert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie eine neue CHECK-Einschränkung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER-Berechtigungen für die Tabelle.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-new-check-constraint"></a>So erstellen Sie eine neue CHECK-Einschränkung  
  
1.  Erweitern Sie im **Objekt-Explorer**die Tabelle, der Sie eine CHECK-Einschränkung hinzufügen möchten, klicken Sie mit der rechten Maustaste auf **Einschränkungen**, und klicken Sie auf **Neue Einschränkung**.  
  
2.  Klicken Sie im Dialogfeld **Einschränkungen überprüfen** auf das Feld **Ausdruck** und dann auf die Auslassungspunkte **(…)** .  
  
3.  Geben Sie im Dialogfeld **CHECK-Einschränkungen** die SQL-Ausdrücke für die CHECK-Einschränkungen ein. Um die Einträge in der Spalte `SellEndDate` der Tabelle `Product` auf einen Wert zu beschränken, der entweder größer oder gleich dem Datum in der Spalte `SellStartDate` ist oder ein NULL-Wert ist, geben Sie z. B. Folgendes ein:  
  
    ```  
    SellEndDate >= SellStartDate OR SellEndDate IS NULL  
    ```  
  
     Wenn die Einträge in der Spalte `zip` aus 5 Ziffern bestehen sollen, müssen Sie Folgendes eingeben:  
  
    ```  
    zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
    ```  
  
    > [!NOTE]  
    >  Achten Sie darauf, dass nichtnumerische Einschränkungswerte in einfache Anführungszeichen (') eingeschlossen werden müssen.  
  
4.  Klicken Sie auf **OK**.  
  
5.  In der Kategorie **Identität** können Sie den Namen der CHECK-Einschränkung ändern und eine Beschreibung (erweiterte Eigenschaft) für die Einschränkung hinzufügen.  
  
6.  In der **Tabellen-Designer**-Kategorie können Sie festlegen, unter welchen Bedingungen die Einschränkung erzwungen werden soll.  
  
    |**An:**|**Wählen Sie in den folgenden Feldern Ja aus:**|  
    |-------------|---------------------------------------------|  
    |Einschränkung für Daten überprüfen, die vorhanden waren, bevor Sie die Einschränkung erstellt haben|**Vorhandene Daten bei Erstellung oder Reaktivierung überprüfen**|  
    |Die Einschränkung jedes Mal erzwingen, wenn ein Replikationsvorgang mit dieser Tabelle auftritt|**Für Replikation erzwingen**|  
    |Die Einschränkung jedes Mal erzwingen, wenn eine Zeile in diese Tabelle eingefügt wird oder darin aktualisiert wird|**Für INSERTs und UPDATEs erzwingen**|  
  
7.  Klicken Sie auf **Schließen**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-new-check-constraint"></a>So erstellen Sie eine neue CHECK-Einschränkung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
       ADD ColumnD int NULL   
       CONSTRAINT CHK_ColumnD_DocExc   
       CHECK (ColumnD > 10 AND ColumnD < 50);  
    GO  
    -- Adding values that will pass the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (49);  
    GO  
    -- Adding values that will fail the check constraint  
    INSERT INTO dbo.DocExc (ColumnD) VALUES (55);  
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
