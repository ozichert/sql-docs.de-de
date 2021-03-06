---
title: Filteroperatoren (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 27914c8b-8951-4b7d-914d-1cbf528dd248
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5d94a453e9eb5794bdd534f7aaf37ca2e1cc3177
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483875"
---
# <a name="filter-operators-master-data-services"></a>Filteroperatoren (Master Data Services)
  Wenn sie eine Liste von Elementen filtern, sind die folgenden Operatoren verfügbar.  
  
> [!NOTE]  
>  Wenn Sie nach mehreren Kriterien filtern, müssen alle Kriterien den Wert "true" haben, um Ergebnisse zurückzugeben. Zum Beispiel SquareFeet = 2000 **AND** Division <> 123.  
  
## <a name="filter-operators"></a>Filteroperatoren  
  
|Steuerelementname|Beschreibung|  
|------------------|-----------------|  
|**Ist gleich**|Gibt Attributwerte zurück, die den angegebenen Kriterien genau entsprechen. Um nach **Mountain-100**zu filtern, müssen Sie z.B. **Mountain-100**eingeben.|  
|**Ist nicht gleich**|Gibt Attributwerte zurück, die keine genaue Übereinstimmung mit den angegebenen Kriterien aufweisen. Die Filterkriterien müssen dem Attributwert, den Sie aus den Ergebnissen ausschließen möchten, genau entsprechen. Um Ergebnisse auszuschließen, die mit **Mountain-100**übereinstimmen, müssen Sie z.B. **Mountain-100**eingeben.<br /><br /> Hinweis: Wenn eine Filteranwendung mit einer „Ist ungleich“-Klausel auf ein Attribut angewendet wird, wird ein Element, dessen Attribut nicht NULL ist, die Filterbedingung übergeben und zurückgegeben werden, wenn in Ihren Datenbankeinstellungen SET ANSI_NULLS auf ON festgelegt ist. Um dieses Verhalten zu beenden, legen Sie SET ANSI_NULLS in den Datenbankeinstellungen auf OFF fest. Wenn SET ANSI_NULLS auf OFF festgelegt ist, werden alle Datenvergleiche mit einem NULL-Wert als TRUE ausgewertet, falls der Datenwert NULL ist. Dies hat zur Folge, dass das Element die „Ist ungleich“-Klausel nicht besteht. Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).|  
|**Ist wie**|Verwendet den LIKE-Operator aus Transact-SQL zum Filtern von Ergebnissen. Weitere Informationen finden Sie unter [LIKE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/like-transact-sql) in der SQL Server-Onlinedokumentation.|  
|**Ist nicht wie**|Verwendet den NOT-Operator aus Transact-SQL zum Filtern von Ergebnissen. Weitere Informationen finden Sie unter [NOT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/not-transact-sql) in der SQL Server-Onlinedokumentation.|  
|**Ist größer als**|Gibt Attributwerte zurück, die größer als die angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit einem Buchstaben größer als **F**beginnen, geben Sie z. B. **F**ein.|  
|**Ist kleiner als**|Gibt Attributwerte zurück, die kleiner als die angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit einem Buchstaben kleiner als **F**beginnen, geben Sie z. B. **F**ein.|  
|**Ist größer als oder gleich**|Gibt Attributwerte zurück, die größer oder gleich den angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit der Zahl **3** oder einer höheren Zahl beginnen, geben Sie z. B. **3**ein.|  
|**Ist kleiner als oder gleich**|Gibt Attributwerte zurück, die kleiner oder gleich den angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit der Zahl **3** oder einer kleineren Zahl beginnen, geben Sie z. B. **3**ein.|  
|**Übereinstimmungen**|Verwendet einen Fuzzysuchindex zum Filtern von Ergebnissen.<br /><br /> Geben Sie im Feld **Ähnlichkeitsgrad** an, wie genau die Abweichung der Attributwerte von den angegebenen Filterkriterien (mit einem Standardwert von „30 %“) sein muss. Wählen Sie eine der folgenden Möglichkeiten im Listenfeld **Algorithmus** aus.<br /><br /> **Levenshtein**: Eine Distanz auf Grundlage der Anzahl von Bearbeitungen (beispielsweise Hinzufügungen oder Löschungen), die benötigt wird, um von einer Zeichenfolge zur nächsten zu gelangen. Dies ist die Standardoption. Erfordert keine zusätzlichen Parameter.<br /><br /> **Jaccard**: Ein Index, der sich am besten eignet, wenn versucht wird, mehrere Zeichenfolgen abzugleichen. Diese Suche unterstützt einen zusätzlichen Parameter der Kapselungsvorspannung (siehe unten).<br /><br /> **Jaro-Winkler**: Eine Distanz, die sich am besten für die Suche von doppelten Personennamen eignet. Diese Methode gibt mehr Ergebnisse zurück als jede andere Methode. Unterstützt keine Kapselungsvorspannung.<br /><br /> **Längste allgemeine**unter Sequenz: funktioniert auf Grundlage einer unter Sequenz, in der die Buchstaben in einem Muster in der Reihenfolge angezeigt werden, obwohl Sie getrennt werden können (z. b. ist "MSR" eine unter Sequenz von "MaSteR"). Diese Suche unterstützt einen zusätzlichen Parameter der Kapselungsvorspannung (siehe unten).<br /><br /> <br /><br /> Fügen Sie für den **Jaccard** - oder den **Längste gemeinsame Teilsequenz**-Algorithmus einen **Verzerrungswert für den Einschluss** hinzu. Der **Verzerrungswert für den Einschluss**ist ein Längenschwellenwert, der in einem dezimalen Prozentsatz zwischen „0“ und „1“ bereitgestellt wird, mit dem Standardwert „0,62“. Ein niedrigerer Schwellenwert vergrößert die Anzahl der möglichen zurückgegebenen Übereinstimmungen.|  
|**Stimmt nicht überein**|Verwendet einen Fuzzysuchindex zum Filtern von Ergebnissen. Geben Sie im Feld **Ähnlichkeitsgrad** an, wie genau die Abweichung der Attributwerte von den angegebenen Filterkriterien sein muss.|  
|**Enthält Muster**|Verwendet reguläre Ausdrücke von .NET Framework, um Ergebnisse nach einem angegebenen Muster zu filtern. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.|  
|**Enthält kein Muster**|Verwendet reguläre Ausdrücke von .NET Framework zum Filtern von Ergebnissen, die einem angegebenen Muster nicht entsprechen. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.|  
|**Ist NULL**|Gibt Attributwerte zurück, die NULL lauten. Das Feld **Kriterien** wird deaktiviert, wenn Sie den **Ist NULL** -Operator auswählen.|  
|**Ist nicht NULL**|Gibt Attributwerte zurück, die nicht NULL lauten. Das Feld **Kriterien** wird deaktiviert, wenn Sie den **Ist nicht NULL** -Operator auswählen.|  
  
  
