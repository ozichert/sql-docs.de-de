---
title: Task „Verlaufscleanup“ (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
ms.openlocfilehash: 37841e848aab5ff991741e5d460500834c9185e6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68115792"
---
# <a name="history-cleanup-task-maintenance-plan"></a>Task 'Verlaufscleanup' (Wartungsplan)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe des Dialogfelds **Task 'Verlaufscleanup'** können Sie alte Verlaufsdaten aus Tabellen in der msdb-Datenbank entfernen. Dieser Task unterstützt das Löschen des Sicherungs- und Wiederherstellungsverlaufs, des Auftragsverlaufs des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents und des Wartungsplanverlaufs.  
  
 Diese Anweisung verwendet die **sp_purge_jobhistory** - und **sp_delete_backuphistory** -Anweisungen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Connection**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird an einer späteren Stelle in diesem Thema beschrieben.  
  
 **Sicherungs- und Wiederherstellungsverlauf**  
 Das Beibehalten von Datensätzen, in denen festgehalten ist, wann Sicherungen erstellt wurden, kann für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Erstellen eines Wiederherstellungsplans hilfreich sein, wenn Sie eine Datenbank wiederherstellen möchten. Die Beibehaltungsdauer muss mindestens dem Intervall entsprechen, in dem vollständige Datenbanksicherungen erstellt werden.  
  
 **Auftragsverlauf des SQL Server-Agents**  
 Dieser Verlauf kann Ihnen bei der Problembehandlung fehlgeschlagener Aufträge bzw. der Ermittlung der Ursache von Datenbankaktionen helfen.  
  
 **Wartungsplanverlauf**  
 Dieser Verlauf kann Ihnen bei der Problembehandlung fehlgeschlagener Wartungsplanaufträge bzw. der Ermittlung der Ursache von Datenbankaktionen helfen.  
  
 **Verlaufsdaten entfernen, die älter sind als**  
 Geben Sie das Alter an, in dem Elemente gelöscht werden sollen.  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## <a name="new-connection-dialog-box"></a>Neue Verbindung (Dialogfeld)  
 **Verbindungsname**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen zum Anmelden am Server ein**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows NT verwenden**  
 Stellt mithilfe der Microsoft Windows-Authentifizierung eine Verbindung zu einer Instanz von SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] her.  
  
 **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**  
 Stellt eine Verbindung zu einer Instanz von SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] mit der SQL Server-Authentifizierung her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)  
  
  
