---
title: Bearbeiten einer Breakpointposition
titleSuffix: T-SQL debugger
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 82709b15e729eb972c28b22c0113682464232809
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253971"
---
# <a name="edit-a-breakpoint-location"></a>Bearbeiten einer Breakpointposition

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Breakpointposition gibt die Zeile und das Zeichen an, wo sich der Breakpoint in einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei befindet. Sie können die Position des Breakpoints bearbeiten, um diesen an eine andere Position im Skript oder in ein anderes Skript zu verschieben.

## <a name="editing-a-location"></a>Bearbeiten einer Position

Wenn Sie die Position eines Breakpoints bearbeiten, wird dieser mitsamt aller vorhandenen Eigenschaften, z. B. der Trefferanzahl oder einer Bedingung, an die neue Position verschoben.  

#### <a name="to-edit-a-breakpoint-location"></a>So bearbeiten Sie eine Breakpointposition

1. Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Speicherort** .  
  
     Oder  
  
     Klicken Sie im **Breakpointfenster** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Speicherort**.  
  
2. Bearbeiten Sie im Dialogfeld **Dateihaltepunkt** die Option **Datei** , um eine neue Datei anzugeben, **Zeile** , um eine neue Zeile anzugeben, oder **Zeichen** , um eine neue Position auf derselben Zeile anzugeben. Wenn die angegebene neue Datei bereits in einem Abfrage-Editor-Fenster geöffnet ist, wird der Breakpoint in dieses Editorfenster verschoben. Wenn die Datei nicht geöffnet wird, wird ein neues Editorfenster geöffnet, die Datei darin geladen und der Breakpoint an die neue Position verschoben.  
  
     Beim Debuggen von **hat die Option** Unterschiede zwischen Quellcode und Originalversion zulassen [!INCLUDE[tsql](../../includes/tsql-md.md)]keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen

- [Angeben einer Trefferanzahl](../../relational-databases/scripting/specify-a-hit-count.md)
- [Angeben einer Breakpointaktion](../../relational-databases/scripting/specify-a-breakpoint-action.md)
- [Angeben einer Breakpointbedingung](../../relational-databases/scripting/specify-a-breakpoint-condition.md)
- [Angeben eines Breakpointfilters](../../relational-databases/scripting/specify-a-breakpoint-filter.md)
