---
title: SIGN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIGN_TSQL
- SIGN
dev_langs:
- TSQL
helpviewer_keywords:
- '- (negative)'
- + (positive sign)
- zero (0)
- SIGN function
- positive values [SQL Server]
- 0 (zero)
- negative values
ms.assetid: c3a98b52-6fbe-4127-a5c9-8a4922e83e28
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ec2e33afb82d3b3a733f98670c20de36681eabfa
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828592"
---
# <a name="sign-transact-sql"></a>SIGN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt das Vorzeichen des angegebenen Ausdrucks zurück: positiv (+1), Null (0) oder negativ (-1).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SIGN ( numeric_expression )  
```  
  

## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) der genauen numerischen oder ungefähren numerischen Datentypkategorie, mit Ausnahme des **bit**-Datentyps.  
  
## <a name="return-types"></a>Rückgabetypen  
  
|Angegebener Ausdruck|Rückgabetyp|  
|--------------------------|-----------------|  
|**bigint**|**bigint**|  
|**int/smallint/tinyint**|**int**|  
|**money/smallmoney**|**money**|  
|**numeric/decimal**|**numeric/decimal**|  
|**Andere Typen**|**float**|  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die SIGN-Werte der Zahlen von -1 bis 1 zurück.  
  
```  
DECLARE @value real  
SET @value = -1  
WHILE @value < 2  
   BEGIN  
      SELECT SIGN(@value)  
      SET NOCOUNT ON  
      SELECT @value = @value + 1  
      SET NOCOUNT OFF  
   END  
SET NOCOUNT OFF  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
(1 row(s) affected)  
  
------------------------   
-1.0                       
  
(1 row(s) affected)  
  
------------------------   
0.0                        
  
(1 row(s) affected)  
  
------------------------   
1.0                        
  
(1 row(s) affected)  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Das folgende Beispiel gibt die SIGN-Werte von drei Zahlen zurück.  
  
```  
SELECT SIGN(-125), SIGN(0), SIGN(564);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
-----  -----  -----  
-1     0      1
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mathematische Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

