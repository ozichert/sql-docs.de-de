---
title: Übergeordnetes Element (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9449c81e9f8e8de0c21d96062337e91b2f56398d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037194"
---
# <a name="parent-mdx"></a>Parent (MDX)


  Gibt das übergeordnete Element eines Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die über **geordnete** Funktion gibt das übergeordnete Element des angegebenen Elements zurück.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird das übergeordnete Element des July 1, 2001-Elements zurückgegeben. Im ersten Beispiel ist dieses Element im Kontext der Date-Attributhierarchie angegeben. Zurückgegeben wird das All Periods-Element.  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel ist das July 1, 2001-Element im Kontext der Calendar-Hierarchie angegeben.  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
