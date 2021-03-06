---
title: sp_dropmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepullsubscription
- sp_dropmergepullsubscription_TSQL
helpviewer_keywords:
- sp_dropmergepullsubscription
ms.assetid: 9301dd80-72f7-4adb-9b13-87e7f9114248
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1a22fdc297c4ce7310b8d71b65dbe1cd4e0abf04
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830056"
---
# <a name="sp_dropmergepullsubscription-transact-sql"></a>sp_dropmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht ein Mergepullabonnement. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergepullsubscription [ @publication= ] 'publication'   
        , [ @publisher= ] 'publisher'   
        , [ @publisher_db= ] 'publisher_db'   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter ist erforderlich. Geben Sie den Wert **alle** an, um Abonnements für alle Veröffentlichungen zu entfernen.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter ist erforderlich.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter ist erforderlich.  
  
`[ @reserved = ] 'reserved'`Ist für die zukünftige Verwendung reserviert. *reserved* ist vom Typ **Bit**. der Standardwert ist **0**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropmergepullsubscription** wird bei der Mergereplikation verwendet.  
  
 **sp_dropmergepullsubscription** löscht die Merge-Agent für dieses Mergepullabonnement, obwohl der Merge-Agent nicht in **sp_addmergepullsubscription**erstellt wird.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepullsubscrip_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der Benutzer, der das Mergepullabonnement erstellt hat, können **sp_dropmergepullsubscription**ausführen. Die **db_owner** festgelegte Daten Bank Rolle kann nur **sp_dropmergepullsubscription** ausgeführt werden, wenn der Benutzer, der das Mergepullabonnement erstellt hat, zu dieser Rolle gehört.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen eines Pullabonnements](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)  
  
  
