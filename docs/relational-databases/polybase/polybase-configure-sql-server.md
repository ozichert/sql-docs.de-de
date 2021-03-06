---
title: 'Zugreifen auf externe Daten: SQL Server – PolyBase'
description: In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in einer anderen SQL Server-Instanz abzufragen. Hier erfahren Sie, wie Sie externe Tabellen erstellen, um auf externe Daten zu verweisen.
ms.date: 12/13/2019
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 17fd981feb92e75bb875a2b40bfd8fe5831f02c8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80215802"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in einer anderen SQL Server-Instanz abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md). Die Voraussetzungen für die Installation werden im entsprechenden Artikel erläutert. Stellen Sie nach der Installation auch sicher, dass Sie [PolyBase aktivieren](polybase-installation.md#enable).

Bevor datenbankweit gültige Anmeldeinformationen erstellt werden können, muss ein [Hauptschlüssel](../../t-sql/statements/create-master-key-transact-sql.md) erstellt werden. 

## <a name="configure-a-sql-server-external-data-source"></a>Konfigurieren einer externen SQL Server-Datenquelle

Um die Daten einer SQL Server-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen. 
 
Damit eine optimale Abfrageleistung erzielt werden kann, sollten Sie Statistiken für externe Tabellenspalten erstellen, insbesondere für die Spalten, die für Joins, Filter und Aggregate verwendet werden.

In diesem Abschnitt werden die folgenden Transact-SQL-Befehle verwendet:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die SQL Server-Quelle. Das folgende Beispiel erstellt eine Anmeldeinformation für die externe Datenquelle mit `IDENTITY = 'username'` und `SECRET = 'password'`.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials
    WITH IDENTITY = 'username', SECRET = 'password';
    ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle. Im folgenden Beispiel:

   - wird eine externe Datenquelle mit dem Namen `SQLServerInstance` erstellt.
   - werden externe Datenquellen (`LOCATION = '<vendor>://<server>[:<port>]'`) identifiziert. Im Beispiel verweist sie auf eine SQL Server-Standardinstanz.
   - wird identifiziert, ob die Berechnung zur Quelle (`PUSHDOWN`) gepusht werden soll. `PUSHDOWN` ist standardmäßig `ON`.

   Schließlich werden im Beispiel die zuvor erstellten Anmeldeinformationen verwendet.

    ```sql
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
        WITH ( LOCATION = 'sqlserver://SqlServer',
        PUSHDOWN = ON,
        CREDENTIAL = SQLServerCredentials);
    ```

1. Optional erstellen Sie Statistiken für eine externe Tabelle.

  Damit eine optimale Abfrageleistung erzielt werden kann, sollten Sie Statistiken für externe Tabellenspalten erstellen, insbesondere für die Spalten, die für Joins, Filter und Aggregate verwendet werden.

  ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY)
    WITH FULLSCAN;
  ```

>[!IMPORTANT] 
>Sobald Sie eine externe Datenquelle erstellt haben, können Sie über den Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) eine abfragbare Tabelle für diese Quelle erstellen.

## <a name="sql-server-connector-compatible-types"></a>Mit dem SQL Server-Connector kompatible Typen

Sie können eine Verbindung mit anderen Datenquellen herstellen, die von einer SQL Server-Verbindung erkannt werden. Mithilfe des PolyBase-Connectors für SQL Server können Sie externe Tabellen in Azure SQL Data Warehouse und Azure SQL-Datenbank erstellen. Führen Sie dafür die zuvor erläuterten Schritte aus. Stellen Sie sicher, dass die für die gesamte Datenbank gültigen Anmeldeinformationen, die Serveradresse, der Port und die Standortzeichenfolge in Korrelation mit denen der kompatiblen Datenquelle stehen, mit der Sie eine Verbindung herstellen möchten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
