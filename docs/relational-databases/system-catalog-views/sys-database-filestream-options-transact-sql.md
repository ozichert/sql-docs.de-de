---
title: sys. database_filestream_options (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4c9ec7c14bf192891e547c68ca85b5b055eb6815
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823497"
---
# <a name="sysdatabase_filestream_options-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt Informationen zur Ebene des nicht transaktionalen Zugriffs auf die aktivierten FILESTREAM-Daten in FileTables an. Enthält eine Zeile für jede Datenbank in der SQL Server-Instanz.  
  
 Weitere Informationen zu FileTables finden Sie unter [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Spalte|Typ|Beschreibung|  
|------------|----------|-----------------|  
|**database_id**|**int**|Die ID der Datenbank. Dieser Wert ist innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig.|  
|**directory_name**|**nvarchar(255)**|Das Verzeichnis auf Datenbankebene für alle FileTable-Namespaces.|  
|**non_transacted_access**|**tinyint**|Die Ebene des nicht transaktionalen Zugriffs auf FILESTREAM-Daten, die aktiviert sind. Die Zugriffsebene wird durch die NON_TRANSACTED_ACCESS-Option der **Create Database** -oder **ALTER DATABASE** -Anweisung festgelegt.<br /><br /> Diese Einstellung besitzt einen der folgenden Werte:<br /><br /> 0-nicht aktiviert. Dies ist der Standardwert. Diese Ebene wird festgelegt, indem der Wert **OFF** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 1-Schreib geschützter Zugriff. Diese Ebene wird festgelegt, indem der Wert **READ_ONLY** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 3: Vollzugriff. Diese Ebene wird festgelegt, indem der Wert **FULL** für die **NON_TRANSACTED_ACCESS** -Option angegeben wird.<br /><br /> 5 – Im Übergang zu READONLY.<br /><br /> 6-in-Übergang zu aus|  
|**non_transacted_access_desc**|**nvarchar(60)**|Die Beschreibung der Ebene des nicht transaktionalen Zugriffs, der in non_transacted_access identifiziert wird.<br /><br /> Diese Einstellung besitzt einen der folgenden Werte:<br /><br /> None: Dies ist der Standardwert.<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren der erforderlichen Komponenten für FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
