---
title: Aktualisieren von Python- und R-Komponenten
description: Führen Sie mit sqlbindr.exe ein Upgrade von Python- und R-Komponenten in SQL Server Machine Learning Services oder SQL Server R Services aus, um diese an Machine Learning Server zu binden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/03/2020
ms.topic: conceptual
author: cawrites
ms.author: chadam
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 4aebb9e64c73762166aa81aebd1bfbab22191bfc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487367"
---
# <a name="upgrade-machine-learning-python-and-r-components-in-sql-server-instances"></a>Upgrade von Machine Learning-Komponenten (Python und R) in SQL Server-Instanzen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die Integration von Python und R in SQL Server umfasst Open-Source- und proprietäre Microsoft-Pakete.
                                                                               
SQL Server-Standardwartung:
                                                                               
- Pakete werden gemäß dem SQL Server-Freigabezyklus aktualisiert.
- Fehlerbehebungen werden auf in der aktuellen Version vorhandene Pakete angewendet.
- Keine Upgrades von Hauptversionen.

Sie können [neuere Versionen von Python und R](#version-map) durch *Binden* an **Microsoft Machine Learning Server** erhalten. Diese Version gilt für sowohl SQL Server Machine Learning Services (datenbankintern) als auch SQL Server R Services (datenbankintern).

Die Möglichkeit, neuere Pakete zu erhalten, wird bevorzugt, wenn Sie in einem datenbezogenen Bereich arbeiten, z. B. als Datenwissenschaftler.

## <a name="what-is-binding"></a>Was ist eine Bindung?

Die Bindung ist ein Installationsprozess, bei dem der Inhalt der Ordner R_SERVICES und PYTHON_SERVICES gegen neuere ausführbare Dateien, Bibliotheken und Tools von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) ausgetauscht wird.

Die hochgeladenen Komponenten, die im Wartungsmodell enthalten sind, wurden geändert.

