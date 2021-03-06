---
title: backupmediafamily (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupmediafamily
- backupmediafamily_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupmediafamily system table
- backup media [SQL Server], backupmediafamily system table
ms.assetid: ee16de24-3d95-4b2e-a094-78df2514d18a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e955cb7378a9da430608bf55d287be0fd7237ef5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807398"
---
# <a name="backupmediafamily-transact-sql"></a>backupmediafamily (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Medienfamilie. Wenn sich eine Medienfamilie in einem gespiegelten Mediensatz befindet, verfügt die Familie über eine separate Zeile für jede Spiegelung im Mediensatz. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
    
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Eindeutige ID, die den Mediensatz kennzeichnet, in dem diese Familie ein Element ist. Verweise auf **backupmediaset (media_set_id)**|  
|**family_sequence_number**|**tinyint**|Position dieser Medienfamilie im Mediensatz.|  
|**media_family_id**|**uniqueidentifier**|Eindeutige ID, die die Medienfamilie kennzeichnet. Kann den Wert NULL haben.|  
|**media_count**|**int**|Anzahl der Medien in der Medienfamilie. Kann den Wert NULL haben.|  
|**logical_device_name**|**nvarchar(128)**|Name dieses Sicherungs Mediums in **sys. backup_devices. Name**. Handelt es sich hierbei um ein temporäres Sicherungsmedium (im Gegensatz zu einem permanenten Sicherungsmedium, das in **sys. backup_devices**vorhanden ist), ist der Wert von **logical_device_name** NULL.|  
|**physical_device_name**|**nvarchar(260)**|Physischer Name des Sicherungsmediums. Kann den Wert NULL haben. Dieses Feld wird für den Sicherungs-und Wiederherstellungsprozess freigegeben. Sie kann den ursprünglichen Sicherungszielpfad oder den ursprünglichen Wiederherstellungs Quell Pfad enthalten. Abhängig davon, ob die Sicherung oder Wiederherstellung zuerst auf einem Server für eine Datenbank erfolgt ist. Beachten Sie, dass bei aufeinander folgenden Wiederherstellungen aus derselben Sicherungsdatei der Pfad unabhängig vom Speicherort des Wiederherstellungs Zeitraums nicht aktualisiert wird. Aus diesem Grund kann **physical_device_name** Feld nicht verwendet werden, um den verwendeten Wiederherstellungs Pfad anzuzeigen.|  
|**device_type**|**tinyint**|Typ des Sicherungsmediums:<br /><br /> 2 = Datenträger<br /><br /> 5 = Band<br /><br /> 7 = Virtuelles Medium<br /><br /> 9 = Azure Storage<br /><br /> 105 = ein dauerhaftes Sicherungsmedium.<br /><br /> Kann den Wert NULL haben.<br /><br /> Alle permanenten Gerätenamen und Gerätenummern finden Sie in **sys. backup_devices**.|  
|**physical_block_size**|**int**|Physische Blockgröße, die zum Schreiben der Medienfamilie verwendet wurde. Kann den Wert NULL haben.|  
|**OL**|**tinyint**|Spiegelnummer (0-3).|  
  
## <a name="remarks"></a>Bemerkungen  
 RESTORE VERIFYONLY FROM *backup_device* mit LOADHISTORY füllt die Spalten der **Backup Mediaset** -Tabelle mit den entsprechenden Werten aus dem Medien Satz Header auf.  
  
 Führen Sie die gespeicherte Prozedur [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) aus, um die Anzahl der Zeilen in dieser Tabelle und in anderen Sicherungs-und Verlaufs Tabellen zu verringern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
