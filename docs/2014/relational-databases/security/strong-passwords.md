---
title: Sichere Kennwörter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5dca0aafb208835a270be3192f8d3c6020229154
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227166"
---
# <a name="strong-passwords"></a>Sichere Kennwörter
  Kennwörter sind möglicherweise das schwächste Glied bei der Bereitstellung von Serversicherheit. Bei der Auswahl eines Kennworts ist immer größte Vorsicht geboten. Ein sicheres Kennwort weist die folgenden Merkmale auf:  
  
-   Es ist wenigstens 8 Zeichen lang.  
  
-   Es besteht aus einer Kombination aus Buchstaben, Ziffern und Sonderzeichen.  
  
-   Es wird in keinem Wörterbuch aufgeführt.  
  
-   Es handelt sich nicht um einen Befehlsnamen.  
  
-   Es handelt sich nicht um den Namen einer Person.  
  
-   Es handelt sich nicht um den Namen eines Benutzers.  
  
-   Es handelt sich nicht um einen Computernamen.  
  
-   Es wird regelmäßig geändert.  
  
-   Es unterscheidet sich deutlich von früheren Kennwörtern.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kennwörter können bis zu 128 Zeichen (einschließlich Buchstaben, Sonderzeichen und Ziffern) enthalten. Bestimmte Symbole müssen jedoch von doppelten Anführungszeichen (") oder eckigen Klammern ([ ]) eingeschlossen werden, da Benutzernamen, Benutzer, Rollen und Kennwörter häufig in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden. Verwenden Sie diese Trennzeichen in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, wenn die Anmeldenamen, Benutzer, Rollen und Kennwörter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] folgende Merkmale aufweisen:  
  
-   Das Element enthält oder beginnt mit einem Leerzeichen.  
  
-   Das Element beginnt mit dem Zeichen $ oder @.  
  
 Bei Verwendung in einer OLE DB- oder ODBC-Verbindungszeichenfolge dürfen die folgenden Zeichen nicht in einem Anmeldenamen oder Kennwort enthalten sein: [] {}() , ; ? * ! @installiert haben. Mithilfe dieser Zeichen wird entweder eine Verbindung initialisiert oder Verbindungswerte werden getrennt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Kennwortrichtlinie](password-policy.md)  
  
  