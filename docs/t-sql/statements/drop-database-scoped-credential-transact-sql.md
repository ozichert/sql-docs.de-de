---
title: DROP DATABASE SCOPED CREDENTIAL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP DATABASE SCOPED CREDENTIAL
- DROP_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- DROP DATABASE SCOPED CREDENTIAL statement
- credential [SQL Server], DROP DATABASE SCOPED CREDENTIAL statement
ms.assetid: 319d59f4-fa82-47ca-869b-3a9cd52900b0
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1dac766755da151913aa8b1a625710ff0be01596
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80271436"
---
# <a name="drop-database-scoped-credential-transact-sql"></a>DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Entfernt datenbankbezogene Anmeldeinformationen vom Server.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP DATABASE SCOPED CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>Argumente  
 *credential_name*  
 Der Name der datenbankbezogenen Anmeldeinformationen, die für den Server entfernt werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können den geheimen Bereich löschen, der Anmeldeinformationen zugeordnet ist, ohne die Anmeldeinformationen zu löschen, indem Sie [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md) verwenden.  
  
 Informationen zu datenbankweit gültigen Anmeldeinformationen werden in der [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)-Katalogsicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `ALTER`-Berechtigung für die Anmeldeinformationen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden datenbankbezogene gültige Anmeldeinformationen mit der Bezeichnung `SalesAccess` entfernt.  
  
```sql  
DROP DATABASE SCOPED CREDENTIAL SalesAccess;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
