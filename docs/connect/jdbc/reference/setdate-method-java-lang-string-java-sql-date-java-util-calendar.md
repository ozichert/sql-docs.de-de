---
title: setDate-Methode für Datums- und Kalenderwerte – Zeichenfolge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setDate (java.lang.String, java.sql.Date, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fd152ad6-dd5e-49ef-b166-917371a2cba6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 42562914e8c99debbc9423c8a5d63cd921779c4a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926669"
---
# <a name="setdate-method-javalangstring-javasqldate-javautilcalendar"></a>setDate-Methode (java.lang.String, java.sql.Date, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf die angegebenen Datums- und Kalenderwerte fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setDate(java.lang.String sCol,  
                    java.sql.Date x,  
                    java.util.Calendar c)  
```  
  
#### <a name="parameters"></a>Parameter  
 *n*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *x*  
  
 Ein Date-Objekt  
  
 *c*  
  
 Ein Calendar-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setDate-Methode wird von der setDate-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
