---
title: sys. dm_pdw_component_health_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dd339e939974d14f4de40eba9dc97dcd73a04fce
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82811287"
---
# <a name="sysdm_pdw_component_health_status-transact-sql"></a>sys. dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen über den aktuellen Zustand der Gerätekomponenten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Nicht NULL|  
|component_id|INT|Die ID der Komponente. Weitere Informationen finden Sie unter [sys. pdw_health_components &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, property_id und component_instance_id bilden den Schlüssel für diese Sicht.|Nicht NULL|  
|property_id|**int**|Die ID der Eigenschaft. Weitere Informationen finden Sie unter [sys. pdw_health_component_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Identifiziert eine Instanz einer Komponente. Beispielsweise kann eine Instanz einer CPU durch component_instance_id = ' CPU1 ' identifiziert werden.<br /><br /> pdw_node_id, component_id, property_id und component_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|property_value|**nvarchar(255)**|Der aktuelle Eigenschafts Wert.|NULL|  
|update_time|**datetime**|Der Zeitpunkt, zu dem die Metrik zuletzt aktualisiert wurde.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
