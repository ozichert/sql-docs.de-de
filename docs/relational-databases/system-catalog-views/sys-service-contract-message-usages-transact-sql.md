---
title: sys. service_contract_message_usages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7a958bf38af003fdbc76ebe3b33b5faabf8e5d11
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831347"
---
# <a name="sysservice_contract_message_usages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Katalogsicht enthält eine Zeile pro Vertrag/Nachrichtentyp-Paar.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|Bezeichner des Vertrags, der den Nachrichtentyp verwendet. Lässt keine NULL-Werte zu.|  
|**message_type_id**|**int**|Bezeichner des Nachrichtentyps, der vom Vertrag verwendet wird. Lässt keine NULL-Werte zu.|  
|**is_sent_by_initiator**|**bit**|Der Nachrichtentyp kann vom Konversationsinitiator gesendet werden. Lässt keine NULL-Werte zu.|  
|**is_sent_by_target**|**bit**|Der Nachrichtentyp kann vom Konversationsziel gesendet werden. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
