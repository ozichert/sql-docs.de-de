---
title: MSpeer_topologyresponse (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_topologyresponse
- MSpeer_topologyresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyresponse
ms.assetid: 1bc5c0c6-c432-405c-89fd-e953d173a247
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 29f4843debb47787cae38cb774957051137cebe5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812499"
---
# <a name="mspeer_topologyresponse-transact-sql"></a>MSpeer_topologyresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Wird in der Peer-zu-Peer-Replikation verwendet, um die Antwort jedes Knotens auf eine Topologiestatusanforderung zu speichern. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Identifiziert einen Eintrag für eine Topologiestatusanforderung in der [Mspeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) Tabelle.|  
|peer|**sysname**|Name der Serverinstanz, die die Antwort generiert hat.|  
|peer_version|**int**|Kennzeichnet die Versionsnummer des Verlegers|  
|peer_db|**sysname**|Abonnementdatenbank auf dem Peer, der die Antwort generiert hat.|  
|originator_id|**int**|Identifiziert jeden Knoten in der Topologie zum Zweck der Konflikterkennung. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Zeitraum in Tagen, für den Metadaten in Konflikttabellen gespeichert werden.|  
|received_date|**datetime**|Uhrzeit, zu der die Topologieanforderung empfangen wurde.|  
|connection_info|**xml**|Informationen über den Knoten, der auf die Anforderung reagiert hat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
