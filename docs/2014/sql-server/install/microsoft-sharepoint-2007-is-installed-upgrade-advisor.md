---
title: Microsoft SharePoint 2007 ist installiert (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6f1da295-d9b7-4948-99d3-ebd3587337c6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 84672ddf6a9b2912f3d53eef8d40727369376ba5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952090"
---
# <a name="microsoft-sharepoint-2007-is-installed-upgrade-advisor"></a>Microsoft SharePoint 2007 ist installiert (Upgrade Advisor)
  Der Upgrade Advisor hat eine Version eines SharePoint-Produkts bzw. einer SharePoint-Technologie erkannt, die nicht unterstützt wird.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Im SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird auf SharePoint 2007 nicht aktualisiert oder installiert. Das Upgrade wird blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, muss SharePoint 2007 entweder deinstalliert oder ein Upgrade von SharePoint 2007 auf ein SharePoint 2010-Produkt ausgeführt werden. Führen Sie den Upgrade Advisor nach dem Upgrade der SharePoint-Installation erneut aus, um zu bestätigen, dass keine weiteren Upgradeprobleme vorliegen.  
  
 Ein direktes Upgrade von SharePoint 2007 auf SharePoint 2013 kann nicht ausgeführt werden. Sie können aber auch eine "Double-Hop"-Datenbank anfügen, um ein Upgrade von Office SharePoint Server 2007 auf SharePoint Server 2010 und dann von SharePoint Server 2010 auf SharePoint Server 2013 durchzuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
