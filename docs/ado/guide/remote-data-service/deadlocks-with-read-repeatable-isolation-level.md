---
title: Deadlocks mit Lese wiederholbarer Isolationsstufe | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
author: rothja
ms.author: jroth
ms.openlocfilehash: 31c90281860473d43e0a6bde4d1dd9e64e39bb3f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749637"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlocks mit Read Repeatable-Isolationsstufe
Wenn ein benutzerdefiniertes Geschäftsobjekt die Isolationsstufe Read REPEATABLE verwendet, um auf einen SQL Server zuzugreifen, und das Geschäftsobjekt gleichzeitig von zwei Clients aufgerufen wird, die eine Abfrage senden und in derselben Transaktion aktualisieren, ist ein Deadlock möglich. Der Remote Data Service ist so konzipiert, dass einem der Prozesse ein Timeout für die Freigabe des Deadlocks ermöglicht wird, das Update für diesen Client jedoch fehlschlägt.  
  
 Verwenden Sie die dynamische Eigenschaft [Cursor Dienst](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **Command** Timeout, um die Länge des Timeouts zu ändern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



