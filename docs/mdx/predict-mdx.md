---
title: Vorhersagen (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 165d03b886ad8e9beeb09bf5a835c879cc23a2a4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68055582"
---
# <a name="predict-mdx"></a>Predict (MDX)


    
> [!CAUTION]  
>  Diese Funktion wird derzeit aufgrund interner Inkonsistenzen entfernt.  
>   
>  Im Beispielabschnitt finden Sie eine Problemumgehung, in der ein DMX-Ausdruck verwendet wird.  
  
 Gibt einen Wert eines numerischen Ausdrucks zurück, der über einem Data Mining-Modell ausgewertet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Mining_Model_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen eines Miningmodells darstellt.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, der einen gültigen DMX-Ausdruck für das angegebene Miningmodell ergibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Vorhersage** Funktion wertet den angegebenen Zeichen folgen Ausdruck innerhalb des Kontexts des angegebenen Mining Modells aus.  
  
 Data Mining-Syntax und -Funktionen werden im Data Mining Expressions (DMX)-Verweis dokumentiert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden mittels des Customer Clusters-Miningmodells der Name des Clusters und die Entfernung eines bestimmten Kunden von diesem vorhergesagt:  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
