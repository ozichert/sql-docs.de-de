---
title: Gleichzeitigkeitssteuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8afba3b3b8c8fee1307473c790186d509b37d982
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294850"
---
# <a name="concurrency-control"></a>Gleichzeitigkeitssteuerung
*Parallelität ist die* Fähigkeit von zwei Transaktionen, dieselben Daten gleichzeitig zu verwenden, und mit erhöhter Transaktions Isolation kommt es in der Regel zu reduzierter Parallelität. Dies liegt daran, dass die Transaktions Isolation normalerweise durch das Sperren von Zeilen implementiert wird. wenn mehr Zeilen gesperrt sind, können weniger Transaktionen abgeschlossen werden, ohne mindestens vorübergehend durch eine gesperrte Zeile blockiert zu werden. Obwohl die geringere Parallelität im Allgemeinen als Kompromiss für die höheren Transaktions Isolations Stufen, die für die Beibehaltung der Datenbankintegrität erforderlich sind, akzeptiert wird, kann es in interaktiven Anwendungen mit hoher Lese-/Schreibaktivität, die Cursor verwenden, zu einem Problem werden.  
  
 Angenommen, eine Anwendung führt die SQL-Anweisung **Select \* from Orders aus**. Er ruft **SQLFetchScroll** auf, um einen Bildlauf um das Resultset durchzuführen, und ermöglicht dem Benutzer das Aktualisieren, löschen oder Einfügen von Aufträgen. Nachdem der Benutzer eine Bestellung aktualisiert, gelöscht oder eingefügt hat, führt die Anwendung einen Commit für die Transaktion aus.  
  
 Wenn die Isolationsstufe REPEATABLE READ ist, kann die Transaktion abhängig von ihrer Implementierung eine Sperre für jede Zeile durchführen, die von **SQLFetchScroll**zurückgegeben wurde. Wenn die Isolationsstufe serialisierbar ist, sperrt die Transaktion möglicherweise die gesamte Orders-Tabelle. In beiden Fällen gibt die Transaktion ihre Sperren nur dann frei, wenn ein Commit oder ein Rollback ausgeführt wird. Wenn der Benutzer also viel Zeit mit dem Lesen von Bestellungen und sehr wenig Zeit verbringt, ihn zu aktualisieren, zu löschen oder einzufügen, könnte die Transaktion eine große Anzahl von Zeilen problemlos sperren, sodass Sie für andere Benutzer nicht verfügbar sind.  
  
 Dies ist ein Problem, auch wenn der Cursor schreibgeschützt ist und die Anwendung es dem Benutzer ermöglicht, nur vorhandene Bestellungen zu lesen. In diesem Fall führt die Anwendung einen Commit für die Transaktion aus und gibt Sperren frei, wenn Sie **SQLCloseCursor** (im Autocommit-Modus) oder **SQLEndTran** (im manuellen Commitmodus) aufruft.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Parallelitätstypen](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Optimistische Nebenläufigkeit](../../../odbc/reference/develop-app/optimistic-concurrency.md)
