---
title: HelpContext, HelpFile-Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
author: rothja
ms.author: jroth
ms.openlocfilehash: 13fb3f0b5bf55ac9acb525183eba6d8645f4de62
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758716"
---
# <a name="helpcontext-helpfile-properties"></a>HelpContext- und HelpFile-Eigenschaft
Gibt die Hilfedatei und das Thema an, die einem [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt zugeordnet sind.  
  
## <a name="return-values"></a>Rückgabewerte  
  
-   **HelpContextID** Gibt eine Kontext-ID als **Long** -Wert für ein Thema in einer Hilfedatei zurück.  
  
-   **HelpFile** Gibt einen **Zeichen** folgen Wert zurück, der zu einem vollständig aufgelösten Pfad zu einer Hilfedatei ausgewertet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Hilfedatei in der **HelpFile** -Eigenschaft angegeben ist, wird die **HelpContext** -Eigenschaft verwendet, um das Hilfethema, das identifiziert wird, automatisch anzuzeigen. Wenn kein relevantes Hilfethema verfügbar ist, gibt die **HelpContext** -Eigenschaft 0 (null) zurück, und die **HelpFile** -Eigenschaft gibt eine Zeichenfolge der Länge 0 (null) zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Beschreibung, HelpContext, HelpFile, NativeError, Number, Source und SQLSTATE Properties Example (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description-Eigenschaft](../../../ado/reference/ado-api/description-property.md)   
 [Number-Eigenschaft (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source-Eigenschaft (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)
