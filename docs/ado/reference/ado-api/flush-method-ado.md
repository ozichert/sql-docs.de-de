---
title: Flush-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: rothja
ms.author: jroth
ms.openlocfilehash: c00f3c92d3d2bd3111201d6f1536884e3e9dceb5
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760086"
---
# <a name="flush-method-ado"></a>Flush-Methode (ADO)
Erzwingt den Inhalt des verbleibenden [Streams](../../../ado/reference/ado-api/stream-object-ado.md) im ADO-Puffer für das zugrunde liegende Objekt, dem der **Stream** zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode kann verwendet werden, um den Inhalt des Streampuffers an das zugrunde liegende Objekt zu senden, z. b. den Knoten oder die Datei, der durch die URL dargestellt wird, die die Quelle des Daten **Strom** Objekts ist. Diese Methode sollte aufgerufen werden, wenn Sie sicherstellen möchten, dass alle Änderungen, die an den Inhalten eines **Streams** vorgenommen wurden, geschrieben wurden. Allerdings ist es in der Regel nicht **erforderlich, eine Leerung aufzurufen**, da ADO den Puffer fortlaufend im Hintergrund leert. Änderungen am Inhalt eines **Streams** werden automatisch vorgenommen, nicht zwischengespeichert **, bis der** Lösch Modus aufgerufen wird.  
  
 Durch das Schließen eines **Streams** mit der [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode wird der Inhalt eines **Streams** automatisch geleert. das Löschen **muss unmittelbar vor** dem **Schließen**nicht explizit aufgerufen werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
