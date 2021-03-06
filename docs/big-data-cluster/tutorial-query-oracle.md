---
title: Abfragen externer Daten in Oracle
titleSuffix: SQL Server big data clusters
description: Dieses Tutorial veranschaulicht, wie Sie Oracle-Daten aus einem Big Data-Cluster für SQL Server 2019 abfragen. Sie erstellen eine externe Tabelle für Daten in Oracle und führen dann eine Abfrage aus.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0955875255acc695133700fd0b5a0b30cdf9045e
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606116"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>Tutorial: Abfragen von Oracle in einem Big-Data-Cluster für SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieses Tutorial veranschaulicht, wie Sie Oracle-Daten aus einem Big Data-Cluster für SQL Server 2019 abfragen. Zum Ausführen dieses Tutorials benötigen Sie Zugriff auf einen Oracle-Server. Auch wenn Sie keinen Zugriff haben, bietet Ihnen dieses Tutorial einen Einblick darin, wie die Datenvirtualisierung für externe Datenquellen in einem SQL Server-Big Data-Cluster funktioniert.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Sie erstellen eine externe Tabelle für Daten in einer externen Oracle-Datenbank.
> * Verknüpfen dieser Daten mit hochwertigen Daten in der Masterinstanz

> [!TIP]
> Wenn Sie möchten, können Sie ein Skript für die Befehle in diesem Tutorial herunterladen und ausführen. Anweisungen finden Sie in den [Beispielen zur Datenvirtualisierung](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) auf GitHub.

## <a name="prerequisites"></a><a id="prereqs"></a> Voraussetzungen

- [Big-Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
- [Laden von Beispieldaten in einen Big Data-Cluster von SQL Server](tutorial-load-sample-data.md)

## <a name="create-an-oracle-table"></a>Erstellen einer Oracle-Tabelle

Mit den folgenden Schritten erstellen Sie eine Beispieltabelle namens `INVENTORY` in Oracle.

1. Stellen Sie eine Verbindung mit einer Oracle-Instanz und -Datenbank her, die Sie für dieses Tutorial verwenden möchten.

1. Führen Sie zum Erstellen der Tabelle `INVENTORY` die folgende Anweisung aus:

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Importieren Sie die Inhalte der Datei **inventory.csv** in diese Tabelle. Diese Datei wurde von den Beispielerstellungsskripts im Abschnitt [Voraussetzungen](#prereqs) erstellt.

## <a name="create-an-external-data-source"></a>Erstellen einer externen Datenquelle

Der erste Schritt besteht darin, eine externe Datenquelle zu erstellen, die auf Ihren Oracle-Server zugreifen kann.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der SQL Server-Masterinstanz Ihres Big Data-Clusters her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie im Fenster **Server** auf die Verbindung, um das Serverdashboard der SQL Server-Masterinstanz anzuzeigen. Wählen Sie **Neue Abfrage** aus.

   ![Abfrage der SQL Server-Masterinstanz](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl aus, um den Kontext in der Masterinstanz in die **Sales**-Datenbank zu ändern.

   ```sql
   USE Sales
   GO
   ```

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen zum Herstellen einer Verbindung mit dem Oracle-Server. Geben Sie in der folgenden Anweisung die entsprechenden Anmeldeinformationen für Ihren Oracle-Server an.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Erstellen Sie eine externe Datenquelle, die auf den Oracle-Server zeigt.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>Erstellen einer externen Tabelle

Erstellen Sie als Nächstes eine externe Tabelle namens **iventory_ora** über der Tabelle `INVENTORY` auf dem Oracle-Server.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Tabellen- und Spaltennamen verwenden beim Abfragen von Oracle SQL-Bezeichner in ANSI-Anführungszeichen. Daher wird bei den Namen nach Groß-/Kleinschreibung unterschieden. Es ist wichtig, den Namen in der externen Tabellendefinition so anzugeben, dass er mit der exakten Groß-und Kleinschreibung der Tabellen- und Spaltennamen in den Oracle-Metadaten übereinstimmt.

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie die folgende Abfrage aus, um die Daten in der externen Tabelle `iventory_ora` mit den Tabellen in der lokalen Datenbank `Sales` zu verknüpfen.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Bereinigung

Verwenden Sie den folgenden Befehl, um die in diesem Tutorial erstellten Datenbankobjekte zu entfernen.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie Daten im Datenpool einfügen:
> [!div class="nextstepaction"]
> [Laden von Daten in den Datenpool](tutorial-data-pool-ingest-sql.md)
