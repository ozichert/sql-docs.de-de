---
title: C2-Überwachungsmodus (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 52e39eda53e08a4267ac97faa3b691ffcd7acaad
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68012999"
---
# <a name="c2-audit-mode-server-configuration-option"></a>C2-Überwachungsmodus (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Der C2-Überwachungsmodus kann durch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit der Option **c2 audit mode** in **sp_configure**konfiguriert werden. Das Auswählen dieser Option konfiguriert den Server so, dass sowohl fehlgeschlagene als auch erfolgreiche Zugriffsversuche auf Anweisungen und Objekte aufgezeichnet werden. Diese Informationen können Sie bei der Profilierung der Systemaktivität unterstützen und mögliche Verletzungen der Sicherheitsrichtlinien nachverfolgen.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Der C2-Sicherheitsstandard wurde durch Common Criteria Certification ersetzt. Weitere Informationen finden Sie unter [Common Criteria-Kompatibilität aktiviert (Serverkonfigurationsoption)](../../database-engine/configure-windows/common-criteria-compliance-enabled-server-configuration-option.md).  
  
## <a name="audit-log-file"></a>Überwachungsprotokolldatei  
 Die C2-Überwachungsmodusdaten werden in einer Datei im Standarddatenverzeichnis der Instanz gespeichert. Wenn die Überwachungsprotokolldatei ihre maximale Größe von 200 Megabyte (MB) erreicht hat, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine neue Datei, schließt die alte Datei und schreibt alle neuen Überwachungsdatensätze in die neue Datei. Dieser Prozess wird fortgesetzt, bis das Überwachungsdatenverzeichnis voll ist oder die Überwachung deaktiviert wird. Um den Status einer C2-Ablaufverfolgung zu bestimmen, fragen Sie die sys.traces-Katalogsicht ab.  
  
> [!IMPORTANT]  
>  Mit dem C2-Überwachungsmodus wird eine große Menge an Ereignisinformationen in der Protokolldatei gespeichert, die rasch anwachsen kann. Wenn im Datenverzeichnis, in dem die Protokolle gespeichert werden, nicht mehr genügend Speicherplatz vorhanden ist, fährt sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst herunter. Wenn ein automatischer Start der Überwachung festgelegt ist, müssen Sie entweder die Instanz mit dem **-f** -Flag (das die Überwachung umgeht) neu starten oder zusätzlichen Speicherplatz für das Überwachungsprotokoll freigeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der C2-Überwachungsmodus aktiviert.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
