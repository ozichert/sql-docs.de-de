---
title: syscollector_collection_items (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8f55a496a5d5fc4a0a0c499056eff5e00bd1ea8
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833813"
---
# <a name="syscollector_collection_items-transact-sql"></a>syscollector_collection_items (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen über ein Element in einem Sammlungssatz zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|Identifiziert den Sammlungssatz. Lässt keine NULL-Werte zu.|  
|**collection_item_id**|**int**|Identifiziert ein Element im Sammlungssatz. Lässt keine NULL-Werte zu.|  
|**collector_type_uid**|**uniqueidentifier**|Die für die Identifikation des Sammlertyps verwendete GUID. Lässt keine NULL-Werte zu.|  
|**name**|**nvarchar(4000)**|Der Name des Sammlungssatzes. Lässt NULL-Werte zu.|  
|**frequency**|**int**|Die Häufigkeit, mit der Daten von einem Sammelelement gesammelt werden. Lässt keine NULL-Werte zu.|  
|**parameters**|**xml**|Beschreibt die Parametrisierung für den Sammlertyp, der dem Sammelelement zugeordnet ist. Das XML-Schema für dieses Sammel Element wird mit dem XML-Schema (XSD) überprüft, das in der **parameter_schema** für einen bestimmten Sammlertyp gespeichert ist. Lässt NULL-Werte zu. Weitere Informationen finden Sie unter [syscollector_collector_types &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT für **dc_operator**, **dc_proxy**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Datensammler Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
