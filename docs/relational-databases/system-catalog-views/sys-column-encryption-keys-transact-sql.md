---
title: sys. column_encryption_keys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_encryption_keys
- column_encryption_keys_TSQL
- sys.column_encryption_keys_TSQL
- column_encryption_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_encryption_keys catalog view
ms.assetid: 43980dd8-b9b1-4869-a304-2c183ae8977d
author: jaszymas
ms.author: jaszymas
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4cd6b4a4cb8eeed0dd0a2a78adc2d39c6a2e895d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73593729"
---
# <a name="syscolumn_encryption_keys--transact-sql"></a>sys. column_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-xxx-md.md)]

  Gibt Informationen zu Spalten Verschlüsselungsschlüsseln (ceks) zurück, die mit der [Create Column Encryption Key](../../t-sql/statements/create-column-encryption-key-transact-sql.md) -Anweisung erstellt wurden. Jede Zeile stellt einen Cek dar.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des CMK.|  
|**column_encryption_key_id**|**int**|ID des Cek.|  
|**create_date**|**datetime**|Das Datum, an dem der Cek erstellt wurde.|  
|**modify_date**|**datetime**|Das Datum, an dem der Cek zuletzt geändert wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **View any Column Encryption Key** -Berechtigung.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Spalten Verschlüsselungsschlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [Alter Column Encryption Key &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [Löschen des Spalten Verschlüsselungsschlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Erstellen eines Spalten Hauptschlüssels &#40;Transact-SQL-&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted mit sicheren Enklaven](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Übersicht über die Schlüsselverwaltung für Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)    

  
  
