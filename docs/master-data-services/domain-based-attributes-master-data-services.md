---
title: Domänenbasierte Attribute
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 966112716bfb484a9615c973ee397de04787862c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728272"
---
# <a name="domain-based-attributes-master-data-services"></a>Domänenbasierte Attribute (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ist ein domänenbasiertes Attribut ein Attribut mit Werten, die mit Elementen aus einer anderen Entität aufgefüllt werden. Stellen Sie sich ein domänenbasiertes Attribut als eingeschränkte Liste vor. Domänenbasierte Attribute verhindern, dass Benutzer Attributwerte eingeben, die nicht gültig sind. Um einen Attributwert auszuwählen, muss der Benutzer aus einer Liste auswählen.  
  
## <a name="domain-based-attribute-example"></a>Beispiel für ein domänenbasiertes Attribut  
 Im folgenden Bild verfügt die Produktentität über das domänenbasierte Attribut namens "Subcategory". Das Subcategory-Attribut wird mit Werten aus der Subcategory-Entität aufgefüllt.  
  
 Die Entität Subcategory hat ein domänenbasiertes Attribut mit Namen Category. Das Category-Attribut wird mit Werten aus der Category-Entität aufgefüllt.  
  
 ![Domänenbasierte Attribute in einer Entität](../master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Domänenbasierte Attribute in einer Entität")  
  
## <a name="use-same-entity-for-multiple-domain-based-attributes"></a>Dieselbe Entität für mehrere domänenbasierte Attribute verwenden  
 Sie können die gleiche Entität als domänenbasiertes Attribut mehrerer Entitäten verwenden. Sie können z. B. eine Entität mit dem Namen "YesNoIndicator" mit den folgenden Elementen erstellen: Yes, No und Maybe. Anschließend erstellen Sie ein domänenbasiertes Attribut mit dem Namen "InStock" und verwenden die "YesNoIndicator"-Entität als Quelle. Außerdem können Sie ein weiteres domänenbasiertes Attribut mit dem Namen "Approved" erstellen und die "YesNoIndicator"-Entität als Quelle verwenden. Jedes Mal, wenn Benutzer aus einer Liste von Elementen der "YesNoIndicator"-Entität auswählen sollen, können Sie die Entität als domänenbasiertes Attribut verwenden.  
  
## <a name="domain-based-attributes-form-derived-hierarchies"></a>Domänenbasierte Attribute bilden abgeleitete Hierarchien  
 Domänenbasierte Attributbeziehungen sind die Grundlage für abgeleitete Hierarchien. Weitere Informationen finden Sie unter [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie ein neues domänenbasiertes Attribut, für das eine vorhandene Entität als Quelle fungiert.|[Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Erstellen Sie eine neue Entität.|[Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Attribute &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [Entitäten &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  
