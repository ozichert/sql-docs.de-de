---
title: Bereinigen von Mergemetadaten (gespeicherte Prozeduren für die Replikation)
description: In diesem Artikel erfahren Sie, wie Sie Daten in Mergereplikationstabellen mithilfe von gespeicherten Prozeduren für die Replikation programmgesteuert bereinigen.
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 50a5b71edd908c3c676f036e7f61197835e49360
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75322087"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Cleanup von Mergemetadaten (Replikationsprogrammierung mit Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der Cleanup von Mergereplikationsmetadaten wird basierend auf der Beibehaltungseinstellung für die Veröffentlichung in regelmäßigen Abständen vom Merge-Agent ausgeführt. Dies erfolgt auf dem Verleger und auf dem Abonnenten in den Systemtabellen [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)und [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . Der Cleanup der Daten in diesen Tabellen kann mithilfe gespeicherter Replikationsprozeduren auch programmgesteuert ausgeführt werden.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>So führen Sie einen Cleanup von Mergemetadaten manuell aus  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md)aus.  
  
2.  (Optional) Beachten Sie die Anzahl von Zeilen, die in Schritt 1 aus den Systemtabellen [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md) und [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) entfernt und jeweils in den Ausgabeparametern `@num_genhistory_rows`, `@num_contents_rows`und `@num_tombstone_rows` zurückgegeben werden.  
  
3.  Wiederholen Sie die Schritte 1 und 2 auf dem Abonnenten, um einen Cleanup der Metadaten für die Abonnementdatenbank auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abonnementablauf und -deaktivierung](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
