---
title: Filtergroupum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: rothja
ms.author: jroth
ms.openlocfilehash: b7b6a8d449d27539100f467da1eea19ec42e0a72
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764511"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Gibt die Gruppe von Datensätzen an, die von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)gefiltert werden sollen.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Filter zum Anzeigen nur der Datensätze, die vom letzten [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)-, [Resync](../../../ado/reference/ado-api/resync-method.md)-, [Update Batch](../../../ado/reference/ado-api/updatebatch-method.md)-oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) -Befehl betroffen sind.|  
|**adFilterConflictingRecords**|5|Filter zum Anzeigen der Datensätze, bei denen das letzte Batch Update nicht erfolgreich war.|  
|**adfilterfetchedrecords**|3|Filter zum Anzeigen der Datensätze im aktuellen Cache, d. h. die Ergebnisse des letzten Aufrufes zum Abrufen von Datensätzen aus der Datenbank.|  
|**adfilternone**|0|Entfernt den aktuellen Filter und stellt alle Datensätze für die Anzeige wieder her.|  
|**adfilterpdingrecords**|1|Filter zum Anzeigen nur von Datensätzen, die geändert wurden, aber noch nicht an den Server gesendet wurden. Gilt nur für den Batch Aktualisierungs Modus.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. filtergroup. affectedrecords|  
|AdoEnums. filtergroup. conflictingrecords|  
|AdoEnums. filtergroup. fetchedrecords|  
|AdoEnums. filtergroup. None|  
|AdoEnums. filtergroup. pdingrecords|  
  
## <a name="applies-to"></a>Gilt für  
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)
