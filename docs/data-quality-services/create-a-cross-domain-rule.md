---
title: Erstellen einer domänenübergreifenden Regel
ms.date: 11/22/2011
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.testcdrule.f1
- sql13.dqs.dm.cdrules.f1
ms.assetid: 0f3f5ba4-cc47-4d66-866e-371a042d1f21
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 070ef5db87ac28b59f01e3927f876f9c757e6caa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75245473"
---
# <a name="create-a-cross-domain-rule"></a>Erstellen einer domänenübergreifenden Regel

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird beschrieben, wie eine domänenübergreifende Regel für eine Verbunddomäne in einer Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) erstellt wird. Eine domänenübergreifende Regel testet die Beziehung zwischen Werten in einzelnen Domänen, die in einer Verbunddomäne enthalten sind. Eine domänenübergreifende Regel muss über eine Verbunddomäne hinweg wahr sein, damit Domänenwerte als genau betrachtet werden und den Geschäftsanforderungen entsprechen. Eine domänenübergreifende Regel wird verwendet, um Domänenwerte zu validieren, zu korrigieren und zu standardisieren.  
  
 Die If-Klausel und die Then-Klausel einer domänenübergreifenden Regel sind jeweils für eine der einzelnen Domänen in der Verbunddomäne definiert. Jede Klausel muss für eine andere einzelne Domäne definiert werden. Eine domänenübergreifende Regel muss sich auf mehrere einzelne Domänen beziehen; Sie können keine einfache Domänenregel (für nur eine einzelne Domäne) für eine Verbunddomäne definieren. Dies wäre der Fall, wenn Sie eine Domänenregel für eine einzelne Domäne definieren. Die If-Klausel und die Then-Klausel können jeweils eine oder mehrere Bedingungen enthalten.  
  
 Eine domänenübergreifende Regel, die definitive Bedingungen hat, übernimmt die Regellogik für Synonyme des Werts in den Bedingungen sowie die Werte selbst. Die definitiven Bedingungen für die If-Klausel und die Then-Klausel sind "Wert ist gleich", Wert ist ungleich", "Wert ist in" oder "Wert ist nicht in". Angenommen, Sie haben die folgende domänenübergreifende Regel für eine Verbunddomäne: „Falls für ‚Stadt‘ Wert ist gleich ‚Los Angeles‘ vorliegt, dann liegt für ‚Bundesland‘ Wert ist gleich ‚CA‘ vor“. Wenn „Los Angeles“ und „LA“ Synonyme sind, gibt diese Regel das richtige Ergebnis für „Los Angeles CA“ und „LA CA“ und einen Fehler für „Los Angeles WA“ und „LA WA“ zurück.  
  
 Abgesehen davon, dass erfahren, ob eine domänenübergreifenden Regel gültig ist, korrigiert die definitive *Then* -Klausel in einer domänenübergreifenden Regel **Wert ist gleich**auch die Daten während der Datenbereinigungsaktivität. Weitere Informationen finden Sie unter [Data Correction using Definitive Cross-Domain Rules](../data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) in [Cleanse Data in a Composite Domain](../data-quality-services/cleanse-data-in-a-composite-domain.md).  
  
 Domänenübergreifende Regeln werden nach allen einfachen Regeln berücksichtigt, die sich auf nur eine einzelne Domäne auswirken. Nur wenn ein Wert einzelne Domänenregeln besteht (falls vorhanden), wird die domänenübergreifende Regel angewendet. Die Verbunddomäne und die einzelnen Domänen, für die eine Regel ausgeführt wird, müssen definiert werden, bevor die Regel ausgeführt werden kann.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Um eine domänenübergreifende Regel zu erstellen, müssen Sie eine Verbunddomäne erstellt und geöffnet haben.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die dqs_kb_editor- oder die dqs_administrator-Rolle in der DQS_MAIN-Datenbank verfügen, um eine domänenübergreifende Regel zu erstellen.  
  
##  <a name="create-cross-domain-rules"></a><a name="Create"></a>Erstellen von Domänen übergreifenden Regeln  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Öffnen oder erstellen Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm eine Wissensdatenbank. Wählen Sie **Domänenverwaltung** als Aktivität aus, und klicken Sie dann auf **Öffnen** oder **Erstellen**. Weitere Informationen finden Sie unter [Erstellen einer Wissensdatenbank](../data-quality-services/create-a-knowledge-base.md) oder [Öffnen einer Wissensdatenbank](../data-quality-services/open-a-knowledge-base.md).  
  
    > [!NOTE]  
    >  Die Domänenverwaltung wird auf einer Seite des Data Quality Service-Clients ausgeführt, der fünf Registerkarten für separate Domänenverwaltungsvorgänge enthält. Es ist kein assistentengesteuerter Prozess; jeder Verwaltungsvorgang kann getrennt ausgeführt werden.  
  
3.  Wählen Sie aus der **Domänenliste** auf der Seite **Domänenverwaltung** die Verbunddomäne aus, für die Sie eine Domänenregel erstellen möchten, oder erstellen Sie eine neue Verbunddomäne. Wenn Sie eine neue Domäne erstellen müssen, finden Sie unter [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md)weitere Informationen.  
  
