---
title: getClientConnectionID-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 461a3a0e217fb2ad973830eaffc86ff048830b83
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907605"
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>getClientConnectionID-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Verbindungs-ID des letzten Versuchs der Verbindungsherstellung ab, wobei es keine Rolle spielt, ob dieser Versuch erfolgreich war oder fehlgeschlagen ist.  
  
## <a name="syntax"></a>Syntax  
  
``` 
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine 16-Byte-GUID, die die Verbindungs-ID des letzten Verbindungsversuchs darstellt bzw. NULL, wenn nach dem Initiieren der Verbindungsanforderung und dem Voranmeldungshandshake ein Fehler aufgetreten ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen über den Zugriff auf Diagnoseinformationen im erweiterten Ereignisprotokoll finden Sie unter [Zugreifen auf Diagnoseinformationen im erweiterten Ereignisprotokoll](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 Das folgende Beispiel zeigt, wie die Verbindungs-ID abgerufen wird:  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 Das folgende Beispiel zeigt eine andere Methode zum Abrufen der Verbindungs-ID:  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("...");  
ds.setPassword("...");  
ds.setServerName("...");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID** funktioniert unabhängig davon, mit welcher Serverversion Sie eine Verbindung herstellen, erweiterte Ereignisprotokolle und Einträge zu Fehlern bei Konnektivitätsringpuffern sind in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 R2 und früher nicht verfügbar.  
  
 Wenn das erweiterte Ereignis zur Protokollierung der Verbindungs-ID aktiviert ist, können Sie die Verbindungs-ID im erweiterten Ereignisprotokoll suchen, um festzustellen, ob der Fehler auf dem Server aufgetreten ist. Bei bestimmten Verbindungsfehlern können Sie die Verbindungs-ID auch im Verbindungsringpuffer suchen ([Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer (Behandeln von Verbindungsproblemen in SQL Server 2008 mit dem Verbindungsringpuffer)](https://go.microsoft.com/fwlink/?LinkId=207752)). Wenn die Verbindungs-ID nicht im Konnektivitätsringpuffer enthalten ist, ist von einem Netzwerkfehler auszugehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
