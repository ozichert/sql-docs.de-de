---
title: sys. server_audit_specification_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_audit_specification_details
- sys.server_audit_specification_details_TSQL
- server_audit_specification_details_TSQL
- sys.server_audit_specification_details
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_audit_specification_details catalog view
ms.assetid: 792724dc-402e-4b17-9f2c-029d910bf88e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68283872613baf6cb64546ef79a9f03996815439
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834067"
---
# <a name="sysserver_audit_specification_details-transact-sql"></a>sys.server_audit_specification_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen über Details der Serverüberwachungsspezifikation (Aktionen) in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Überwachung auf einer Serverinstanz. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md). Eine Liste aller audit_action_id und deren Namen finden Sie unter [sys. dm_audit_actions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|server_specification_id|**int**|ID der Serverüberwachungsspezifikation|  
|audit_action_id|**int**|ID der Überwachungsaktion|  
|audit_action_name|**sysname**|Name der Gruppe oder Name der Überwachungsaktion|  
|class|**tinyint**|Reserved|  
|class_desc|**nvarchar(60)**|Reserved|  
|major_id|**int**|Reserved|  
|minor_id|**int**|Reserved|  
|audited_principal_id|**int**|Reserved|  
|audited_result|**nvarchar(60)**|Überwachtes Ergebnis:<br /><br /> - SUCCESS AND FAILURE<br /><br /> - SUCCESS<br /><br /> - FAILURE|  
|is_group|**bit**|Zeigt an, ob das überwachte Objekt eine Gruppe ist:<br /><br /> 0 – Keine Gruppe<br /><br /> 1 – Gruppe|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale mit der Berechtigung **Alter any Server Audit** oder **View any Definition** haben Zugriff auf diese Katalog Sicht. Außerdem darf dem Prinzipal die **View any Definition** -Berechtigung nicht verweigert werden.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Create Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [Alter Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [Drop Server Audit &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Create Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [Alter Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [Drop Server Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Create Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [Alter Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [Drop Database Audit Specification &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [Alter Authorization &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys. fn_get_audit_file &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys. server_audits &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys. server_file_audits &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_actions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
