---
title: Erstellen oder Bearbeiten einer Servergruppe
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.editgroup.f1
- sql13.swb.newgroup.f1
helpviewer_keywords:
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- groups [SQL Server], server
ms.assetid: d4a942bd-2dd1-42db-ad0e-e9a9ae5b856d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 61b9111eb218f479a2b46636b648a5c9715d49f7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246549"
---
# <a name="create-or-edit-a-server-group-sql-server-management-studio"></a>Erstellen oder Bearbeiten einer Servergruppe (SQL Server Management Studio)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

In diesem Thema wird beschrieben, wie Sie die Server in Registrierte Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] organisieren, indem Sie Servergruppen erstellen und die Server den Servergruppen zuordnen. Servergruppen können jederzeit in Registrierte Server erstellt werden, aber auch beim Registrieren von Servern.  

## <a name="SSMSProcedure"></a>

### <a name="to-create-a-server-group-in-registered-servers"></a>So erstellen Sie eine Servergruppe in Registrierte Server  

1. Klicken Sie in Registrierte Server auf der Symbolleiste Registrierte Server auf den Servertyp. Wenn die Option Registrierte Server nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Registrierte Server** .  

2. Klicken Sie mit der rechten Maustaste auf einen Server oder eine Servergruppe, zeigen Sie auf **Neu**, und klicken Sie dann auf **Servergruppe**.  

3. Geben Sie im Dialogfeld **Neue Servergruppe** in das Feld **Gruppenname** einen Namen für die Servergruppe ein. Der Servergruppenname muss für die aktuelle Position in der Struktur Registrierte Server eindeutig sein.

4. Geben Sie in das Listenfeld **Gruppenbeschreibung** optional einen Anzeigenamen ein, der die Servergruppe beschreibt, wie z. B. "Finanzserver für Lateinamerika".  

5. Klicken Sie im Feld **Wählen Sie einen Speicherort für die neue Servergruppe aus** auf einen Speicherort für die Gruppe, und klicken Sie dann auf **Speichern**.  

   > [!NOTE]
   > Sie können beim Registrieren eines Servers auch eine neue Servergruppe erstellen, indem Sie auf **Neue Gruppe**klicken und die entsprechenden Informationen im Dialogfeld **Neue Gruppe** eingeben.  

## <a name="see-also"></a>Weitere Informationen

[Registrieren von Servern](../../tools/sql-server-management-studio/register-servers.md)