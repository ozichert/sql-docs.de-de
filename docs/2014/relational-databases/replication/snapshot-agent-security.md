---
title: Sicherheit für den Momentaufnahme-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e63cee642738036933b0a1e2a9da6b48192fba9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62676643"
---
# <a name="snapshot-agent-security"></a>Sicherheit für den Momentaufnahme-Agent
  Mithilfe des Dialogfelds **Sicherheit für den Momentaufnahme-Agent** können Sie folgende Angaben machen:  
  
-   Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, unter dem der Momentaufnahme-Agent auf dem Verteiler ausgeführt wird. Das Windows-Konto wird auch als *Prozesskonto*bezeichnet, da der Agentprozess unter diesem Konto ausgeführt wird.  
  
-   Kontext, unter dem der Momentaufnahmen-Agent Verbindungen mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger herstellt Die Verbindung kann entweder durch Identitätswechsel zum Windows-Konto oder unter dem Kontext eines von Ihnen angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kontos hergestellt werden.  
  
    > [!NOTE]  
    >  Der Momentaufnahme-Agent stellt Verbindungen mit dem Verleger her, auch wenn der Verleger und der Verteiler auf demselben Computer ausgeführt werden. Der Momentaufnahme-Agent stellt auch Verbindungen mit dem Verteiler her. Diese Verbindungen werden immer durch einen Identitätswechsel zum Windows-Konto hergestellt, unter dem der Agent ausgeführt wird.  
  
     Geben Sie für Oracle-Verleger im Dialogfeld **Verlegereigenschaften** den Kontext an, unter dem der Momentaufnahme-Agent eine Verbindung mit dem Verleger herstellt (das Dialogfeld ist vom Dialogfeld **Verteilereigenschaften** aus verfügbar). Weitere Informationen finden Sie unter [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Alle Konten müssen gültig sein, und für jedes Konto muss das richtige Kennwort angegeben sein. Konten und Kennwörter werden erst bei der Ausführung eines Agents überprüft.  
  
## <a name="options"></a>Tastatur  
 **Prozesskonto**  
 Geben Sie das Windows-Konto an, unter dem der Momentaufnahme-Agent auf dem Verteiler ausgeführt wird. Das angegebene Windows-Konto muss folgende Bedingungen erfüllen:  
  
-   Es muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.  
  
-   Es muss über Schreibberechtigungen für die Momentaufnahme-Freigabe verfügen.  
  
 **Kennwort** und **Kennwort bestätigen**  
 In diese Felder geben Sie das Kennwort für das Windows-Konto ein.  
  
 **Verbindung mit dem Verleger herstellen**  
 Wählen Sie aus, ob der Momentaufnahme-Agent die Verbindungen mit dem Verleger entweder durch Annahme der Identität des im Textfeld **Prozesskonto** angegebenen Kontos oder mithilfe eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kontos herstellen soll. Wenn Sie sich für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto entscheiden, müssen Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzernamen und ein Kennwort eingeben.  
  
> [!NOTE]  
>  Es wird empfohlen, kein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto zu verwenden und stattdessen festzulegen, dass der Agent die Identität des Windows-Kontos annimmt.  
  
 Das für die Verbindung verwendete Windows-Konto bzw. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Veröffentlichungsdatenbank sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Anmeldungen und Kenn Wörtern in der Replikation](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Sicherheitsmodell des Replikations-Agents](security/replication-agent-security-model.md)   
 [Replikations-Agents (Übersicht)](agents/replication-agents-overview.md)   
 [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)  
  
  
