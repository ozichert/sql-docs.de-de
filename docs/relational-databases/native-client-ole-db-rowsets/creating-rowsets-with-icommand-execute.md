---
title: Erstellen von Rowsets mit ICommand::Execute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0658928bcf1e4ee5fd67e3c934cd589cc13a28b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286800"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Erstellen von Rowsets mit 'ICommand::Execute'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei Rowsets, die mithilfe der **ICommand::Execute**-Methode erstellt wurden, können die gewünschten Eigenschaften im resultierenden Rowset den Befehlstext einschränken. Dies ist insbesondere für Consumer wichtig, die dynamischen Befehlstext unterstützen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Cursor verwenden, um die von vielen Befehlen generierten Ergebnisse von mehreren Rowsets zu unterstützen. Wenn ein Consumer ein Rowset anfordert, das Unterstützung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursor benötigt, tritt ein Fehler auf, falls der Befehlstext mehr als ein einzelnes Rowset als Ergebnis generiert. Weitere Informationen finden Sie unter [Befehle, die mehrere Rowsetergebnisse erzeugen](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Scrollfähige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter-Rowsets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden von Cursorn unterstützt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzwingt Einschränkungen für Cursor, die durch Änderungen anderer Benutzer der Datenbank beeinflusst werden können. Konkret kann die Reihenfolge der Zeilen in einigen Cursorn nicht verändert werden, und der Versuch, ein Rowset mithilfe eines Befehls zu erstellen, der eine SQL ORDER BY-Klausel enthält, kann fehlschlagen. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
