---
title: Löschen einer Planhinweisliste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38065b8cc27526cccc8c1554b25a288662fef8a6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63151166"
---
# <a name="delete-a-plan-guide"></a>Löschen einer Planhinweisliste
  Sie können eine Planhinweisliste in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen. Mit [!INCLUDE[tsql](../../includes/tsql-md.md)]können Sie auch alle Planhinweislisten in einer Datenbank löschen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So löschen Sie eine Planhinweisliste mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Das Löschen einer OBJECT-Planhinweisliste erfordert die ALTER-Berechtigung für das Objekt (z. B. Funktion, gespeicherte Prozedur), auf das von der Planhinweisliste verwiesen wird. Für alle anderen Planhinweislisten ist die ALTER DATABASE-Berechtigung erforderlich.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-plan-guide"></a>So löschen Sie eine Planhinweisliste  
  
1.  Klicken Sie auf das Pluszeichen, um die Datenbank zu erweitern, in der Sie eine Planhinweisliste löschen möchten, und klicken Sie dann auf das Pluszeichen, um den Ordner **Programmierbarkeit** zu erweitern.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Planhinweislisten** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Planhinweisliste, die Sie löschen möchten, und klicken Sie dann auf **Löschen**.  
  
4.  Stellen Sie im Dialogfeld **Objekt löschen** sicher, dass die richtige Planhinweisliste ausgewählt ist, und klicken Sie dann auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-single-plan-guide"></a>So löschen Sie eine einzelne Planhinweisliste  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a>So löschen Sie alle Planhinweislisten in einer Datenbank  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).  
  
  
