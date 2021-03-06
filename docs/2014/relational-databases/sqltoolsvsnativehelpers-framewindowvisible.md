---
title: FrameWindowVisible | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: fd09d5d20b2a84050390c3e131265feddc09a409
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63285596"
---
# <a name="framewindowvisible"></a>FrameWindowVisible
  Eigenschaft, die angibt, ob ein angegebener Fensterrahmen sichtbar ist. Die Hilfsmethode wird in verwaltetem Code verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a>Parameter  
 *frame*  
  
 IVsWindowFrame*-Zeiger auf Visual Studio WindowFrame.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Boolescher Wert, der angibt, ob der Fensterrahmen, der durch *frame* angegeben wird, sichtbar ist.  
  

<!-- Necessary temporarily. GeneMi, 2018-05-01.
     But 'release-sql2014-migration' should win the Conflict Resolution later in May, because this will then be a good link!
## See Also  
 [SqlToolsVSNativeHelpers](sqltoolsvsnativehelpers.md)  
-->
  
  
