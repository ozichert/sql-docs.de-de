---
title: Interpretieren der Ergebnisse von SQL Server-Komponententests
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 1708c6aa8a082cfc06aadf832e0dbf30f2c23e23
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246431"
---
# <a name="interpreting-sql-server-unit-test-results"></a>Interpretieren der Ergebnisse von SQL Server-Komponententests

Wenn Sie einen SQL Server-Komponententest ausführen, werden die Testergebnisse automatisch erzeugt, auf dem Datenträger gespeichert und im Fenster **Testergebnisse** zusammengefasst. Sobald Sie einen Testlauf starten, wird das Fenster **Testergebnisse** mit dem Status des Testlaufs angezeigt. In diesem Fenster sind sowohl die aktiven als auch die abgeschlossenen Tests enthalten.  
  
Sie können ausführliche Informationen zu einem Testergebnis anzeigen, indem Sie im Fenster **Testergebnisse** darauf doppelklicken, um die Seite **Testergebnisdetails** zu öffnen. Um weitere Informationen zu einem Testergebnis zu erhalten, doppelklicken Sie auf das Ergebnis.  
  
Weitere Informationen dazu, wie Sie die Darstellung im Fenster **Testergebnisse** anpassen, finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Spalten in Testfenstern (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182508(VS.100).aspx) oder [Gewusst wie: Hinzufügen oder Entfernen von Spalten in Testfenstern (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182508.aspx).  
  
## <a name="storing-test-results"></a>Speichern von Testergebnissen  
Die Ergebnisse der Komponententests werden in einer Datei mit der Erweiterung TRX automatisch auf der Festplatte gespeichert. Eine TRX-Datei ist eine XML-Datei, die die Details eines Testlaufs enthält. Sie können TRX-Dateien vorheriger Testläufe laden, um die Ergebnisse dieser Testläufe zu überprüfen oder um frühere Tests erneut auszuführen. Weitere Informationen finden Sie unter [Gewusst wie: Erneutes Ausführen eines Tests (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
> [!NOTE]  
> Komponententests können nicht remote ausgeführt werden.  
  
Wenn Ihr Team die Arbeit mithilfe eines Visual Studio Team Foundation Server-Teamprojekts verwaltet, können Sie die Testdaten auch in einer SQL Server-Datenbank veröffentlichen, die als Betriebsspeicher bezeichnet wird.  
  
Weitere Informationen dazu, wie Sie Testergebnisse speichern, erneut verwenden und mit dem Team gemeinsam nutzen, finden Sie unter [Gewusst wie: Speichern und Öffnen von Testergebnissen in Visual Studio 2010](https://msdn.microsoft.com/library/ms404662(VS.100).aspx) oder [Gewusst wie: Speichern und Öffnen von Testergebnissen in Visual Studio 2012](https://msdn.microsoft.com/library/ms404662.aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von SQL Server-Komponententests](../ssdt/running-sql-server-unit-tests.md)  
  
