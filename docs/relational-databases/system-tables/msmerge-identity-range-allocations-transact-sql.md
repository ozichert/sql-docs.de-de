---
title: MSmerge_identity_range_allocations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9adbc21b0c226746c879bf1b32377c93b2d76c1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829259"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_identity_range_allocations** Tabelle dient zum Nachverfolgen des Verlaufs der Identitäts Bereichs Zuweisungen für Verleger und Abonnenten für veröffentlichte Artikel. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**nvarchar(128)**|Der Name der Veröffentlichungs Datenbank.|  
|**ung**|**nvarchar(128)**|Der Name der Veröffentlichung.|  
|**Artikel**|**nvarchar(128)**|Der Name des Artikels.|  
|**Abonnenten**|**nvarchar(128)**|Den Namen des Abonnenten.|  
|**subscriber_db**|**nvarchar(128)**|Der Name der Abonnement Datenbank.|  
|**is_pub_range**|**bit**|Zeigt an, ob der Identitätsbereich einem Verleger zugewiesen ist.|  
|**ranges_allocated**|**tinyint**|Die Anzahl zugewiesener Identitätsbereiche.|  
|**range_begin**|**numerisch (38)**|Der Anfangswert des Bereichs.|  
|**range_end**|**numerisch (38)**|Der letzte Wert des Bereichs.|  
|**next_range_begin**|**numerisch (38)**|Der Anfangswert des nächsten zuzuweisenden Bereichs.|  
|**next_range_end**|**numerisch (38)**|Der letzte Wert des nächsten zuzuweisenden Bereichs.|  
|**max_used**|**numerisch (38)**|Der höchste verwendete Identitätswert.|  
|**time_of_allocation**|**datetime**|Der Zeitpunkt, zu dem die Zuweisung erfolgte.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
