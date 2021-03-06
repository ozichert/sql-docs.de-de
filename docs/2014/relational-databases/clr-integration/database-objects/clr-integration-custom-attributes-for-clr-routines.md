---
title: Benutzerdefinierte Attribute für CLR-Routinen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 817591cec64a4210c4cc573588be1b8ac6dfb8a7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62873805"
---
# <a name="custom-attributes-for-clr-routines"></a>Benutzerdefinierte Attribute für CLR-Routinen
  Die aufgelisteten Attribute können auf Common Language Runtime (CLR)-Routinen, benutzerdefinierte Typen und benutzerdefinierte Aggregate angewendet werden, die in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]registriert sind. Wenn das Attribut nicht angewendet wird, nimmt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Standardwert an. Die aufgelisteten Attribute werden im `Microsoft.SqlServer.Server`-Namespace definiert.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Das 'SqlUserDefinedAggregate'-Attribut  
 Das `SqlUserDefinedAggregate`-Attribut gibt an, dass die Methode als benutzerdefiniertes Aggregat registriert werden soll. Jedem benutzerdefinierten Aggregat muss dieses Attribut angefügt werden.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Das 'SqlFunction'-Attribut  
 Das `SqlFunction`-Attribut gibt an, dass die Methode als eine Funktion mit den entsprechend festgelegten Funktionsattributen registriert werden soll.  
  
 Weitere Informationen finden Sie unter [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Das 'SqlFacet'-Attribut  
 Das `SqlFacet`-Attribut wird verwendet, um Informationen über den Rückgabetyp eines UDT-Ausdrucks (Benutzerdefinierter Typ, User Defined Type) zurückzugeben.  
  
 Weitere Informationen finden Sie unter [sqlfaketattribute](https://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Das 'SqlProcedure'-Attribut  
 Das `SqlProcedure`-Attribut gibt an, dass die Methode als gespeicherte Prozedur registriert werden soll. Dieses Attribut wird nur von Visual Studio verwendet, um die angegebene Methode automatisch als gespeicherte Prozedur zu registrieren. Sie wird nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet.  
  
 Weitere Informationen finden Sie unter [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Das 'SqlTrigger'-Attribut  
 Das `SqlTrigger`-Attribut gibt an, dass die Methode als Trigger registriert werden soll.  
  
 Weitere Informationen finden Sie unter [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) und [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>Das 'SqlUserDefinedTypeAttribute'-Attribut  
 Sie können das SqlUserDefinedTypeAttribute-Attribut in eine Klassendefinition in der Assembly übernehmen. Es bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einen benutzerdefinierten Typ erstellt, der an die Klassendefinition mit diesem benutzerdefinierten Attribut gebunden ist.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Das 'SqlMethod'-Attribut  
 Das `SqlMethod`-Attribut gibt die Verwendung und die Datenzugriffseigenschaften einer Methode oder Eigenschaft in einem benutzerdefinierten Typ (UDT) an.  
  
 Weitere Informationen finden Sie unter [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Aggregate](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Benutzerdefinierte CLR-Funktionen](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Benutzerdefinierte CLR-Typen](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Gespeicherte CLR-Prozeduren](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [CLR-Trigger](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
