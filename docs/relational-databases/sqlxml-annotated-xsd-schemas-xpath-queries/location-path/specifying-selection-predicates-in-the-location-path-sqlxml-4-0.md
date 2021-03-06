---
title: Festlegen von Auswahl Prädikaten im Speicherort Pfad (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84a3eade8a706e95b3ddba72d96e37d8fabf1fd3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75255999"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Angeben von Auswahlprädikaten im Speicherortpfad (SQLXML 4.0) 
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ein Prädikat filtert eine Knotengruppe in Bezug auf eine Achse (ähnlich einer WHERE-Klausel in einer SELECT-Anweisung). Das Prädikat wird zwischen Klammern angegeben. Für jeden Knoten in der zu filternden Knotengruppe wird der Prädikatausdruck mit dem entsprechenden Knoten als Kontextknoten ausgewertet. Die Anzahl der Knoten in der Knotengruppe dient dabei als Kontextgröße. Ergibt die Auswertung des Prädikatausdrucks für den betreffenden Knoten TRUE, wird dieser Knoten in die resultierende Knotengruppe aufgenommen.  
  
 XPath ermöglicht auch die positionsbasierte Filterung. Ein Prädikatausdruck, der eine Zahl ergibt, wählt diesen Ordinalzahlenknoten aus. Beispielsweise gibt der Speicherortpfad `Customer[3]` den dritten Kunden zurück. Solche numerische Prädikate werden nicht unterstützt. Nur Prädikatausdrücke, die ein boolesches Ergebnis zurückgeben, werden unterstützt.  
  
> [!NOTE]  
>  Informationen zu den Einschränkungen dieser XPath-Implementierung von XPath und den Unterschieden zwischen der XPath-Implementierung und der W3C-Spezifikation finden Sie unter [Einführung in die Verwendung von XPath-Abfragen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Auswahl Prädikat: Beispiel 1  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt alle untergeordneten Elemente des ** \<Kunden>** Elements aus dem aktuellen Kontext Knoten aus, die das **CustomerID-** Attribut mit dem Wert "ALFKI" aufweisen:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 In dieser XPath-Abfrage sind `child` und `attribute` die Achsennamen. `Customer`ist der Knoten Test (true, `Customer` wenn ein ** \<Elementknoten>** ist, da ** \<Element>** der Haupt Knotentyp für `child` die Achse ist). `attribute::CustomerID="ALFKI"` ist das Prädikat. Im `attribute` Prädikat ist die Achse und `CustomerID` ist der Knoten Test (true, wenn **CustomerID** ein Attribut des Kontext Knotens ist, da ** \<das Attribut>** der Haupt Knotentyp der **Attribut** Achse ist).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Auswahl Prädikat: Beispiel 2  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt aus dem aktuellen Kontext Knoten alle ** \<Reihenfolge>** Enkel aus, die über das **SalesOrderID** -Attribut mit dem Wert 1 verfügen:  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 In diesem XPath-Ausdruck sind `child` und `attribute` die Achsennamen. `Customer`, `Order` und `SalesOrderID` sind die Knotentests. `attribute::OrderID="1"` ist das Prädikat.  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Auswahl Prädikat: Beispiel 3  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt alle ** \<Kunden>** untergeordneten Elemente aus dem aktuellen Kontext Knoten aus, die über mindestens ein ** \<ContactName>** Children-Element verfügen:  
  
```  
child::Customer[child::ContactName]  
```  
  
 In diesem Beispiel wird davon ausgegangen, dass das ** \<ContactName->** ein untergeordnetes Element des ** \<Customer>** -Elements im XML-Dokument ist, das in einem XSD-Schema mit Anmerkungen als *Element zentrierte Zuordnung* bezeichnet wird.  
  
 In diesem XPath-Ausdruck ist `child` der Achsenname. `Customer`ist der Knoten Test (true, `Customer` wenn ein ** \<Element>** Knoten ist, da ** \<Element>** der Haupt Knotentyp `child` für die-Achse ist). `child::ContactName` ist das Prädikat. Im Prädikat ist die `child` Achse und `ContactName` ist der Knoten Test (true, wenn `ContactName` ein ** \<Element>** Knoten ist).  
  
 Dieser Ausdruck gibt nur die ** \<** untergeordneten Elemente des Kunden>-Elements des Kontext Knotens zurück, die über ** \<die untergeordneten Elemente ContactName>** .  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Auswahl Prädikat: Beispiel 4  
 Der folgende XPath-Ausdruck wählt ** \<Kunden>** untergeordneten Elementen des Kontext Knotens aus, die keine ** \<ContactName->** untergeordneten Elemente aufweisen:  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 In diesem Beispiel wird davon ausgegangen, dass ** \<das ContactName->** ein untergeordnetes Element des ** \<Customer>** -Elements im XML-Dokument ist und das ContactName-Feld in der Datenbank nicht erforderlich ist.  
  
 In diesem Beispiel ist `child` die Achse. `Customer`ist der Knoten Test (true, `Customer` wenn ein \<Element> Knoten ist). `not(child::ContactName)` ist das Prädikat. Im Prädikat ist die `child` Achse und `ContactName` ist der Knoten Test (true, wenn `ContactName` ein \<Element> Knoten ist).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Auswahl Prädikat: Beispiel 5  
 Der folgende XPath-Ausdruck wählt alle ** \<Kunden>** untergeordneten Elemente mit dem **CustomerID-** Attribut aus dem aktuellen Kontext Knoten aus:  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 In diesem Beispiel ist `child` die Achse und `Customer` der Knoten Test (true, wenn `Customer` ein \<Element> Knoten ist). `attribute::CustomerID` ist das Prädikat. Im Prädikat ist die `attribute` Achse und `CustomerID` das Prädikat (true, wenn `CustomerID` ein ** \<Attribut>** Knoten ist).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Auswahlprädikat: Beispiel 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt XPath-Abfragen mit einem Kreuzprodukt im Prädikat, wie im folgenden Beispiel gezeigt:  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 Durch diese Abfrage werden alle Kunden mit einer `Order` ausgewählt, bei der `OrderDate` dem `ShipDate` für eine beliebige `Order`entspricht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Client seitige XML-Formatierung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