4.  Klicken Sie auf die Registerkarte **VD-Regeln** .  
  
5.  Klicken Sie auf **Neue Domänenregel hinzufügen**, und geben Sie einen Namen und eine Beschreibung für die Regel an.  
  
6.  Wählen Sie **Aktiv** aus, um anzugeben, dass die Regel ausgeführt wird (Standard), und deaktivieren Sie Option, um zu verhindern, dass die Regel ausgeführt wird.  
  
7.  Erstellen Sie die If-Klausel wie folgt:  
  
    1.  Wählen Sie in der Domänenliste im If-Klausel Bereich eine der einzelnen Domänen aus, die in der Verbunddomäne enthalten ist, damit sie zum Thema der If-Klausel wird. Sie können jede einzelne Domäne in der Verbunddomäne auswählen.  
  
    2.  Wählen Sie eine Bedingung aus der Dropdownliste für die erste Bedingung der Klausel aus.  
  
    3.  Falls die Bedingung einen Wert erfordert, geben Sie den Wert im der Bedingung zugeordneten Textfeld ein.  
  
    4.  Wenn die If-Klausel eine andere Bedingung erfordert, klicken Sie auf **Fügt der ausgewählten Klausel eine neue Bedingung hinzu**. Wählen Sie den Operator aus, wählen Sie eine Bedingung aus, und geben Sie ggf. einen Wert für die Bedingung ein.  
  
    5.  Um die Reihenfolge der Bedingungen zu ändern, wählen Sie eine Bedingung aus, indem Sie links neben die Bedingung klicken. Klicken Sie dann auf den NACH-OBEN- oder NACH-UNTEN-Pfeil.  
  
    6.  Um die Bedingungen auszublenden, klicken Sie auf das Minuszeichen links vom Domänennamen. Klicken Sie auf das Pluszeichen, um die Bedingungen anzuzeigen.  
  
8.  Erstellen Sie die Then-Klausel, indem Sie in der Domänenliste in Then-Klausel-Bereich eine andere einzelne Domäne auswählen als das Thema der If-Klausel. Erstellen Sie dann die Then-Klausel mithilfe der gleichen Schritte, die Sie zum Erstellen der If-Klausel verwendet haben.  
  
9. Fahren Sie mit der nachfolgenden Testprozedur fort.  
  
##  <a name="test-cross-domain-rules"></a><a name="Test"></a>Testen von Domänen übergreifenden Regeln  
  
1.  Testen Sie die domänenübergreifende Regel, wie folgt:  
  
    1.  Klicken Sie auf das Symbol **Ausgewählte Domänenregel für Testdaten ausführen** in der oberen rechten Ecke des Verbunddomänenbereichs.  
  
    2.  Klicken Sie im Dialogfeld **Testdomänenregel** auf das Symbol **Fügt einen neuen Testbegriff für die Domänenregel hinzu** .  
  
    3.  Geben Sie Testwerte für die einzelne Domäne ein, die der If-Klausel und der einzelnen der Then-Klausel zugeordneten Domäne zugeordnet ist. Die in der If-Klausel eingegebenen Testwerte müssen die Bedingungen für diese Klausel erfüllen, oder ein Fragezeichen wird in der Spalte **Gültigkeit** eingegeben, das darauf hinweist, dass die domänenübergreifende Regel nicht für die Testdaten gilt.  
  
    4.  Klicken Sie auf das Symbol **Fügt einen neuen Testbegriff für die Domänenregel hinzu** , um einen anderen Satz von Testwerten hinzuzufügen.  
  
    5.  Klicken Sie **auf das Symbol Domänen Regel für alle Begriffe testen** . Wenn ein Satz von Testwerten gültig ist, gibt DQS eine Überprüfung in der Spalte **Gültigkeit** für die Zeile ein. Wenn der Satz von Testwerten nicht gültig ist, gibt DQS in der Spalte "Gültigkeit" für die Zeile ein Dreieck mit einem Ausrufezeichen ein.  
  
    6.  Nachdem die Tests abgeschlossen wurden, klicken Sie im Dialogfeld **Verbunddomänenregel testen** auf **Schließen** .  
  
2.  Wenn Sie die domänenübergreifenden Regeln vervollständigt haben, klicken Sie auf **Fertig stellen** , um die Domänenverwaltungsaktivität abzuschließen, wie in [End the Domain Management Activity](https://msdn.microsoft.com/library/ab6505ad-3090-453b-bb01-58435e7fa7c0)beschrieben.  
  
##  <a name="follow-up-after-creating-a-cross-domain-rule"></a><a name="FollowUp"></a>Nachverfolgung: nach dem Erstellen einer Domänen übergreifenden Regel  
 Nachdem Sie eine übergreifende Regel erstellt haben, können Sie andere Domänenverwaltungstasks in der Domäne ausführen, Sie können die Wissensermittlung durchführen, um der Domäne Wissen hinzuzufügen, oder Sie können der Domäne eine Abgleichsrichtlinie hinzufügen. Weitere Informationen finden Sie unter [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../data-quality-services/managing-a-domain.md) oder [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md).  
  
  
