---
title: MSSQLSERVER_18752 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8aa5f3a75c4d21e148d50fe71b75a21a287a2a2b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68137041"
---
# <a name="mssqlserver_18752"></a>MSSQLSERVER_18752
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|18752|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REPL_INUSE|  
|Meldungstext|Nur jeweils ein Protokolllese-Agent oder eine protokollbezogene Prozedur (sp_repldone, sp_replcmds oder sp_replshowcmds) kann eine Verbindung mit einer Datenbank herstellen. Falls Sie eine protokollbezogene Prozedur ausgeführt haben, löschen Sie vor dem Starten des Protokolllese-Agents oder dem Ausführen einer weiteren protokollbezogenen Prozedur die Verbindung, über die sie ausgeführt wurde, oder führen Sie 'sp_replflush' über diese Verbindung aus.|  
  
## <a name="explanation"></a>Erklärung  
Nur jeweils ein Protokolllese-Agent oder eine protokollbezogene Prozedur kann eine Verbindung mit einer Datenbank herstellen.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass kein weiterer Protokolllese-Agent für die gleiche Veröffentlichungsdatenbank ausgeführt wird und dass keine aktive Verbindung zuvor sp_replcmds/sp_repltrans/sp_repldone ausgeführt hat, ohne anschließend sp_replflush auszuführen oder die Verbindung zu trennen.  
  
