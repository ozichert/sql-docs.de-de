---
title: Keine Datensynchronisierung durch Verfügbarkeitsreplikate
description: Mögliche Ursachen und Lösungen für den Fall, dass mindestens ein Verfügbarkeitsreplikat in einer Always On-Verfügbarkeitsgruppen nicht mit dem primären Replikat synchronisiert werden kann
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 66ebb11535fe2eecc6495b8c5e194d286ecc88ed
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74822581"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a>Einige Verfügbarkeitsreplikate synchronisieren keine Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Datensynchronisierungsstatus der Verfügbarkeitsreplikate|  
|**Problem**|Einige Verfügbarkeitsreplikate synchronisieren keine Daten.|  
|**Kategorie**|**Warning**|  
|**Facet**|Verfügbarkeitsgruppe|  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Richtlinie führt ein Rollup des Datensynchronisierungsstatus aller Verfügbarkeitsreplikate in der Verfügbarkeitsgruppe aus und überprüft, ob die Synchronisierung der Verfügbarkeitsreplikate ggf. nicht betriebsbereit ist. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn einer der Datensynchronisierungsstatus des Verfügbarkeitsreplikats NOT SYNCHRONIZING lautet.  
  
 Diese Richtlinie befindet sich in einem ordnungsgemäßen Zustand, wenn keiner der Datensynchronisierungsstatus des Verfügbarkeitsreplikats NOT SYNCHRONIZING lautet.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Einige Verfügbarkeitsreplikate synchronisieren keine Daten](https://go.microsoft.com/fwlink/p/?LinkId=220852) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 In dieser Verfügbarkeitsgruppe weist mindestens ein sekundäres Replikat den Synchronisierungsstatus NOT SYNCHRONIZING auf und empfängt keine Daten vom primären Replikat.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie den Verfügbarkeitsreplikat-Richtlinienstatus, um das Verfügbarkeitsreplikat mit dem Status NOT SYNCHRONIZING zu ermitteln, und beheben Sie dann das Problem des Verfügbarkeitsreplikats.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
