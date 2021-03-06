---
title: Installationsprogramm-dll-API-Referenzfunktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installer DLL [ODBC]
ms.assetid: 47fcadc3-f102-4989-9ee7-a1c65233142a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3502dfe6cdf54214041e3654d20e1b6dd2ff6f21
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298780"
---
# <a name="installer-dll-api-reference-function"></a>Installer-DLL-API-Referenz – Funktion
In diesem Abschnitt wird die Syntax der Funktionen in der Installer-DLL-API beschrieben. Die Installer-DLL-API besteht aus 20 Funktionen. Drei dieser Funktionen, **sqlgettranslator**, **sqlremovedsnfromini**und **sqlschreitedsndeini**, werden nur von Setup-DLLs aufgerufen. Die anderen Funktionen werden von den Setup-und Verwaltungsprogrammen aufgerufen.  
  
 Jede Funktion wird mit der Version von ODBC bezeichnet, in der Sie eingeführt wurde.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [SQLConfigDataSource-Funktion](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)  
  
-   [SQLConfigDriver-Funktion](../../../odbc/reference/syntax/sqlconfigdriver-function.md)  
  
-   [SQLCreateDataSource-Funktion](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)  
  
-   [SQLGetConfigMode-Funktion](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)  
  
-   [SQLGetInstalledDrivers-Funktion](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)  
  
-   [SQLGetPrivateProfileString-Funktion](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)  
  
-   [SQLGetTranslator-Funktion](../../../odbc/reference/syntax/sqlgettranslator-function.md)  
  
-   [SQLInstallDriverEx-Funktion](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)  
  
-   [SQLInstallDriverManager-Funktion](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)  
  
-   [SQLInstallerError-Funktion](../../../odbc/reference/syntax/sqlinstallererror-function.md)  
  
-   [SQLInstallTranslator-Funktion](../../../odbc/reference/syntax/sqlinstalltranslator-function.md)  
  
-   [SQLInstallTranslatorEx-Funktion](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)  
  
-   [Sqlmanagedatasources-Funktion](../../../odbc/reference/syntax/sqlmanagedatasources.md)  
  
-   [SQLPostInstallerError-Funktion](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)  
  
-   [SQLReadFileDSN-Funktion](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)  
  
-   [SQLRemoveDefaultDataSource-Funktion](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)  
  
-   [SQLRemoveDriver-Funktion](../../../odbc/reference/syntax/sqlremovedriver-function.md)  
  
-   [SQLRemoveDriverManager-Funktion](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)  
  
-   [SQLRemoveDSNFromIni-Funktion](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)  
  
-   [SQLRemoveTranslator-Funktion](../../../odbc/reference/syntax/sqlremovetranslator-function.md)  
  
-   [SQLSetConfigMode-Funktion](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)  
  
-   [SQLValidDSN-Funktion](../../../odbc/reference/syntax/sqlvaliddsn-function.md)  
  
-   [SQLWriteDSNToIni-Funktion](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)  
  
-   [SQLWriteFileDSN-Funktion](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)  
  
-   [SQLWritePrivateProfileString-Funktion](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)
