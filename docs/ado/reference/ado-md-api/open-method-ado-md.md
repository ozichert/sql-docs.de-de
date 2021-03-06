---
title: Open-Methode (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: rothja
ms.author: jroth
ms.openlocfilehash: c0469bef1bce402efe143fbaa1ac760e3465d630
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765101"
---
# <a name="open-method-ado-md"></a>Open-Methode (ADO MD)
Ruft die Ergebnisse einer mehrdimensionalen Abfrage ab und gibt die Ergebnisse in einem [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Eine **Variante** , die eine gültige mehrdimensionale Abfrage ergibt, z. b. eine MDX-Abfrage (Multidimensional Expression). Das *Source* -Argument entspricht der [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md) -Eigenschaft. Weitere Informationen zu MDX finden Sie im [OLE DB für die Online Analytical Processing (OLAP)-](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) Dokumentation im Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Dies ist optional. Eine **Variante** , die zu einer Zeichenfolge ausgewertet wird, die entweder einen gültigen ADO- [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objektvariablen Namen oder eine Definition für eine Verbindung angibt. Das *ActiveConnection* -Argument gibt die Verbindung an, in der das [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekt geöffnet werden soll. Wenn Sie eine Verbindungs Definition für dieses Argument übergeben, öffnet ADO mit den angegebenen Parametern eine neue Verbindung. Das *ActiveConnection* -Argument entspricht der [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) -Eigenschaft.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Open** -Methode generiert einen Fehler, wenn einer der Parameter ausgelassen wird und der zugehörige Eigenschafts Wert nicht festgelegt wurde, bevor versucht wird, das **Cellset**zu öffnen.  
  
## <a name="applies-to"></a>Gilt für  
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cellset-Beispiel (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close-Methode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
