---
title: MSMQ-Verbindungs-Manager-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msmqconnectionmanager.f1
helpviewer_keywords:
- MSMQ Connection Manager Editor
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 91b448a87408a830464b50f641e6eefa8cf3f12c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057641"
---
# <a name="msmq-connection-manager-editor"></a>MSMQ-Verbindungs-Manager-Editor
  Mithilfe des Dialogfelds **MSMQ-Verbindungs-Manager** geben Sie den Pfad zu einer Message Queuing-Meldungswarteschlange (auch bekannt als MSMQ) an.  
  
 Weitere Informationen zum MSMQ-Verbindungs-Manager finden Sie unter [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Der MSMQ-Verbindungs-Manager unterstützt lokale öffentliche und private Warteschlangen sowie öffentliche Remotewarteschlangen. Er unterstützt keine privaten Remotewarteschlangen. Eine Problemumgehung mithilfe des Skripttasks finden Sie unter [Senden mit dem Skripttask an eine private Remotemeldungswarteschlange](control-flow/script-task.md).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Verbindungs-Manager im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie den Verbindungs-Manager. Die bewährte Methode ist hierbei, den Verbindungs-Manager zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Pfad**  
 Geben Sie den vollständigen Pfad der Meldungswarteschlange ein. Das Format des Pfades ist vom Typ der Warteschlange abhängig.  
  
|Warteschlangentyp|Beispielpfad|  
|----------------|-----------------|  
|Public|\<Computername>\\<Name der Warteschlange\>|  
|Private|\<Computername>\Private$\\<Name der Warteschlange\>|  
  
 Sie können "." verwenden, um den lokalen Computer darzustellen.  
  
 **Test**  
 Nachdem die Konfiguration des MSMQ-Verbindungs-Managers abgeschlossen ist, überprüfen Sie die Gültigkeit der Verbindung, indem Sie auf **Testen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
