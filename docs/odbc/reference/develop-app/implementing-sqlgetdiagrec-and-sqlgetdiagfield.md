---
title: Implementieren von SQLGetDiagRec und SQLGetDiagField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300140"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implementieren von SQLGetDiagRec und SQLGetDiagField
**SQLGetDiagRec** und **SQLGetDiagField** werden vom Treiber-Manager und den einzelnen Treibern implementiert. Der Treiber-Manager und jeder Treiber behalten Diagnosedaten Sätze für jede Umgebung, jede Verbindung, jede Anweisung und dieses Deskriptorhandle bei und gibt diese Datensätze nur frei, wenn eine andere Funktion mit diesem Handle aufgerufen oder das Handle freigegeben wird.  
  
 Obwohl sowohl der Treiber-Manager als auch der Treiber den ersten Statusdaten Satz gemäß der [Rangfolge der Statusdaten Sätze](../../../odbc/reference/develop-app/sequence-of-status-records.md)bestimmen müssen, bestimmt der Treiber-Manager die endgültige Sequenz von Datensätzen.  
  
 **SQLGetDiagRec** und **SQLGetDiagField** veröffentlichen keine Diagnosedaten Sätze über sich selbst.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Regeln der Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rolle des Treiber-Managers](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rolle des Treibers](../../../odbc/reference/develop-app/role-of-the-driver.md)
