---
title: Mithilfe von Try.. Catch in nativ kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f730e70c-4f92-411d-9984-289e241e43ee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa7115be43361e25f5ad2b082a92929298ce8bef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62842478"
---
# <a name="using-trycatch-in-natively-compiled-stored-procedures"></a>Verwenden von TRY...CATCH in systemintern kompilierten gespeicherten Prozeduren
  Sie können Try/Catch-Blöcke in einer systemintern kompilierten gespeicherten Prozedur verwenden. Die folgenden Konstrukte werden unterstützt:  
  
-   ERROR_LINE  
  
-   ERROR_MESSAGE  
  
-   ERROR_NUMBER  
  
-   ERROR_PROCEDURE  
  
-   ERROR_SEVERITY  
  
-   ERROR_STATE  
  
```sql  
CREATE PROCEDURE test_try_catch  
with native_compilation, schemabinding, execute as owner   
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
  BEGIN TRY  
    -- generate error  
    declare @i int = 1,  
    @j int = 0  
    select @i/@j  
  END TRY  
  BEGIN CATCH  
    -- Execute error retrieval routine.  
    SELECT  
    ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage  
  END CATCH  
end  
go  
  
exec test_try_catch  
go  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [System intern kompilierte gespeicherte Prozeduren](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
