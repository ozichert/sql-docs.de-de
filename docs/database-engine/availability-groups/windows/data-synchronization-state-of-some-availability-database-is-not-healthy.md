---
title: Datensynchronisierungsstatus einer Verfügbarkeitsdatenbank ist nicht fehlerfrei
description: Bestimmen Sie mögliche Gründe für einen nicht fehlerfreien Status der Datensynchronisierung bei einigen Datenbanken in einer Always On-Verfügbarkeitsgruppe.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c42ee67fe0c01570eadd6e3aa1d23019672172
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67968330"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a>Datensynchronisierungsstatus einer Verfügbarkeitsdatenbank ist nicht fehlerfrei
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Datensynchronisierungsstatus des Verfügbarkeitsreplikats|  
|**Problem**|Der Datensynchronisierungsstatus einer Verfügbarkeitsdatenbank ist nicht fehlerfrei.|  
|**Kategorie**|**Warning**|  
|**Facet**|Verfügbarkeitsreplikat|  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Richtlinie überprüft den Datensynchronisierungsstatus der Verfügbarkeitsdatenbank (auch bekannt als "Datenbankreplikat"). Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn der Datensynchronisierungsstatus NOT SYNCHRONIZING lautet oder wenn der Status für das Datenbankreplikat mit synchronem Commit SYNCHRONIZED lautet.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei](https://go.microsoft.com/fwlink/p/?LinkId=220863) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Mindestens eine Verfügbarkeitsdatenbank des Replikats verfügt über einen fehlerhaften Datensynchronisierungsstatus. Wenn das Replikat ein Verfügbarkeitsreplikat für asynchrone Commits ist, sollten alle Verfügbarkeitsdatenbanken den Status SYNCHRONIZING aufweisen. Falls es sich dabei um ein Verfügbarkeitsreplikat für synchrone Commits handelt, sollten sich alle Verfügbarkeitsdatenbanken im Status SYNCHRONIZED befinden. Dieses Problem kann folgende Ursachen haben:  
  
-   Die Verbindung des Verfügbarkeitsreplikats wurde getrennt.  
  
-   Die Datenverschiebung wurde angehalten.  
  
-   Auf die Datenbank kann nicht zugegriffen werden.  
  
-   Es liegt ein vorübergehendes Verzögerungsproblem aufgrund der Netzwerklatenzzeit oder der Last auf dem primären oder sekundären Replikat vor.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Beheben Sie alle Probleme in Bezug auf die Verbindung oder auf die angehaltene Datenverschiebung. Überprüfen Sie die Ereignisse für dieses Problem mit SQL Server Management Studio, und ermitteln Sie den Datenbankfehler. Führen Sie die entsprechenden Schritte der Problembehandlung für den Fehler aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
