---
title: sys. data_spaces (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- data_spaces
- sys.data_spaces_TSQL
- sys.data_spaces
- data_spaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.data_spaces catalog view
ms.assetid: f39d55fe-2c0f-472d-a77f-cebc6fea95b5
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab7be8ba4aba0241b45800b77e28b44e168ab182
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823410"
---
# <a name="sysdata_spaces-transact-sql"></a>sys.data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jeden Datenspeicherplatz. Dies kann eine Dateigruppe, ein Partitionsschema oder eine FILESTREAM-Datendateigruppe sein.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Name des Datenspeicherplatzes, eindeutig innerhalb der Datenbank.|  
|data_space_id|**int**|ID-Nummer des Datenspeicherplatzes, eindeutig innerhalb der Datenbank.|  
|Typ|**char (2)**|Typ des Datenspeicherplatzes:<br /><br /> FG = Dateigruppe (Filegroup)<br /><br /> FD = FILESTREAM-Datendateigruppe<br /><br /> FX = speicheroptimierte Tabellendateigruppe<br /><br /> **Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> PS = Partitionsschema (Partition scheme)|  
|type_desc|**nvarchar(60)**|Beschreibung des Datenspeicherplatztyps:<br /><br /> FILESTREAM_DATA_FILEGROUP<br /><br /> MEMORY_OPTIMIZED_DATA_FILEGROUP<br /><br /> **Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> PARTITION_SCHEME<br /><br /> ROWS_FILEGROUP|  
|is_default|**bit**|1 = Dies ist der Standard-Datenspeicherplatz. Dieser Standard-Datenspeicherplatz wird verwendet, wenn in einer CREATE TABLE- oder CREATE INDEX-Anweisung keine Dateigruppe und kein Partitionsschema angegeben ist.<br /><br /> 0 = Dies ist nicht der Standard-Datenspeicherplatz.|  
|is_system|**bit**|**Gilt für**:  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br /><br /> 1 = Der Datenbereich wird für Volltextindexfragmente verwendet.<br /><br /> 0 = Der Datenbereich wird nicht für Volltextindexfragmente verwendet.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbereiche &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. destination_data_spaces &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys. File Groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys. partition_schemes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
