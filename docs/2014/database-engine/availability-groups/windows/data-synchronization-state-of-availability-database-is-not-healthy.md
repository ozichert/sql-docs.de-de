---
title: Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 895e65f9538b588299520e9e22192935535b7931
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62815117"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Datensynchronisierungsstatus der Verfügbarkeitsdatenbank|  
|**Problem**|Der Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei.|  
|**Kategorie**|**Warning**|  
|**Facet**|Verfügbarkeitsdatenbank|  
  
## <a name="description"></a>Beschreibung  
 Diese Richtlinie führt ein Rollup des Datensynchronisierungsstatus aller Verfügbarkeitsdatenbanken (auch bekannt als "Datenbankreplikate") im Verfügbarkeitsreplikat aus. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn ein beliebiges Datenbankreplikat nicht den erwarteten Datensynchronisierungsstatus aufweist. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für dieses Release von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Datensynchronisierungsstatus einer Verfügbarkeitsdatenbank ist nicht fehlerfrei](https://go.microsoft.com/fwlink/p/?LinkId=220858) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Der Datensynchronisierungsstatus dieser Verfügbarkeitsdatenbank ist fehlerhaft. Auf einem Verfügbarkeitsreplikat für asynchrone Commits sollte sich jede Verfügbarkeitsdatenbank im Status SYNCHRONIZING befinden. Auf einem Replikat für synchrone Commits muss sich jede Verfügbarkeitsdatenbank im Status SYNCHRONIZED befinden.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie die Datenbankreplikatrichtlinie zum Suchen nach dem Datenbankreplikat mit einem fehlerhaften Datensynchronisierungsstatus, und beheben Sie das Problem für das Datenbankreplikat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
