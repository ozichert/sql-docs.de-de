---
title: MSSQL_ENG018456 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 671ecb319f65fae97cc2e9ad8f54c6dd0069574c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76285532"
---
# <a name="mssql_eng018456"></a>MSSQL_ENG018456
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|18456|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Fehler bei der Anmeldung für den Benutzer '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Erklärung  
 Der Fehler MSSQL_ENG018456 wird ausgelöst, wenn ein Anmeldeversuch einen Fehler erzeugt. Enthält die Fehlermeldung das Konto **distributor_admin** (Fehler bei der Anmeldung des Benutzers 'distributor_admin'.), liegt das Problem an einem Konto, das durch die Replikation verwendet wird. Die Replikation erstellt einen Remoteserver **repl_distributor**, der die Kommunikation zwischen dem Verteiler und dem Verleger ermöglicht. Die Anmeldung **distributor_admin** wird diesem Remoteserver zugeordnet und muss ein gültiges Kennwort besitzen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass Sie ein Kennwort für dieses Konto angegeben haben. Weitere Informationen finden Sie unter [Schützen des Verteilers](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
