---
title: USER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- USER
- USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- system-supplied usernames [SQL Server]
- USER function
- users [SQL Server], database names
- names [SQL Server], database users
- database usernames [SQL Server]
ms.assetid: 82bbbd94-870c-4c43-9ed9-d9abc767a6be
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 21ae6663e264b84987b50ea48ffc91f06c9f2052
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832075"
---
# <a name="user-transact-sql"></a>USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Ermöglicht das Einfügen eines vom System bereitgestellten Werts für den Datenbankbenutzernamen des aktuellen Benutzers in eine Tabelle, wenn kein Standardwert angegeben ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
USER  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Bemerkungen  
 USER bietet die gleiche Funktionalität wie die USER_NAME-Systemfunktion.  
  
 Verwenden Sie die USER-Funktion mit DEFAULT-Einschränkungen in der CREATE TABLE- oder ALTER TABLE-Anweisung oder als beliebige Standardfunktion.  
  
 USER gibt immer den Namen des aktuellen Kontexts zurück. Wenn USER nach einer EXECUTE AS-Anweisung aufgerufen wird, wird der Name des Kontexts zurückgegeben, dessen Identität angenommen wurde.  
  
 Greift ein Windows-Prinzipal über die Mitgliedschaft in einer Gruppe auf die Datenbank zu, gibt USER den Namen des Windows-Prinzipals statt des Namens der Gruppe zurück.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-user-to-return-the-database-user-name"></a>A. Verwenden von USER zum Zurückgeben des Datenbankbenutzernamens  
 Im folgenden Beispiel wird eine Variable als `char`-Datentyp deklariert, ihr wird der aktuelle Wert von USER zugewiesen, und anschließend wird die Variable mit einer Textbeschreibung gedruckt.  
  
```  
DECLARE @usr char(30)  
SET @usr = user  
SELECT 'The current user''s database username is: '+ @usr  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
-----------------------------------------------------------------------  
The current user's database username is: dbo  
  
(1 row(s) affected)
```  
  
### <a name="b-using-user-with-default-constraints"></a>B. Verwenden von USER mit DEFAULT-Einschränkungen  
 Im folgenden Beispiel wird eine Tabelle mit `USER` als `DEFAULT`-Einschränkung für den Verkäufer in einer Zeile mit Verkaufszahlen erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE inventory22  
(  
 part_id int IDENTITY(100, 1) NOT NULL,  
 description varchar(30) NOT NULL,  
 entry_person varchar(30) NOT NULL DEFAULT USER   
)  
GO  
INSERT inventory22 (description)  
VALUES ('Red pencil')  
INSERT inventory22 (description)  
VALUES ('Blue pencil')  
INSERT inventory22 (description)  
VALUES ('Green pencil')  
INSERT inventory22 (description)  
VALUES ('Black pencil')  
INSERT inventory22 (description)  
VALUES ('Yellow pencil')  
GO  
```  
  
 Im Folgenden wird die Abfrage zur Auswahl aller Informationen aus der `inventory22`-Tabelle aufgeführt:  
  
```  
SELECT * FROM inventory22 ORDER BY part_id;  
GO  
```  
  
 Im Folgenden wird das Resultset aufgeführt (beachten Sie den `entry-person`-Wert):  
  
 ```
part_id     description                    entry_person
----------- ------------------------------ -------------------------
100         Red pencil                     dbo
101         Blue pencil                    dbo
102         Green pencil                   dbo
103         Black pencil                   dbo
104         Yellow pencil                  dbo
  
(5 row(s) affected)
```  
  
### <a name="c-using-user-in-combination-with-execute-as"></a>C. Verwenden von USER in Kombination mit EXECUTE AS  
 Im folgenden Beispiel wird das Verhalten von `USER` bei Aufruf in einer Sitzung mit Identitätswechsel gezeigt.  
  
```  
SELECT USER;  
GO  
EXECUTE AS USER = 'Mario';  
GO  
SELECT USER;  
GO  
REVERT;  
GO  
SELECT USER;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
DBO
Mario
DBO
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40;Transact-SQL&#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER &#40;Transact-SQL&#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [SESSION_USER &#40;Transact-SQL&#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [SYSTEM_USER &#40;Transact-SQL&#41;](../../t-sql/functions/system-user-transact-sql.md)   
 [USER_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/user-name-transact-sql.md)  
  
  

