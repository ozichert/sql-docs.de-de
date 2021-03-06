---
title: Verschieben von Datenbankdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: c53e9ee51714ebfcce81a722f78a4f79cbc2530f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68067321"
---
# <a name="move-database-files"></a>Verschieben von Datenbankdateien
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können Sie System- und Benutzerdatenbanken durch Angeben des neuen Dateispeicherorts in der FILENAME-Klausel der [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) -Anweisung verschieben. Auf diese Weise können Daten-, Protokoll- und Volltextkatalogdateien verschoben werden. Dies kann in folgenden Situationen nützlich sein:  
  
-   Bei der Wiederherstellung nach Fehlern. Wenn z. B. die Datenbank aufgrund eines Hardwarefehlers als fehlerverdächtig eingestuft oder heruntergefahren wurde.  
  
-   Bei geplanter Verschiebung.  
  
-   Verschiebung aufgrund planmäßiger Datenträgerwartung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Verschieben von Benutzerdatenbanken](../../relational-databases/databases/move-user-databases.md)|Beschreibt die Prozeduren, um Benutzerdatenbankdateien und Volltextkatalogdateien an einen neuen Speicherort zu verschieben.|  
|[Verschieben von Systemdatenbanken](../../relational-databases/databases/move-system-databases.md)|Beschreibt die Prozeduren, um Systemdatenbankdateien an einen neuen Speicherort zu verschieben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
