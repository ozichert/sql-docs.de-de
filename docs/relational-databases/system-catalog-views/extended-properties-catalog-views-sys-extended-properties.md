---
title: sys. extended_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.extended_properties
- sys.extended_properties_TSQL
- extended_properties
- extended_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_properties catalog view
ms.assetid: 439b7299-dce3-4d26-b1c7-61be5e0df82a
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb36dddcab514692a7d6b59dee969846430d75b5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823437"
---
# <a name="extended-properties-catalog-views---sysextended_properties"></a>Katalog Sichten für erweiterte Eigenschaften-sys. extended_properties
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Gibt eine Zeile für jede erweiterte Eigenschaft in der aktuellen Datenbank zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|class|**tinyint**|Identifiziert die Elementklasse, für die die Eigenschaft vorhanden ist. Kann eines der folgenden Elemente sein:<br /><br /> 0 = Datenbank<br /><br /> 1 = Objekt oder Spalte<br /><br /> 2 = Parameter<br /><br /> 3 = Schema<br /><br /> 4 = Datenbankprinzipal<br /><br /> 5 = Assembly<br /><br /> 6 = Typ<br /><br /> 7 = Index<br /><br /> 10 = XML-Schemaauflistung<br /><br /> 15 = Nachrichtentyp<br /><br /> 16 = Dienstvertrag<br /><br /> 17 = Dienst<br /><br /> 18 = Remotedienstbindung<br /><br /> 19 = Route<br /><br /> 20 = Datenspeicher (Dateigruppe oder Partitionsschema)<br /><br /> 21 = Partitionsfunktion<br /><br /> 22 = Datenbankdatei<br /><br /> 27 = Planhinweisliste|  
|class_desc|**nvarchar(60)**|Beschreibung der Klasse, für die die erweiterte Eigenschaft vorhanden ist. Kann eines der folgenden Elemente sein:<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> PARAMETER<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> INDEX<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> DATASPACE<br /><br /> PARTITION_FUNCTION<br /><br /> DATABASE_FILE<br /><br /> PLAN_GUIDE|  
|major_id|**int**|ID des Elements, für das die erweiterte Eigenschaft vorhanden ist, interpretiert gemäß der entsprechenden Klasse. Bei den meisten Elementen ist dies die ID, die für die Darstellung der Klasse gilt. Die Interpretation von Haupt-IDs, die nicht dem Standard entsprechen, lautet wie folgt:<br /><br /> Wenn class gleich 0 ist, ist major_id immer 0.<br /><br /> Wenn die Klasse den Wert 1, 2 oder 7 hat, major_id object_id ist.|  
|minor_id|**int**|Sekundäre ID des Elements, für das die erweiterte Eigenschaft vorhanden ist, interpretiert gemäß der entsprechenden Klasse. Bei den meisten Elementen ist dies der Wert 0; andernfalls lautet die ID wie folgt:<br /><br /> Wenn class = 1, ist minor_id bei einer Spalte gleich column_id, bei einem Objekt gleich 0.<br /><br /> Wenn class = 2, ist minor_id gleich parameter_id.<br /><br /> Wenn class 7 = minor_id ist die index_id.|  
|name|**sysname**|Eigenschaftenname, durch class, major_id und minor_id eindeutig bestimmt.|  
|value|**sql_variant**|Wert der erweiterten Eigenschaft|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalog Sichten für erweiterte Eigenschaften &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)   
 [sys. fn_listextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)  
  
  
