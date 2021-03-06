---
title: Sicherheit für den Verteilungs-Agent (Peer-zu-Peer-Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78d8baed7783459db79bb9facb0141cc570c4127
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721381"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>Sicherheit für den Verteilungs-Agent (Peer-zu-Peer-Replikation)
   Mithilfe der Seite **Sicherheit für den Verteilungs-Agent** können Sie die Konten angeben, unter denen der Verteilungs-Agent ausgeführt wird und Verbindungen mit den Computern in einer Peer-zu-Peer-Topologie hergestellt werden. Informationen zu erforderlichen Berechtigungen für Agents und bewährten Methoden für die Replikationssicherheit finden Sie unter [Sicherheitsmodell des Replikations-Agent](security/replication-agent-security-model.md) und [Replikationssicherheit, bewährte Methoden](security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Wenn der Verteilungs-Agent für ein Abonnement bereits in einer früheren Ausführung dieses Assistenten konfiguriert wurde, können Sie die entsprechenden in diesem Assistenten verwendeten Anmeldeinformationen nicht ändern. Von Ihnen neu angegebene Anmeldeinformationen werden ignoriert. Sie können die Anmeldeinformationen im Dialogfeld **Abonnementeigenschaften** ändern. Weitere Informationen finden Sie unter [anzeigen und Ändern von Replikations Sicherheitseinstellungen](security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Optionen  
 Klicken Sie in der Zeile für jeden Abonnenten auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um auf das Dialogfeld **Sicherheit für den Verteilungs-Agent** zuzugreifen. Klicken Sie im geöffneten Dialogfeld **Sicherheit für den Verteilungs-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die von den Agents verwendeten Konten erforderlich sind.  
  
 Wenn Sie die Einstellungen in einem der beiden Dialogfelder eingegeben haben, werden im Raster die Verbindungsinformationen zu dem Abonnenten angezeigt.  
  
 **Agent für Abonnent**  
 Der Name der einzelnen Peers.  
  
 **Peerdatenbank**  
 Die Datenbank auf dem Peer, der sowohl als Veröffentlichungs- als auch als Abonnementdatenbank dient.  
  
 **Verbindung mit Verteiler**  
 Der Kontext, unter dem die Verbindung mit dem Verteiler hergestellt wird. Lokale Verbindungen werden immer unter dem Kontext des Windows-Kontos hergestellt, das zum Ausführen der Agents verwendet wird. Dieser Assistent erstellt Pushabonnements (die Verbindung mit dem Verteiler ist gleichzeitig die lokale Verbindung), sodass in dem betreffenden Feld immer **Impersonate '\<Domain>\\<Login\>'** oder **Impersonate '\<Computer>\\<Login\>'** angezeigt wird.  
  
 **Verbindung mit Abonnent**  
 Der Kontext, unter dem die Verbindung mit dem Abonnenten hergestellt wird. Die Verbindung kann entweder mithilfe des Kontexts des Windows-Kontos hergestellt werden, unter dem der Agent ausgeführt wird, oder mithilfe des Kontexts einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung. Das Feld zeigt eine der folgenden Angaben **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** oder **Impersonate '\<Computer>\\<Login\>'** an. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, alle Verbindungen unter dem Kontext des Windows-Kontos herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikations Programmierung mit Transact-SQL&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-zu-Peer-Transaktionsreplikation](transactional/peer-to-peer-transactional-replication.md)  
  
  
