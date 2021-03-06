---
title: Herstellen einer Verbindung mit einer Datenquelle (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c1114dd63b9082c6be7486ab5e576a6b8270485
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087342"
---
# <a name="connect-to-a-data-source-ssas"></a>Mit einer Datenquelle verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie eine neue Datenquellenverbindung mit einer Vielzahl von Datenquellen erstellen, z. B. relationalen Datenbanken, Datenfeeds und Dateien. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen. Außerdem muss der entsprechende Anbieter auf dem Arbeitsbereichsdatenbankserver installiert sein. Für 32-Bit (x86)-Server müssen 32-Bit-Anbieter installiert sein. Für 64-Bit (x64)-Server müssen 64-Bit-Anbieter installiert sein.  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] wird unabhängig von der Architektur immer in einem 32-Bit-Prozess ausgeführt. Wenn [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] auf einem 64-Bit-Computer ausgeführt wird, sollten Sie beim Installieren von Datenanbietern Folgendes beachten:  
  
-   Für Anbieter, die die parallele Installation von 32-Bit- und 64-Bit-Anbietern unterstützen, sollten Sie beide Anbieter installieren.  
  
-   Für den ACE-Anbieter müssen Sie die 64-Bit-Version des Anbieters installieren. Da Office den ACE-Anbieter automatisch installiert, sollten Sie keine 32-Bit-Version von Microsoft Office auf einem 64-Bit-Computer ausführen, der den Arbeitsbereichsdatenbankserver hostet.  
  
     Der ACE-Anbieter wird zum Importieren aus Text-, Excel- und Access-Dateien verwendet. Wenn die Unterstützung für diese Datenquellen nicht erforderlich ist, können Sie eine 32-Bit-Version von Microsoft Office auf einem Computer mit einem 64-Bit-Arbeitsbereichsdatenbankserver ausführen.  
  
-   Für andere Anbieter, die keine parallele Installation von 32-Bit- und 64-Bit-Anbietern unterstützen, müssen Sie den 32-Bit-Anbieter installieren. Wenn nur 64-Bit-Computer verfügbar sind, müssen Sie einen Remotecomputer mit einem als Arbeitsbereichsdatenbankserver installierten 64-Bit-Anbieter verwenden.  
  
  
