---
title: Size-Eigenschaft (ADO-Stream) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: rothja
ms.author: jroth
ms.openlocfilehash: e17bb879c63e01d8f912bb7147061099bd3e2c10
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759866"
---
# <a name="size-property-ado-stream"></a>Size-Eigenschaft (ADO-Stream)
Gibt die Größe des Streams in Byte an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Long** -Wert zurück, der die Größe des Streams in Byte Anzahl angibt. Der Standardwert ist die Größe des Streams, oder-1, wenn die Größe des Streams nicht bekannt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Größe** kann nur mit geöffneten [Streamobjekten](../../../ado/reference/ado-api/stream-object-ado.md) verwendet werden.  
  
> [!NOTE]
>  Eine beliebige Anzahl von Bits kann in einem **Streamobjekt** gespeichert werden, nur durch Systemressourcen beschränkt. Wenn der **Stream** mehr Bits enthält, als durch einen **Long** -Wert dargestellt werden können, wird die **Größe** abgeschnitten und stellt die Länge des **Streams**daher nicht genau dar.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Size-Eigenschaft (ADO-Parameter)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
