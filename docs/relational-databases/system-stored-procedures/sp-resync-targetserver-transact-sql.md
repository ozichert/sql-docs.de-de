---
title: sp_resync_targetserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_resync_targetserver
- sp_resync_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resync_targetserver
ms.assetid: 40e44df7-d3e3-44ee-b149-08aba629a21f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6aa435a7c0a65634323f6c3f90874cd3694fa876
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82816842"
---
# <a name="sp_resync_targetserver-transact-sql"></a>sp_resync_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Synchronisiert alle Multiserveraufträge auf dem angegebenen Zielserver neu.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_resync_targetserver  
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server'`Der Name des Servers, der neu synchronisiert werden soll. *server* ist vom Datentyp **sysname**und hat keinen Standardwert. Mit **ALL** werden alle Zielserver neu synchronisiert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Meldet das Ergebnis von **sp_post_msx_operation** -Aktionen.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_resync_targetserver** löscht die aktuellen Anweisungen für den Zielserver und stellt neue Anweisungen für den Zielserver zum Herunterladen bereit. Die neuen Anweisungen bestehen aus einer Anweisung zum Löschen aller Multiserveraufträge, gefolgt von einem Eintrag für jeden Auftrag, der an diesen Server gerichtet ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigungen zum Ausführen dieser Prozedur werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Zielserver `SEATTLE1` neu synchronisiert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_resync_targetserver  
    N'SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_downloadlist &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)   
 [sp_post_msx_operation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
