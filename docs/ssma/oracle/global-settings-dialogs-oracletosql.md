---
title: Globale Einstellungen (Dialogfelder) (oracletosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 43989355-cebf-4d8b-ba3d-fa8546e70230
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 4fc68e8b8d3fc009b766f0fb0be97f1124797764
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68259653"
---
# <a name="global-settings-dialogs--oracletosql"></a>Globale Einstellungen (Dialogfelder) (oracletosql)
Auf der Seite Dialoge des Dialog Felds **globale Einstellungen** können Sie die Standardeinstellungen für Benutzeraktionen und Warnungen für SSMA festlegen.  
  
Um auf die Dialogfeld Einstellungen im **Menü Extras** zuzugreifen, klicken Sie auf **globale Einstellungen**, klicken Sie unten im linken Bereich auf **GUI** , und wählen Sie dann **Dialoge**aus.  
  
## <a name="options"></a>Optionen  
**Vor dem Überschreiben von Objekten warnen**  
Wenn SSMA Objekte in SQL Server konvertiert, sind einige Objekte möglicherweise bereits in den SQL Server Metadaten des Projekts vorhanden. Diese Objekte wurden möglicherweise bereits konvertiert, oder die Objekte können im Ziel Schema einfach denselben Namen haben wie Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob Sie von SSMA aufgefordert werden sollen, doppelte Objekt Definitionen zu überschreiben:  
  
-   Wenn Sie " **true**" auswählen, zeigt SSMA ein Warn Dialogfeld an, wenn ein doppeltes Objekt gefunden wird. In diesem Dialogfeld können Sie angeben, dass einzelne Objekte oder alle doppelten Objekte überschrieben oder einzelne Objekte oder alle doppelten Objekte übersprungen werden sollen.  
  
-   Wenn Sie **false**auswählen, wird die Option **Objekt Standardaktion überschreiben** angezeigt, in der Sie die Standardaktion angeben.  
  
**Standardaktion zum Überschreiben von Objekten**  
Diese Option wird angezeigt, wenn Sie für die Option **Warnungen vor Überschreiben von Objekten** die Option **false** auswählen.  
  
Verwenden Sie diese Option, um das standardmäßige Objekt Überschreibungs Verhalten festzulegen:  
  
-   Wenn Sie **true**auswählen, werden Objekte in den SQL Server Projekt Metadaten, die denselben Namen aufweisen und sich im gleichen Ziel Schema wie das zu konvertierende Objekt befinden, von SSMA automatisch überschrieben.  
  
-   Wenn Sie **false**auswählen, werden Objekt Metadaten von SSMA während der Konvertierung nicht überschrieben.  
  
