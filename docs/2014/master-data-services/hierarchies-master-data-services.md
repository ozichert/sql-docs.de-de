---
title: Hierarchien (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e2b606fae657fdc7d5652e4f33c6d14ccff690c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176016"
---
# <a name="hierarchies-master-data-services"></a>Hierarchien (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ist eine Hierarchie eine Baumstruktur, die Sie für folgende Zwecke verwenden können:

-   Gruppieren ähnlicher Elemente zu organisatorischen Zwecken

-   Konsolidieren und Zusammenfassen von Elementen zu Berichts- und Analysezwecken

## <a name="what-hierarchies-contain"></a>Inhalt von Hierarchien
 Jede Hierarchie enthält Elemente aus einer oder mehreren Entitäten. Wenn ein Element hinzugefügt, geändert oder gelöscht wird, werden alle Hierarchien aktualisiert. Dadurch wird sichergestellt, dass die Daten in allen Hierarchien exakt sind. Mit Hierarchien wird zudem sichergestellt, dass jedes Element genau einmal gezählt wird.

 Wenn Sie eine Gruppierung einer Teilmenge von Elementen erstellen möchten, erwägen Sie die Verwendung einer Auflistung. Weitere Informationen finden Sie unter [Sammlungen &#40;Master Data Services&#41;](collections-master-data-services.md).

## <a name="kinds-of-hierarchies"></a>Arten von Hierarchien
 Sie können mehrere Hierarchien erstellen, um Elemente auf verschiedene Weisen anzuzeigen und zu organisieren. Sie können Folgendes erstellen:

-   Unregelmäßige Hierarchien für eine einzelne Entität, als explizite Hierarchien bezeichnet. Weitere Informationen finden Sie unter [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).

-   Ebenenbasierte Hierarchien für mehrere Entitäten auf der Grundlage der vorhandenen Beziehungen zwischen Entitäten und deren Attributen, als abgeleitete Hierarchie bezeichnet. Weitere Informationen finden Sie unter [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).

> [!NOTE]
>  Alle Elemente in einer Hierarchie müssen demselben Modell angehören.

## <a name="hierarchies-are-not-taxonomies"></a>Hierarchien sind keine Taxonomien
 Eine Hierarchie unterscheidet sich von einer Taxonomie. In einer Taxonomie werden Elemente nach mehreren Attributen gleichzeitig organisiert, während Elemente in einer Hierarchie jeweils nach einem Attribut organisiert werden. Eine Taxonomie kann das gleiche Element mehrfach enthalten, während eine Hierarchie ein Element nur einmal enthalten darf.

 Beispielsweise kann das gleiche Fahrrad zweimal in eine Taxonomie aufgenommen werden, einmal, weil es rot ist, und ein weiteres Mal, weil es eine 38er Größe hat. In einer Hierarchie ist das Fahrrad nur einmal enthalten. Sie müssen also festlegen, ob es mit Bezug zu seiner Farbe oder Größe angezeigt werden soll.

## <a name="hierarchy-example"></a>Hierarchiebeispiel
 Im folgenden Beispiel werden Produktelemente nach Unterkategorieelementen gruppiert.

 ![Beispiel für nach Unterkategorie gruppierte Hierarchie](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Beispiel für nach Unterkategorie gruppierte Hierarchie")

## <a name="related-tasks"></a>Related Tasks

|Taskbeschreibung|Thema|
|----------------------|-----------|
|Aktivieren Sie eine Entität für explizite Hierarchien und Auflistungen.|[Aktivieren einer Entität für explizite Hierarchien und Auflistungen &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|Erstellen Sie explizite Hierarchie.|[Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|Erstellen Sie eine abgeleitete Hierarchie.|[Erstellen einer abgeleiteten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|Blenden Sie Ebenen in einer vorhandenen abgeleiteten Hierarchie aus, oder löschen Sie Ebenen.|[Ausblenden oder Löschen von Ebenen in einer abgeleiteten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a>Verwandte Inhalte

-   [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [Rekursive Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [Abgeleitete Hierarchien mit expliziten Abschlüssen &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [Sammlungen &#40;Master Data Services&#41;](collections-master-data-services.md)


