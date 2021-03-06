---
title: Implementieren einer Connection-Klasse für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fbd293c156f373de0cdad53b4419633ded15af8a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63164124"
---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>Implementieren einer Connection-Klasse für Datenverarbeitungserweiterungen
  Das **Connection**-Objekt stellt eine Datenbankverbindung oder eine ähnliche Ressource dar und bildet den Ausgangspunkt für Benutzer einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung. Es stellt Verbindungen zum Datenbankserver dar, obwohl auch jede Entität mit ähnlichem Verhalten als **Connection** zur Verfügung gestellt werden kann.  
  
 Erstellen Sie eine Klasse, die **und optional** implementiert, um ein <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>Connection<xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>-Objekt zu implementieren.  
  
 Sie müssen in Ihrer Implementierung sicherstellen, dass eine Verbindung erstellt und geöffnet wird, bevor die Befehle ausgeführt werden können. Stellen Sie in Ihrer Implementierung sicher, dass Clients die Verbindungen ausdrücklich (und nicht implizit) öffnen und schließen. Führen Sie die Sicherheitsprüfungen aus, wenn die Verbindung hergestellt wird. Dadurch, dass eine Verbindung für die anderen Klassen in der [!INCLUDE[ssRS](../../../includes/ssrs.md)]-Datenverarbeitungserweiterung vorhanden sein muss, wird sichergestellt, dass bei der Arbeit mit Ihrer Datenquelle stets Sicherheitsprüfungen durchgeführt werden.  
  
 Die Eigenschaften der gewünschten Verbindung werden als Verbindungszeichenfolge dargestellt. Die [!INCLUDE[ssRS](../../../includes/ssrs.md)]-Datenverarbeitungserweiterungen sollten unbedingt die Eigenschaft <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> unterstützen und das bekannte Name/Wert-Paar verwenden, das von der OLE DB definiert ist.  
  
> [!NOTE]  
>  **Connection**-Objekte können häufig nur mit großem Ressourcenaufwand abgerufen werden. Daher sollten Sie zur Reduzierung dieses Effekts ein Pooling der Verbindungen oder andere Techniken in Erwägung ziehen.  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> erbt von <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Sie müssen die <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstelle als Teil der Implementierung der Verbindungsklassen implementieren. Durch die <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstelle kann eine Klasse einen lokalisierten Erweiterungsnamen implementieren und erweiterungsspezifische Konfigurationsdaten verarbeiten, die in der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Konfigurationsdatei gespeichert sind.  
  
 Das **Connection**-Objekt enthält die <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A>-Eigenschaft durch seine Implementierung von <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterungen sollten unbedingt die Eigenschaft <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> unterstützen, sodass die Benutzer einen bekannten und lokalisierten Namen auf der Benutzeroberfläche, z. B. dem Berichts-Manager, vorfinden.  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension> versetzt das **Connection**-Objekt in die Lage, in der Datei „RSReportServer.config“ gespeicherte, benutzerdefinierte Konfigurationsdaten abzurufen und zu verarbeiten. Weitere Informationen zur Verarbeitung benutzerdefinierter Konfigurationsdaten finden Sie in der Methode <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Die Klasse, mit der <xref:Microsoft.ReportingServices.Interfaces.IExtension> implementiert wird, wird nicht aus dem Arbeitsspeicher entladen, wenn der Rest der Datenverarbeitungserweiterungsklassen entladen wird. Daher können Sie mithilfe der **Extension**-Klasse verbindungsübergreifende Statusdaten oder Daten speichern, die im Arbeitsspeicher zwischengespeichert werden können. Die **Extension**-Klasse verbleibt im Arbeitsspeicher, solange der Berichtsserver ausgeführt wird.  
  
 Sie können die **Connection**-Klasse so erweitern, dass Anmeldeinformationen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt werden, indem Sie <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> implementieren. Wenn Sie die Eigenschaften <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A> und <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> der Schnittstelle <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> implementieren, aktivieren Sie das Kontrollkästchen **Integrierte Sicherheit** und die Textfelder **Benutzername** und **Kennwort** im Dialogfeld **Datenquelle** im Berichts-Designer. Hierdurch kann der Berichts-Designer die Anmeldeinformationen für Datenquellen speichern und abrufen, die die Authentifizierung unterstützen. Die Anmeldeinformationen werden sicher gespeichert und verwendet, wenn Berichte im Vorschaumodus gerendert werden.  
  
> [!NOTE]  
>  Die Implementierung von <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> erfordert es implizit, dass Sie die Elemente der <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>-Schnittstelle und der <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstelle implementieren.  
>   
>  Eine Beispiel-**Connection**-Klassenimplementierung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
