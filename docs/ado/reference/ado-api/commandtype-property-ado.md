---
title: CommandType-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: rothja
ms.author: jroth
ms.openlocfilehash: bbc90dc2d818ca880a9f712d551fd6a98fb9ecf3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760426"
---
# <a name="commandtype-property-ado"></a>CommandType-Eigenschaft (ADO)
Gibt den Typ eines [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen oder mehrere [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) -Werte fest oder gibt ihn zurück.  
  
> [!NOTE]
>  Verwenden Sie die **commandtypeaufum** -Werte **adcmdfile** oder **adCmdTableDirect** nicht mit **CommandType**. Diese Werte können nur als Optionen mit den [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -und [Requery](../../../ado/reference/ado-api/requery-method.md) -Methoden eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandType** -Eigenschaft, um die Auswertung der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft zu optimieren.  
  
 Wenn der **CommandType** -Eigenschafts Wert auf den Standardwert **adCmdUnknown**festgelegt ist, kann die Leistung beeinträchtigt werden, da ADO Aufrufe an den Anbieter ausführen muss, um zu bestimmen, ob die **CommandText** -Eigenschaft eine SQL-Anweisung, eine gespeicherte Prozedur oder ein Tabellenname ist. Wenn Sie wissen, welche Art von Befehl Sie verwenden, weist das Festlegen der **CommandType** -Eigenschaft ADO an, direkt zum relevanten Code zu wechseln. Wenn die **CommandType** -Eigenschaft nicht mit dem Typ des Befehls in der **CommandText** -Eigenschaft identisch ist, tritt ein Fehler auf, wenn Sie die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode aufruft.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
