---
title: Prüfen der Integrität von Datenbanken mit fehlerverdächtigen Seiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f0be2586d83aaf859ba6b5f4b57f08a4d679b9be
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68109884"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Prüfen der Integrität von Datenbanken mit fehlerverdächtigen Seiten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft Benutzerdatenbanken, deren Datenbankstatus auf Fehlerverdächtig festgelegt ist. Wenn [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eine Datenbankseite mit einem Fehler vom Typ 824 liest, wird die Seite als "fehlerverdächtig" betrachtet und ihre Seiten-ID in der suspect_pages-Tabelle der msdb-Datenbank aufgezeichnet. Der Status der Datenbank, die diese Seite enthält, wird auf Fehlerverdächtig festgelegt.  
  
 Der Fehler vom Typ 824 gibt an, dass ein logischer Konsistenzfehler während eines Lesevorgangs aufgetreten ist. Dieser Fehler gibt häufig eine von einer fehlerhaften E/A-Subsystem-Komponente verursachte Datenbeschädigung an. Dies ist ein schwerer Fehler, der die Datenbankintegrität bedroht und sofort behoben werden muss.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
  
-   Weitere Details zum Fehler des Typs 824 finden Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll dieser Datenbank.  
  
-   Führen Sie eine vollständige Datenbankkonsistenzprüfung ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)) aus.  
  
-   Implementieren Sie die Benutzeraktionen, die in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)definiert werden.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Verwalten der suspect_pages-Tabelle &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
