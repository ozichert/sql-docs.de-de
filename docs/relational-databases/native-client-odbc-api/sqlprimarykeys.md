---
title: SQLPrimaryKeys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2695d253030f13f71785046a25997ec6ee768622
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288981"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Tabelle kann über eine Spalte oder Spalten verfügen, die als eindeutige Zeilen Bezeichner fungieren können, und Tabellen, die ohne PRIMARY KEY-Einschränkung erstellt werden, geben ein leeres Resultset an SQLPrimaryKeys zurück. Die ODBC-Funktion [SQLSpecialColumns meldet Zeilenbezeichnerkandidaten](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) für Tabellen ohne Primärschlüssel.  
  
 SQLPrimaryKeys gibt SQL_SUCCESS zurück, ob Werte für die Parameter *CatalogName*, Schema Name oder *TableName* *vorhanden sind.* SQLFetch gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 SQLPrimaryKeys kann in einem statischen Server Cursor ausgeführt werden. Der Versuch, SQLPrimaryKeys auf einem aktualisierbaren (dynamischen oder Keyset-) Cursor auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys und Tabellenwertparameter  
 Wenn das Anweisungs Attribut SQL_SOPT_SS_NAME_SCOPE den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE anstelle des Standardwerts SQL_SS_NAME_SCOPE_TABLE hat, gibt SQLPrimaryKeys Informationen zu Primärschlüssel Spalten von Tabellentypen zurück. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLPrimaryKeys-Funktion](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
