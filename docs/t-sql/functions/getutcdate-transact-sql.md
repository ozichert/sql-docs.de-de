---
title: GETUTCDATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/02/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GETUTCDATE
- GETUTCDATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], UTC time
- dates [SQL Server], functions
- UTC time [SQL Server]
- date and time [SQL Server], GETUTCDATE
- Universal Time Coordinate [SQL Server]
- GETUTCDATE function [SQL Server]
- current date and time [SQL Server]
- time [SQL Server], current
- Greenwich Mean Time [SQL Server]
- functions [SQL Server], time
- system date and time [SQL Server]
- current UTC date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: 48a5b230-102e-4a89-bb2a-fcf0cac862bb
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ca78e55c8897a9c0cc71be0eb9650ab89125d21
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826861"
---
# <a name="getutcdate-transact-sql"></a>GETUTCDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den aktuellen Zeitstempel des Datenbanksystems als **datetime**-Wert zurück. Der Zeitzonenoffset der Datenbank wird nicht einbezogen. Dieser Wert stellt die aktuelle UTC-Zeit (Coordinated Universal Time) dar. Dieser Wert wird aus dem Betriebssystem des Computers abgeleitet, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
> [!NOTE]  
>  SYSDATETIME und SYSUTCDATETIME weisen eine höhere Genauigkeit bezüglich der Bruchteile von Sekunden auf als GETDATE und GETUTCDATE. SYSDATETIMEOFFSET schließt den Zeitzonenoffset des Systems ein. SYSDATETIME, SYSUTCDATETIME und SYSDATETIMEOFFSET können einer Variablen eines beliebigen Datums- und Zeittyps zugewiesen werden.  
  
 Eine Übersicht über alle Datums- und Uhrzeitdatentypen und zugehörige Funktionen für [!INCLUDE[tsql](../../includes/tsql-md.md)] finden Sie unter [Date and Time Data Types and Functions &#40;Transact-SQL&#41; (Datums- und Uhrzeitdatentypen und zugehörige Funktionen)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
GETUTCDATE()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **datetime**  
  
## <a name="remarks"></a>Bemerkungen  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen können auf eine beliebige Position von GETUTCDATE verweisen, die auf einen **datetime**-Ausdruck verweisen kann.  
  
 GETUTCDATE ist eine nicht deterministische Funktion. Sichten und Ausdrücke, die in einer Spalte auf diese Funktion verweisen, können nicht indiziert werden.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen werden die sechs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemfunktionen verwendet, die das aktuelle Datum und die aktuelle Uhrzeit wiedergeben, um das Datum, die Uhrzeit oder beides zurückzugeben. Die Werte werden der Reihe nach zurückgegeben und können sich daher in Bruchteilen von Sekunden unterscheiden.  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. Abrufen des aktuellen Systemdatums und der aktuellen Systemzeit  
  
```  
SELECT 'SYSDATETIME()      ', SYSDATETIME();  
SELECT 'SYSDATETIMEOFFSET()', SYSDATETIMEOFFSET();  
SELECT 'SYSUTCDATETIME()   ', SYSUTCDATETIME();  
SELECT 'CURRENT_TIMESTAMP  ', CURRENT_TIMESTAMP;  
SELECT 'GETDATE()          ', GETDATE();  
SELECT 'GETUTCDATE()       ', GETUTCDATE();  
/* Returned:  
SYSDATETIME()            2007-05-03 18:34:11.9351421  
SYSDATETIMEOFFSET()      2007-05-03 18:34:11.9351421 -07:00  
SYSUTCDATETIME()         2007-05-04 01:34:11.9351421  
CURRENT_TIMESTAMP        2007-05-03 18:34:11.933  
GETDATE()                2007-05-03 18:34:11.933  
GETUTCDATE()             2007-05-04 01:34:11.933  
*/  
```  
  
### <a name="b-getting-the-current-system-date"></a>B. Abrufen des aktuellen Systemdatums  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (date, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (date, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (date, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (date, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (date, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (date, GETUTCDATE());  
  
/* Returned:   
SYSDATETIME()            2007-05-03  
SYSDATETIMEOFFSET()      2007-05-03  
SYSUTCDATETIME()         2007-05-04  
CURRENT_TIMESTAMP        2007-05-03  
GETDATE()                2007-05-03  
GETUTCDATE()             2007-05-04  
*/  
```  
  
### <a name="c-getting-the-current-system-time"></a>C. Abrufen der aktuellen Systemzeit  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (time, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (time, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (time, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (time, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (time, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (time, GETUTCDATE());  
/* Returned  
SYSDATETIME()            18:25:01.6958841  
SYSDATETIMEOFFSET()      18:25:01.6958841  
SYSUTCDATETIME()         01:25:01.6958841  
CURRENT_TIMESTAMP        18:25:01.6930000  
GETDATE()                18:25:01.6930000  
GETUTCDATE()             01:25:01.6930000  
*/  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


