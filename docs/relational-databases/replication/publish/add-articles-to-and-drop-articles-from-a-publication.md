---
title: Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung (SSMS)
description: In diesem Thema wird beschrieben, wie Sie mithilfe von SQL Server Management Studio (SSMS) Artikel zu einer Veröffentlichung hinzufügen und aus einer Veröffentlichung löschen.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 0b0194dec7902311ef48dc889dab6eb6d299df9f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "76286547"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Sie können einer Veröffentlichung bereits bei Ihrer Erstellung im Assistenten für neue Veröffentlichung Artikel hinzufügen. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Zum Hinzufügen und Löschen von Artikeln zu bzw. aus einer bereits erstellten Veröffentlichung steht Ihnen die Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** zur Verfügung. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Informationen zu Überlegungen für das Hinzufügen und Löschen von Artikeln finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>So fügen Sie einer bereits erstellten Veröffentlichung einen Artikel hinzu  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Option **Nur aktivierte Objekte in der Liste anzeigen**. Auf diese Weise werden nur die nicht veröffentlichten Objekte in der Veröffentlichungsdatenbank angezeigt.  
  
2.  Markieren Sie die Kontrollkästchen für alle Artikel, die Sie der Veröffentlichung hinzufügen möchten.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>So löschen Sie einen Artikel  
  
1.  Deaktivieren Sie auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Kontrollkästchen für alle Artikel, die aus der Veröffentlichung gelöscht werden sollen.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
