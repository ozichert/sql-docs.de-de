---
title: Arbeiten mit umfangreichen Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a94761b9c85e4d3aa1d88a21efdce51a0f46e6f7
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922545"
---
# <a name="working-with-large-data"></a>Arbeiten mit umfangreichen Daten

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Der JDBC-Treiber bietet Unterstützung für die adaptive Pufferung, mit der Sie beliebige Daten mit umfangreichen Werten ohne den Aufwand von Servercursorn abrufen können. Mithilfe der adaptiven Pufferung ruft der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Ergebnisse der Anweisungsausführung erst dann aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ab, wenn sie in der Anwendung benötigt werden, statt alle Ergebnisse auf einmal abzurufen. Der Treiber verwirft außerdem die Ergebnisse, sobald die Anwendung nicht mehr auf sie zugreifen kann.  
  
In der JDBC-Treiberversion 1.2 für [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] war der Puffermodus standardmäßig auf **full** festgelegt. Wenn die responseBuffering-Verbindungseigenschaft in der Anwendung nicht auf **adaptive** festgelegt war – entweder in den Verbindungseigenschaften oder mit der [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode des [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts –, unterstützte der Treiber das Lesen des gesamten Resultsets vom Server in einem einzigen Vorgang. Um ein adaptives Pufferungsverhalten zu erzielen, musste die responseBuffering-Verbindungseigenschaft in der Anwendung explizit auf **adaptive** festgelegt werden.  
  
Der **adaptive**-Wert ist der Standardpuffermodus, und der JDBC-Treiber puffert nach Bedarf so wenig Daten wie möglich. Weitere Informationen zur Verwendung von adaptiver Pufferung finden Sie unter [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
Die Themen in diesem Abschnitt beschreiben verschiedene Möglichkeiten, wie Sie Daten mit einer großen Menge an Werten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abrufen können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                                                         | BESCHREIBUNG                                                              |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Beispiel zum Lesen umfangreicher Daten](../../../connect/jdbc/code-samples/reading-large-data-sample.md)                                               | Beschreibt die Verwendung einer SQL-Anweisung zum Abrufen von Daten mit umfangreichen Werten.       |
| [Beispiel zum Lesen umfangreicher Daten mit gespeicherten Prozeduren](../../../connect/jdbc/code-samples/reading-large-data-with-stored-procedures-sample.md) | Beschreibt das Abrufen eines umfangreichen CallableStatement OUT-Parameterwerts. |
| [Beispiel zum Aktualisieren umfangreicher Daten](../../../connect/jdbc/code-samples/updating-large-data-sample.md)                                             | Beschreibt das Aktualisieren von Daten mit umfangreichen Werten in einer Datenbank.                |
  
## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  
