---
title: Andere Anmerkungen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 169d65e801aca6ed34735649757b37a3ffe13193
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703452"
---
# <a name="other-annotations-sqlxml-40"></a>Andere Anmerkungen (SQLXML 4.0)
  Neben den in den vorherigen Themen in diesem Abschnitt beschriebenen Anmerkungen interpretiert XML-Massenladen diese anderen Anmerkungen folgendermaßen:  
  
 `sql:id-prefix`  
 Wenn das Schema Präfixe für die XML-Daten festlegt, entfernt XML-Massenladen die Präfixe, bevor die Daten an Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gesendet werden.  
  
 `sql:use-cdata`  
 XML-Massenladen liest den Text, der in den CDATA-Abschnitten gespeichert wird, und sendet ihn an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:url-encode`  
 XML-Massenladen unterstützt diese Anmerkung nicht. Eine in der XML-Dateneingabe angegebene URL wird beispielsweise von XML-Massenladen an diesem Speicherort nicht gelesen, sodass sie in der Datenbank gespeichert werden kann.  
  
 `sql:is-mapping-schema`  
 XML-Massenladen unterstützt weder diese Anmerkung noch `sql:id`.  
  
> [!NOTE]  
>  XML-Massenladen unterstützt keine Inlinezuordnungsschemas.  
  
 `sql:key-fields`  
 XML-Massenladen ignoriert stets diese Anmerkung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Interpretation der Anmerkung &#40;SQLXML 4,0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  
