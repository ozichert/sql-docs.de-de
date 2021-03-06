---
title: Blobs und OLE-Objekte | Microsoft-Dokumentation
description: BLOBs und OLE-Objekte
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 70d3ffccfc9613434b09335944e445a2705b95c3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67988667"
---
# <a name="blobs-and-ole-objects"></a>BLOBs und OLE-Objekte
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **ISequentialStream**-Schnittstelle verfügbar, um den Consumerzugriff auf die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen **ntext**, **text**, **image**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** und XML als Binary Large Objects (Blobs) zu unterstützen. Die Methode **Read** für **ISequentialStream** ermöglicht dem Consumer, große Datenmengen in überschaubaren Abschnitten abzurufen.  
  
 Ein Beispiel für diese Feature finden Sie unter [Festlegen von großen Daten &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Der OLE DB-Treiber für SQL Server kann eine vom Consumer implementierte **IStorage**-Schnittstelle verwenden, wenn der Consumer den Schnittstellenzeiger in einem für Datenänderungen gebundenen Accessor bereitstellt.  
  
 Für Datentypen mit umfangreichen Werten prüft der OLE DB-Treiber für SQL Server, ob in **IRowset** und DDL-Schnittstellen Annahmen über die Typgröße vorhanden sind. Spalten mit den Datentypen **varchar**, **nvarchar** und **varbinary**, bei denen die maximale Größe auf „Unlimited“ festgelegt ist, werden von den Schemarowsets und Schnittstellen, die Spaltendatentypen wiedergeben, als ISLONG dargestellt.  
  
 Der OLE DB-Treiber für SQL Server macht die Datentypen **varchar(max)** , **varbinary(max)** und **nvarchar(max)** als DBTYPE_STR, DBTYPE_BYTES bzw. DBTYPE_WSTR verfügbar.  
  
 Um mit diesen Typen zu arbeiten, stehen der Anwendung die folgenden Optionen zur Verfügung:  
  
-   Als den betreffenden Typ binden (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Wenn der Puffer nicht groß genug ist, werden Daten abgeschnitten, wie dies auch in früheren Versionen der Fall war (obwohl jetzt umfangreichere Werte verfügbar sind).  
  
-   Als den betreffenden Typ binden und zudem DBTYPE_BYREF angeben  
  
-   Als DBTYPE_IUNKNOWN binden und Streaming verwenden  
  
 Wenn die Bindung an DBTYPE_IUNKNOWN erfolgt, wird die Streamingfunktion ISequentialStream verwendet. Der OLE DB-Treiber für SQL Server unterstützt das Binden von Ausgabeparametern als DBTYPE_IUNKNOWN für Datentypen mit großen Werten. Damit werden Szenarios unterstützt, in denen gespeicherte Prozeduren diese Datentypen als Rückgabewerte zurückgeben, die alle als DBTYPE_IUNKNOWN an den Client zurückgegeben werden.  
  
## <a name="storage-object-limitations"></a>Speicherobjekteinschränkungen  
  
-   Der OLE DB-Treiber für SQL Server kann nur ein einzelnes geöffnetes Speicherobjekt unterstützen. Wenn versucht wird, mehrere Speicherobjekte zu öffnen (um einen Verweis auf mehrere **ISequentialStream**-Schnittstellenzeiger abzurufen), wird DBSTATUS_E_CANTCREATE zurückgegeben.  
  
-   Im OLE DB-Treiber für SQL Server lautet der Standardwert der schreibgeschützten DBPROP_BLOCKINGSTORAGEOBJECTS-Eigenschaft VARIANT_TRUE. Deshalb schlagen einige Methoden (solche, die sich nicht in den Speicherobjekten befinden) mit E_UNEXPECTED fehl, wenn ein Speicherobjekt aktiv ist.  
  
-   Die Länge der Daten eines von einem Consumer implementierten Speicherobjekts muss dem OLE DB-Treiber für SQL Server mitgeteilt werden, wenn der auf das Speicherobjekt verweisende Zeilenaccessor erstellt wird. Der Consumer muss einen Längenindikator in der zur Accessorerstellung verwendeten DBBINDING-Struktur binden.  
  
-   Wenn eine Zeile mehrere große Datenwerte enthält und DBPROP_ACCESSORDER nicht auf DBPROPVAL_AO_RANDOM lautet, muss der Consumer entweder ein vom Cursor des OLE DB-Treibers für SQL Server unterstütztes Rowset verwenden, um Zeilendaten abzurufen, oder alle großen Datenwerte vor dem Abrufen weiterer Zeilenwerte verarbeiten. Wenn DBPROP_ACCESSORDER auf DBPROPVAL_AO_RANDOM lautet, speichert der OLE DB-Treiber für SQL Server alle XML-Datentypen als Binary Large Objects (BLOBs) zwischen, damit in jeder beliebigen Reihenfolge auf sie zugegriffen werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Abrufen großer Datenmengen](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Festlegen großer Datenmengen](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Streamingunterstützung für BLOB-Ausgabeparameter](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB Driver for SQL Server Programming (OLE DB-Treiber für SQL Server-Programmierung)](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Verwenden von Datentypen mit umfangreichen Werten](../../oledb/features/using-large-value-types.md)  
  
  
