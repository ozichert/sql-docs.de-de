---
title: Type-Eigenschaft (ADO-Stream) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: rothja
ms.author: jroth
ms.openlocfilehash: de61f4877dc6adcdfaa9644f5f266cd827a1d096
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765341"
---
# <a name="type-property-ado-stream"></a>Type-Eigenschaft (ADO-Stream)
Gibt den Typ der im [Stream](../../../ado/reference/ado-api/stream-object-ado.md) enthaltenen Daten an (binär oder Text).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [streamtypeenum](../../../ado/reference/ado-api/streamtypeenum.md) -Wert fest, der den Typ der im **Stream** -Objekt enthaltenen Daten angibt, oder gibt ihn zurück. Der Standardwert ist **adtypetext**. Wenn jedoch Binärdaten anfänglich in einen neuen, leeren **Stream**geschrieben werden, wird der **Typ** in **adTypeBinary**geändert.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Type** -Eigenschaft ist nur Lese-/Schreibzugriff, wenn sich die aktuelle Position am Anfang des **Streams** befindet ([Position](../../../ado/reference/ado-api/position-property-ado.md) ist 0) und an jeder anderen Position schreibgeschützt ist.  
  
 Die**Type** -Eigenschaft bestimmt, welche Methoden zum Lesen und Schreiben des **Streams**verwendet werden sollen. Verwenden Sie für **Textstreams**den Text "read [Text](../../../ado/reference/ado-api/readtext-method.md) " und " [Write Text](../../../ado/reference/ado-api/writetext-method.md)". Verwenden Sie **Streams**für binäre Streams [Lese](../../../ado/reference/ado-api/read-method.md) -und [Schreib](../../../ado/reference/ado-api/write-method.md)Vorgänge.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [RecordType-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type-Eigenschaft (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
