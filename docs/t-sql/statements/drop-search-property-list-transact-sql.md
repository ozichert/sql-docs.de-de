---
title: DROP SEARCH PROPERTY LIST (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 746d2f33d780e4eada7accabdd029998c9e61742
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68070181"
---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Löscht eine Eigenschaftenliste aus der aktuellen Datenbank, wenn die Sucheigenschaftenliste derzeit keinem Volltextindex in der Datenbank zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>Argumente  
 *property_list_name*  
 Der Name der Sucheigenschaftenliste, die gelöscht werden soll. *property_list_name* ist ein Bezeichner.  
  
 Mit der [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)-Katalogsicht können Sie die Namen der vorhandenen Eigenschaftenlisten wie folgt aufrufen:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können keine Sucheigenschaftenliste aus einer Datenbank löschen, während diese einem Volltextindex zugeordnet ist. Um eine Sucheigenschaftenliste aus einem angegebenen Volltextindex zu löschen, geben Sie die [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)-Anweisung und die SET SEARCH PROPERTY LIST-Klausel mit OFF oder dem Namen einer anderen Sucheigenschaftenliste an.  
  
 **Anzeigen der Eigenschaftenlisten auf einer Serverinstanz**  
  
-   [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **Anzeigen der den Volltextindizes zugeordneten Eigenschaftenlisten**  
  
-   [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **Entfernen einer Eigenschaftenliste aus einem Volltextindex**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert CONTROL-Berechtigungen für die Sucheigenschaftenliste.  
  
> [!NOTE]  
>  Der Besitzer der Eigenschaftenliste kann CONTROL-Berechtigungen für die Liste erteilen. Besitzer der Sucheigenschaftenliste ist standardmäßig der Benutzer, der sie erstellt. Der Besitzer kann mithilfe der [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung geändert werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `JobCandidateProperties`-Eigenschaftenliste aus der `AdventureWorks2012`-Datenbank gelöscht.  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  
