---
title: GetAdminSiteUrl-Methode (WMI) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0032f92c79916cbd12962e792b51a05e9f353388
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65581023"
---
# <a name="configurationsetting-method---getadminsiteurl"></a>ConfigurationSetting-Methode: GetAdminSiteUrl
  Ruft die absolute URL für die Zentraladministrationswebsite für die Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-, [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]-, [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]- oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] -Farm ab, in die der Berichtsserver integriert ist  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *AdminSiteUrl*  
 [out] Eine Zeichenfolge, die die absolute URL für die Zentraladministrationswebsite für die SharePoint-Farm enthält, in die der Berichtsserver integriert ist.  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Methods (MSReportServer_ConfigurationSetting-Methoden)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  
