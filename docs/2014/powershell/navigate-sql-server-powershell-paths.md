---
title: Navigieren in SQL Server PowerShell-Pfaden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce1e3a2088214c222cd2c2e84fc333f4993b7a6b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797811"
---
# <a name="navigate-sql-server-powershell-paths"></a>Navigieren in SQL Server PowerShell-Pfaden
  Der [!INCLUDE[ssDE](../includes/ssde-md.md)] -PowerShell-Anbieter macht den Satz von Objekten in einer Instanz von SQL Server in einer Struktur verfügbar, die einem Dateipfad ähnelt. Sie können im Anbieterpfad mithilfe von Windows PowerShell-Cmdlets navigieren und benutzerdefinierte Laufwerke erstellen, um den Pfad zu kürzen, den Sie eingeben müssen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Windows PowerShell implementiert Cmdlets, um in der Pfadstruktur zu navigieren, die die Hierarchie von Objekten darstellt, die von einem PowerShell-Anbieter unterstützt werden. Wenn Sie zu einem Knoten im Pfad navigiert haben, können Sie andere Cmdlets verwenden, um grundlegende Vorgänge für das aktuelle Objekt auszuführen. Da die Cmdlets häufig verwendet werden, haben sie kurze, kanonische Aliase. Es gibt auch einen Satz von Aliasen, der die Cmdlets ähnlichen Eingabeaufforderungsbefehlen zuordnet, und einen weiteren Satz für UNIX-Shell-Befehle.  
  
 Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter implementiert eine Teilmenge der Anbieter-Cmdlets, wie in der folgenden Tabelle aufgeführt.  
  
|Cmdlet|Kanonischer Alias|Cmd-Alias|UNIX-Shell-Alias|BESCHREIBUNG|  
|------------|---------------------|---------------|----------------------|-----------------|  
|**Get-Location**|**gl**|**PWD**|**PWD**|Ruft den aktuellen Knoten ab.|  
|`Set-Location`|**SL**|**cd, chdir**|**cd, chdir**|Ändert den aktuellen Knoten.|  
|**Get-ChildItem**|**gci**|**dir**|**ls**|Listet die am aktuellen Knoten gespeicherten Objekte auf.|  
|**Get-Item**|**gi**|||Gibt die Eigenschaften des aktuellen Elements zurück.|  
|**Umbenennen-Element**|**rni**|**Mar**|**ren**|Benennt ein Objekt um.|  
|**Remove-Item**|**Volk**|**del, rd**|**rm, rmdir**|Entfernt ein Objekt.|  
  
