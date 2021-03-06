---
title: STConvexHull (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b3d06da6d6f972c64d4bf196699b55a611b0f992
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042470"
---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt ein Objekt zurück, das die konvexe Hülle einer **geography** -Instanz darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt ein `FullGlobe` -Objekt für **geography** -Instanzen mit einem Umschlagwinkel größer als 90 Grad zurück.  
  
 Gibt eine leere **geography** -Auflistung für eine leere **geography** -Instanz zurück.  
  
 Gibt **null** für eine nicht initialisierte **geography** -Instanz zurück.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>A. Verwenden von STConvexHull() in einer nicht initialisierten geography-Instanz  
 Im folgenden Beispiel wird `STConvexHull()` in einer nicht initialisierten **geography** -Instanz darstellt.  
  
```
 DECLARE @g geography;  
 SELECT @g.STConvexHull();
 ```  
  
### <a name="b-using-stconvexhull-on-an-empty-geography-instance"></a>B. Verwenden von STConvexHull in einer leeren geography-Instanz  
 Im folgenden Beispiel wird `STConvexHull()` in einer leeren `Polygon` -Instanz verwendet.  
  
```
 DECLARE @g geography = 'POLYGON EMPTY';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
### <a name="c-finding-the-convex-hull-of-a-non-convex-polygon-instance"></a>C. Suchen der konvexen Hülle einer nicht konvexen Polygoninstanz  
 Im folgenden Beispiel wird `STConvexHull()` verwendet, um die konvexe Hülle einer nicht-konvexen `Polygon`-Instanz zu suchen.  
  
```  
 DECLARE @g geography;  
 SET @g = geography::Parse('POLYGON((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
 SELECT @g.STConvexHull().ToString();  
```  
  
### <a name="d-finding-the-convex-hull-on-a-geography-instance-with-an-envelope-angle-larger-than-90-degrees"></a>D: Suchen der konvexen Hülle in einer geography-Instanz mit einem Umschlagwinkel größer als 90 Grad  
 Im folgenden Beispiel wird `STConvexHull()` in einer **geography** -Instanz mit einem Umschlagwinkel größer als 90 Grad verwendet.  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  
