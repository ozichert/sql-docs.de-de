---
title: IsNull (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d0b05e5d73c75e340535c3323a8219dedf5be76d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101227"
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Der Typ einer **geometry**-Instanz ist NULL. Gibt 0 zurück, wenn die Instanz nicht NULL ist.
  
## <a name="syntax"></a>Syntax  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **bit**  
  
 CLR-Typ: **SqlBoolean**  
  
## <a name="remarks"></a>Bemerkungen  
 `IsNull` kann verwendet werden, um zu überprüfen, ob eine **geometry**-Instanz NULL ist. `IsNull` gibt 0 zurück, wenn die Instanz nicht NULL ist, gibt aber Null zurück, wenn die Instanz NULL ist.  
  
 Diese Methode wird in erster Linie von der SQL Server-Infrastruktur verwendet. Es wird nicht empfohlen, mit `IsNull` zu prüfen, ob eine Instanz NULL ist.  
  

## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

