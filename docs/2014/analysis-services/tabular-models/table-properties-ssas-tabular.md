---
title: Tabellen Eigenschaften (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97d6731c5e85c3b37facc7172ecacbd2c7c74176
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066472"
---
# <a name="table-properties-ssas-tabular"></a>Tabelleneigenschaften (SSAS – tabellarisch)
  In diesem Thema werden Tabelleneigenschaften für tabellarische Modelle beschrieben. Die hier beschriebenen Eigenschaften unterscheiden sich von den Eigenschaften im Dialogfeld Tabelleneigenschaften bearbeiten, mit denen definiert wird, welche Spalten aus der Quelle importiert werden.  
  
 Abschnitte in diesem Thema:  
  
-   [Tabelleneigenschaften](#bkmk_properties)  
  
-   [So konfigurieren Sie Einstellungen für Tabelleneigenschaften](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a>Tabellen Eigenschaften  
 **Grundlegend**  
  
|Eigenschaft|Standardeinstellung|BESCHREIBUNG|  
|--------------|---------------------|-----------------|  
|**Verbindungsname**|\<Verbindungs Name>|Der Name der Verbindung mit der Datenquelle der Tabelle.<br /><br /> Klicken Sie auf die Schaltfläche, um die Verbindung zu bearbeiten.|  
|**Verbirgt**|False|Gibt an, ob die Tabelle in den Feldlisten von Berichtserstellungsclients ausgeblendet wird.|  
|**Partitionen**||Partitionen für die Tabelle können nicht im **Eigenschaftenfenster** angezeigt werden. Klicken Sie zum Anzeigen, Erstellen oder Bearbeiten von Partitionen auf die Schaltfläche, um den Partitions-Manager zu öffnen.|  
|**Quelldaten**||Quelldaten für die Tabelle können nicht im **Eigenschaftenfenster** angezeigt werden. Klicken Sie zum Anzeigen oder Bearbeiten der Quelldaten auf die Schaltfläche, um das Dialogfeld Tabelleneigenschaften bearbeiten zu öffnen.|  
|**Tabellenbeschreibung**||Eine Textbeschreibung für die Tabelle.<br /><br /> Wenn ein Endbenutzer in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]den Cursor über dieser Tabelle in der Feldliste platziert, wird die Beschreibung als QuickInfo angezeigt.|  
|**Tabellenname**|\<Anzeige Name>|Gibt den anzeigen amen der Tabelle an. Der Tabellenname kann angegeben werden, wenn eine Tabelle mit dem Tabellenimport-Assistenten importiert wird, oder jederzeit nach dem Import. Der Tabellenname im Modell kann sich von der zugeordneten Tabelle am Quellort unterscheiden. Der Anzeigename der Tabelle wird in der Feldliste einer Clientanwendung zur Berichterstellung sowie in der Modelldatenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt.|  
  
 **Berichterstellungseigenschaften**  
  
 Ausführliche Beschreibungen und Informationen zur Konfiguration für Berichterstellungseigenschaften finden Sie unter [Power View-Berichterstellungseigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md).  
  
|Eigenschaft|Standardeinstellung|Beschreibung|  
|--------------|---------------------|-----------------|  
|**Standardfeldsatz**|||  
|Tabellenverhalten|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a>So konfigurieren Sie Einstellungen für Tabellen Eigenschaften  
  
1.  Klicken Sie im Modell-Designer in der Datensicht auf eine Tabelle (Registerkarte) oder in der Diagrammsicht auf einen Tabellenkopf.  
  
2.  Klicken Sie im **Eigenschaftenfenster** auf eine Eigenschaft, und geben Sie einen Wert ein, oder klicken Sie auf die Schaltfläche für weitere Konfigurationsoptionen.  
  
  
