---
title: Cursor locationumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: rothja
ms.author: jroth
ms.openlocfilehash: 278f69e504ed4af7589b7e2be2c281e5de5957fa
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760176"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Gibt den Speicherort des Cursor Dienstanbieter an.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Verwendet Client seitige Cursor, die von einer lokalen Cursor Bibliothek bereitgestellt werden. Lokale Cursor Dienste ermöglichen häufig viele Features, die vom Treiber bereitgestellten Cursorn möglicherweise nicht. Daher kann die Verwendung dieser Einstellung in Bezug auf Funktionen, die aktiviert werden, einen Vorteil bieten. Aus Gründen der Abwärtskompatibilität wird auch das Synonym **aduseclientbatch** unterstützt.|  
|**adusenone**|1|Cursor Dienste werden von nicht verwendet. (Diese Konstante ist veraltet und wird nur aus Gründen der Abwärtskompatibilität angezeigt.)|  
|**AD-eServer**|2|Standard. Verwendet Cursor, die vom Datenanbieter oder Treiber bereitgestellt werden. Diese Cursor sind manchmal sehr flexibel und ermöglichen eine zusätzliche Sensitivität bei Änderungen, die andere an der Datenquelle vornehmen. Einige Features des [Microsoft-Cursor Dienstanbieter für OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), z. b. die Zuordnung<br /><br /> [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekte können nicht mit serverseitigen Cursorn simuliert werden, und diese Features sind mit dieser Einstellung nicht verfügbar.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoteums. Cursor Location. Client|  
|Adoumums. Cursor Location. None|  
|Adoumums. Cursor Location. Server|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorLocation-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
