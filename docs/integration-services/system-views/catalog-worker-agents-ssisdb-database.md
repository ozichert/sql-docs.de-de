---
title: catalog.worker_agents (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2678853d13436811b53b40473a04191625535db
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295136"
---
# <a name="catalogworker_agents-ssisdb-database"></a>catalog.worker_agents (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Zeigt die Informationen für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out-Worker an.

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|Die Worker-Agent-ID für den Scale Out-Worker.|
|isEnabled|**bit**|Gibt an, ob der Scale Out-Worker aktiviert ist.|
|DisplayName|**nvarchar(256)**|Der Anzeigename des Scale Out-Workers.|
|BESCHREIBUNG|**nvarchar(256)**|Die Beschreibung des Scale Out-Workers.|
|MachineName|**nvarchar(256)**|Der Computername für den Scale Out-Worker.|
|`Tags`|**nvarchar(max)**|Die Tags des Scale Out-Workers.|
|UserAccount|**nvarchar(256)**|Das Benutzerkonto, unter dem der Dienst für den Scale Out-Worker ausgeführt wird.|
|LastOnlineTime|**datetimeoffset(7)**|Der letzte Zeitpunkt, zu dem der Scale Out-Worker online war.|

## <a name="remarks"></a>Bemerkungen
In dieser Ansicht wird eine Zeile für jeden Scale Out-Worker angezeigt, der eine Verbindung mit dem Scale Out-Master herstellt, der mit dem SSISDB-Katalog zusammenarbeitet.

## <a name="permissions"></a>Berechtigungen
Diese Sicht erfordert eine der folgenden Berechtigungen:

- Mitgliedschaft in der Datenbankrolle **ssis_admin**

- Mitgliedschaft in der Datenbankrolle **ssis_cluster_executor**

- Mitgliedschaft in der Serverrolle **sysadmin**
