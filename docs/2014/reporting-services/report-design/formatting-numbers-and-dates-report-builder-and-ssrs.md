---
title: Formatieren von Zahlen und Datumsangaben (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.placeholderproperties.number.f1
- sql12.rtp.rptdesigner.serieslabelproperties.number.f1
- "10127"
- sql12.rtp.rptdesigner.axisproperties.number.f1
- "10130"
- "10286"
- sql12.rtp.rptdesigner.textboxproperties.number.f1
- "10285"
ms.assetid: 6de1a725-9f06-4708-be26-2d55e442e344
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ee681c291d9dd96733f083138af39ef2b280e1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105840"
---
# <a name="formatting-numbers-and-dates-report-builder-and-ssrs"></a>Formatieren von Zahlen und Datumsangaben (Berichts-Generator und SSRS)
  Sie können Zahlen und Datumsangaben in Datenbereichen formatieren, indem Sie im Dialogfeld **Eigenschaften** des betreffenden Datenbereichs auf der Seite **Zahl** ein Format auswählen.  
  
 Wenn Sie in einem Textfeld-Berichtselement Formatzeichenfolgen angeben möchten, wählen Sie das zu formatierende Element aus, klicken Sie mit der rechten Maustaste, wählen Sie **Textfeldeigenschaften**aus, und klicken Sie anschließend auf **Zahl**. Einzelne Zellen einer Tabelle oder eines Matrixdatenbereichs können auf die gleiche Weise formatiert werden, da es sich bei den Zellen in einer Tabelle oder Matrix um einzelne Textfelder handelt.  
  
 Diagrammdatenbereiche werden häufig zum Anzeigen von Daten auf der Kategorieachse (x) sowie von Werten auf der Wertachse (y) verwendet. Klicken Sie mit der rechten Maustaste auf eine Achse, und wählen Sie **Achseneigenschaften**aus, um die Formatierung in einem Diagramm anzugeben. Auf der Wertachse können Formatierungen nur für Zahlen angegeben werden. Weitere Informationen finden Sie unter [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
 Zur Angabe einer Formatierung in einem Messgerätdatenbereich klicken Sie mit der rechten Maustaste auf die Skala des Messgeräts, und wählen Sie **Radiale Skalierungseigenschaften** bzw. **Lineare Skalierungseigenschaften**aus.  
  
> [!NOTE]  
>  Wenn gewünschte Formatierungsoptionen ausgegraut sind, bedeutet dies, dass die Formatierungsoptionen mit dem Datentyp des Felds, das in der Datenquelle festgelegt ist, inkompatibel sind. Wenn das Feld beispielsweise numerische Werte enthält, der Datentyp des Felds jedoch auf "string" festgelegt ist, können Formatierungsoptionen für numerische Daten (z. B. Währungsdaten oder Dezimalzahlen) nicht angewendet werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="considerations-for-formatting-numbers-and-dates"></a>Überlegungen zum Formatieren von Zahlen und Datumsangaben  
 Beachten Sie vor dem Formatieren von Zahlen und Datumsangaben im Bericht folgende Punkte:  
  
-   Standardmäßig werden Zahlen so formatiert, dass sie die Kultureinstellungen auf dem Clientcomputer widerspiegeln. Geben Sie mithilfe von Formatzeichenfolgen an, wie Zahlen angezeigt werden, sodass die Formatierung unabhängig vom Aufenthaltsort der Person, die den Bericht anzeigt, einheitlich ist.  
  
-   Die auf der Seite **Zahl** angegebenen Formate bilden einen Teil der numerischen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Standardformatzeichenfolgen. Zum Formatieren einer Zahl oder eines Datums mit einem benutzerdefinierten Format, das nicht im Dialogfeld angezeigt wird, können Sie beliebige [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Formatzeichenfolgen für Zahlen oder Datumsangaben verwenden. Weitere Informationen zu benutzerdefinierten Formatzeichenfolgen finden Sie auf MSDN im Thema [Formatierung von Typen](https://go.microsoft.com/fwlink/?LinkId=112024) .  
  
-   Wenn eine benutzerdefinierte Formatzeichenfolge angegeben wurde, besitzt diese eine höhere Priorität als die kulturspezifischen Standardeinstellungen. Angenommen, Sie legen die benutzerdefinierte Formatzeichenfolge "#,###" fest, um die Zahl 1234 als 1,234 anzuzeigen. Für Benutzer in den Vereinigten Staaten hat diese Zeichenfolge eine andere Bedeutung als in Europa. Überlegen Sie vor dem Festlegen eines benutzerdefinierten Formats, wie sich das ausgewählte Format von Benutzern in unterschiedlichen Kulturen, die den Bericht möglicherweise anzeigen, verstanden werden kann.  
  
-   Wenn Sie eine ungültige Formatzeichenfolge angeben, wird der formatierte Text als Literalzeichenfolge interpretiert, die die Formatierung überschreibt.  
  
-   Wenn Sie eine Mischung aus Zahlen und anderen Zeichen in demselben Textfeld formatieren, empfiehlt es sich möglicherweise, einen Platzhalter zum getrennten Formatieren der Zahl und des restlichen Texts zu verwenden. Weitere Informationen finden Sie unter [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md). Wenn für die Format-Eigenschaft des Textfelds eine ungültige Zeichenfolge angegeben wird, wird die Formatzeichenfolge ignoriert. Wenn für die Format-Eigenschaft des Diagramms oder Messgeräts eine ungültige Zeichenfolge angegeben wird, wird die von Ihnen angegebene Formatzeichenfolge als Zeichenfolge interpretiert und die Formatierung nicht angewendet.  
  
-   Wenn Sie unter **Kategorie** die Option **Währung** auswählen und die Option **Werte anzeigen in**aktivieren, können Sie **Tausender**, **Millionen**oder **Milliarden** auswählen, um Zahlen in Finanzformaten anzuzeigen. Wenn der Feldwert zum Beispiel 1.789.905.394 lautet und Sie **Milliarden** auswählen und zwei Dezimalstellen angeben, wird im Bericht der Wert 1,78 angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Formatieren von Linien, Farben und Bildern (Berichts-Generator und SSRS)](images-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung (Berichts-Generator und SSRS)](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Formatieren von Skalen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)  
  
  
