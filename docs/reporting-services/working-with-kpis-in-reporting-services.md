---
title: Arbeiten mit KPIs in Reporting Services | Microsoft-Dokumentation
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.date: 07/02/2017
ms.openlocfilehash: dd8dc50b9885bb33df66d152b432092b6ac9868d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68329360"
---
# <a name="working-with-kpis-in-reporting-services"></a>Arbeiten mit KPIs in Reporting Services

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Ein *Key Performance Indicator (KPI)* ist ein sichtbarer Hinweis, der Auskunft über den Fortschritt im Hinblick auf das Erreichen eines Ziels gibt.  Key Performance Indicators sind wertvoll für Teams, Manager und Unternehmen, um schnell den bei messbaren Zielen erzielten Fortschritt zu evaluieren.
  
Mit KPIs in SQL Server Reporting Services können Sie einfach Antworten für die folgenden Fragen visualisieren:  
  
- Womit bin ich weit vorangekommen, oder womit hänge ich hinterher?  
  
- Wie weit habe ich vorausgearbeitet, oder wie weit hänge ich hinterher?  
  
- Wie viel Fortschritt habe ich mindestens gemacht?  

> [!NOTE]
> KPIs sind nur in den Enterprise-Editionen (Developer) des SSRS-Portals verfügbar.

## <a name="creating-a-dataset"></a>Erstellen eines Dataset

Eine KPI wird nur die erste Zeile der Daten aus einem freigegebenen Dataset verwenden. Stellen Sie sicher, dass sich die Daten, die Sie verwenden möchten, in dieser ersten Zeile befinden. Um ein freigegebenes Dataset zu erstellen, können Sie entweder den Berichts-Generator oder SQL Server Data Tools verwenden.  
  
> **Hinweis**: Das Dataset muss sich nicht im selben Ordner wie die KPI befinden.  
  
## <a name="placement-of-kpis"></a>Platzierung von KPIs  
  
KPIs können in einem beliebigen Ordner auf Ihrem Berichtsserver erstellt werden.  Bevor Sie eine KPI erstellen, sollten Sie überlegen, wo der richtige Speicherort dafür wäre. Sie können sie in einem Ordner ablegen, der für Benutzer sichtbar ist. Gleichzeitig sollte der Ordner auch relevant für andere Berichte sowie KPIs in der Umgebung sein.  
## <a name="adding-a-kpi"></a>Hinzufügen einer KPI
  
Nachdem Sie den Speicherort der KPI bestimmt haben, wechseln Sie zu dem Ordner, und wählen Sie **Neu** > **KPI** im oberen Menü aus.  
  
![rsCreateKPI1](../reporting-services/media/rscreatekpi1.png)  
  
Dies zeigt Ihnen den Bildschirm **Neue KPI** an.  
  
![rsCreateKPI2](../reporting-services/media/rscreatekpi2.png)  
  
Sie können entweder statische Werte zuweisen oder Daten aus einem freigegebenen Dataset verwenden. Wenn Sie eine neue KPI erstellen, wird diese mit zufälligen manuellen Daten aufgefüllt.  
  
| Feld | BESCHREIBUNG |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Wertformat | Wird verwendet, um das Format des angezeigten Werts zu ändern. |
| value | Der für die KPI anzuzeigender Wert. |
| Zielsetzung | Wird als Vergleich mit einem numerischen Wert verwendet und als prozentuale Differenz angezeigt. |
| Status | Zum Bestimmen der KPI-Kachelfarbe verwendete und durch Komma getrennte numerische Werte. Gültige Werte sind 1 (Grün), 0 (gelb) und-1 (Rot). |
| Trendsatz | Für Diagrammvisualisierungen verwendete durch Komma getrennte numerische Werte. Dies kann auch für eine Spalte eines Dataset mit Werten festgelegt werden, die den Trend darstellen. |
| Verwandte Inhalte | Hier können Sie einen Drillthroughlink angeben. Dieser Link kann entweder ein mobiler Bericht sein, der im Portal veröffentlicht wurde, oder eine benutzerdefinierte URL. |
  
