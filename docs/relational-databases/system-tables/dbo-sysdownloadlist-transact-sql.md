---
title: dbo. sysdownloadlist (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b3b87a32aec99b0b5775e492191683dd1b3b2366
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813725"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält die Warteschlange der Downloadanweisungen für alle Zielserver.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Identitätsspalte, die die natürliche Einfügesequenz der Zeilen bereitstellt|  
|**source_server**|**sysname**|Name des Quellservers|  
|**operation_code**|**tinyint**|Vorgangscode für den Auftrag<br /><br /> **1** = INS (INSERT)<br /><br /> **2** = UPD (UPDATE)<br /><br /> **3** = DEL (DELETE)<br /><br /> **4** = START<br /><br /> **5** = STOP|  
|**object_type**|**tinyint**|Code des Objekttyps|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Objekt-ID.|  
|**target_server**|**sysname**|Name des Zielservers|  
|**error_message**|**nvarchar(1024)**|Fehlermeldung, wenn der Zielserver beim Verarbeiten einer bestimmten Zeile einen Fehler feststellt|  
|**date_posted**|**datetime**|Datum und Uhrzeit, an dem bzw. zu der der Auftrag auf dem Zielserver bereitgestellt wurde|  
|**date_downloaded**|**datetime**|Datum und Uhrzeit, an dem bzw. zu der der Auftrag zuletzt heruntergeladen wurde|  
|**status**|**tinyint**|Status des Auftrags:<br /><br /> **0** = Noch nicht heruntergeladen<br /><br /> **1** = Erfolgreich heruntergeladen|  
|**deleted_object_name**|**sysname**|Name des gelöschten Objekts|  
  
 <sup>1</sup> die **object_id** Spalte kann den Wert **-1**aufweisen, was dem Wert all entspricht, wenn die **operation_code** Spalte den Wert DELETE hat.  
  
  
