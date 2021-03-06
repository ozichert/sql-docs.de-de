---
title: EndOf Recordset-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
author: rothja
ms.author: jroth
ms.openlocfilehash: fd7710ebc7a5af323c247860baedd4b30d91fe21
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765551"
---
# <a name="endofrecordset-event-ado"></a>EndOfRecordset-Ereignis (ADO)
Das **EndOfRecordset** -Ereignis wird aufgerufen, wenn versucht wird, zu einer Zeile nach dem Ende des [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)zu wechseln.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *"Datentyp"*  
 Ein **VARIANT_BOOL** -Wert, der, wenn er auf VARIANT_TRUE festgelegt ist, angibt, dass dem **Recordset**weitere Zeilen hinzugefügt wurden.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 Wenn **EndOfRecordset** aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war. Sie wird auf **adStatus-kandeny** festgelegt, wenn dieses Ereignis keinen Abbruch des Vorgangs anfordern kann, der dieses Ereignis verursacht hat.  
  
 Bevor **EndOfRecordset** zurückgibt, legen Sie diesen Parameter auf **adstatuingunwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt. Das **Recordset** , für das dieses Ereignis aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **endogrecordset** -Ereignis tritt ggf. auf, wenn der Vorgang " [wvenext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) " fehlschlägt  
  
 Dieser Ereignishandler wird aufgerufen, wenn versucht wird, nach dem Ende des **Recordset** -Objekts zu wechseln, möglicherweise aufgrund des Aufrufs von **MoveNext**. In diesem Fall können Sie jedoch weitere Datensätze aus einer Datenbank abrufen und am Ende des **Recordsets**anfügen. Legen Sie in diesem Fall *fmoredata* auf VARIANT_TRUE fest, und geben Sie von **EndOfRecordset**zurück. **Wiederholen** Sie dann den Befehl "" für den Zugriff auf die neu abgerufenen Datensätze.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
