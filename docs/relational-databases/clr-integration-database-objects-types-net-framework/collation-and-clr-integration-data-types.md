---
title: Collations-und CLR-Integrations Datentypen | Microsoft-Dokumentation
description: In SQL Server CLR-Integration verwenden die .NET Framework String-APIs die CompareInfo-Eigenschaft von CultureInfo des aktuellen Threads, um Zeichen folgen Vergleiche auszuführen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 46e4d450db90e4bfc93187a48ca8adae472036c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488492"
---
# <a name="collation-and-clr-integration-data-types"></a>Sortierung und Datentypen für die CLR-Integration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]werden Sortierungen vom **CompareInfo** -Objekt gehandhabt. Die Zeichenfolgen-APIs (Application Programming Interface, API) von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verwenden die **CompareInfo** -Eigenschaft zusammen mit dem **CultureInfo** -Objekt des aktuellen Threads, um Zeichenfolgenvergleiche durchzuführen. Die Standardeinstellung des **CultureInfo** -Objekts basiert auf der Einstellung für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema des Computers, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dies bestimmt die Standardvergleichssemantik bei Vergleichen von **CultureInfo** -Werten, wenn **System.String** nicht explizit angegeben wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die **CompareInfo** -Eigenschaft wird von nicht explizit in die Datenbank-oder Server Sortierung geändert. Falls erforderlich, müssen Benutzer die entsprechende **CompareInfo** -Eigenschaft in ihren Routinen festlegen.  
  
## <a name="parameter-collation"></a>Parametersortierung  
 Wenn Sie eine Common Language Runtime (CLR)-Routine erstellen und ein Parameter einer CLR-Methode, die an die Routine gebunden ist, den Typ **SqlString**hat, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt eine Instanz des-Parameters mit der Standardsortierung der Datenbank, die die aufrufende Routine enthält. Wenn ein Parameter nicht vom Typ **SqlType** ist (beispielsweise **String** , nicht **SQLString**), werden die Sortierungsinformationen der Datenbank nicht mit dem Parameter verknüpft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
