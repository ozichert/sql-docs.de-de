---
title: Getschemaobject-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
author: rothja
ms.author: jroth
ms.openlocfilehash: a8853e967a75a67aadccc7e48d684ab92819a71d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764211"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject-Modell (ADO MD)
Ruft ein ADO MD Schema Objekt ([Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) [oder Element](../../../ado/reference/ado-md-api/member-object-ado-md.md)) nach dem [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjType*  
 Ein [schemaobjecttypeenum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) -Wert, der angibt, welcher Typ von Schema Objekt (Dimension, Hierarchie, Ebene oder Element) abgerufen werden soll.  
  
 *UniqueName*  
 Eine **Zeichenfolge** , die den **UniqueName** -Eigenschafts Wert des abzurufenden-Objekts angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 **Getschemaobject** Ruft Objekte mithilfe ihrer eindeutigen Namen ab, wie von der **UniqueName** -Eigenschaft angegeben. Die Namen der übergeordneten Objekte müssen nicht bekannt sein, und übergeordnete Auflistungen müssen nicht aufgefüllt werden, um ein Schema Objekt abzurufen.  
  
## <a name="applies-to"></a>Gilt für  
 [CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CubeDef-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
