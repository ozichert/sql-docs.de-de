---
title: Sicherungs Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f620bafc0a734651adfe43bcf0367ca5328dc40c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076957"
---
# <a name="backup-options"></a>Sicherungsoptionen
  Es gibt viele Möglichkeiten, um Ihre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbanken zu sichern, und für alle ist es erforderlich, dass Sie über Server Administrator-und Datenbankadministrator Berechtigungen verfügen. Sie können das **Sichern** -Dialogfeld in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]öffnen, die geeignete Optionskonfiguration auswählen und dann die Sicherung aus dem Dialogfeld starten. Sie können aber auch ein Skript erstellen, wobei die bereits in der Datei angegebenen Einstellungen verwendet werden. Dieses Skript kann dann gespeichert und beliebig häufig ausgeführt werden.  
  
## <a name="backup-and-synchronize"></a>Sichern und Synchronisieren  
 Wenn sich die Datenbank auf einer Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]befindet, können Sie die Datenbank mit der Synchronisierungsfunktion auf der lokalen Instanz sichern. Auf diese Weise können Entwicklungsbuilds einer Datenbank in die Produktionsumgebung verschoben werden. Sie können zwar auch das herkömmliche, auf Dateien basierende Sichern und Wiederherstellen verwenden, um das Entwicklungsbuild in die Produktionsumgebung zu verschieben, die Synchronisierung bietet aber zusätzliche Features. Wenn z. B. auf dem Entwicklungscomputer andere Sicherheitseinstellungen vorliegen als auf dem Produktionscomputer, haben Sie bei der Synchronisierung die Option, diese Einstellungen beizubehalten und alle Objekte außer Rollen zu synchronisieren. Außerdem erfolgt bei der Synchronisierung typischerweise ein inkrementelles Update der Objekte, die sich auf dem Quell- und auf dem Zielcomputer unterscheiden. Diese Art der inkrementellen Sicherung steht beim Verwenden der Sichern/Wiederherstellen-Funktion nicht zur Verfügung. Weitere Informationen finden Sie unter [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  Das Analysis Services-Dienstkonto muss über die Berechtigung zum Schreiben von Daten in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Administratorrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung Vollzugriff (Administrator) für die wiederherzustellende Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld "Datenbank sichern" &#40;Analysis Services Mehrdimensionale Daten&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](backup-and-restore-of-analysis-services-databases.md)   
 [Backup-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Sichern, Wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
