---
title: Eigenschaften von SQL Server-Browser (Registerkarte „Anmelden“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e881f0087bb3f4a6ae6e29d20b0f9103c4576be1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63137628"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Eigenschaften von SQL Server-Browser (Registerkarte Anmelden)
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Programm wird als Dienst auf dem Server ausgeführt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser lauscht auf eingehende Anforderungen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressourcen und stellt Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzen zur Verfügung, die auf dem Computer installiert sind.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser lauscht an einem UDP-Port. Nicht authentifizierte Anforderungen werden mithilfe von SSRP ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol) akzeptiert.  
  
 Das Ändern eines Kennworts für ein Konto wird sofort wirksam. Es ist kein Neustart des Dienstes erforderlich.  
  
## <a name="options"></a>Tastatur  
 **Lokales System**  
 Führen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst im Sicherheitskontext des lokalen Systemkontos aus. Verwenden Sie nach Möglichkeit ein Konto mit geringen Berechtigungen.  
  
 **Dieses Konto**  
 Geben Sie ein lokales oder ein Domänenbenutzerkonto an, das die Windows-Authentifizierung verwendet. Das Verwenden eines Domänenbenutzerkontos mit minimalen Berechtigungen für Dienste wird empfohlen. Informationen zum Auswählen eines Kontos finden Sie unter "Einrichten von Windows-Dienstkonten" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **Durchsuchen**  
 Suchen Sie nach einem Benutzer oder einem integriertem Sicherheitsprinzipal.  
  
> [!IMPORTANT]  
>  Verwenden Sie ein Konto mit geringen Berechtigungen. Informationen zu den Berechtigungen, die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst erforderlich sind, finden Sie im Abschnitt „Sicherheit“ von [SQL Server-Browserdienst](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 **Kennwort**  
 Geben Sie das Kennwort des Sicherheitsprinzipals ein.  
  
 **Kennwort bestätigen**  
 Bestätigen Sie das Kennwort des Sicherheitsprinzipals.  
  
 **Dienststatus**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist. „ **…** “ gibt einen ausstehenden Statuswechsel an.  
  
 **Starten**  
 Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst.  
  
 **Beenden**  
 Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst.  
  
 **Anhalten**  
 Halten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst an.  
  
 **Fortsetzen**  
 Setzen Sie die Ausführung eines angehaltenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdiensts fort.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Browserdienst](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
