---
title: Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69877c6a20e37e012925185d0b807e9579066e35
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754395"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung)
  Geben Sie bei Verwendung der Windows-Authentifizierung die Dienstkonten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an, wenn die Serverinstanzen verschiedene Konten verwenden. Diese Dienstkonten müssen alle Domänenkonten (in derselben oder vertrauenswürdigen Domäne) sein.  
  
 Wenn alle Serverinstanzen das gleiche Domänenkonto oder die zertifikatbasierte Authentifizierung verwenden, lassen Sie die Felder leer. Klicken Sie einfach auf **Fertig stellen**, und der Assistent konfiguriert automatisch die Konten auf Basis des Kontos des aktuellen Assistenten.  
  
> [!IMPORTANT]  
>  Wenn die Endpunkte für die Datenbankspiegelung der Serverinstanzen für die Verwendung von Zertifikaten konfiguriert sind, müssen Sie die Felder für die Dienstkonten leer lassen.  
  
 **So konfigurieren Sie die Datenbankspiegelung mithilfe von SQL Server Management Studio**  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Optionen  
 **Prinzipal**  
 Geben Sie das Dienstkonto der Prinzipalserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *Domain Name*\\*username*  
  
 **Spiegel**  
 Geben Sie das Dienstkonto der Spiegelserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *Domain Name*\\*username*  
  
 **Zeuge**  
 Geben Sie das Dienstkonto der Zeugenserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *Domain Name*\\*username*  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten Bank Eigenschaften &#40;Seite "Spiegelung"&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Starten Sie Datenbankspiegelungs-Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Einrichten von Anmeldekonten für die Daten Bank Spiegelung oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
