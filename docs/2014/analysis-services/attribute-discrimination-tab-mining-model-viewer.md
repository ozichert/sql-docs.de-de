---
title: Registerkarte "Attribut Unterscheidung" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7e8d9593cd45ec5a92ea07051fe424698d8ece6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66063130"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a>Registerkarte "Attributunterscheidung" (Miningmodell-Viewer)
  Mithilfe der Registerkarte **Attributunterscheidung** können Sie die Status der Eingabeattribute vergleichen und anzeigen, in welcher Beziehung sie zum Ausgabeattribut stehen. Die Attributwerte, die für die größte Differenz zwischen den beiden ausgewählten vorhersagbaren Attributstatus sorgen, werden zuerst aufgeführt.  
  
 **Weitere Informationen:** [Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird automatisch im richtigen benutzerdefinierten Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Für jedes Modell können Sie entweder den benutzerdefinierten Viewer oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte auswählen. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Versehen**  
 Wählen Sie ein vorhersagbares Attribut aus.  
  
 **Wert 1**  
 Wählen Sie einen Status des vorhersagbaren Attributs aus, der mit dem in **Wert 2**enthaltenen Wert verglichen wird.  
  
 **Wert 2**  
 Wählen Sie einen Status des vorhersagbaren Attributs aus, der mit dem in **Wert 1**enthaltenen Wert verglichen wird. Sie können auch **alle anderen Zustände** auswählen, um den Wert in **Wert 1** mit seinem Komplement zu vergleichen, d. h. alle anderen Werte außer Wert 1.  
  
 **Unterscheidungs Ergebnisse \<für Wert 1> \<und Wert 2>**  
 Das Diagramm enthält die folgenden Spalten, in denen beschrieben wird, in welcher Beziehung das Zielattribut zu den spezifischen Status des Eingabeattributs steht.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Attribute**|Ein Eingabeattribut im Miningmodell.|  
|**Werte**|Ein Status des Attributs, das unter **Attribute**aufgeführt ist.|  
|**Begünstigt \<Wert 1>**|Der Balken gibt an, ob das aktuelle Attribut und der aktuelle Wert das in **Wert 1**ausgewählte Zielergebnis begünstigen.|  
|**Begünstigt \<Wert 2>**|Der Balken gibt an, ob das aktuelle Attribut und der aktuelle Wert das in **Wert 2**ausgewählte Zielergebnis begünstigen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
