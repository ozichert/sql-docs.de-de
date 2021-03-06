---
title: sys. fulltext_semantic_languages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: c060f08ff70e04a22af1eb9de09aeb1e3bf4ff71
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133777"
---
# <a name="sysfulltext_semantic_languages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Sprache zurück, deren Statistikmodell für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert ist. Wenn ein Sprachenmodell registriert ist, wird diese Sprache für die semantische Indizierung aktiviert.  
  
 Diese Katalog Sicht ähnelt [sys. fulltext_languages &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
    
||||  
|-|-|-|  
|**Spaltenname**|**Typ**|**Beschreibung**|  
|lcid|INT|Microsoft Windows-Gebietsschemabezeichner (Locale Identifier, LCID) für die Sprache.|  
|Name|sysname|Ist entweder der Wert des Alias in [sys. syslanguages &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) , der dem Wert von **LCID**entspricht, oder die Zeichen folgen Darstellung der numerischen LCID.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Weitere Informationen zur Datenbank für die semantische sprach Statistik, die zur Unterstützung der semantischen Indizierung installiert wird, finden Sie in der Katalog Sicht [sys. fulltext_semantic_language_statistics_database &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie **sys. fulltext_semantic_languages** abgefragt wird, um Informationen zu allen Sprachmodellen zu erhalten, die für die semantische Indizierung in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]registriert sind.  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
