---
title: Befehlszeilenoptionen in der SSMA-Konsole (mysqldesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Command line options, help option
- Command line options, log file option
- Command line options, project environment folder option
- Command line options, script file option
- Command line options, secure password option
- Command line options, SecurePassword help option
- Command line options, server connection file option
- Command line options, variable value file option
- Command line options, XML output option
ms.assetid: a2310b10-68ad-4285-a08b-c8694cf84416
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 017136669bd6478bb4e08ed0ff5c2adc01786d20
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68103250"
---
# <a name="command-line-options-in-ssma-console-mysqltosql"></a>Befehlszeilenoptionen in der SSMA-Konsole (MySqlToSql)
Microsoft stellt Ihnen eine robuste Befehlszeilenoption zur Verfügung, mit der Sie SSMA-Aktivitäten ausführen und steuern können. Die nachfolgenden Abschnitte beschreiben die gleichen.  
  
## <a name="command-line-options-in-ssma-console"></a>Befehlszeilenoptionen in der SSMA-Konsole  
Hier werden die Konsolen Befehlsoptionen beschrieben.  
  
Für den Zweck dieses Abschnitts wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
Bei den Optionen wird die Groß-/Kleinschreibung nicht beachtet**-**, und es kann**/** entweder mit dem Zeichen ' ' oder ' ' beginnen.  
  
Wenn Optionen angegeben werden, ist es obligatorisch, die entsprechenden Optionsparameter anzugeben.  
  
Optionsparameter müssen von dem Options Zeichen durch Leerzeichen getrennt werden.  
  
**Syntax Beispiele:**  
  
`C:\> SSMAforMySQLConsole.EXE -s scriptfile`  
  
`C:\> SSMAforMySQLConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
Ordner-oder Dateinamen, die Leerzeichen enthalten, müssen in doppelten Anführungszeichen angegeben werden.  
  
Die Ausgabe der Befehlszeilen Einträge und-Fehlermeldungen wird in stdout oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option--sscript"></a>Skriptdatei Option:-s/Skript  
Ein obligatorischer Switch: der Pfad/Name der Skriptdatei gibt das Skript der Befehlssequenzen an, die von SSMA ausgeführt werden.  
  
**Syntax Beispiele:**  
  
`C:\>SSMAforMySQLConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Variable value file-Option:-v/Variable  
Diese Datei umfasst Variablen, die in der Skriptdatei verwendet werden. Dies ist ein optionaler Switch. Wenn Variablen nicht in der Variablen Datei deklariert und in der Skriptdatei verwendet werden, generiert die Anwendung einen Fehler und beendet die Konsolen Ausführung.  
  
**Syntax Beispiele:**  
  
In mehreren Variablen Wert Dateien definierte Variablen, eventuell eine mit einem Standardwert und eine andere mit einem instanzspezifischen Wert, falls zutreffend. Die letzte in den Befehlszeilen Argumenten angegebene Variablen Datei hat die bevorzugte Einstellung, wenn eine Duplizierung der Variablen vorliegt:  
  
`C:\>SSMAforMySQLConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
`projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Server Verbindungs Datei (Option):-c/Server Connection  
Diese Datei enthält Server Verbindungsinformationen für jeden Server. Jede Server Definition wird durch eine eindeutige Server-ID identifiziert. Auf die Server-IDs wird in der Skriptdatei für verbindungsbezogene Befehle verwiesen.  
  
Die Server Definition kann ein Teil der Server Verbindungs Datei und/oder der Skriptdatei sein. Die Server-ID in der Skriptdatei hat Vorrang vor der Server Verbindungs Datei, wenn eine Duplizierung der Server-ID vorliegt.  
  
**Syntax Beispiele:**  
  
Server-IDs werden in der Skriptdatei verwendet und in einer separaten Server Verbindungs Datei definiert. die Server Verbindungs Datei verwendet Variablen, die in der Variablen Wert Datei definiert sind:  
  
`C:\>SSMAforMySQLConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
`c:\SsmaProjects\myvaluefile1.xml -c`  
  
`c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
Die Server Definition ist in die Skriptdatei eingebettet:  
  
`C:\>SSMAforMySQLConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Ausgabe Option:-x/xmloutput [xmloutputfile]  
Dieser Befehl wird verwendet, um die Befehlsausgabe Nachrichten in einem XML-Format entweder an die Konsole oder an eine XML-Datei auszugeben.  
  
Für xmloutput stehen zwei Optionen zur Verfügung:  
  
-   Wenn der filePath nach dem xmloutput-Switch bereitgestellt wird, wird die Ausgabe an die Datei umgeleitet.  
  
    **Syntax Beispiel:**  
  
    `C:\>SSMAforMySQLConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Wenn nach dem xmloutput-Schalter kein filePath bereitgestellt wird, wird das xmlout in der Konsole angezeigt.  
  
    **Syntax Beispiel:**  
  
    `C:\>SSMAforMySQLConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Protokolldatei Option:-l/Log  
Alle SSMA-Vorgänge in der Konsolenanwendung werden in einer Protokolldatei aufgezeichnet. Dies ist ein optionaler Switch. Wenn eine Protokolldatei und ihr Pfad in der Befehlszeile angegeben werden, wird das Protokoll am angegebenen Speicherort generiert. Andernfalls wird Sie an Ihrem Standard Speicherort generiert.  
  
**Syntax Beispiel:**  
  
`C:\>SSMAforMySQLConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Projekt Umgebungs Ordner Option:-e/projectenvironment  
Dies kennzeichnet den Ordner mit den Projekt Umgebungseinstellungen für das aktuelle SSMA-Projekt. Dieser Schalter ist optional.  
  
**Syntax Beispiel:**  
  
`C:\>SSMAforMySQLConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Sichere Kenn Wort Option:-p/SecurePassword  
Diese Option gibt das verschlüsselte Kennwort für Serververbindungen an. Dies unterscheidet sich von allen anderen Optionen: die Option führt keines der Skripts aus und unterstützt keine migrationsbezogenen Aktivitäten, sondern hilft bei der Verwaltung der Kenn Wort Verschlüsselung für die Serververbindungen, die im Migrationsprojekt verwendet werden.  
  
Sie können keine andere Option oder kein anderes Kennwort als Befehlszeilenparameter eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie im Abschnitt Verwalten von Kenn [Wörtern](managing-passwords-mysqltosql.md) .  
  
Die folgenden unter Optionen werden für `-p/securepassword`unterstützt:  
  
-   Zum Hinzufügen eines Kennworts zum geschützten Speicher für eine angegebene Server-ID oder für alle Server-IDs, die in der Server Verbindungs Datei definiert sind. Mit der Option-überschreiben (unten) wird das Kennwort aktualisiert, wenn es bereits vorhanden ist:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   So entfernen Sie das verschlüsselte Kennwort aus dem geschützten Speicher der angegebenen Server-ID oder für alle Server-IDs:  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   So zeigen Sie eine Liste der Server-IDs an, für die das Kennwort verschlüsselt ist:  
  
    `-p/securepassword -l/list`  
  
-   , Um die im geschützten Speicher gespeicherten Kenn Wörter in eine verschlüsselte Datei zu exportieren. Diese Datei wird mit dem vom Benutzer angegebenen Passphrase verschlüsselt.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   Die verschlüsselte Datei, die zuvor exportiert wurde, wird mit dem vom Benutzer angegebenen Pass-Phrase in den lokalen geschützten Speicher importiert. Nachdem die Datei entschlüsselt wurde, wird Sie in einer neuen Datei gespeichert, die wiederum auf dem lokalen Computer verschlüsselt ist.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Mehrere Server-IDs können mithilfe von Komma Trennzeichen angegeben werden.  
  
### <a name="help-option--help"></a>Hilfe Option:-?/Help  
Zeigt die Syntax Zusammenfassung der Optionen der SSMA-Konsole an:  
  
`C:\>SSMAforMySQLConsole.EXE -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;mysqldesql&#41;](../../ssma/mysql/appendix-1-mysqltosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>SecurePassword-Hilfe Option:-SecurePassword-?/Help  
Zeigt die Syntax Zusammenfassung der Optionen der SSMA-Konsole an:  
  
`C:\>SSMAforMySQLConsole.EXE -securepassword -?`  
  
Eine tabellarische Anzeige der Befehlszeilenoptionen der SSMA-Konsole finden Sie in [Anhang-1 &#40;mysqlto SQL&#41;](../../ssma/mysql/appendix-1-mysqltosql.md)  
  
### <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;MySQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
-   Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;mysqldesql&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
-   Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;mysqldesql&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
