---
title: Befehle, die mehrere Rowsetergebnisse erzeugen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2cbdba7e16240b5adfd14c43a5916aaaf8cf0400
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304481"
---
# <a name="commands-generating-multiple-rowset-results"></a>Mehrere Rowsetergebnisse generierende Befehle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann mehrere Rowsets von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anweisungen zurückgeben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anweisungen geben unter folgenden Bedingungen mehrere Rowsetergebnisse zurück:  
  
-   SQL-Anweisungen im Batchmodus werden als einzelner Befehl gesendet.  
  
-   Gespeicherte Prozeduren implementieren einen Batch SQL-Anweisungen.  
  
## <a name="batches"></a>Batches  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt das Semikolon als Batch Trennzeichen für SQL-Anweisungen:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Mehrere SQL-Anweisungen in einem Batch zu senden ist effizienter, als jede SQL-Anweisung einzeln auszuführen. Durch Senden eines Batches werden die Netzwerkroundtrips vom Client auf den Server reduziert.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt ein Resultset für jede Anweisung in einer gespeicherten Prozedur zurück, sodass die meisten gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren mehrere Resultsets zurückgeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets](../../relational-databases/native-client-ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