> [!IMPORTANT]  
>  Einige [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Bezeichner (Objektnamen) enthalten Zeichen, die Windows PowerShell in Pfadnamen nicht unterstützt. Weitere Informationen zum Verwenden von Namen, die diese Zeichen enthalten, finden Sie unter [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).  
  
### <a name="sql-server-information-returned-by-get-childitem"></a>Von Get-ChildItem zurückgegebene SQL Server-Informationen  
 Die von **Get-ChildItem** (oder den zugehörigen Aliasen **dir** und **ls** ) zurückgegebenen Informationen richten sich danach, wo Sie sich in einem SQLSERVER:-Pfad befinden.  
  
|Pfadposition|Get-ChildItem-Ergebnisse|  
|-------------------|----------------------------|  
|SQLSERVER:\SQL|Gibt den Namen des lokalen Computers zurück. Wenn Sie die Verbindung mit Instanzen von [!INCLUDE[ssDE](../includes/ssde-md.md)] auf anderen Computern mithilfe von SMO oder WMI hergestellt haben, werden diese Computer ebenfalls aufgelistet.|  
|SQLSERVER:\SQL\\*Computername*|Die Liste der Instanzen von [!INCLUDE[ssDE](../includes/ssde-md.md)] auf dem Computer.|  
|SQLServer: \ SQL\\*Computername*\\*instanceName*|Die Liste von Objekttypen der höchsten Ebene in der Instanz, wie Endpunkte, Zertifikate und Datenbanken.|  
|Objektklassenknoten, z. B. Datenbanken|Die Liste der Objekte dieses Typs, z. B. die Liste von Datenbanken: master, model, AdventureWorks20008R2.|  
|Objektnamenknoten, z.B. AdventureWorks2012|Die Liste von im Objekt enthaltenen Objekttypen. Zum Beispiel würden in einer Datenbank Objekttypen wie Tabellen und Sichten aufgeführt werden.|  
  
 Standardmäßig listet **Get-ChildItem** keine Systemobjekte auf. Verwenden Sie den Parameter *Force* , um Systemobjekte anzuzeigen, wie z. B. die Objekte im **sys** -Schema.  
  
### <a name="custom-drives"></a>Benutzerdefinierte Laufwerke  
 Mit Windows PowerShell können Benutzer virtuelle Laufwerke definieren, die als PowerShell-Laufwerke bezeichnet werden. Diese werden über die Startknoten einer Pfadanweisung zugeordnet. Sie werden in der Regel verwendet, um Pfade, die häufig eingegeben werden, zu kürzen. SQLSERVER: Pfade können lang werden, somit viel Platz im Windows PowerShell-Fenster einnehmen und umfangreiche Eingaben erfordern. Wenn Sie vorhaben, viel mit einem bestimmten Pfadknoten zu arbeiten, können Sie ein benutzerdefiniertes Windows PowerShell-Laufwerk definieren, das dem Knoten zugeordnet ist.  
  
## <a name="use-powershell-cmdlet-aliases"></a>Verwenden von PowerShell-Cmdlet-Aliasen  
 **Verwenden eines Cmdlet-Alias**  
  
-   Statt einen vollständigen Cmdlet-Namen einzugeben, geben Sie einen kürzeren Alias ein, oder geben Sie einen ein, der einem bekannten, an der Eingabeaufforderung einzugebenden Befehl entspricht.  
  
### <a name="alias-example-powershell"></a>Beispiel für einen Alias (PowerShell)  
 Sie können beispielsweise einen der folgenden Sätze von Cmdlets oder Aliasen verwenden, um eine Auflistung der Ihnen zur Verfügung stehenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanzen abzurufen, indem Sie zum "SQLSERVER:\SQL"-Ordner navigieren und die Liste der untergeordneten Elemente des Ordners anfordern:  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a>Verwenden von Get-ChildItem  

### <a name="return-information-by-using-get-childitem"></a>Zurückgeben von Informationen mit Get-ChildItem
  
1.  Navigieren Sie zu dem Knoten, für den Sie eine Liste von untergeordneten Elementen abrufen möchten.  
  
2.  Führen Sie Get-ChildItem aus, um die Liste abzurufen.  
  
### <a name="get-childitem-example-powershell"></a>Beispiel für Get-ChildItem (PowerShell)  
 In diesen Beispielen werden die von Get-ChildItem für andere Knoten in einem SQL Server-Anbieterpfad zurückgegebenen Informationen veranschaulicht.  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a>Erstellen eines benutzerdefinierten Laufwerks  

### <a name="create-and-use-a-custom-drive"></a>Erstellen und Verwenden eines benutzerdefinierten Laufwerks
  
1.  Verwenden Sie `New-PSDrive`, um ein benutzerdefiniertes Laufwerk zu definieren. Verwenden Sie den `Root`-Parameter, um den Pfad anzugeben, der durch den Namen des benutzerdefinierten Laufwerks dargestellt wird.  
  
2.  Verweisen Sie in Pfadnavigations-Cmdlets, wie z. B. `Set-Location`, auf den Namen des benutzerdefinierten Laufwerks.  
  
### <a name="custom-drive-example-powershell"></a>Beispiel für ein benutzerdefiniertes Laufwerk (PowerShell)  
 In diesem Beispiel wird ein virtuelles Laufwerk mit dem Namen AWDB erstellt, das dem Knoten für eine bereitgestellte Kopie der Beispieldatenbank AdventureWorks2012 zugeordnet ist. Das virtuelle Laufwerk wird dann verwendet, um zu einer Tabelle in der Datenbank zu navigieren.  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server PowerShell Anbieter](sql-server-powershell-provider.md)   
 [Arbeiten mit SQL Server PowerShell Pfaden](work-with-sql-server-powershell-paths.md)   
 [Konvertieren von URNs in SQL Server Anbieter Pfade](../database-engine/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server-PowerShell](sql-server-powershell.md)  
