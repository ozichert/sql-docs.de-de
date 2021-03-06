---
title: catalog.deploy_packages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0a1828925494ca2e1e8f593e3f133a21cd10a9ee
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296774"
---
# <a name="catalogdeploy_packages"></a>catalog.deploy_packages 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Stellt in einem Ordner im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog mindestens ein Paket bereit oder aktualisiert ein vorhandenes Paket, das zuvor bereitgestellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners. Der *folder_name* ist **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Der Name des Projekts im Ordner. Der *project_name* ist **nvarchar(128)** .  
  
 [ @packages_table = ] *packages_table*  
 Die binären Inhalte der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketdatei(en) (DTSX). Das Argument *packages_table* ist vom Typ **[catalog].[Package_Table_Type]** .  
  
 [ @operation_id = ] *operation_id*  
 Gibt den eindeutigen Bezeichner für den Bereitstellungsvorgang zurück. Der *operation_id* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   CREATE_OBJECTS-Berechtigungen für das Projekt oder MODIFY-Berechtigungen für das Paket, um ein Paket zu aktualisieren.  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden Bedingungen beschrieben, die möglicherweise bewirken, dass diese gespeicherte Prozedur einen Fehler auslöst:  
  
-   Ein Parameter verweist auf ein Objekt, das nicht vorhanden ist, ein Parameter versucht, ein bereits vorhandenes Objekt zu erstellen, oder ein Parameter ist aus anderen Gründen ungültig.  
  
-   Der Benutzer verfügt nicht über ausreichende Berechtigungen  
  
  
