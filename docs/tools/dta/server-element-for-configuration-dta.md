---
title: Server-Element für Konfiguration (DTA)
description: Im Hilfsprogramm „DTA“ enthält das Element „Server“ für die Konfiguration die Identifikationsinformationen für den Server, auf dem Sie eine Konfiguration auswerten möchten.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: f723e02b13ed5613d3606927ae500c3072c8c6fc
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151798"
---
# <a name="server-element-for-configuration-dta"></a>Server-Element für Konfiguration (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Enthält die Identifikationsinformationen für den Server, auf dem der Datenbankoptimierungsratgeber die hypothetische Konfiguration auswerten soll (wird durch das **Configuration**-Element angegeben).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro **Configuration** -Element erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Configuration-Element &#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Server &#40;DTA&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Database-Element für Konfiguration &#40;DTA&#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können nur ein **Server** -Element für das **Configuration** -Element angeben. Dieses Element hat den Namen **ServerTypecomplexType** im [XML-Schema des Datenbankoptimierungsratgebers](https://go.microsoft.com/fwlink/?linkid=43100). Dieses **Server** -Element ist nicht mit dem untergeordneten Element für das **DTAInput** -Element identisch. Weitere Informationen finden Sie unter [Server-Element &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Syntax finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
