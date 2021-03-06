---
title: Stat-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: rothja
ms.author: jroth
ms.openlocfilehash: 6295640a0d9ec0815ebac9086efc3835915e0e0c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759776"
---
# <a name="stat-method"></a>Stat-Methode
Ruft Informationen zu einem [Streamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **langer** Wert, der den Status des Vorgangs angibt.  
  
#### <a name="parameters"></a>Parameter  
 *Status g*  
 Eine Statuslisten Struktur, die mit Informationen über den Stream ausgefüllt wird. Die Implementierung der vom ADO-Streamobjekt verwendeten **stat** -Methode gibt nicht alle Felder der Struktur aus.  
  
 *STATFLAG*  
 Gibt an, dass diese Methode nicht einige der Member in der Statuslisten Struktur zurückgibt, wodurch eine Speicher Belegungs Operation gespeichert wird. Werte werden aus der STATFLAG-Enumeration entnommen. Die STATFLAG-Enumeration weist zwei Werte auf.  
  
|Konstante|Wert|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Bemerkungen  
 Die Version der für das ADO-Stream-Objekt implementierten Stat-Methode füllt die folgenden Felder der STATSTG-Struktur aus:  
  
 *pwcsName*  
 Eine Zeichenfolge, die den Namen des Streams enthält, wenn ein solcher verfügbar ist und der STATFLAG-Wert STATFLAG_NONAME nicht angegeben wurde.  
  
 *CBSIZE*  
 Gibt die Größe des Streams oder Bytearrays in Bytes an.  
  
 *mtime*  
 Gibt für diesen Speicher, diesen Stream oder dieses Bytearray den Zeitpunkt der letzten Änderung an.  
  
 *CTime*  
 Gibt für diesen Speicher, diesen Stream oder dieses Bytearray den Erstellungszeitpunkt an.  
  
 *atime*  
 Gibt für diesen Speicher, diesen Stream oder dieses Bytearray den Zeitpunkt des letzten Zugriffs an.  
  
 Wenn STATFLAG_NONAME im STATFLAG-Parameter angegeben wird, wird der Name des Streams nicht zurückgegeben.  
  
 Wenn STATFLAG_NONAME im STATFLAG-Parameter nicht angegeben wurde und für den aktuellen Stream kein Name verfügbar ist, wird dieser Wert E_NOTIMPL.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
