---
title: REVOKE – Sucheigenschaftenlisten-Berechtigungen
description: Heben Sie Berechtigungen für eine Sucheigenschaftenliste auf.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], permissions
- search property lists [SQL Server], permissions
- revoking permissions [SQL Server]
- REVOKE statement, search property list permissions
ms.assetid: a6b8b37c-0015-4596-898c-51a567659e2e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5f8d098a6a06605a6d3b1d611d58e2dc75e97591
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634102"
---
# <a name="revoke-search-property-list-permissions-transact-sql"></a>REVOKE-Sucheigenschaftenlisten-Berechtigungen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt Berechtigungen für eine Sucheigenschaftenliste auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON  
        SEARCH PROPERTY LIST :: search_property_list_name  
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Argumente  
 GRANT OPTION FOR  
 Gibt an, dass das Recht zum Erteilen der angegebenen Berechtigung für andere Prinzipale aufgehoben wird. Die Berechtigung selbst wird nicht aufgehoben.  
  
> [!IMPORTANT]  
>  Falls der Prinzipal die angegebene Berechtigung ohne GRANT-Option besitzt, wird die Berechtigung selbst aufgehoben.  
  
 *permission*  
 Der Name einer Berechtigung. Die gültigen Zuordnungen von Berechtigungen zu sicherungsfähigen Elementen werden im Abschnitt mit den Hinweisen weiter unten in diesem Thema beschrieben.  
  
 ON SEARCH PROPERTY LIST **::** _search_property_list_name_  
 Gibt die Sucheigenschaftenliste an, für die die Berechtigung aufgehoben wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 *database_principal*  
 Gibt den Prinzipal an, für den die Berechtigung aufgehoben wird. Die folgenden Prinzipale sind möglich:  
  
-   Datenbankbenutzer  
  
-   Datenbankrolle (database role)  
  
-   Anwendungsrolle  
  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
 CASCADE  
 Gibt an, dass die aufgehobene Berechtigung auch für andere Prinzipale aufgehoben wird, denen diese Berechtigung vom Prinzipal erteilt wurde.  
  
> [!CAUTION]  
>  Durch ein kaskadiertes Aufheben einer Berechtigung, die mit WITH GRANT OPTION erteilt wurde, werden sowohl GRANT als auch DENY für diese Berechtigung aufgehoben.  
  
 AS *revoking_principal*  
 Gibt einen Prinzipal an, von dem der Prinzipal, der diese Abfrage ausführt, sein Recht zum Aufheben der Berechtigung ableitet. Die folgenden Prinzipale sind möglich:  
  
-   Datenbankbenutzer  
  
-   Datenbankrolle (database role)  
  
-   Anwendungsrolle  
  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="search-property-list-permissions"></a>SEARCH PROPERTY LIST-Berechtigungen  
 Eine Sucheigenschaftenliste ist ein sicherungsfähiges Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und restriktivsten Berechtigungen, die für eine Sucheigenschaftenliste aufgehoben werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Sucheigenschaftenlisten-Berechtigung|Impliziert durch Sucheigenschaftenlisten-Berechtigung|Impliziert durch Datenbankberechtigung|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für den Volltextkatalog.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DENY (Berechtigungen für Sucheigenschaftenlisten) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-search-property-list-permissions-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [GRANT (Berechtigungen für Sucheigenschaftenlisten) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
