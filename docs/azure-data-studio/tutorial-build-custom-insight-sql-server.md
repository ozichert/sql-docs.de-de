---
title: 'Tutorial: Erstellen eines benutzerdefinierten Erkenntnis-Widgets'
titleSuffix: Azure Data Studio
description: In diesem Tutorial wird veranschaulicht, wie Sie benutzerdefinierte Erkenntnis-Widgets erstellen und diese in Azure Data Studio zu Datenbank- und Serverdashboards hinzufügen.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 34ee9c23569897247f05d6b9b5f9f2610f5d68fc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67959099"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Tutorial: Erstellen eines benutzerdefinierten Erkenntnis-Widgets

In diesem Tutorial wird veranschaulicht, wie Sie Ihre eigenen Erkenntnisabfragen erstellen, um benutzerdefinierte Erkenntnis-Widgets zu erstellen.

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Ausführen ihrer eigenen Abfrage und Anzeigen der Abfrage in einem Diagramm
> * Erstellen eines benutzerdefinierten Erkenntnis-Widgets aus dem Diagramm
> * Hinzufügen des Diagramms zu einem Server- oder Datenbankdashboard
> * Hinzufügen von Details zu Ihrem benutzerdefinierten Erkenntnis-Widget

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die SQL Server- oder Azure SQL-Datenbank *TutorialDB* erforderlich. Um die *TutorialDB*-Datenbank zu erstellen, führen Sie eine der folgenden Schnellstartanleitungen vollständig aus:

- [Herstellen einer Verbindung mit und Abfragen von SQL Server mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank mithilfe von [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Ausführen ihrer eigenen Abfrage und Anzeigen des Ergebnisses in einer Diagrammansicht
In diesem Schritt führen Sie ein SQL-Skript aus, um die aktuellen aktiven Sitzungen abzufragen.

1. Um einen neuen Editor zu öffnen, drücken Sie **STRG+N**. 

2. Ändern Sie den Verbindungskontext in **TutorialDB**.

3. Fügen Sie die folgende Abfrage im Abfrage-Editor ein:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Speichern Sie die Abfrage im Editor in einer \*.sql-Datei. Speichern Sie das Skript für dieses Tutorial als *activeSession.sql*.

5. Um die Abfrage auszuführen, drücken Sie **F5**.

6. Nachdem die Abfrageergebnisse angezeigt werden, klicken Sie auf **Als Diagramm anzeigen**, und klicken Sie dann auf die Registerkarte **Diagramm-Viewer**.

7. Ändern Sie **Diagrammtyp** in **count**. Diese Einstellung bewirkt, dass ein Zählungsdiagramm gerendert wird.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Hinzufügen der benutzerdefinierten Erkenntnis zum Datenbankdashboard

1. Um die Konfiguration des Erkenntnis-Widgets zu öffnen, klicken Sie auf **Erkenntnis erstellen** auf dem *Diagramm-Viewer*:

   ![Konfiguration](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Kopieren Sie die Erkenntniskonfiguration (die JSON-Daten). 

3. Drücken Sie **STRG+Komma**, um *Benutzereinstellungen* zu öffnen.

4. Geben Sie *dashboard* in *Sucheinstellungen* ein.

5. Klicken Sie für *dashboard.database.widgets* auf **Bearbeiten**.

   ![Dashboardeinstellungen](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Fügen Sie die Erkenntniskonfiguration aus der JSON-Datei in *dashboard.database.widgets* ein. Die Einstellungen des Datenbankdashboards sehen wie folgt aus:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql"
                }
            }
        }
    ]
   ```

7. Speichern Sie die *Benutzereinstellungen*-Datei, und öffnen Sie das Datenbankdashboard *TutorialDB*, um das aktive Sitzungen-Widget anzuzeigen:

   ![Einblick in aktive Sitzung](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Hinzufügen von Details zu einer benutzerdefinierten Erkenntnis

1. Um einen neuen Editor zu öffnen, drücken Sie **STRG+N**.

2. Ändern Sie den Verbindungskontext in **TutorialDB**.

3. Fügen Sie die folgende Abfrage im Abfrage-Editor ein:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Speichern Sie die Abfrage im Editor in einer \*.sql-Datei. Speichern Sie das Skript für dieses Tutorial als *activeSessionDetail.sql*.

5. Drücken Sie **STRG+Komma**, um *Benutzereinstellungen* zu öffnen.

6. Bearbeiten Sie den vorhandenen *dashboard.database.widgets*-Knoten in Ihrer Einstellungsdatei:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. Speichern Sie die *Benutzereinstellungen*-Datei, und öffnen Sie das Datenbankdashboard *TutorialDB*. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...) neben *My-Widget*, um die Details anzuzeigen:

    ![Einblick in aktive Sitzung](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Nächste Schritte
In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> * Ausführen ihrer eigenen Abfrage und Anzeigen der Abfrage in einem Diagramm
> * Erstellen eines benutzerdefinierten Erkenntnis-Widgets aus dem Diagramm
> * Hinzufügen des Diagramms zu einem Server- oder Datenbankdashboard
> * Hinzufügen von Details zu Ihrem benutzerdefinierten Erkenntnis-Widget

Um zu erfahren, wie Datenbanken gesichert und wiederhergestellt werden, führen Sie die Schritte im nächsten Tutorial aus:

> [!div class="nextstepaction"]
> [Sichern und Wiederherstellen von Datenbanken](tutorial-backup-restore-sql-server.md).
