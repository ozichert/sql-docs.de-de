---
title: Vorbereiten der Implementierung von Übermittlungserweiterungen | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 949ab416b0d30f7bb20ec2b797a04121d49b9811
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "63193713"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Vorbereiten der Implementierung von Übermittlungserweiterungen
  Bevor Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung implementieren, sollten Sie definieren, welche Schnittstellen implementiert werden sollen. Sie müssen zuerst überlegen, wie die Übermittlungserweiterung verwendet werden soll, welche Einstellungen benötigt werden und welche speziellen Funktionen Sie implementieren müssen, um die Berichtsbenachrichtigungen zu übermitteln.  
  
 Jede [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung muss die folgenden Funktionen enthalten:  
  
-   Eine <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstellenimplementierung, die die Erweiterung und einen lokalisierten Erweiterungsnamen darstellt.  
  
-   Eine <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>-Implementierung, die eine Übermittlungserweiterung erstellt, mit der die Berichtsbenachrichtigungen an die Endbenutzer übermittelt werden können.  
  
-   Die Fähigkeit, bestimmte Benutzerdaten für ein Abonnement zu verarbeiten.  
  
 Jede Übermittlungserweiterung kann auf folgende Funktionen erweitert werden:  
  
-   Eine [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]-Implementierung von Benutzersteuerelementen, anhand der Endbenutzer mithilfe des Berichts-Managers Berichtsabonnements erstellen, die diese Übermittlungserweiterung verwenden.  
  
 In der folgenden Tabelle werden die verfügbaren Schnittstellen und Klassen für Übermittlungserweiterungen beschrieben.  
  
|Schnittstelle oder Klasse|BESCHREIBUNG|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> -Schnittstelle|Stellt eine Erweiterung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> -Schnittstelle|Stellt eine Übermittlungserweiterung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> -Schnittstelle|Enthält auch Informationen zum Berichtsserver, die von den Übermittlungserweiterungen benötigt werden (z. B. eine Liste der verfügbaren Renderingerweiterungen).|  
|<xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse|Stellt eine Einstellung für eine Erweiterung dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse|Enthält Abonnementinformationen, mithilfe der die Übermittlungserweiterungen Berichte übermitteln.|  
|<xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse|Stellt berichtsspezifische Informationen und Methoden dar, anhand derer die Übermittlungserweiterungen Berichte an die Benutzer übermitteln können.|  
|<xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Klasse|Stellt die Ausgabe von einer Renderingerweiterung dar. Ein <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt enthält die dazugehörigen Informationen zu Dateiname und Dateityp, die von der Übermittlungserweiterung benötigt werden, um den von der Renderingerweiterung zurückgegebenen Datenstrom zu verarbeiten.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> -Schnittstelle|Ein Benutzersteuerelement, mit dem Abonnementinformationen, die für die Übermittlungserweiterung spezifisch sind, vom Benutzer im Berichts-Manager abgerufen werden können (z. B. eine E-Mail-Adresse oder der Pfad zu einer Dateifreigabe).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementieren von Übermittlungserweiterungen](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
