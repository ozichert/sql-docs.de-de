---
title: Data Mining Extensions (DMX)-Operator Referenz | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e0dfafb74e6e86185872ea8e736b95dce7d4058
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68070913"
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>Data Mining-Erweiterungen (DMX) - Operatorreferenz
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die DMX-Sprache (Data Mining Extensions) [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in unterstützt arithmetische, Zuweisungs-, Vergleichs-, logische und unäre Operatoren. In der folgenden Tabelle sind die Operatoren aufgeführt, die DMX unterstützt.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|[+ &#40;&#41; &#40;DMX hinzufügen&#41;](../dmx/add-dmx.md)|Ein arithmetischer Operator, der zwei Zahlen addiert.|  
|[-&#40;subtrahieren&#41; &#40;DMX-&#41;](../dmx/subtract-dmx.md)|Ein arithmetischer Operator, der eine Zahl von einer anderen Zahl subtrahiert.|  
|[&#42; &#40;multiplizieren&#41; &#40;DMX-&#41;](../dmx/multiply-dmx.md)|Ein arithmetischer Operator, der eine Zahl mit einer anderen Zahl multipliziert.|  
|[&#40;dividieren&#41; &#40;DMX-&#41;](../dmx/divide-dmx.md)|Ein arithmetischer Operator, der eine Zahl durch eine andere Zahl dividiert.|  
|[&#60; &#40;kleiner als&#41; &#40;DMX-&#41;](../dmx/less-than-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die Werte ungleich NULL ergeben, true zurück, wenn der Wert des Arguments auf der linken Seite kleiner ist als der Wert des Arguments auf der rechten Seite. gibt andernfalls false zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62; &#40;größer als&#41; &#40;DMX-&#41;](../dmx/greater-than-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite größer ist als der Wert des Arguments auf der rechten Seite; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[= &#40;gleich&#41; &#40;DMX-&#41;](../dmx/equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite gleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;&#62; &#40;nicht gleich&#41; &#40;DMX-&#41;](../dmx/not-equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite ungleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;= &#40;kleiner als oder gleich&#41; &#40;DMX-&#41;](../dmx/less-than-or-equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die Werte ungleich NULL ergeben, true zurück, wenn der Wert des Arguments auf der linken Seite kleiner oder gleich dem Wert des Arguments auf der rechten Seite ist. gibt andernfalls false zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62;= &#40;größer oder gleich&#41; &#40;DMX-&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite größer gleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[Und &#40;DMX-&#41;](../dmx/and-dmx.md)|Ein logischer Operator, der eine Konjunktion zweier numerischer Ausdrücke ausführt.|  
|[DMX-&#41;nicht &#40;](../dmx/not-dmx.md)|Ein logischer Operator, der eine Negation für einen numerischen Ausdruck ausführt.|  
|[Oder &#40;DMX-&#41;](../dmx/or-dmx.md)|Ein logischer Operator, der eine Disjunktion zweier numerischer Ausdrücke ausführt.|  
|[+ &#40;positiver&#41; &#40;DMX-&#41;](../dmx/positive-dmx.md)|Ein unärer Operator, der den positiven Wert eines numerischen Ausdrucks zurückgibt.|  
|[-&#40;negative&#41; &#40;DMX-&#41;](../dmx/negative-dmx.md)|Ein unärer Operator, der den negativen Wert eines numerischen Ausdrucks zurückgibt.|  
|[Doppelter Schrägstrich &#40;Kommentar&#41; &#40;DMX-&#41;](../dmx/double-slash-comment-dmx.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
|[--&#40;Kommentar&#41; &#40;DMX-&#41; Zusammenfassung](../dmx/comment-dmx-summary.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
|[Schrägstrich-Stern &#40;Kommentar&#41; &#40;DMX-&#41;](../dmx/slash-star-comment-dmx.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Operatoren &#40;DMX-&#41;](../dmx/operators-dmx.md)  
  
  
