---
title: sp_db_increased_partitions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8efcbb99bfbb7d1b4492c7945304de65192804e6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826199"
---
# <a name="sp_db_increased_partitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktiviert oder deaktiviert die Unterstützung für bis zu 15.000 Partitionen für die angegebene Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @dbname =] '*database_name*'  
 Der Name der Datenbank. *dbname* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Wenn *dbname* nicht angegeben wird, wird die aktuelle Datenbank verwendet.  
  
 [ @increased_partitions =] '*increased_partitions*'  
 Aktiviert oder deaktiviert die Unterstützung für bis zu 15.000 Partitionen in der angegebenen Datenbank. *increased_partitions* ist vom Datentyp **varchar (6)** und hat den Standardwert NULL. Zulässige Werte sind 'ON' bzw. 'TRUE', um die Unterstützung zu aktivieren, und 'OFF' bzw. 'FALSE', um die Unterstützung zu deaktivieren. Wenn *increased_partitions* nicht angegeben wird, gibt die Prozedur 1 zurück, um anzugeben, dass die Unterstützung für die angegebene Datenbank aktiviert ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER DATABASE-Berechtigung für die angegebene Datenbank.  
  
  
