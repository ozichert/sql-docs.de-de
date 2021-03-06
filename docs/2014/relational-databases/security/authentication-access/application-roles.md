---
title: Anwendungsrollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 56f075ff4a26af4913d792c20a8d7c1d6a58fcb0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63011679"
---
# <a name="application-roles"></a>Anwendungsrollen
  Eine Anwendungsrolle ist ein Datenbankprinzipal, mit dem eine Anwendung mit eigenen Berechtigungen ausgeführt werden kann. Sie können Anwendungsrollen verwenden, um den Zugriff auf bestimmte Daten nur den Benutzern zu ermöglichen, die über eine bestimmte Anwendung eine Verbindung herstellen. Im Gegensatz zu Datenbankrollen enthalten Anwendungsrollen keine Mitglieder und sind standardmäßig inaktiv. Anwendungsrollen können in beiden Authentifizierungsmodi verwendet werden. Anwendungsrollen werden mit **sp_setapprole**aktiviert, wofür ein Kennwort erforderlich ist. Da es sich bei Anwendungsrollen um einen Prinzipal auf Datenbankebene handelt, können sie auf andere Datenbanken nur über die Berechtigungen zugreifen, die in diesen Datenbanken dem Konto **guest**erteilt wurden. Anwendungsrollen anderer Datenbanken können daher auf keine Datenbank zugreifen, in der **guest** deaktiviert wurde.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]können Anwendungsrollen nicht auf Metadaten auf Serverebene zugreifen, da sie nicht mit einem Prinzipal auf Serverebene verbunden sind. Sie können diese Einschränkung deaktivieren und dabei den Anwendungsrollen den Zugriff auf Metadaten auf Serverebene ermöglichen, indem Sie das globale Flag 4616 festlegen. Weitere Informationen finden Sie unter [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) und [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).  
  
## <a name="connecting-with-an-application-role"></a>Herstellen einer Verbindung mit einer Anwendungsrolle  
 Der Prozess, in dem eine Anwendungsrolle den Sicherheitskontext wechselt, besteht aus den folgenden Schritten:  
  
1.  Ein Benutzer führt eine Clientanwendung aus.  
  
2.  Die Clientanwendung stellt eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Benutzer her.  
  
3.  Die Anwendung führt dann die gespeicherte Prozedur **sp_setapprole** mit einem Kennwort aus, das nur der Anwendung bekannt ist.  
  
4.  Wenn der Name und das Kennwort der Anwendung gültig sind, wird die Anwendungsrolle aktiviert.  
  
5.  An diesem Punkt verliert die Verbindung die Berechtigungen des Benutzers und nimmt die Berechtigungen der Anwendungsrolle an.  
  
 Die über die Anwendungsrolle erhaltenen Berechtigungen bleiben für die Dauer der Verbindung wirksam.  
  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]bestand die einzige Möglichkeit für einen Benutzer, seinen ursprünglichen Sicherheitskontext nach dem Starten einer Anwendungsrolle zurückzuerhalten, darin, die Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu trennen und erneut eine Verbindung herzustellen. Seit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]besitzt **sp_setapprole** eine Option, die ein Cookie erstellt. Das Cookie enthält die vor der Aktivierung der Anwendungsrolle gültigen Kontextinformationen. Das Cookie kann von **sp_unsetapprole** zum Wiederherstellen des ursprünglichen Kontexts der Sitzung verwendet werden. Weitere Informationen über diese neue Option sowie ein Beispiel finden Sie unter [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)erteilt wurden.  
  
> [!IMPORTANT]  
>  Die **encrypt** -Option von ODBC wird von **SqlClient**nicht unterstützt. Wenn Sie vertrauliche Informationen über das Netzwerk übertragen, sollten Sie zum Verschlüsseln des Kanals SSL (Secure Sockets Layer) oder IPSec verwenden. Wenn Sie Anmeldeinformationen innerhalb der Clientanwendung persistent speichern müssen, verschlüsseln Sie diese mit den CryptoAPI-Funktionen. In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und höheren Versionen wird der *password* -Parameter als unidirektionaler Hash gespeichert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|Erstellen einer Anwendungsrolle.|[Erstellen einer Anwendungsrolle](create-an-application-role.md) und [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)|  
|Ändern einer Anwendungsrolle.|[ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|Löschen einer Anwendungsrolle.|[DROP APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|Verwenden einer Anwendungsrolle.|[sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von SQL Server](../securing-sql-server.md)  
  
  
