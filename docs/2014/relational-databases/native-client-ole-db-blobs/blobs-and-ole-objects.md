---
title: Blobs und OLE-Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1bdea3453c38303dc6aaa6989f905db243d0be90
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709155"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **ISequentialStream** -Schnittstelle verfügbar, um den Consumerzugriff auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen **ntext**, **Text**, **Image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)** und XML als Binary Large Objects (BLOB) zu unterstützen. Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.  
  
 Ein Beispiel für diese Feature finden Sie unter [Festlegen von großen Daten &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann eine vom Consumer implementierte **IStorage** -Schnittstelle verwenden, wenn der Consumer den Schnittstellen Zeiger in einem Accessor bereitstellt, der für die Datenänderung gebunden ist.  
  
 Bei Datentypen mit umfangreichen Werten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft der Native Client OLE DB-Anbieter die typgrößen Annahmen in **IRowset** und DDL-Schnittstellen. Spalten mit den Datentypen **varchar**, **nvarchar**und **varbinary** , deren maximale Größe auf Unlimited festgelegt ist, werden durch die Schemarowsets und Schnittstellen, die Spaltendatentypen zurückgeben, als ISLONG dargestellt.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die Typen **varchar (max)**, **varbinary (max)** und **nvarchar (max)** als DBTYPE_STR, DBTYPE_BYTES und DBTYPE_WSTR verfügbar.  
  
 Um mit diesen Typen zu arbeiten, hat eine Anwendung die folgenden Optionen:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit großen Werten, um Szenarios zu vereinfachen, in denen eine gespeicherte Prozedur diese Datentypen als Rückgabewerte zurückgibt, die als DBTYPE_IUNKNOWN für den Client verfügbar gemacht werden.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann nur ein einzelnes geöffnetes Speicher Objekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der Standardwert der DBPROP_BLOCKINGSTORAGEOBJECTS schreibgeschützten Eigenschaft VARIANT_TRUE. Das zeigt an, dass einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehlschlagen, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten, die von einem vom Consumer implementierten Speicher Objekt vorgelegt werden, muss dem Native Client OLE DB-Anbieter bekannt gemacht werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn der Zeilen Accessor erstellt wird, der auf das Speicher Objekt verweist. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehr als einen einzelnen großen Datenwert enthält und DBPROP_ACCESSORDER nicht DBPROPVAL_AO_RANDOM ist, muss der Consumer entweder ein vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cursor unterstütztes Native Client OLE DB Anbieter-Rowset verwenden, um Zeilendaten abzurufen oder alle großen Datenwerte zu verarbeiten, bevor andere Zeilen Werte abgerufen werden. Wenn DBPROP_ACCESSORDER DBPROPVAL_AO_RANDOM ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert der Native Client OLE DB-Anbieter alle XML-Datentypen als Binary Large Objects (BLOB) zwischen, sodass in beliebiger Reihenfolge auf ihn zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von Datentypen mit umfangreichen Werten](../native-client/features/using-large-value-types.md)  
  
  
