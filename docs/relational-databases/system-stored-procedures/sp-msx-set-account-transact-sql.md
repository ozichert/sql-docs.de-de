---
title: sp_msx_set_account (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1ba416b8e23bb56879e492e2970414f56e92776
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834396"
---
# <a name="sp_msx_set_account-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt den Namen und das Kennwort für das Masterserverkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents auf dem Zielserver fest.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @credential_name = ] 'credential_name'`Der Name der Anmelde Informationen, die für die Anmeldung beim Master Server verwendet werden sollen. Der bereitgestellte Name muss der Name vorhandener Anmeldeinformationen sein. Es muss entweder *credential_name* oder *credential_id* angegeben werden.  
  
`[ @credential_id = ] credential_id`Der Bezeichner für die Anmelde Informationen, die für die Anmeldung am Master Server verwendet werden sollen. Der Bezeichner muss ein Bezeichner für vorhandene Anmeldeinformationen sein. Es muss entweder *credential_name* oder *credential_id* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Anmeldeinformationen zum Speichern des Benutzernamens und der Kennwortinformationen, die ein Zielserver für die Anmeldung an einem Masterserver verwendet. Diese Prozedur legt die Anmeldeinformationen fest, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent für diesen Zielserver verwendet, um sich am Masterserver anzumelden.  
  
 Bei den angegebenen Anmeldeinformationen muss es sich um vorhandene Anmeldeinformationen handeln. Weitere Informationen zum Erstellen von Anmelde Informationen finden Sie unter [Create Credential &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungs Berechtigungen für **sp_msx_set_account** werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird festgelegt, dass dieser Server die Anmeldeinformationen `MsxAccount` für die Anmeldung am Masterserver verwenden soll.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Create Credential &#40;Transact-SQL-&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