Die Updates des Diensts entsprechen dem [Supportablauffristen für Microsoft R Server und Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) im [modernen Lebenszyklus](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Abgesehen von Komponentenversionen und Dienstupdates ändert die Bindung nichts an den Grundlagen Ihrer Installation:

- Die Integration von Python und R ist weiterhin Teil einer Datenbank-Engine-Instanz.
- Die Lizenzierung ist unverändert (keine zusätzlichen Kosten im Zusammenhang mit der Bindung).
- SQL Server-Supportrichtlinien für die Datenbank-Engine gelten weiterhin. 

Im weiteren Verlauf dieses Artikels wird der Bindungsmechanismus erklärt und wie er für die verschiedenen Versionen von SQL Server funktioniert.

> [!NOTE]
> Die Bindung gilt nur für (datenbankinterne) Instanzen, die an SQL Server-Instanzen gebunden sind. Für eine (eigenständige) Installation ist die Bindung in diesem Fall nicht nötig.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Überlegungen zur SQL Server 2016-Bindung**

SQL Server 2016 R Services-Kunden bietet die Bindung Folgendes:

- Aktualisierte R-Pakete
- Neue Pakete, die nicht Teil der ursprünglichen Installation ([MicrosoftML](https://  docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)) sind
- Vortrainierte Machine Learning-[Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) für Stimmungsanalyse und Bilderkennung.

Die gesamte Bindung kann außerdem bei jeder neuen Haupt- und Nebenversion von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) aktualisiert werden.
::: moniker-end

## <a name="version-map"></a>Versionsübersicht

Die folgenden Tabellen enthalten Versionsübersichten. Jede Übersicht zeigt Paketversionen in den jeweiligen Releases. Sie können Upgradepfade überprüfen, wenn Sie eine Bindung an Microsoft Machine Learning Server (früher bekannt als R-Server vor der Einführung von Python-Unterstützung ab Machine Learning Server 9.2.1) vornehmen.

Die Bindung garantiert nicht, dass R oder Anaconda auf dem neuesten Stand sind. Bei der Bindung an Microsoft Machine Learning Server wird die R- oder Python-Version über das Setup installiert, wobei es sich möglicherweise nicht um die neueste, online verfügbare Version handelt.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Komponente |Erstrelease | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [Machine Learning Server 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [Machine Learning Server 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) über R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| k. A. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| k. A. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| k. A. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | k. A. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
[**SQL Server 2017 Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Komponente |Erstrelease | Machine Learning Server 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) über R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 über Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>Funktionsweise von Komponentenupgrades

Ausführbare Dateien sowie Python- und R-Bibliotheken werden aktualisiert, wenn Sie eine vorhandene Installation von Python und R an Machine Learning Server binden.

Die Bindung wird vom [Microsoft Machine Learning Server-Installationsprogramm](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) vorgenommen, wenn Sie das Setup auf einer vorhandenen SQL Server-Datenbank-Engine mit Python- und R-Integration ausführen. 

Bei der Einrichtung werden die vorhandenen Funktionen erkannt, und Sie werden aufgefordert, erneut eine Bindung mit Machine Learning Server herzustellen.

Beim Binden wird der Inhalt von `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` und `\PYTHON_SERVICES` mit den neueren ausführbaren Dateien und Bibliotheken von `C:\Program Files\Microsoft\ML Server\R_SERVER` und `\PYTHON_SERVER` überschrieben.

Die Bindung betrifft nur Python- und R-Features. Die Open-Source-Pakete von Python and R bestehen aus Folgendem:

- Anaconda
- Microsoft R Open
- Proprietäre Pakete für RevoScaleR
- Revoscalepy

Die Bindung ändert weder das Supportmodell für die Datenbank-Engine-Instanz noch die Version der SQL Server-Instanz.

Die Bindung kann rückgängig gemacht werden. Sie können die SQL Server-Wartung wiederherstellen, indem Sie [die Bindung der Instanz aufheben](#bkmk_Unbind) und Ihre SQL Server-Datenbank-Engine-Instanz reparieren.

<a name="bkmk_BindWizard"></a>

## <a name="bind-to-machine-learning-server-using-setup"></a>Binden an Machine Learning Server über Setup

Befolgen Sie die folgenden Anweisungen, um SQL Server über das Setup an Microsoft Machine Learning Server zu binden. 

1. Führen Sie in SSMS `SELECT @@version` aus, um sicherzustellen, dass der Server die Mindestanforderungen für die Erstellung erfüllt.

   Bei SQL Server 2016 R Services ist die Mindestanforderung [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) und [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Überprüfen Sie die Version der R-Basisinstallation und RevoScaleR-Pakete, um sicherzustellen, dass die vorhandenen Versionen niedriger sind als die, durch die Sie sie ersetzen möchten. 

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. Schließen Sie SSMS und alle anderen Tools mit einer offenen Verbindung zu SQL Server. Beim Binden werden Programmdateien überschrieben. Wenn in SQL Server offene Sitzungen vorhanden sind, schlägt die Bindung mit dem Bindungsfehlercode 6 fehl.

1. Laden Sie Microsoft Machine Learning Server auf den Computer herunter, auf dem sich die Instanz befindet, die Sie aktualisieren möchten. Es wird die [aktuelle Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) empfohlen.

1. Entpacken Sie den Ordner, und führen Sie die ServerSetup.exe-Datei aus, die sich unter MLSWIN93 befindet.

1. Bestätigen Sie unter **Configure the installation** (Konfigurieren der Installation) die zu aktualisierenden Komponenten, und überprüfen Sie die Liste der kompatiblen Instanzen.

1. Wählen Sie auf der Seite **License agreement** (Lizenzvereinbarung) **I accept these terms** (Ich akzeptiere diese Bedingungen) aus, um die Lizenzbedingungen für Machine Learning Server zu akzeptieren. 

1. Geben Sie auf den folgenden Seiten Ihre Zustimmung zu weiteren Lizenzbedingungen für alle von Ihnen ausgewählten Open-Source-Komponenten, wie Microsoft R Open oder die Python-Anaconda-Distribution.

1. Notieren Sie sich auf der Seite **Almost there** (Fast geschafft) den Installationsordner. Der Standardordner ist \Programme\Microsoft\ML Server.

    Wenn Sie den Installationsordner ändern möchten, klicken Sie auf **Advanced** (Erweitert), um zur ersten Seite des Assistenten zurückzukehren. Sie müssen jedoch die bisherige Auswahl wiederholen.

Wenn das Upgrade nicht erfolgreich ist, finden Sie weitere Informationen in den [SqlBindR-Fehlercodes](#sqlbindr-error-codes).

## <a name="offline-binding-no-internet-access"></a>Offlinebindung (kein Internetzugang)

Bei Systemen ohne Internetverbindung können Sie das Installationsprogramm und die CAB-Dateien auf einen mit dem Internet verbundenen Computer herunterladen und die Dateien dann auf den isolierten Server übertragen.

Das Installationsprogramm (ServerSetup.exe) enthält die Microsoft-Pakete (RevoScaleR, MicrosoftML, olapR, sqlRUtils). Die CAB-Dateien stellen weitere wichtige Komponenten bereit. So enthält beispielsweise die CAB-Datei „SRO“ R Open, die Microsoft-Version der Open-Source-Distribution von R.

In den folgenden Anweisungen wird beschrieben, wie Sie die Dateien für eine Offlineinstallation bereitstellen.

1. Laden Sie das Installationsprogramm MLSWIN93 herunter. Es wird als einzelne ZIP-Datei heruntergeladen. Es wird empfohlen, die [aktuelle Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) zu verwenden, aber Sie können auch [frühere Versionen](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components) installieren.

1. Laden Sie die CAB-Dateien herunter. Unter den folgenden Links finden Sie das Release 9.3. Wenn Sie frühere Versionen benötigen, finden Sie weitere Links unter [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Denken Sie daran, dass Python/Anaconda nur einer SQL Server Machine Learning Services-Instanz hinzugefügt werden kann. Sowohl für Python als auch für R gibt es vorab trainierte Modelle. Die CAB-Dateien stellen Modelle in den Sprachen bereit, die Sie verwenden.

    | Funktion | Download |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Vortrainierte Modelle | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Übertragen Sie die ZIP- und CAB-Dateien auf den Zielserver.

1. Geben Sie auf dem Server in die Befehlszeile `%temp%` ein, um den physischen Speicherort des temporären Verzeichnisses aufzurufen. Der physische Pfad ist in der Regel `C:\Users\<your-user-name>\AppData\Local\Temp`, kann aber auch von Computer zu Computer variieren.

1. Platzieren Sie die CAB-Dateien im Ordner %Temp%.

1. Entpacken Sie das Installationsprogramm.

1. Führen Sie die ServerSetup.exe-Datei aus, und befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen.

## <a name="command-line-operations"></a><a name="bkmk_BindCmd"></a>Befehlszeilenvorgänge


> [!TIP]
> Sie können SqlBindR nicht finden? Dann haben Sie wahrscheinlich das Setup nicht ausgeführt.
> SqlBindR ist nur nach dem Ausführen des Machine Learning Server-Setups verfügbar.

1. Öffnen Sie als Administrator eine Eingabeaufforderung und navigieren Sie zum Ordner, der „sqlbindr.exe“ enthält. Der Standardspeicherort lautet C:\Programme\Microsoft\MLServer\Setup

2. Geben Sie den folgenden Befehl ein, um eine Liste der verfügbaren Instanzen anzuzeigen: `SqlBindR.exe /list`
  
   Merken Sie sich den vollständigen aufgelisteten Namen der Instanz. Beispielsweise kann der Instanzname für eine Standardinstanz MSSQL14.MSSQLSERVER oder etwas wie SERVERNAME.MYNAMEDINSTANCE sein.

3. Führen Sie den Befehl **SqlBindR.exe** mit dem Argument */bind* aus. Geben Sie den Namen der zu aktualisierenden Instanz an, indem Sie den im vorherigen Schritt zurückgegebenen Instanznamen verwenden.

   Geben Sie beispielsweise Folgendes ein, um die Standardinstanz zu aktualisieren: `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Wenn das Upgrade abgeschlossen ist, starten Sie den Launchpad-Dienst neu, der mit einer beliebigen aktualisierten Instanz verknüpft ist.

## <a name="revert-or-unbind-an-instance"></a><a name="bkmk_Unbind"></a>Wiederherstellen oder Aufheben der Bindung einer Instanz

Sie können eine gebundene Instanz in einer Erstinstallation von Python- und R-Komponenten wiederherstellen, die beim SQL Server-Setup eingerichtet wurden. Zum Wiederherstellen der SQL Server-Wartung sind drei Schritte erforderlich:

+ [Schritt 1: Aufheben der Bindung zu Microsoft Machine Learning Server](#step-1-unbind)
+ [Schritt 2: Wiederherstellen des ursprünglichen Status der Instanz](#step-2-restore)
+ [Schritt 3: Erneutes Installieren aller zur Installation hinzugefügten Pakete](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Schritt 1: Aufheben der Bindung

Es gibt zwei Möglichkeiten, die Bindung aufzuheben: das Setup erneut ausführen oder das Befehlszeilenprogramm SqlBindR verwenden.

#### <a name="unbind-using-setup"></a><a name="bkmk_wizunbind"></a> Aufheben der Bindung über das Setup

1. Navigieren Sie zum Installationsprogramm für Machine Learning Server. Wenn Sie das Installationsprogramm bereits entfernt haben, müssen Sie es ggf. wieder herunterladen oder von einem anderen Computer kopieren.
2. Stellen Sie sicher, dass Sie das Installationsprogramm auf dem Computer ausführen, auf dem sich die Instanz befindet, deren Bindung Sie aufheben möchten.
2. Das Installationsprogramm identifiziert die lokalen Instanzen, die für das Aufheben der Bindung in Frage kommen.
3. Deaktivieren Sie das Kontrollkästchen neben der Instanz, für die Sie die ursprüngliche Konfiguration wiederherstellen möchten.
4. Akzeptieren Sie alle Lizenzvereinbarungen.
5. Klicken Sie auf **Fertig stellen**. Der Prozess dauert eine Weile.

#### <a name="unbind-using-the-command-line"></a><a name="bkmk_cmdunbind"></a> Aufheben der Bindung über die Befehlszeile

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Ordner, der **sqlbindr.exe** enthält, wie im vorherigen Abschnitt beschrieben.

2. Führen Sie den Befehl **SqlBindR.exe** mit dem */unbind*-Argument aus, und geben Sie die Instanz an.

   Beispielsweise wird die Standardinstanz über folgenden Befehl wiederhergestellt:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Schritt 2: Reparieren der SQL Server-Instanz

Führen Sie das SQL Server-Setup aus, um die Datenbank-Engine-Instanz mit den Python- und R-Features zu reparieren. Bereits vorhandene Updates bleiben erhalten. Der nächste Schritt gilt, wenn ein Update bei den Wartungsupdates von Python- und R-Paketen versäumt wurde.

Alternativlösung: Sie können die Datenbank-Engine-Instanz vollständig deinstallieren, neu installieren und dann alle Wartungsupdates anwenden.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Schritt 3: Hinzufügen von Drittanbieterpaketen

Möglicherweise haben Sie der Paketbibliothek andere Open-Source- oder Drittanbieterpakete hinzugefügt. Da durch das Umkehren der Bindung der Speicherort der Standardpaketbibliothek geändert wird, müssen Sie die Pakete in der Bibliothek neu installieren, die jetzt von Python und R verwendet wird. Weitere Informationen finden Sie unter [R-Paketinformationen](../package-management/r-package-information.md) und [Installation](../package-management/install-additional-r-packages-on-sql-server.md) sowie unter [Python-Paketinformationen](../package-management/python-package-information.md) und [Installation](../package-management/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe-Befehlssyntax

### <a name="usage"></a>Verwendung

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parameter

|Name|BESCHREIBUNG|
|------|------|
|*list*| Zeigt eine Liste aller SQL-Datenbankinstanz-IDs auf dem aktuellen Computer an|
|*bind*| Aktualisiert die angegebene SQL-Datenbankinstanz auf die neueste Version von R Server und stellt sicher, dass die Instanz automatisch künftige Upgrades von R Server erhält|
|*unbind*|Die neueste Version von R Server wird auf der angegebenen SQL-Datenbankinstanz deinstalliert, und es wird verhindert, dass künftige R Server-Upgrades auf die Instanz angewendet werden|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Bindungsfehler

Das Machine Learning Server-Installationsprogramm und SqlBindR geben beide die folgenden Fehlercodes und -meldungen zurück.

|Fehlercode  | `Message`           | Details               |
|------------|-------------------|-----------------------|
|Bindungsfehler 0 | OK (bei Erfolg) | Bindung ohne Fehler übergeben. |
|Bindungsfehler 1 | Ungültige Argumente | Syntaxfehler. |
|Bindungsfehler 2 | Ungültige Aktion | Syntaxfehler. |
|Bindungsfehler 3 | Ungültige Instanz | Es ist eine Instanz vorhanden, aber für die Bindung nicht zulässig. |
|Bindungsfehler 4 | Keine Bindung möglich | |
|Bindungsfehler 5 | Bereits gebunden | Sie haben den *bind* -Befehl ausgeführt, die angegebene Instanz ist aber bereits gebunden. |
|Bindungsfehler 6 | Fehler beim Binden | Beim Aufheben der Bindung der Instanz ist ein Fehler aufgetreten. Dieser Fehler kann auftreten, wenn Sie das Machine Learning Server-Installationsprogramm ohne Auswahl von Features ausführen. Für die Bindung muss sowohl eine MSSQL-Instanz als auch Python und R ausgewählt werden, vorausgesetzt, es handelt sich um eine SQL Server 2017-Instanz. Dieser Fehler tritt auch auf, wenn SqlBindR nicht in den Ordner „Programme“ schreiben konnte. Bei offenen Sitzungen oder Handles für SQL Server tritt dieser Fehler auf. Wenn Sie diese Fehlermeldung erhalten, starten Sie den Computer neu. Wiederholen Sie dann die Bindungsschritte, bevor Sie neue Sitzungen starten.|
|Bindungsfehler 7 | Nicht gebunden | Die Datenbank-Engine-Instanz verfügt über R Services oder SQL Server Machine Learning Services. Die Instanz ist nicht an Microsoft Machine Learning Server gebunden. |
|Bindungsfehler 8 | Fehler beim Aufheben der Bindung | Beim Aufheben der Bindung der Instanz ist ein Fehler aufgetreten. |
|Bindungsfehler 9 | Keine Instanzen gefunden | Auf diesem Computer wurden keine Datenbank-Engine-Instanzen gefunden. |

## <a name="known-issues"></a>Bekannte Probleme

In diesem Abschnitt werden bekannte Probleme aufgelistet, die für die Verwendung des SqlBindR.exe-Hilfsprogramms oder für Upgrades von Machine Learning Server, die ggf. SQL Server-Instanzen betreffen, spezifisch sind.

### <a name="restoring-packages-that-were-previously-installed"></a>Wiederherstellen von zuvor installierten Paketen

SqlBindR.exe kann die Originalpakete oder R-Komponenten bei einem Upgrade auf Microsoft R Server 9.0.1 nicht wiederherstellen. Wenden Sie die SQL Server-Reparatur auf die Instanz und alle Dienstreleases an. Starten Sie die Instanz neu.

In der späteren Version von SqlBindR werden die ursprünglichen R-Funktionen automatisch wiederhergestellt, sodass keine Neuinstallation von R-Komponenten oder ein erneutes Patchen des Servers erforderlich ist. Sie müssen jedoch alle R-Paketupdates installieren, die möglicherweise nach der Erstinstallation hinzugefügt wurden.

Verwenden Sie R-Befehle, um installierte Pakete unter Verwendung von Datensätzen in der Datenbank mit dem Dateisystem zu synchronisieren. Weitere Informationen finden Sie unter [R-Paketverwaltung für SQL Server](https://docs.microsoft.com/sql/machine-learning/package-management/install-additional-r-packages-on-sql-server).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Probleme bei mehreren Upgrades von SQL Server

Szenario: Instanz von SQL Server 2016 R Services wurde zuvor auf 9.0.1 aktualisiert. Das neue Installationsprogramm für Microsoft R Server 9.1.0 wurde ausgeführt. Das Installationsprogramm zeigt eine Liste aller gültigen Instanzen an.
Standardmäßig wählt das Installationsprogramm zuvor gebundene Instanzen aus. Wenn Sie den Vorgang fortsetzen, wird die Bindung der zuvor gebundenen Instanzen aufgehoben. Infolgedessen wird die frühere Installation der Version 9.0.1 entfernt, einschließlich aller zugehörigen Pakete, aber die neue Version von Microsoft R Server (9.1.0) wird nicht installiert.

Um dieses Problem zu umgehen, können Sie die vorhandene R Server-Installation wie folgt ändern:
1. Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.
2. Wählen Sie Microsoft R Server aus, und klicken Sie auf **Ändern/Bearbeiten**.
3. Wenn das Installationsprogramm gestartet wird, wählen Sie die Instanzen aus, die Sie an 9.1.0 binden möchten.

Bei Microsoft Machine Learning Server 9.2.1 und 9.3 besteht dieses Problem nicht.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Mehrere temporäre Ordner nach dem Binden bzw. Aufheben der Bindung

Entfernen Sie temporäre Ordner nach Abschluss der Installation.

> [!NOTE]
> Warten Sie unbedingt, bis die Installation abgeschlossen ist. Es kann lange dauern, bis R-Bibliotheken, die einer Version zugeordnet sind, entfernt und dann die neuen R-Bibliotheken hinzugefügt werden. Sobald der Vorgang abgeschlossen ist, werden temporäre Ordner entfernt.

## <a name="see-also"></a>Weitere Informationen

+ [Install Machine Learning Server for Windows (Internet connected) (Installieren von Machine Learning Server für Windows (mit Internetzugang))](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Install Machine Learning Server for Windows (offline) (Installieren von Machine Learning Server für Windows (ohne Internetzugang))](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Known issues in Machine Learning Server (Bekannte Probleme in Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Feature announcements from previous release of R Server (Funktionsankündigungen aus vorherigem Release von R Server)](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Deprecated, discontinued, or changed features in Machine Learning Server (Veraltete, nicht mehr unterstützte oder geänderte Features in Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
