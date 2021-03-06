---
title: sp_dropmergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepublication
- sp_dropmergepublication_TSQL
helpviewer_keywords:
- sp_dropmergepublication
ms.assetid: 9e1cb96e-5889-4f97-88cd-f60cf313ce68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 27fb3a99167dce450a3d4f50e9d19036db8d896f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830074"
---
# <a name="sp_dropmergepublication-transact-sql"></a>sp_dropmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Mergeveröffentlichung und den zugehörigen Momentaufnahme-Agent. Vor dem Löschen einer Mergeveröffentlichung müssen alle Abonnements gelöscht werden. Die Artikel in der Veröffentlichung werden automatisch gelöscht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergepublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der zu löschenden Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn **alle**vorhanden sind, werden alle vorhandenen Mergeveröffentlichungen und der ihr zugeordnete Momentaufnahmen-Agent Auftrag entfernt. Wenn Sie einen bestimmten Wert für die *Veröffentlichung*angeben, werden nur diese Veröffentlichung und der zugehörige Momentaufnahmen-Agent Auftrag gelöscht.  
  
`[ @ignore_distributor = ] ignore_distributor`Wird verwendet, um eine Veröffentlichung zu löschen, ohne Cleanuptasks auf dem Verteiler auszuführen. *ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**. Dieser Parameter wird auch bei der Neuinstallation des Verteilers verwendet.  
  
`[ @reserved = ] reserved`Ist für die zukünftige Verwendung reserviert. *reserved* ist vom Typ **Bit**. der Standardwert ist **0**.  
  
`[ @ignore_merge_metadata = ] ignore_merge_metadata`Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropmergepublication** wird bei der Mergereplikation verwendet.  
  
 **sp_dropmergepublication** löscht alle Artikel, die einer Veröffentlichung zugeordnet sind, rekursiv und löscht dann die Veröffentlichung selbst. Solange für eine Veröffentlichung ein Abonnement vorhanden ist, kann sie nicht gelöscht werden. Weitere Informationen zum Entfernen von Abonnements finden Sie unter [Löschen eines Pushabonnements](../../relational-databases/replication/delete-a-push-subscription.md) und [Löschen eines](../../relational-databases/replication/delete-a-pull-subscription.md)Pullabonnements.  
  
 Durch das Ausführen **sp_dropmergepublication** zum Löschen einer Veröffentlichung werden veröffentlichte Objekte nicht aus der Veröffentlichungs Datenbank oder den entsprechenden Objekten aus der Abonnement Datenbank entfernt. Verwenden \< Sie Drop Object>, um diese Objekte bei Bedarf manuell zu entfernen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_dropmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepublication-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_dropmergepublication**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen einer Veröffentlichung](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
