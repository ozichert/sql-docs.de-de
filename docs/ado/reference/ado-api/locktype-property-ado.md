---
title: LockType-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: rothja
ms.author: jroth
ms.openlocfilehash: 4a8d0f94d4482649030561f2ac71ed6de1374e46
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754488"
---
# <a name="locktype-property-ado"></a>LockType-Eigenschaft (ADO)
Gibt den Typ der Sperren an, die während der Bearbeitung in Datensätzen eingefügt werden  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) -Wert fest oder gibt ihn zurück. Der Standardwert ist **adlockread only**.  
  
## <a name="remarks"></a>Bemerkungen  
 Legen Sie die **LockType** -Eigenschaft vor dem Öffnen eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) fest, um anzugeben, welcher Sperrentyp beim Öffnen des Anbieters verwendet werden soll. Lesen Sie die-Eigenschaft, um den in einem geöffneten **Recordset** -Objekt verwendeten Sperrentyp zurückzugeben.  
  
 Anbieter unterstützen möglicherweise nicht alle Sperr Typen. Wenn ein Anbieter die angeforderte **LockType** -Einstellung nicht unterstützt, wird ein anderer Sperrentyp ersetzt. Um die tatsächliche Sperr Funktionalität zu ermitteln, die in einem **Recordset** -Objekt verfügbar ist, verwenden Sie die [unterstützte](../../../ado/reference/ado-api/supports-method.md) Methode mit **adupdate** und **adUpdateBatch**.  
  
 Die **adlockpessimi-** Einstellung wird nicht unterstützt, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist. Wenn ein nicht unterstützter Wert festgelegt ist, wird kein Fehler ausgegeben. Stattdessen wird der nächstgelegene unterstützte **LockType** verwendet.  
  
 Die **LockType** -Eigenschaft ist Lese-/Schreibzugriff, wenn das **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Bei Verwendung auf einem Client seitigen **Recordset** -Objekt kann die **LockType** -Eigenschaft nur auf **adlockbatchoptimifest**gelegt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Cursor Type, LockType und EditMode Properties (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Beispiel für Cursor Type, LockType und EditMode Properties (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
