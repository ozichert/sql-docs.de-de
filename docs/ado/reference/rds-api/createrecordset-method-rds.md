---
title: Methode "samaterecordset" (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ae2d78f4647e2aefa707e97349daa73d08ee492
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748844"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset-Methode (RDS)
Erstellt ein leeres, nicht verbundenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Objekt*  
 Eine Objekt Variable, die ein [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oder [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *ColumnsInfos*  
 Ein **Variant** -Array von Attributen, das jede Spalte im erstellten **Recordset** definiert. Jede Spaltendefinition enthält ein Array von vier erforderlichen Attributen und ein optionales Attribut.  
  
|Attribut|BESCHREIBUNG|  
|---------------|-----------------|  
|Name|Der Name des Spalten Headers.|  
|type|Ganzzahliger Wert des Datentyps.|  
|Größe|Ganzzahlige Breite in Zeichen, unabhängig vom Datentyp.|  
|NULL-Zulässigkeit|Boolescher Wert.|  
|Skalieren (optional)|Dieses optionale Attribut definiert die Skala für numerische Felder. Wenn dieser Wert nicht angegeben wird, werden numerische Werte auf drei Dezimalstellen abgeschnitten. Die Genauigkeit ist nicht betroffen, aber die Anzahl der Ziffern nach dem Dezimaltrennzeichen wird auf drei gekürzt.|  
  
 Der Satz von Spalten Arrays wird dann in ein Array gruppiert, das das **Recordset**definiert.  
  
## <a name="remarks"></a>Bemerkungen  
 Das serverseitige Geschäftsobjekt kann das resultierende **Recordset** mit Daten aus einem nicht OLE DB Datenanbieter auffüllen, z. b. eine Betriebssystem Datei mit Kurs Anführungszeichen.  
  
 In der folgenden Tabelle **sind die von der Methode "** |-Methode" unterstützten [datatyetenum](../../../ado/reference/ado-api/datatypeenum.md) -Werte aufgeführt. Die aufgeführte Zahl ist die Verweis Nummer, die zum Definieren von Feldern verwendet wird.  
  
 Jeder Datentyp ist entweder eine mit fester oder variabler Länge. Typen mit fester Länge sollten mit einer Größe von-1 definiert werden, da die Größe vorgegeben ist und eine Größen Definition noch erforderlich ist. Datentypen mit variabler Länge lassen eine Größe zwischen 1 und 32767 zu.  
  
 Für einige der Variablen Datentypen kann der Typ in den Typ umgewandelt werden, der in der Ersetzungs Spalte angegeben ist. Die Ersetzungen werden erst angezeigt, nachdem das **Recordset** erstellt und gefüllt wurde. Anschließend können Sie ggf. den tatsächlichen Datentyp überprüfen.  
  
|Länge|Konstante|Number|Ersetzung|  
|------------|--------------|------------|------------------|  
|Fest|**adTinyInt**|16||  
|Fest|**adSmallInt**|2||  
|Fest|**adInteger**|3||  
|Fest|**adBigInt**|20||  
|Fest|**adUnsignedTinyInt**|17||  
|Fest|**adUnsignedSmallInt**|18||  
|Fest|**adUnsignedInt**|19||  
|Fest|**adUnsignedBigInt**|21||  
|Fest|**adSingle**|4||  
|Fest|**adDouble**|5||  
|Fest|**adCurrency**|6||  
|Fest|**adDecimal**|14||  
|Fest|**adNumeric**|131||  
|Fest|**adBoolean**|11||  
|Fest|**adError**|10||  
|Fest|**adGuid**|72||  
|Fest|**adDate**|7||  
|Fest|**adDBDate**|133||  
|Fest|**adDBTime**|134||  
|Fest|**adDBTimestamp**|135|7|  
|Variable|**adBSTR**|8|130|  
|Variable|**adChar**|129|200|  
|Variable|**adVarChar**|200||  
|Variable|**adLongVarChar**|201|200|  
|Variable|**adWChar**|130||  
|Variable|**adVarWChar**|202|130|  
|Variable|**adLongVarWChar**|203|130|  
|Variable|**adBinary**|128||  
|Variable|**adVarBinary**|204||  
|Variable|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die Methode "kreaterecordset" (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Beispiel für die Methode "kreaterecordset" (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject-Methode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



