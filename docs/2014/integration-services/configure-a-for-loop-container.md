---
title: Konfigurieren eines for-Schleifen Containers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 766a82c975b607687f79a696ce587422b93322bf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486998"
---
# <a name="configure-a-for-loop-container"></a>Konfigurieren eines For-Schleifencontainers
  In diesem Verfahren wird beschrieben, wie Sie einen For-Schleifencontainer mithilfe des Dialogfelds **For-Schleifen-Editor** konfigurieren.  
  
### <a name="to-configure-the-for-loop-container"></a>So konfigurieren Sie den For-Schleifencontainer  
  
1.  Doppelklicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf den For-Schleifencontainer, um den **For-Schleifen-Editor**zu öffnen.  
  
2.  Ändern Sie optional den Namen und die Beschreibung des For-Schleifencontainers.  
  
3.  Geben Sie optional einen Initialisierungsausdruck in das Textfeld **InitExpression** ein.  
  
4.  Geben Sie einen Auswertungsausdruck in das Textfeld **EvalExpression** ein.  
  
    > [!NOTE]  
    >  Der Ausdruck muss zu einem booleschen Wert ausgewertet werden. Wenn der Ausdruck zu `false` ausgewertet wird, wird die Ausführung der Schleife beendet.  
  
5.  Geben Sie optional einen Zuweisungsausdruck in das Textfeld **AssignExpression** ein.  
  
6.  Klicken Sie optional auf **Ausdrücke** , und erstellen Sie auf der Seite **Ausdrücke** Eigenschaftsausdrücke für die Eigenschaften des For-Schleifencontainers. Weitere Informationen finden Sie unter [Hinzufügen oder Ändern eines Eigenschaftsausdrucks](expressions/add-or-change-a-property-expression.md).  
  
7.  Klicken Sie auf **OK** , um den **For-Schleifen-Editor**zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [For-Schleifen Container](control-flow/for-loop-container.md)   
 [Integration Services &#40;SSIS-&#41; Ausdrücke](expressions/integration-services-ssis-expressions.md)   
 [Verwenden von Eigenschaftsausdrücken in Paketen](expressions/use-property-expressions-in-packages.md)  
  
  
