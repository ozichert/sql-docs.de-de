---
title: Medieninhalt (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 890a03221888693c1696059ed5d31a9907ea2872
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62876047"
---
# <a name="device-contents-sql-server"></a>Medieninhalt (SQL Server)
  Mithilfe dieses Dialogfelds können Sie die Sicherungsinformationen anzeigen. Diese Informationen beschreiben das Gerät, die Medien, den Mediensatz und den Sicherungssatz bzw. die Sicherungssätze.  
  
 **So verwenden Sie SQL Server Management Studio zum Anzeigen des Inhalts eines Sicherungsmediums**  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Tastatur  
 **Medien**  
 Ein Datenträger oder ein Satz von Bändern, auf dem Sicherungsinformationen gespeichert sind.  
  
 **Mediensequenz**  
 Führt die Mediensequenznummer, die Familiensequenznummer und ggf. den Spiegelbezeichner auf. Die physischen Sicherungsmedien sind jeweils mit einer Mediensequenznummer gekennzeichnet, die die Reihenfolge angibt, in der die Medien verwendet wurden. Das erste Sicherungsmedium wird mit 1 markiert, das zweite Medium (das erste Anschlussband) mit 2 usw. Beim Wiederherstellen des Sicherungssatzes stellen die Sequenznummern sicher, dass der Operator, der die Sicherung wiederherstellt, das richtige Medium in der richtigen Reihenfolge einlegt.  
  
 **Erstellt am**  
 Zeigt das Erstellungsdatum des Mediums an.  
  
 **Mediensatz**  
 Ein Mediensatz ist eine geordnete Sammlung von Sicherungsmedien, auf die mithilfe einer konstanten Anzahl von Sicherungsmedien ein oder mehrere Sicherungsvorgänge geschrieben wurden.  
  
 **Name**  
 Zeigt den Namen des Mediensatzes an.  
  
 **Beschreibung**  
 Zeigt die Beschreibung des Mediensatzes an.  
  
 **Anzahl von Medienfamilien**  
 Zeigt die Anzahl der Medienfamilien an. Jeder Mediensatz ist eine Sammlung, die sich aus einer oder mehreren Medienfamilien zusammensetzt. Die gesamte Ausgabe auf ein angegebenes einzelnes Sicherungsmedium (oder eine Gruppe gespiegelter Sicherungsmedien) bildet eine einzelne Medienfamilie. Jeder Mediensatz enthält eine Medienfamilie pro separates Medium (oder Gruppe gespiegelter Medien). Wenn ein Mediensatz beispielsweise zwei nicht gespiegelte Sicherungsmedien verwendet, enthält der Mediensatz zwei Medienfamilien.  
  
 **Sicherungssätze**  
 Zeigt Informationen zum Sicherungssatz bzw. den Sicherungssätzen an, der oder die auf dem Medium enthalten sind. Ein Sicherungssatz ist das Ergebnis eines erfolgreichen Sicherungsvorgangs, dessen Inhalt auf die Medien im Satz von Sicherungsmedien verteilt wird.  
  
|Header|Werte|  
|------------|------------|  
|**Name**|Name des Sicherungssatzes.|  
|**Typ**|Der Typ der ausgeführten Sicherung: Vollständig, Differenziell oder Transaktionsprotokoll.|  
|**Komponente**|Die gesicherte Komponente: Datenbank, Datei oder *\<leer>* (bei Transaktionsprotokollen).|  
|**Server**|Name der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] , durch die der Sicherungsvorgang ausgeführt wurde.|  
|**Datenbank**|Name der Datenbank, die gesichert wurde.|  
|**Position**|Position des Sicherungssatzes auf dem Volume.|  
|**Date**|Datum und Uhrzeit des Endes des Sicherungsvorgangs, entsprechend den Ländereinstellungen des Clients.|  
|**Größe**|Größe des Sicherungssatzes in Byte.|  
|**Benutzername**|Name des Benutzers, der den Sicherungsvorgang ausgeführt hat.|  
|**Ablauf**|Datum und Uhrzeit des Zeitpunkts, an dem der Sicherungssatz verfällt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
