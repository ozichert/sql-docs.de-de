---
title: Registrieren von Geschäftsobjekten auf dem Client für die Verwendung mit DCOM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 79f88f36b7eae83163ef2754f9b2c2265550c684
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747667"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Registrieren von Geschäftsobjekten auf dem Client für die Verwendung mit DCOM
Benutzerdefinierte Geschäftsobjekte müssen sicherstellen, dass die Clientseite ihren Programmnamen (ProgID) einem Bezeichner (CLSID) zuordnen kann, der über DCOM verwendet werden kann. Aus diesem Grund muss sich die ProgID des DCOM-Objekts in der Client seitigen Registrierung befinden und der Klassen-ID des serverseitigen Geschäftsobjekts zugeordnet werden. Für die anderen unterstützten Protokolle (http, HTTPS und in-Process) ist dies nicht erforderlich.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Wenn Sie z. b. ein serverseitiges Geschäftsobjekt mit dem Namen mybobj mit einer bestimmten Klassen-ID verfügbar machen, z. b. "{00112233-4455-6677-8899-00aabbccddee}", stellen Sie sicher, dass der Client seitigen Registrierung die folgenden Einträge hinzugefügt werden:  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


