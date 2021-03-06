---
title: SET-Anweisungen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET
- SET_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ISO SET statements
- queries [SQL Server], executing
- dates [SQL Server], SET statements
- time [SQL Server], SET statements
- SET statement, about SET statement
- SET statement
- statistical information [SQL Server], SET statements
- locking [SQL Server], SET statements
ms.assetid: f7e107f8-0fcf-408b-b30f-da2323eeb714
author: CarlRabeler
ms.author: carlrab
monikerRange: = azure-sqldw-latest ||= azuresqldb-current || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 20cf6e1c3c98a99898a7b302980d76cef327be5d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "70228494"
---
# <a name="set-statements-transact-sql"></a>SET-Anweisungen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

Die Programmiersprache [!INCLUDE[tsql](../../includes/tsql-md.md)] bietet eine Reihe von SET-Anweisungen, mit denen die Verarbeitung bestimmter Informationen durch die aktuelle Sitzung geändert werden kann. Die SET-Anweisungen sind in die in der folgenden Tabelle gezeigten Kategorien unterteilt.  
  
Informationen zum Festlegen von lokalen Variablen mit der SET-Anweisung finden Sie unter [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|Category|Anweisungen|  
|--------------|----------------|  
|Datums- und Zeitanweisungen|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|Sperranweisungen|[SET DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [SET LOCK_TIMEOUT](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|Verschiedene Anweisungen|[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [SET FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [SET OFFSETS](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|Abfrageausführungsanweisungen|[SET ARITHABORT](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [SET ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [SET FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /> Hinweis: [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [SET NOCOUNT](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [SET NOEXEC](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [SET NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [SET PARSEONLY](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [SET RESULT SET CACHING](../../t-sql/statements/set-result-set-caching-transact-sql.md?view=azure-sqldw-latest) (Vorschau)<br /> Hinweis:  Diese Funktion gilt nur für Azure SQL Data Warehouse.<br /><br /> [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [SET TEXTSIZE](../../t-sql/statements/set-textsize-transact-sql.md)|  
|Anweisungen für ISO-Einstellungen|[SET ANSI_DEFAULTS](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|Statistikanweisungen|[SET FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [SET STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [SET STATISTICS TIME](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|Transaktionsanweisungen|[SET IMPLICIT_TRANSACTIONS](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [SET REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [SET XACT_ABORT](../../t-sql/statements/set-xact-abort-transact-sql.md)| 
  
## <a name="considerations-when-you-use-the-set-statements"></a>Überlegungen beim Verwenden von SET-Anweisungen  
  
- Alle SET-Anweisungen werden zur Ausführungs- oder Laufzeit ausgeführt, mit Ausnahme der folgenden Anweisungen, die zur Analysezeit ausgeführt werden:

  - SET FIPS_FLAGGER
  - SET OFFSETS
  - SET PARSEONLY
  - und SET QUOTED_IDENTIFIER  
  
- Wenn eine SET-Anweisung in einer gespeicherten Prozedur oder einem Trigger ausgeführt wird, so wird der Wert der SET-Option wiederhergestellt, nachdem die gespeicherte Prozedur oder der Trigger die Steuerung zurückgegeben hat. Wenn Sie eine SET-Anweisung in einer dynamischen SQL-Zeichenfolge angeben, die entweder mithilfe von **sp_executesql** oder mithilfe von EXECUTE ausgeführt wird, wird der Wert der SET-Option ebenfalls wiederhergestellt, nachdem der von Ihnen in der dynamischen SQL-Zeichenfolge angegebene Batch die Steuerung zurückgegeben hat.  
  
- Gespeicherte Prozeduren werden mit den SET-Einstellungen ausgeführt, die zur Ausführungszeit angegeben wurden. Ausgenommen hiervon sind SET ANSI_NULLS und SET QUOTED_IDENTIFIER. Gespeicherte Prozeduren, für die SET ANSI_NULLS oder SET QUOTED_IDENTIFIER angegeben ist, verwenden die Einstellung, die zur Erstellungszeit der gespeicherten Prozedur angegeben wurde. Bei Verwendung innerhalb einer gespeicherten Prozedur werden SET-Einstellungen ignoriert.  
  
- Die **Benutzeroptionen**-Einstellung von **sp_configure** ermöglicht serverweite Einstellungen, und sie arbeitet datenbankübergreifend. Diese Einstellung wirkt außerdem wie eine explizite SET-Anweisung, mit der Ausnahme, dass sie zur Anmeldezeit erfolgt.  
  
- Datenbankeinstellungen, die mithilfe von ALTER DATABASE festgelegt werden, sind nur auf Datenbankebene gültig und treten nur dann in Kraft, wenn sie explizit festgelegt werden. Datenbankeinstellungen überschreiben Instanzoptionseinstellungen, die mithilfe von **sp_configure** festgelegt werden.  
  
- Wenn eine SET-Anweisung die Einstellungen ON und OFF verwendet, können Sie eine der Einstellungen für mehrere SET-Optionen angeben.
  
    > [!NOTE]  
    >  Dies gilt nicht für die statistikbezogenen SET-Optionen.
  
     Beispielsweise legt `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` sowohl für QUOTED_IDENTIFIER als auch für ANSI_NULLS die Einstellung ON fest.  
  
- Einstellungen von SET-Anweisungen überschreiben die Einstellungen identischer Datenbankoptionen, die mithilfe von ALTER DATABASE festgelegt werden. Beispielsweise überschreibt der in einer SET ANSI_NULLS-Anweisung angegebene Wert die Datenbankeinstellung für ANSI_NULLs. Darüber hinaus werden einige Verbindungseinstellungen automatisch auf ON festgelegt, wenn ein Benutzer eine Verbindung zu einer Datenbank herstellt und dabei die Werte verwendet, die durch vorherige Verwendung der **sp_configure Benutzeroptionen**-Einstellung in Kraft getreten sind oder die auf alle ODBC- und OLE DB-Verbindungen angewendet werden.  
  
- Die Anweisungen ALTER, CREATE und DROP DATABASE berücksichtigen die Einstellung von SET LOCK_TIMEOUT nicht.  
  
- Wenn eine globale oder zusammengefasste SET-Anweisung mehrere Einstellungen festlegt, setzt das Ausgeben einer solchen SET-Anweisung die vorherigen Einstellungen aller Optionen außer Kraft, auf die sich die zusammengefasste SET-Anweisung auswirkt. Wird eine SET-Option, die von einer zusammengefassten SET-Anweisung betroffen ist, nach Ausgabe der zusammengefassten SET-Anweisung festgelegt, überschreibt die individuelle SET-Anweisung die vergleichbaren Einstellungen der zusammengefassten SET-Anweisung. Ein Beispiel für eine zusammengefasste SET-Anweisung wäre SET ANSI_DEFAULTS.  
  
- Wenn Batches verwendet werden, wird der Datenbankkontext durch den Batch bestimmt, der mithilfe der USE-Anweisung eingerichtet wird. Ungeplante Abfragen und alle anderen Anweisungen, die außerhalb der gespeicherten Prozedur ausgeführt werden und sich in Batches befinden, übernehmen die Optionseinstellungen der Datenbank und der Verbindung, die mit der USE-Anweisung eingerichtet werden.  
  
- MARS-Anforderungen (Multiple Active Result Set) nutzen gemeinsam einen globalen Status, der die jeweils aktuellen Einstellungen der SET-Optionen für die Sitzung enthält. Bei der Ausführung kann jede Anforderung die SET-Optionen ändern. Die Änderungen gelten speziell für den Anforderungskontext, in dem sie festgelegt werden, und haben keine Auswirkungen auf andere gleichzeitige MARS-Anforderungen. Nachdem die Anforderungsausführung abgeschlossen ist, werden die neuen SET-Optionen jedoch in den globalen Status der Sitzung kopiert. Neue Anforderungen, die nach dieser Änderung unter der gleichen Sitzung ausgeführt werden, verwenden diese neuen SET-Optionseinstellungen.  
  
- Wird eine gespeicherte Prozedur aus einem Batch oder einer anderen gespeicherten Prozedur heraus ausgeführt, werden hierbei die Optionswerte verwendet, die in der Datenbank eingerichtet sind, die die gespeicherte Prozedur enthält. Wenn z.B. die gespeicherte Prozedur **db1.dbo.sp1** die gespeicherte Prozedur **db2.dbo.sp2** aufruft, wird die gespeicherte Prozedur **sp1** unter der aktuellen Einstellung des Kompatibilitätsgrades von Datenbank **db1** ausgeführt, und die gespeicherte Prozedur **sp2** wird unter der aktuellen Einstellung des Kompatibilitätsgrades von Datenbank **db2** ausgeführt.  
  
- Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung Objekte betrifft, die sich in mehreren Datenbanken befinden, gelten der aktuelle Datenbankkontext und der aktuelle Verbindungskontext für die Anweisung. Befindet sich die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung in diesem Fall in einem Batch, handelt es sich bei dem aktuellen Verbindungskontext um die durch die USE-Anweisung definierte Datenbank. Befindet sich die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung in einer gespeicherten Prozedur, handelt es sich bei dem Verbindungskontext um die Datenbank, die die gespeicherte Prozedur enthält.  
  
- Beim Erstellen und Bearbeiten von Indizes für berechnete Spalten oder indizierten Sichten müssen Sie die folgenden SET-Optionen auf ON festlegen: ARITHABORT, CONCAT_NULL_YIELDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING und ANSI_WARNINGS. Die Option NUMERIC_ROUNDABORT muss auf OFF festgelegt sein.  
  
  Wenn Sie keine dieser Optionen auf die erforderlichen Werte festlegen, schlagen die Aktionen INSERT, UPDATE, DELETE, DBCC CHECKDB und DBCC CHECKTABLE für die indizierten Sichten oder Tabellen mit Indizes für berechnete Spalten fehl. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] löst einen Fehler aus, wobei alle Optionen aufgelistet werden, die nicht ordnungsgemäß festgelegt sind. Außerdem verarbeitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die SELECT-Anweisungen in diesen Tabellen oder indizierten Sichten so, als seien die Indizes auf den berechneten Spalten oder Sichten nicht vorhanden. 

- Wenn RESULT_SET_CACHING auf ON festgelegt ist, aktiviert dies die Funktion für Ergebniszwischenspeicherung für die aktuelle Clientsitzung.   Result_set_caching kann für eine Sitzung nicht aktiviert werden (ON), wenn es auf Datenbankebene deaktiviert (OFF) ist.    Wenn RESULT_SET_CACHING auf OFF festgelegt ist, ist die Funktion für Ergebniszwischenspeicherung für die aktuelle Clientsitzung deaktiviert. Um diese Einstellung zu ändern, ist die Mitgliedschaft in der Rolle „public“ (Öffentlich) erforderlich.
Gilt für: Azure SQL Data Warehouse Gen2
