---
title: Webserverinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b5f5c2385b4c58447db008544124ae9048566958
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63199941"
---
# <a name="web-server-information"></a>Webserverinformationen
  Webserverinformationen sind erforderlich, um die Websynchronisierungsoption für die Mergereplikation zu verwenden. Informationen zur Konfiguration der Websynchronisierung finden Sie unter [Konfigurieren der Websynchronisierung](configure-web-synchronization.md).  
  
## <a name="options"></a>Tastatur  
 **Webserveradresse**  
 Wenn Sie auf der Seite **FTP-Momentaufnahme und Internet** des Dialogfelds **Veröffentlichungseigenschaften** eine Webserveradresse angegeben haben, wird diese in diesem Feld als Standardwert angezeigt. Übernehmen Sie entweder den Standardwert, oder geben Sie eine vollqualifizierte Webserveradresse für den Server für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internetinformationsdienste (IIS, Internet Information Services) an, der diese Abonnements synchronisiert.  
  
 **Wie stellt der Abonnent eine Verbindung mit dem Webserver her?**  
 Geben Sie den für das Herstellen einer Verbindung mit dem Webserver verwendeten Authentifizierungstyp an. Sie sollten für SSL-Verbindungen (Secure Sockets Layer) mit dem IIS-Server die Standardauthentifizierung verwenden. Geben Sie bei Auswahl der Standardauthentifizierung den Anmeldenamen und das Kennwort ein, die beim Herstellen der Verbindung vom Abonnenten zum IIS-Server verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Anzeigen und Ändern der Eigenschaften von Pullabonnements](view-and-modify-pull-subscription-properties.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Websynchronisierung für die Mergereplikation](web-synchronization-for-merge-replication.md)  
  
  
