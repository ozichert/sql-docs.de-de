---
title: Überprüfen der Parameter für die Systemkonfigurationsprüfung
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 09f7ccbaf84f035b882f56a6dc32f1233686db4d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75251561"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Überprüfen der Parameter für die Systemkonfigurationsprüfung

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchsucht die Systemkonfigurationsprüfung (System Configuration Checker, SCC) den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden soll. Die SCC sucht nach Bedingungen, die eine erfolgreiche Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindern. Bevor Setup den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installations-Assistenten startet, ruft SCC den Status jedes Elements ab. SCC vergleicht dann das Ergebnis mit den erforderlichen Bedingungen und gibt Anweisungen zum Entfernen der Blockierungsprobleme.  
  
Die Systemkonfigurationsprüfung generiert einen Bericht, der eine kurze Beschreibung für jede ausgeführte Regel sowie den Ausführungsstatus enthält. Der Bericht der Systemkonfigurationsprüfung befindet sich unter %programfiles%\Microsoft SQL Server\140\Setup Bootstrap\Log\\\<JJJJMMTT_hhmm>\\\..    
  
Weitere Informationen finden Sie unter den folgenden Links:

- [Hardware- und Softwareanforderungen für die Installation von SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
- [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
- [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  