> **Warnung**: Bei der Verwendung des Wordwerts für das **Status** -Feld zur Entwurfszeit, sollten Sie den Zahlenwert verwenden, wenn Sie ein Dataset aktualisieren. Wenn Sie ein Dataset mit dem Wortwert anstelle des Zahlenwerts aktualisieren, könnten die KPIs auf Ihrem Server beschädigt werden.  
>
> **Hinweis:** : Die Felder **Wert**, **Ziel** und **Status** können nur einen Wert aus der ersten Zeile des Ergebnisses eines Datasets auswählen. Das Feld **Trendsatz** kann jedoch wählen, welche Spalte den Trend widerspiegelt.  
  
Um Daten aus einem freigegebenen Dataset zu verwenden, können Sie die folgenden Schritte durchführen.
  
1. Ändern Sie das Dropdownfeld des Felds von **Manuell festlegen**oder **Nicht festgelegt**auf **Datasetfeld**.  
  
    ![rsCreateKPI3](../reporting-services/media/rscreatekpi3.png)  
  
2. Klicken Sie im Datenfeld auf die **Auslassungspunkte (…)** . Hierdurch erscheint der Bildschirm **Wählen Sie ein Dataset** .  
  
    ![rsCreateKPI4](../reporting-services/media/rscreatekpi4.png)  
  
3. Wählen Sie das Dataset aus, das die Daten enthält, die Sie anzeigen möchten.  
  
4. Wählen Sie das Feld aus, das Sie verwenden möchten. Klicken Sie auf **OK**.  
  
    ![rsCreateKPI5](../reporting-services/media/rscreatekpi5.png)  
  
5. Ändern Sie das **Wertformat** , damit es mit dem Format Ihres Werts übereinstimmt. In diesem Beispiel ist der Wert einer Währung.  
  
    ![rsCreateKPI6](../reporting-services/media/rscreatekpi6.png)  
  
6. Wählen Sie **Übernehmen**.  
  
    ![rsCreateKPI7](../reporting-services/media/rscreatekpi7.png)

## <a name="configuring-related-content"></a>Konfigurieren verwandter Inhalte

Wenn Sie sich für die Option **Mobiler Bericht** entscheiden, können Sie in einem zweiten Feld das Ziel auswählen.

   ![Mobilgerätebericht](media/rscreatekpi-related-content-mobile-report.png)

Wenn Sie nun im Portal auf den KPI klicken, wird im Dropdown für verwandte Inhalte eine Miniaturansicht des mobilen Berichts angezeigt. Mit einem Klick auf die Miniaturansicht gelangen Sie direkt zum Bericht.

Sie können auch eine benutzerdefinierte URL angeben. Diese kann zu einer beliebigen Sache führen, z. B. zu einer Website, zu eine SharePoint-Website oder zu einem SSRS-Bericht (so könnten Sie hartcodierte Parameter weitergeben).

![Benutzerdefinierte URL](media/rscreatekpi-related-content-custom-url.png)

Wenn Sie nun auf den KPI klicken, wird die URL als verwandter Inhalt angezeigt.

Sie können nur einen mobilen Bericht oder eine benutzerdefinierte URL hinzufügen.
  
## <a name="removing-a-kpi"></a>Entfernen einer KPI  
  
Um eine KPI zu entfernen, können Sie die folgenden Schritte durchführen.
  
1. Klicken Sie bei der KPI, die Sie entfernen möchten, auf die **Auslassungspunkte (…)** . Wählen Sie **Verwalten** aus.  
  
    ![rsRemoveKPI1](../reporting-services/media/rsremovekpi1.png)  
  
2. Klicken Sie auf **Löschen**. Wählen Sie **Löschen** erneut im Bestätigungsdialogfeld aus.  
  
    ![rsRemoveKPI2](../reporting-services/media/rsremovekpi2.png)  
  
## <a name="refreshing-a-kpi"></a>Aktualisieren einer KPI  
  
Um eine KPI zu aktualisieren, müssen Sie eine Zwischenspeicherung für das freigegebene Dataset konfigurieren. Weitere Informationen zu Cacheaktualisierungsplänen finden Sie unter [Arbeiten mit freigegebenen Datasets – Webportal](../reporting-services/work-with-shared-datasets-web-portal.md).  
  
## <a name="next-steps"></a>Nächste Schritte
  
[Web portal (Webportal)](../reporting-services/web-portal-ssrs-native-mode.md)  
[Work with shared datasets (Arbeiten mit freigegebenen Datasets)](../reporting-services/work-with-shared-datasets-web-portal.md)

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
