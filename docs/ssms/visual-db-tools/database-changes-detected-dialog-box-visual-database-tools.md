---
title: Es wurden Änderungen in der Datenbank festgestellt (Dialogfeld)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: b3944c7fa09ba71ea79eef976bab8ad4e88a56ef
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254700"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a>Es wurden Änderungen in der Datenbank festgestellt (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Dieses Dialogfeld wird angezeigt, wenn Sie ein Datenbankdiagramm oder ausgewählte Tabellen speichern möchten, jedoch einige der Datenbankobjekte, auf die sich der Speichervorgang auswirkt, in Bezug auf die Datenbank veraltet sind. Das Übernehmen der in diesem Dialogfeld angezeigten Änderungen führt dazu, dass die Datenbank entsprechend dem Diagramm aktualisiert wird und Änderungen anderer Benutzer überschrieben werden.  
  
> [!NOTE]  
> Die in einer Tabelle oder einem Datenbankdiagramm vorgenommenen Änderungen können zwar nicht rückgängig gemacht werden, doch werden sie erst dann in der Datenbank gespeichert, wenn Sie die Tabelle bzw. das Diagramm speichern. Sie können nicht gespeicherte Änderungen verwerfen, indem Sie **Nein** auswählen und alle geöffneten Diagramme schließen, ohne sie zu speichern.  
  
## <a name="options"></a>Tastatur  
**Warnung bei Unterschiederkennung**  
Geben Sie an, ob dieses Dialogfeld beim nächsten Versuch angezeigt wird, ein Datenbankdiagramm oder ausgewählte Tabellen zu speichern. Wenn diese Option aktiviert ist, wird das Dialogfeld weiterhin immer dann angezeigt, wenn Sie ein Diagramm oder eine Tabelle speichern, das bzw. die in Bezug auf die Datenbank veraltet ist. Ist die Option deaktiviert, wird das Dialogfeld nicht angezeigt. Dieses Kontrollkästchen ist standardmäßig aktiviert. Wenn Sie diese Option deaktivieren, können Sie sie im Dialogfeld **Optionen** erneut aktivieren.  
  
**Ja**  
Aktualisieren Sie die Datenbank mit allen in der Liste aufgeführten Änderungen.  
  
**Nein**  
Brechen Sie den Speichervorgang ab.  
  
> [!NOTE]  
> Um das Diagramm anhand der Datenbank zu aktualisieren, schließen Sie es, ohne Änderungen zu speichern. Klicken Sie im Server-Explorer mit der rechten Maustaste auf das Diagramm, und klicken Sie dann auf Aktualisieren. Öffnen Sie anschließend das Diagramm erneut.  
  
**Textdatei speichern**  
Zeigen Sie das Dialogfeld **Speichern unter** an, in dem Sie einen Speicherort für eine Textdatei mit einer Liste der Datenbankänderungen angeben können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Abgleichen eines Datenbankdiagramms mit einer geänderten Datenbank &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/reconcile-a-database-diagram-with-a-modified-database-visual-database-tools.md)  
[Mehrbenutzerumgebungen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
