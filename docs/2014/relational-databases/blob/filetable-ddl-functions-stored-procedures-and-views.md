---
title: FileTable-DDL, Funktionen, gespeicherte Prozeduren und Ansichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85e0c761f5dc784698b3aed361ce50488a93e366
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010101"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>FileTable-DDL, Funktionen, gespeicherte Prozeduren und Sichten
  Listet die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekte auf, die zur Unterstützung der FileTable-Funktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hinzugefügt oder geändert wurden.  
  
 Die Spalte "Status" in den folgenden Tabellen gibt an, ob das Element in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]neu ist oder in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden war und in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] geändert wurde, um die semantische Suche zu unterstützen.  
  
 Eine Liste der Anweisungen und Datenbankobjekte, die FILESTREAM unterstützen, finden Sie unter [FILESTREAM DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Transact-SQL-DDL-Anweisungen (Data Definition Language, Datendefinitionssprache)  
  
|Object|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)<br /><br /> [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Geändert|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)|Geändert|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)|Geändert|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)|Geändert|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)<br /><br /> [RESTORE-Argumente &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)|Geändert||  
  
##  <a name="functions"></a><a name="func"></a> Funktionen  
  
|Object|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|**Hinzugefügt**|[Verwenden von Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|**Hinzugefügt**|[Verwenden von Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|**Hinzugefügt**|[Verwenden von Verzeichnissen und Pfaden in FileTables](work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="stored-procedures"></a><a name="sproc"></a> Gespeicherte Prozeduren  
  
|Object|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
  
##  <a name="catalog-views"></a><a name="cv"></a> Katalogsichten  
  
|Object|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)|**Hinzugefügt**|[Aktivieren der erforderlichen Komponenten für FileTable](enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)|**Hinzugefügt**|[Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Verwalten von FileTables](manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Geändert|[Verwalten von FileTables](manage-filetables.md)|  
  
##  <a name="dynamic-management-views"></a><a name="dmv"></a> Dynamische Verwaltungssichten  
  
|Object|Status|Weitere Informationen|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)|**Hinzugefügt**|[Verwalten von FileTables](manage-filetables.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von FileTables](manage-filetables.md)  
  
  
