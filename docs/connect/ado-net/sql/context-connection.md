---
title: Die Kontextverbindung
description: Beschreibt die Kontextverbindung
ms.date: 08/15/2019
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a70614ce43ee94894d88e1bc9aaae0c2ed87076a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928885"
---
# <a name="the-context-connection"></a>Die Kontextverbindung

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Der interne Datenzugriff ist ein verbreitetes Problem. Es tritt auf, wenn Sie auf denselben Server zugreifen möchten, auf dem auch die CLR-gespeicherte Prozedur (Common Language Runtime, CLR) oder -Funktion ausgeführt wird. Eine der Optionen besteht darin, mithilfe von <xref:Microsoft.Data.SqlClient.SqlConnection> eine Verbindung zu erstellen, eine Verbindungszeichenfolge anzugeben, die auf den lokalen Server zeigt, und die Verbindung anschließend zu öffnen. Dies erfordert die Angabe von Anmeldeinformationen für die Anmeldung. Die Verbindung wurde in einer anderen Datenbanksitzung als die gespeicherte Prozedur oder Funktion hergestellt, sie verwendet möglicherweise andere `SET`-Optionen, befindet sich in einer separaten Transaktion, hat keinen Zugriff auf die temporären Tabellen usw. Wenn der Code Ihrer verwalteten gespeicherten Prozedur oder Funktion im SQL Serverprozess ausgeführt wird, liegt das daran, dass jemand eine Verbindung mit diesem Server hergestellt und eine SQL-Anweisung ausgeführt hat, um den Code aufzurufen. Nun möchten Sie eventuell die gespeicherte Prozedur oder Funktion im Kontext dieser Verbindung ausführen, zusammen mit deren Transaktion, `SET`-Optionen und so weiter. Dies wird als Kontextverbindung bezeichnet.  
  
Die Kontextverbindung ermöglicht, Transact-SQL-Anweisungen im selben Kontext auszuführen wie den Code, der anfänglich aufgerufen wurde. Ausführlichere Informationen finden Sie im Artikel zur [Kontextverbindung](https://go.microsoft.com/fwlink/?LinkId=115395) der Microsoft SQL Server-Onlinedokumentation.
