---
title: Flatfilequelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6338c7a306f163f786f2c1e7d44ae4dbc66504ec
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62902447"
---
# <a name="flat-file-source"></a>Flatfilequelle
  Die Flatfilequelle liest Daten aus einer Textdatei. Die Textdatei kann in einem Format mit Trennzeichen, fester Breite oder einem gemischten Format vorliegen.  
  
-   Beim Format mit Trennzeichen werden Spalten und Zeilen mithilfe von Spalten- und Zeilentrennzeichen definiert.  
  
-   Beim Format mit fester Breite werden Spalten und Zeilen mithilfe der Breite definiert. Dieses Format schließt außerdem ein Zeichen zur Auffüllung der Felder auf die maximale Breite ein.  
  
-   Beim Format mit einem rechten Flatterrand werden mithilfe der Breite alle Spalten definiert, außer der letzten Spalte, die durch das Zeilentrennzeichen getrennt wird.  
  
 Es gibt folgende Möglichkeiten, um die Flatfilequelle zu konfigurieren:  
  
-   Fügen Sie der Transformationsausgabe eine Zeile hinzu, die den Namen der Textdatei enthält, aus der die Flatfilequelle Daten extrahiert.  
  
-   Geben Sie an, ob die Flatfilequelle leere Zeichenfolgen in Spalten als NULL-Werte interpretiert.  
  
    > [!NOTE]  
    >  Für den von der Flatfilequelle verwendeten Verbindungs-Manager für Flatfiles muss die Verwendung eines Formats mit Trennzeichen konfiguriert werden, damit leere Zeichenfolgen als NULL-Werte interpretiert werden. Falls der Verbindungs-Manager ein Format mit fester Breite oder mit einem Flatterrand verwendet, können aus Leerzeichen bestehende Daten nicht als NULL-Werte interpretiert werden.  
  
 Die Ausgabespalte in der Ausgabe der Flatfilequelle schließt die FastParse-Eigenschaft ein. FastParse gibt an, ob die Spalte die schnelleren gebietsschemaneutralen Analyseroutinen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] oder die gebietsschemabezogenen Standardanalyseroutinen verwendet. Weitere Informationen finden Sie unter [Fast Parse](../fast-parse.md) und [Standard Parse](../standard-parse.md).  
  
 Ausgabespalten schließen auch UseBinaryFormat-Eigenschaft ein. Sie verwenden diese Eigenschaft, um Unterstützung für binäre Daten in Dateien zu implementieren, wie für Daten mit dem gepackten Dezimalformat. Standardmäßig ist UseBinaryFormat auf `false`festgelegt. Wenn Sie ein Binärformat verwenden möchten, legen Sie UseBinaryFormat auf `true` und den Datentyp in der Ausgabe Spalte auf `DT_BYTES`fest. Bei diesem Vorgang überspringt die Flatfilequelle die Datenkonvertierung und leitet die Daten durch die Ausgabespalte, wie sie ist. Sie können eine Transformation verwenden, wie Abgeleitete Spalte oder Datenkonvertierung um die `DT_BYTES`-Daten in einen anderen Datentyp umzuwandeln, oder Sie können ein benutzerdefiniertes Skript in eine Skripttransformation schreiben, um die Daten zu interpretieren. Sie können auch eine benutzerdefinierte Datenflusskomponente schreiben, um die Daten zu interpretieren. Weitere Informationen zu den Datentypen, die Sie `DT_BYTES` in umwandeln können, finden Sie unter [Cast &#40;SSIS-Ausdrucks&#41;](../expressions/cast-ssis-expression.md).  
  
 Diese Quelle verwendet für den Zugriff auf die Textdatei einen Verbindungs-Manager für Flatfiles. Durch Festlegen von Eigenschaften im Verbindungs-Manager für Flatfiles können Sie Informationen zur Datei und zu jeder enthaltenen Spalte bereitstellen und angeben, wie die Flatfilequelle die Daten in der Textdatei behandeln soll. Beispielsweise können Sie die Zeichen angeben, mit denen Spalten und Zeilen in der Datei getrennt werden, sowie den Datentyp und die Länge jeder Spalte. Weitere Informationen finden Sie unter [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Diese Quelle weist eine Ausgabe und eine Fehlerausgabe auf.  
  
## <a name="configuration-of-the-flat-file-source"></a>Konfiguration der Flatfilequelle  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Quellen-Editor für Flatfiles** festlegen können:  
  
-   [Quellen-Editor für Flatfiles &#40;Seite „Verbindungs-Manager“&#41;](../flat-file-source-editor-connection-manager-page.md)  
  
-   [Quellen-Editor für Flatfiles &#40;Seite Spalten&#41;](../flat-file-source-editor-columns-page.md)  
  
-   [Quellen-Editor für Flatfiles &#40;Seite Fehlerausgabe&#41;](../flat-file-source-editor-error-output-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der Flatfile](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Weitere Informationen zum Festlegen der Eigenschaften einer Datenflusskomponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Flatfileziel](flat-file-destination.md)   
 [Datenfluss](data-flow.md)  
  
  
