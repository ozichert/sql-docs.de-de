---
title: CERTPRIVATEKEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7a8bf334be11a219dccf84f6732fb94254034403
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832194"
---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt den privaten Schlüssel eines Zertifikats im Binärformat zurück. Diese Funktion akzeptiert drei Argumente.
-   Eine Zertifikat-ID.  
-   Ein Verschlüsselungskennwort, das verwendet wird, um die Bits des privaten Schlüssels zu verschlüsseln, die von der Funktion zurückgegeben werden. Diese Vorgehensweise legt die Schlüssel nicht als Klartext für Benutzer offen.  
-   Ein optionales Entschlüsselungskennwort. Ein angegebenes Entschlüsselungskennwort wird verwendet, um den privaten Schlüssel für dieses Zertifikat zu entschlüsseln. Andernfalls wird der Hauptschlüssel der Datenbank verwendet.  
  
Diese Funktion kann nur von Benutzern mit Zugriff auf den privaten Zertifikatschlüssel verwendet werden. Diese Funktion gibt den privaten Schlüssel im PVK-Format zurück.
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>Argumente  
*certificate_ID*  
Die **certificate_id** des Zertifikats. Rufen Sie diesen Wert von „sys.certificates“ oder von [CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md) ab. *cert-id* weist den Datentyp **int** auf.
  
*encryption_password*  
Das Kennwort, das verwendet wird, um den zurückgegebenen Binärwert zu verschlüsseln.
  
*decryption_password*  
Das Kennwort, das verwendet wird, um den zurückgegebenen Binärwert zu entschlüsseln.
  
## <a name="return-types"></a>Rückgabetypen
**varbinary**
  
## <a name="remarks"></a>Bemerkungen  
Verwenden Sie **CERTENCODED** und **CERTPRIVATEKEY** zusammen, um andere Teile eines Zertifikats in binärer Form zurückzugeben.
  
## <a name="permissions"></a>Berechtigungen  
**CERTPRIVATEKEY** ist öffentlich verfügbar.
  
## <a name="examples"></a>Beispiele  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20401031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
Ein komplexeres Beispiel für die Verwendung von [CERTPRIVATEKEY](../../t-sql/functions/certencoded-transact-sql.md) und **CERTENCODED** zum Kopieren eines Zertifikats in eine andere Datenbank finden Sie in Beispiel B im Artikel zu **CERTENCODED &#40;Transact-SQL&#41;** .
  
## <a name="see-also"></a>Weitere Informationen
[Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)
[Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
