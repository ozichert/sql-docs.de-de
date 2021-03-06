---
title: Deskriptorübergänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec5c26bdde8a0d470f2d93e753504bf1c51edcc0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307041"
---
# <a name="descriptor-transitions"></a>Deskriptorübergänge
ODBC-Deskriptoren weisen die folgenden drei Zustände auf.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|D0|Nicht zugeordneter Deskriptor|  
|D1i|Implizit zugeordneter Deskriptor|  
|D1e|Explizit zugeordneter Deskriptor|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den deskriptorzustand auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlcopydesc"></a>Sqlcopyde SC  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|IH 2,2|(HY017)|D0|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|IH 1|--|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn *descriptorhandle* das Handle einer ARD, APD oder IPD war, oder (für **SQLSetDescField**), als *descriptorhandle* das Handle eines IRD-Werts war und *fieldidentifier* SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR war.  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|D0<br /><br /> Nicht zugeordnet|D1i<br /><br /> Implicit (Implizit)|D1e<br /><br /> Explizit|  
|------------------------|----------------------|----------------------|  
|--|--|--|
