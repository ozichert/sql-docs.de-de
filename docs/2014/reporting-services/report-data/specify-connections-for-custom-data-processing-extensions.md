---
title: Angeben von Verbindungen für benutzerdefinierte Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- IDbConnection interface, connection strings
- impersonation [Reporting Services]
- IDbConnectionExtension interface, connection strings
- data sources [Reporting Services], security
- connection strings [Reporting Services]
- credentials [Reporting Services]
- authentication [Reporting Services]
- external data sources [Reporting Services]
- data processing extensions [Reporting Services], connections
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 734eca26e94b4b879590c889c6c3c479c155c7be
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107044"
---
# <a name="specify-connections-for-custom-data-processing-extensions"></a>Angeben von Verbindungen für benutzerdefinierte Datenverarbeitungserweiterungen
  Sie können benutzerdefinierte Datenverarbeitungserweiterungen von Drittanbietern auf einem Berichtsserver erstellen oder verwenden, um die Datenverarbeitungsfunktionen für unterstützte Datenquellen zu erweitern oder um weitere Typen von Datenquellen zu unterstützen, die in einer standardmäßigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation nicht verfügbar sind. Verbindungen werden abhängig von der Implementierung unterschiedlich behandelt. Die folgenden Implementierungen sind für Datenverarbeitungserweiterungen verfügbar:  
  
-   Benutzerdefinierte [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter (wenn Sie auf Daten aus DB2.NET-, Oracle-, ODP.NET- oder Teradata-Datenquellen zugreifen, verwenden Sie möglicherweise einen benutzerdefinierten .NET-Datenanbieter)  
  
-   Benutzerdefinierte Datenverarbeitungserweiterungen zur Unterstützung von <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Benutzerdefinierte Datenverarbeitungserweiterungen zur Unterstützung von <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Fragen Sie den betreffenden Drittanbieterprovider, wie Ihre benutzerdefinierte Datenverarbeitungserweiterung implementiert ist.  
  
## <a name="impersonation-and-custom-data-processing-extensions"></a>Identitätswechsel und benutzerdefinierte Datenverarbeitungserweiterungen  
 Falls die benutzerdefinierte Datenverarbeitungserweiterung die Verbindung mit Datenquellen mithilfe eines Identitätswechsels herstellt, müssen Sie die Anforderung mithilfe der Open-Methode an der Schnittstelle <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> oder <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> stellen. Alternativ können Sie das Benutzeridentitätsobjekt (System.Security.Principal.WindowsIdentity) speichern und anschließend in den APIs der anderen Datenverarbeitungserweiterungen erneut verwenden.  
  
 In früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]wurden alle benutzerdefinierten Datenverarbeitungserweiterungen mit Benutzeridentitätswechsel aufgerufen. In diesem Release wird nur während des Aufrufs der Open-Methode die Identität des Benutzers angenommen. Falls für eine vorhandene Datenverarbeitungserweiterung die integrierte Sicherheit erforderlich ist, müssen Sie den Code so ändern, dass die Open-Methode verwendet wird, oder das Benutzeridentitätsobjekt speichern.  
  
