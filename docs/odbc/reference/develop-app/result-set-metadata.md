---
title: Resultsetmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b78cdeb4c8b3522f4677c0277401cd9395a36a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300080"
---
# <a name="result-set-metadata"></a>Resultsetmetadaten
*Metadaten* sind Daten, mit denen andere Daten beschrieben werden. Die Resultsetmetadaten beschreiben z. b. das Resultset, z. b. die Anzahl der Spalten im Resultset, die Datentypen dieser Spalten, deren Namen, Genauigkeit, NULL-Zulässigkeit usw.  
  
 Interoperable Anwendungen sollten immer die Metadaten von Resultsetspalten überprüfen. Die Metadaten für eine Spalte in einem Resultset unterscheiden sich möglicherweise von den Metadaten für die Spalte, wie Sie von einer Katalog Funktion zurückgegeben werden. Angenommen, eine aktualisierbare Spalte ist in einem Resultset enthalten, das durch den Beitritt zweier Tabellen erstellt wurde. **SQLColumnPrivileges** gibt zwar möglicherweise an, dass ein Benutzer die Spalte aktualisieren kann, aber die Resultsetmetadaten sind möglicherweise nicht, wenn sich die Spalte auf der n-Seite des Joins befindet. Viele Datenquellen können Spalten auf der Seite "1" eines Joins aktualisieren, aber nicht auf der Seite "Many". Auch Datentypen können nicht als identisch angesehen werden, da die Datenquelle den Datentyp beim Erstellen des Resultsets herauf Stufen kann.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Wie werden Metadaten verwendet?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)
