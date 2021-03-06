---
title: Webkonfigurationsreferenz
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e9d3cd20fc219a7159de0b271dafcc0e9fb2c3ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728830"
---
# <a name="web-configuration-reference-master-data-services"></a>Webkonfigurationsreferenz (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] benutzt die Datei „Web.config“, die die Konfigurationseinstellungen enthält, die Internetinformationsdienste (IIS) aktivieren, um die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und den entsprechenden Webdienst zu hosten. Diese Datei Web.config Datei befindet sich im Ordner WebApplication des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Installationspfads. Weitere Informationen zu Pfaden und Berechtigungen finden Sie unter [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Web.Config-Elemente  
 Die Datei Web. config enthält zusätzlich zu [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] den Konfigurationselementen Standard-IIS, .NET Framework, ASP.net und Windows Communication Foundation (WCF) ein benutzerdefiniertes Element ( ** \<masterdataservices>**). Die folgende Tabelle beschreibt die Elemente mit den enthaltenen Web.config-Dateien.  
  
|Konfigurationselement|BESCHREIBUNG|  
|---------------------------|-----------------|  
|**masterDataServices**|Benutzerdefiniertes Element. Verbindet den [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Web-Service mit einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank.|  
|**connectionStrings**|ASP.NET-Element. Weitere Informationen finden Sie unter [connectionStrings-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178347) in der MSDN Library.|  
|**System. Web**|ASP.NET-Element. Weitere Informationen finden Sie unter [system.web-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178348) in der MSDN Library.|  
|**Starts**|.NET Framework-Element. Weitere Informationen finden [ \<Sie unter Startup>-Element](https://go.microsoft.com/fwlink/?LinkId=178349) in der MSDN Library.|  
|**Runtime**|.NET Framework-Element. Weitere Informationen finden [ \<Sie unter Runtime>-Element](https://go.microsoft.com/fwlink/?LinkId=178350) in der MSDN Library.|  
|**system.codedom**|.NET Framework-Element. Weitere Informationen finden [ \<Sie unter System. CodeDom>-Element](https://go.microsoft.com/fwlink/?LinkId=178351) in der MSDN Library.|  
|**System. Web. Extensions**|ASP.NET-Element. Weitere Informationen finden Sie unter [system.web.extensions-Element (ASP.NET-Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178352) in der MSDN Library.|  
|**system.webServer**|Abschnittsgruppe, die IIS-Elemente enthält. Weitere Informationen finden Sie unter [system.webServer Section Group \[IIS 7 Settings Schema\]](https://go.microsoft.com/fwlink/?LinkId=178353) (Abschnittsgruppe „system.webServer“ [IIS 7-Einstellungsschema]) in der MSDN Library.|  
|**system.serviceModel**|WCF-Element. Weitere Informationen finden [ \<Sie unter System. Service Model>](https://go.microsoft.com/fwlink/?LinkId=178354) in der MSDN Library.|  
|**system.diagnostics**|.NET Framework-Element. Weitere Informationen finden [ \<Sie unter System. Diagnostics>-Element](https://go.microsoft.com/fwlink/?LinkId=178355) in der MSDN Library.|  
|**appSettings**|ASP.NET-Element. Weitere Informationen finden Sie unter [appSettings-Element (allgemeines Einstellungsschema)](https://go.microsoft.com/fwlink/?LinkId=178356) in der MSDN Library.|  
  
## <a name="masterdataservices-element"></a>masterDataServices-Element  
 Das ** \<masterdataservices->** Element ist ein benutzerdefiniertes Element, das verwendet [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] wird, um einen [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Webdienst mit einer-Datenbank zu verbinden.  
  
### <a name="syntax"></a>Syntax  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Elemente und Attribute  
  
|Element|BESCHREIBUNG|  
|----------|-----------------|  
|**lichen**|Untergeordnetes Element. Enthält Attribute, die Informationen für den Webdienst und Datenbankverbindungszeichenfolge angeben.|  
|**virtualPath**|Attribute. Gibt den virtuellen Pfad der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und des entsprechenden Diensts an. Dies entspricht dem Wert des **path**-Attributs des **\<application>**-Elements unter dem **\<site>**-Element der IIS-Datei „ApplicationHost.config“.|  
|**Sitename**|Attribute. Gibt den Namen der Website an, die die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung und den entsprechenden Dienst hostet. Dies entspricht dem Wert des **name**-Attributs des **\<site>**-Elements unter dem **\<sites>**-Element der IIS-Datei „ApplicationHost.config“.|  
|**ConnectionName**|Attribute. Gibt den Namen der zu verwendeten Verbindung an. Dies entspricht dem **name**-Attribut des **\<add>**-Elements unter dem **\<connectionStrings>**-Element in der Web.config-Datei.|  
|**serviceName**|Attribute. Gibt den Namen des Web-Services an. Dies entspricht dem **name**-Attribut des **\<service>**-Elements unter dem **\<services>**-Element in der Web.config-Datei.|  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Dienst mit dem Namen MDS1 auf der Contoso-Website veranschaulicht und /MDs-Pfad, der eine von MDSDB angegebene Verbindungszeichenfolge verwendet.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