## <a name="connections-for-custom-net-framework-data-providers"></a>Verbindungen für benutzerdefinierte .NET Framework-Datenanbieter  
 Beim Konfigurieren eines Berichts für eine bestimmte Datenquelle legen Sie Eigenschaften fest, die den Datenquellentyp, die Verbindungszeichenfolge und die Anmeldeinformationen für den Zugriff auf die Datenquelle bestimmen. In der folgenden Tabelle sind die Anmeldeinformationstypen beschrieben, die für [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter unterstützt werden. Weitere Informationen zum Festlegen von Eigenschaften für Berichtsdatenquellen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Anmeldeinformationen|Verbindungen|  
|-----------------|-----------------|  
|Integrierte Sicherheit|Falls dies vom verwendeten Datenanbieter unterstützt wird, können Sie die integrierte Sicherheit von Windows verwenden. Die Anforderung wird mit den Anmeldeinformationen des aktuellen Benutzers gesendet.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z. B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle `Integrated Security=SSPI` enthalten).|  
|Windows-Authentifizierung|Sofern vom Datenprovider unterstützt, können Sie ein Windows-Domänenbenutzerkonto verwenden. Der Berichtsserver nimmt vor dem Aufruf der Datenverarbeitungserweiterung die Identität des Benutzerkontos an.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z. B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle `Integrated Security=SSPI` enthalten).|  
|Datenbank-Anmeldeinformationen|Die Datenbankauthentifizierung wird für Verbindungen über einen benutzerdefinierten .NET-Datenanbieter nicht unterstützt. In diesen Fällen kann vom Berichtsserver keine Verbindung hergestellt werden.|  
|Keine Anmeldeinformationen|Die Option zum Verzicht auf Anmeldeinformationen kann bei .NET-Datenanbietern verwendet werden. Falls das Konto für die unbeaufsichtigte Ausführung angegeben ist, werden die verwendeten Anmeldeinformationen durch die Verbindungszeichenfolge bestimmt. Der Berichtsserver nimmt zum Herstellen der Verbindung die Identität des Kontos für die unbeaufsichtigte Ausführung an.<br /><br /> Falls das Konto für die unbeaufsichtigte Ausführung nicht angegeben ist, kann keine Verbindung vom Berichtsserver hergestellt werden. Weitere Informationen zum Definieren des Kontos finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## <a name="connections-for-idbconnection"></a>Verbindungen für IDbConnection  
 Wenn Sie eine benutzerdefinierte Datenverarbeitungserweiterung verwenden, die nur <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>unterstützt, müssen Sie die Verbindung folgendermaßen angeben:  
  
1.  Konfigurieren Sie das Konto für die unbeaufsichtigte Ausführung. Das Konfigurieren des Kontos ist für Verbindungen erforderlich, die mit `IDbConnection` hergestellt werden. Der Berichtsserver nimmt die Identität des Kontos beim Herstellen der Verbindung an.  
  
2.  Konfigurieren Sie die Datenquelleneigenschaften für den Bericht mit der Option **Keine Anmeldeinformationen**.  
  
3.  Nehmen Sie die Anmeldeinformationen für die Verbindung mit der Datenquelle in die Verbindungszeichenfolge auf.  
  
 Bei Verwendung von `IDbConnection` werden die folgenden Anmeldeinformationstypen nicht unterstützt: integrierte Sicherheit, Windows-Benutzerkonten und Datenbank-Anmeldeinformationen. Wenn diese Optionen für eine Datenquellenverbindung verwendet werden, kann die Verbindung vom Berichtsserver nicht hergestellt werden.  
  
## <a name="connections-for-idbconnectionextension"></a>Verbindungen für IDbConnectionExtension  
 Wenn Sie eine benutzerdefinierte Datenverarbeitungserweiterung verwenden, die <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>unterstützt, können Sie die Verbindung auf folgende Arten angeben:  
  
|Anmeldeinformationen|Verbindungen|  
|-----------------|-----------------|  
|Integrierte Sicherheit|Falls dies vom Datenanbieter unterstützt wird, können Sie die integrierte Sicherheit von Windows bei benutzerdefinierten Datenverarbeitungserweiterungen verwenden, die `IDbConnectionExtension` verwenden.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z. B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle `Integrated Security=SSPI` enthalten).|  
|Windows-Authentifizierung|Sofern vom Datenprovider unterstützt, können Sie ein Windows-Domänenbenutzerkonto bei benutzerdefinierten Datenverarbeitungserweiterungen verwenden, die `IDbConnectionExtension` verwenden.<br /><br /> Der Berichtsserver nimmt vor dem Aufruf der Datenverarbeitungserweiterung die Identität des Benutzerkontos an. Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z. B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle `Integrated Security=SSPI` enthalten).|  
|Datenbank-Anmeldeinformationen|Sie können Verbindungen mit benutzerdefinierten Datenverarbeitungserweiterungen, die `IDbConnectionExtension` verwenden, mit der Datenbankauthentifizierung konfigurieren.|  
|Keine Anmeldeinformationen|Falls das Konto für die unbeaufsichtigte Ausführung angegeben ist, werden die verwendeten Anmeldeinformationen durch die Verbindungszeichenfolge bestimmt.<br /><br /> Falls das Konto für die unbeaufsichtigte Ausführung nicht angegeben ist, kann keine Verbindung vom Berichtsserver hergestellt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des unbeaufsichtigten Ausführungskontos &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](specify-credential-and-connection-information-for-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Implementieren von Datenverarbeitungserweiterungen](../extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Konfigurieren von Datenquelleneigenschaften für einen Bericht &#40;Berichts-Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md)  
  
  
