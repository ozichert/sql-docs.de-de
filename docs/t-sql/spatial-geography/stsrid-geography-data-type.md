---
title: STSrid (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4561b52049da9c051b7e8eda3835545f600c0e70
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68120779"
---
# <a name="stsrid-geography-data-type"></a>STSrid (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** ist eine ganze Zahl, die die SRID (Spatial Reference Identifier) der Instanz darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **int**  
  
 CLR-Typ: **SqlInt32**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft kann geändert werden.  
  
## <a name="examples"></a>Beispiele  
 Im ersten Beispiel wird eine `geography` -Instanz mit dem SRID-Wert 4326 (WGS84) erstellt und `STSrid` verwendet, um die SRID zu bestätigen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 Im zweiten Beispiel wird `STSrid` verwendet, um die SRID-Wert der Instanz in 4267 (NAD27) zu ändern und dann den geänderten SRID-Wert zu bestätigen.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
