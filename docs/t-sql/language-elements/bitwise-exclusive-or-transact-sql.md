---
title: ^ (Bitweises exklusives OR) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 664e3cd0fc687509c630258a681c155d94863d39
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67943063"
---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (Bitweises exklusives OR) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Führt einen bitweisen exklusiven OR-Vorgang zwischen zwei ganzzahligen Werten aus.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein gültiger [expression](../../t-sql/language-elements/expressions-transact-sql.md)-Ausdruck eines beliebigen Datentyps der ganzzahligen Datentypkategorie oder des Datentyps **bit**, **binary** oder **varbinary**. *expression* wird in der bitweisen Operation als binäre Zahl behandelt.  
  
> [!NOTE]  
>  Nur eines der *expression*-Argumente kann in einer bitweisen Operation vom Datentyp **binary** oder **varbinary** sein.  
  
## <a name="result-types"></a>Ergebnistypen  
 **int**, wenn die Eingabewerte vom Typ **int** sind.  
  
 **smallint**, wenn die Eingabewerte vom Typ **smallint** sind.  
  
 **tinyint**, wenn die Eingabewerte vom Typ **tinyint** sind  
  
## <a name="remarks"></a>Bemerkungen  
 Mit dem bitweisen Operator **^** wird zwischen zwei Ausdrücken ein bitweises logisches exklusives OR ausgeführt, indem die jeweils entsprechenden Bits der beiden Ausdrücke verarbeitet werden. Ein Ergebnisbit wird genau dann auf den Wert 1 festgelegt, wenn genau ein Bit, also nicht beide Bits (für das aktuell aufzulösende Bit), der Eingabeausdrücke den Wert 1 aufweist. Falls die Bits beide den Wert 0 oder beide den Wert 1 besitzen, wird das entsprechende Bit im Ergebnis auf 0 festgelegt.  
  
 Wenn der linke und der rechte Ausdruck unterschiedliche ganzzahlige Datentypen aufweisen (beispielsweise ist der linke *expression*-Ausdruck vom Datentyp **smallint** und der rechte *expression*-Ausdruck von Datentyp **int**), wird das Argument mit dem kleineren Datentyp in den größeren Datentyp konvertiert. In diesem Fall wird **smallint**_expression_ in einen **int**-Typ konvertiert.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Tabelle mit dem **int**-Datentyp erstellt, um die ursprünglichen Werte zu speichern, und zwei Werte in eine Zeile einfügt.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 Die folgende Abfrage führt das bitweise exklusive OR für die Spalten `a_int_value` und `b_int_value` aus.  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Im Folgenden wird das Resultset aufgeführt:  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 Die binäre Darstellung von 170 (`a_int_value` oder `A`) ist `0000 0000 1010 1010`. Die binäre Darstellung von 75 (`b_int_value` oder `B`) ist `0000 0000 0100 1011`. Die Anwendung des bitweisen exklusiven OR-Vorgangs auf diese beiden Werte erzeugt das binäre Ergebnis `0000 0000 1110 0001`, was dem dezimalen Wert 225 entspricht.  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Bitweise Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^= &#40;Bitwise Exclusive OR Assignment&#41; &#40;Transact-SQL&#41; (^= (Zuweisung mit bitweisem exklusiven OR (Transact-SQL))](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [Verbundoperatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


