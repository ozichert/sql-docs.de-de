---
title: catalog.environment_references (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: efec53ef-3e5a-4b76-b71d-a0cf9e11ac00
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 848e337ecfacd16df1b34a60e392b572b612735d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295199"
---
# <a name="catalogenvironment_references-ssisdb-database"></a>catalog.environment_references (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Umgebungsverweise für alle Projekte im **SSISDB** -Katalog an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|reference_id|**bigint**|Der eindeutige Bezeichner (ID) des Verweises.|  
|project_id|**bigint**|Die eindeutige ID des Projekts.|  
|reference_type|**char(1)**|Gibt an, ob sich die Umgebung im gleichen Ordner wie das Projekt (relativer Verweis) oder in einem anderen Ordner (absoluter Verweis) befinden kann. Wenn der Wert `R`ist, wird der Speicherort der Umgebung mit einem relativen Verweis angegeben. Wenn der Wert `A`ist, wird die Umgebung mit einem absoluten Verweis angegeben.|  
|environment_folder_name|**sysname**|Der Name des Ordners, wenn der Speicherort der Umgebung mit einem absoluten Verweis angegeben wird.|  
|environment_name|**sysname**|Der Name der Umgebung, auf die das Projekt verweist.|  
|validation_status|**char(1)**|Der Status der Überprüfung.|  
|last_validation_time|**datatimeoffset(7)**|Der Zeitpunkt der letzten Überprüfung.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jeden Umgebungsverweis im Katalog angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für das entsprechende Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die READ-Berechtigung für ein Projekt verfügen, verfügen Sie auch über die READ-Berechtigung für alle Pakete und Umgebungsverweise, die diesem Projekt zugeordnet sind. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Projekt kann über relative oder absolute Umgebungsverweise verfügen. Relative Verweise verweisen mit dem Namen auf die Umgebung und erfordern, dass sich diese im gleichen Ordner wie das Projekt befindet. Absolute Verweise verweisen mit Name und Ordner auf die Umgebung und verweisen möglicherweise auf Umgebungen, die sich in einem anderen Ordner als das Projekt befinden. Ein Projekt kann auf mehrere Umgebungen verweisen.  
  
  
