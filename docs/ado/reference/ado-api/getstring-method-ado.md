---
title: GetString-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
author: rothja
ms.author: jroth
ms.openlocfilehash: 166bfad93d994a4b85bdb944a5d5505987182044
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758746"
---
# <a name="getstring-method-ado"></a>GetString-Methode (ADO)
Gibt das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt das **Recordset** als Zeichen folgen Wert **Variante** (BSTR) zurück.  
  
#### <a name="parameters"></a>Parameter  
 *StringFormat*  
 Ein [stringformatenum](../../../ado/reference/ado-api/stringformatenum.md) -Wert, der angibt, wie das **Recordset** in eine Zeichenfolge konvertiert werden soll. Die Parameter " *RowDelimiter*", " *ColumnDelimiter*" und " *nullexpr* " werden nur mit einem *StringFormat* von " **adclipstring**" verwendet.  
  
 *NumRows*  
 Dies ist optional. Die Anzahl der Zeilen, die in das **Recordset**konvertiert werden sollen. Wenn *numRows* nicht angegeben wird, oder wenn es größer als die Gesamtzahl der Zeilen im **Recordset**ist, werden alle Zeilen im **Recordset** konvertiert.  
  
 *ColumnDelimiter*  
 Dies ist optional. Ein Trennzeichen, das zwischen Spalten verwendet wird, sofern angegeben, andernfalls das Tabulator Zeichen.  
  
 *RowDelimiter*  
 Dies ist optional. Ein Trennzeichen, das zwischen Zeilen verwendet wird, sofern angegeben, andernfalls das Wagen Rücklauf Zeichen.  
  
 *Nullexpr*  
 Dies ist optional. Ein Ausdruck, der anstelle eines NULL-Werts verwendet wird, sofern angegeben, andernfalls die leere Zeichenfolge.  
  
## <a name="remarks"></a>Bemerkungen  
 Zeilendaten, aber keine Schema Daten, werden in der Zeichenfolge gespeichert. Daher kann ein **Recordset** nicht mit dieser Zeichenfolge erneut geöffnet werden.  
  
 Diese Methode entspricht der RDO **GetClipString** -Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [GetString-Methode – Beispiel (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
