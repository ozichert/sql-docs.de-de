---
title: MSSQL_ENG014005 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 418628c33764c6e765e8ba855da20f0890f6191a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62666880"
---
# <a name="mssql_eng014005"></a>MSSQL_ENG014005
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14005|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Veröffentlichung konnte nicht gelöscht werden. Es besteht ein Abonnement für sie.|  
  
## <a name="explanation"></a>Erklärung  
 Sie haben versucht, eine Veröffentlichung zu löschen, der ein oder mehrere Abonnements zugeordnet sind. Eine Veröffentlichung kann aber nur gelöscht werden, wenn ihr keine Abonnements zugeordnet sind.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie erst die Abonnements, bevor Sie die Veröffentlichung löschen. Wenn Sie zum Löschen der Veröffentlichung [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, haben Sie die Möglichkeit, vor dem Löschen der Veröffentlichung automatisch alle zugeordneten Abonnements löschen zu lassen. Wenn Sie zum Löschen der Veröffentlichung gespeicherte Prozeduren verwenden, müssen Sie die Abonnements zuerst explizit löschen. Weitere Informationen finden Sie unter [Delete a Push Subscription](delete-a-push-subscription.md) und [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
 Wenn für die Veröffentlichung keine Abonnements vorhanden zu sein scheinen oder wenn dieser Fehler beim Erstellen einer Veröffentlichung angezeigt wird, könnte noch ein vorheriges Abonnement vorhanden sein, das nicht vollständig leer war, bevor versucht wurde, es zu entfernen. Führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) in der Datenbank aus, um alle mit der Replikation zusammenhängenden Objekte und Einstellungen zu entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
