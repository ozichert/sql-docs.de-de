---
title: Registrieren eines benutzerdefinierten Geschäftsobjekts | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f110447fbb0f00c037361b00945b228449caf4f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747714"
---
# <a name="registering-a-custom-business-object"></a>Registrieren eines benutzerdefinierten Geschäftsobjekts
Damit ein benutzerdefiniertes Geschäftsobjekt (. dll oder. exe) über den Webserver erfolgreich gestartet werden kann, muss die ProgID des Geschäftsobjekts in die Registrierung eingegeben werden, wie in diesem Verfahren erläutert. Diese RDS-Funktion schützt die Sicherheit Ihres Webservers, indem nur sanktionierte ausführbare Dateien ausgeführt werden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
> [!NOTE]
>  Bei MDAC 2,0 und höher und Windows DAC wird das standardmäßige Geschäftsobjekt [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)bei der MDAC-/Windows DAC-Installation nicht standardmäßig registriert. Wenn jedoch **RDSServer. DataFactory** vor der Installation als sicher für die Ausführung auf dem Computer registriert wurde, wird der Registrierungs Eintrag für die neue Installation beibehalten.  
  
### <a name="to-register-a-custom-business-object"></a>So registrieren Sie ein benutzerdefiniertes Geschäftsobjekt:  
  
1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
2.  Geben Sie **Regedit** ein und klicken Sie auf **OK**.  
  
3.  Navigieren Sie im Registrierungs-Editor zum **HKEY_LOCAL_MACHINE \system\currentcontrolset\services\w3svc\parameters\adclaunch** Registry Key.  
  
4.  Wählen Sie **adclaunch** Key aus, und zeigen Sie dann im Menü **Bearbeiten**auf **neu** , und klicken Sie auf **Schlüssel**.  
  
5.  Geben Sie die ProgID Ihres benutzerdefinierten Geschäftsobjekts ein, und drücken Sie die **Eingabe**Taste. Lassen Sie den **Wert** Eintrag leer.


