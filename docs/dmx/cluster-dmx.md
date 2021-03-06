---
title: Cluster (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fa7df2782b8102e386c70d5e874a25f7868dbb1c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68071079"
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Cluster zurück, der mit der höchsten Wahrscheinlichkeit den Eingabefall enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>Gilt für  
 Diese Funktion kann nur verwendet werden, wenn das zugrunde liegende Data Mining-Modell Cluster unterstützt.  
  
## <a name="return-type"></a>Rückgabetyp  
 Für die **Cluster** Funktion sind keine Parameter erforderlich.  
  
 Die **Cluster** Funktion gibt einen skalaren Wert eines Cluster namens zurück. Wenn Sie diese Funktion jedoch als Argument einer anderen Funktion verwenden, müssen Sie Sie als \<Cluster Spalten Verweis> berücksichtigen.  
  
## <a name="remarks"></a>Bemerkungen  
 **Cluster** kann auch als `<`Clusterspaltenverweis`>` für eine **präthistogram** -Funktion verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine SINGLETON-Abfrage mit dem [präthistogram-&#40;DMX-&#41;](../dmx/predicthistogram-dmx.md) und Cluster Funktionen verwendet, um die Entfernung des einzelnen falls von jedem Cluster des TM Clustering-Mining Modells und die Wahrscheinlichkeit zurückzugeben, dass der jeweilige Fall in jedem Cluster vorhanden ist.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Clusterwahrscheinlichkeit &#40;DMX-&#41;](../dmx/clusterprobability-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funktionen &#40;DMX-&#41;](../dmx/functions-dmx.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
