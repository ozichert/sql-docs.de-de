---
title: SQL-Module | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 351d1c6a34413b385bd76dfebb009b34c4c0f150
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280424"
---
# <a name="sql-modules"></a>SQL-Module
Die zweite Methode zum Senden von SQL-Anweisungen an das DBMS ist die Verwendung von Modulen. Kurz gesagt besteht ein Modul aus einer Gruppe von Prozeduren, die von der Host Programmiersprache aufgerufen werden. Jede Prozedur enthält eine einzelne SQL-Anweisung, und die Daten werden über Parameter an und aus der Prozedur übermittelt.  
  
 Ein Modul kann als Objektbibliothek betrachtet werden, die mit dem Anwendungscode verknüpft ist. Die Art und Weise, in der die Prozeduren und der Rest der Anwendung verknüpft sind, ist jedoch implementierungsabhängig. Die Prozeduren können z. b. in den Objektcode kompiliert und direkt mit dem Anwendungscode verknüpft werden. Sie können auf dem DBMS kompiliert und gespeichert werden, und es können Aufrufe von Zugriffs Plan Bezeichner erfolgen, die im Anwendungscode abgelegt werden, oder Sie können zur Laufzeit interpretiert werden.  
  
 Der Hauptvorteil von Modulen besteht darin, dass Sie SQL-Anweisungen ordnungsgemäß von der Programmiersprache trennen. Theoretisch sollte es möglich sein, eine Änderung zu ändern, ohne die andere zu ändern und Sie einfach neu zu verknüpfen.
