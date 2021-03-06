---
title: sys. sensitivity_classifications (Transact-SQL) | Microsoft-Dokumentation
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- rank
monikerRange: '>= sql-server-ver15 || = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4ee73a840be6ec29e3ac34c4c43fe0c8e87185f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "77903902"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Gibt eine Zeile für jedes klassifizierte Element in der Datenbank zurück.

|Spaltenname|Datentyp|BESCHREIBUNG|
|-----------------|---------------|-----------------|  
|**class**|**int**|Identifiziert die Klasse des Elements, für das die Klassifizierung vorhanden ist. Hat immer den Wert 1 (die eine Spalte darstellt)|  
|**class_desc**|**varchar (16)**|Eine Beschreibung der Klasse des Elements, für das die Klassifizierung vorhanden ist. hat immer den Wert *OBJECT_OR_COLUMN*|  
|**major_id**|**int**|Stellt die ID der Tabelle dar, die die klassifizierte Spalte enthält. Dies entspricht sys. all_objects. object_id|  
|**minor_id**|**int**|Stellt die ID der Spalte dar, für die die Klassifizierung vorhanden ist. Dies entspricht sys. ALL_COLUMNS. column_id|   
|**label**|**sysname**|Die Bezeichnung (Menschen lesbar), die für die Vertraulichkeits Klassifizierung zugewiesen ist.|  
|**label_id**|**sysname**|Eine ID, die der Bezeichnung zugeordnet ist und von einem Informationsschutz System wie z. b. Azure Information Protection (AIP) verwendet werden kann.|  
|**information_type**|**sysname**|Der Informationstyp (Menschen lesbar), der der Sensitivität-Klassifizierung zugewiesen ist.|  
|**information_type_id**|**sysname**|Eine ID, die dem Informationstyp zugeordnet ist und von einem Informationsschutz System wie z. b. Azure Information Protection (AIP) verwendet werden kann.|  
|**gehören**|**int**|Ein numerischer Wert des Rangs: <br><br>0 für keine<br>10 für niedrig<br>20 für Mittel<br>30 für hoch<br>40 für kritisch| 
|**rank_desc**|**sysname**|Textdarstellung des Rangs:  <br><br>keine, niedrig, Mittel, hoch, kritisch|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Bemerkungen  

- Diese Ansicht bietet Einblick in den Klassifizierungs Status der Datenbank. Sie kann zum Verwalten der Daten Bank Klassifizierungen sowie zum Erstellen von Berichten verwendet werden.
- Derzeit wird nur die Klassifizierung von Daten Bank Spalten unterstützt.
 
## <a name="examples"></a>Beispiele

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Auflisten aller klassifizierten Spalten und der entsprechenden Klassifizierung

Im folgenden Beispiel wird eine Tabelle mit dem Tabellennamen, dem Spaltennamen, der Bezeichnung, der Bezeichnungs-ID, dem Informationstyp und der Informationstyp-ID für jede klassifizierte Spalte in der Datenbank zurückgegeben.

> [!NOTE]
> Bezeichnung ist ein Schlüsselwort für Azure SQL Data Warehouse.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID], [Rank], [Rank_Desc]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Berechtigungen  
 Erfordert die **View any Sensitivität-Klassifizierungs** Berechtigung. 
 
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>Weitere Informationen  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Azure SQL-Datenbank – Datenermittlung und -klassifizierung](https://aka.ms/sqlip)
