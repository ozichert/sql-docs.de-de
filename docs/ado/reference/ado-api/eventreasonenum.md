---
title: Eventreasonaufumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 28d923476d8abff4dfa283e58eb6394bdb3b9593
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755186"
---
# <a name="eventreasonenum"></a>EventReasonEnum
Gibt den Grund an, warum ein Ereignis aufgetreten ist.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adrsnaddnew**|1|Ein Vorgang hat einen neuen Datensatz hinzugefügt.|  
|**adrsnclose**|9|Ein Vorgang hat das **Recordset**geschlossen.|  
|**adrsndelete**|2|Ein Vorgang hat einen Datensatz gelöscht.|  
|**adrsnfirstchange**|11|Ein Vorgang hat die erste Änderung an einem Datensatz vorgenommen.|  
|**adrsnmove**|10|Ein Vorgang hat den Daten Satz Zeiger innerhalb des **Recordsets**verschoben.|  
|**adrsnmuvefirst**|12|Ein Vorgang hat den Daten Satz Zeiger auf den ersten Datensatz im **Recordset**verschoben.|  
|**adrsnmuvelast**|15|Ein Vorgang hat den Daten Satz Zeiger auf den letzten Datensatz im **Recordset**verschoben.|  
|**adrsnmuvenext**|13|Ein Vorgang hat den Daten Satz Zeiger auf den nächsten Datensatz im **Recordset**verschoben.|  
|**adrsnmuveprevious**|14|Ein Vorgang hat den Daten Satz Zeiger auf den vorherigen Datensatz im **Recordset**verschoben.|  
|**adrsnrequery**|7|Ein Vorgang, der das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)angefordert hat.|  
|**adrsnresynch**|8|Ein Vorgang hat das **Recordset** mit der Datenbank erneut synchronisiert.|  
|**adrsnundoaddnew**|5|Ein Vorgang hat das Hinzufügen eines neuen Datensatzes rückgängig gemacht.|  
|**adrsnundodelete**|6|Ein Vorgang hat das Löschen eines Datensatzes rückgängig gemacht.|  
|**adrsnundoupdate**|4|Ein Vorgang hat das Update eines Datensatzes rückgängig gemacht.|  
|**adrsnupdate**|3|Ein Vorgang hat einen vorhandenen Datensatz aktualisiert.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. eventreason. AddNew|  
|Adoumums. eventreason. Close|  
|Adoumums. eventreason. Delete|  
|Adoumums. eventreason. firstchange|  
|Adoumums. eventreason. Move|  
|Adoumums. eventreason. muvefirst|  
|Adoumums. eventreason. muvelast|  
|Adoumums. eventreason...|  
|Adoumums. eventreason. muveprevious|  
|Adoumums. eventreason. Requery|  
|Adotenums. eventreason. Resynch|  
|Adoumums. eventreason. undoaddnew|  
|Adoumums. eventreason. undodelete|  
|Adoumums. eventreason. undoupdate|  
|Adoerums. eventreason. Update|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillMove- und MoveComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
