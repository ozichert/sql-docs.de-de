---
title: Write Text-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee7f4b99b40b6aec3e384f9f5739f8f5d2280f4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764411"
---
# <a name="writetext-method"></a>WriteText-Methode
Schreibt eine angegebene Text Zeichenfolge in ein Daten [Strom](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Daten*  
 Ein **Zeichen** folgen Wert, der den Text in zu schreibenden Zeichen enthält.  
  
 *Optionen*  
 Dies ist optional. Ein [streamschreibwert](../../../ado/reference/ado-api/streamwriteenum.md) , der angibt, ob ein Zeilen Trennzeichen am Ende der angegebenen Zeichenfolge geschrieben werden muss.  
  
## <a name="remarks"></a>Bemerkungen  
 Angegebene Zeichen folgen werden in das **Stream** -Objekt geschrieben, ohne dass dazwischen liegende Leerzeichen oder Zeichen zwischen den einzelnen Zeichen folgen liegen  
  
 Die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) wird auf das Zeichen festgelegt, das den geschriebenen Daten folgt. Die Methode " **Write Text** " schneidet den Rest der Daten in einem Stream nicht ab. Wenn Sie diese Zeichen abschneiden möchten [, nennen Sie](../../../ado/reference/ado-api/seteos-method.md)"*".  
  
 Wenn Sie über die aktuelle [EOS](../../../ado/reference/ado-api/eos-property.md) -Position hinaus schreiben, wird die [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) des **Streams** um alle neuen Zeichen erweitert, und **EOS** wechselt zum neuen letzten Byte im **Stream**.  
  
> [!NOTE]
>  Die Methode " **Write Text** " wird mit Textstreams verwendet ([Typ](../../../ado/reference/ado-api/type-property-ado-stream.md) : **adtypetext**). Verwenden Sie für binäre Datenströme (**Typ** : **adTypeBinary**) " [Write](../../../ado/reference/ado-api/write-method.md)".  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Write-Methode](../../../ado/reference/ado-api/write-method.md)
