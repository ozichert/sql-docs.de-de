---
title: Eine Auflistung der gespeicherten XML-Schemas anzeigen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef32368031876bc14619cd14aa215402c67618b6
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662923"
---
# <a name="view-a-stored-xml-schema-collection"></a>Anzeigen einer gespeicherten XML-Schemaauflistung
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Nach dem Importieren einer XML-Schemaauflistung mithilfe von [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)werden die Schemakomponenten in den Metadaten gespeichert. Mit der systeminternen Funktion [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md)können Sie die XML-Schemaauflistung rekonstruieren. Diese Funktion gibt eine Instanz vom Datentyp **xml** zurück.  
  
 So ruft beispielsweise die folgende Abfrage eine XML-Schemaauflistung (`ProductDescriptionSchemaCollection`) aus dem relationalen Schema 'production' der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ab.  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Wenn nur ein Schema der XML-Schemaauflistung angezeigt werden soll, können Sie eine XQuery-Abfrage für das Ergebnis vom Typ **xml** angeben, das von `xml_schema_namespace`zurückgegeben wird.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 So ruft beispielsweise die folgende Abfrage XML-Schemainformationen zur Produktgarantie und -wartung aus der XML-Schemaauflistung `ProductDescriptionSchemaCollection` ab.  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 Sie können auch den optionalen Zielnamespace als dritten Parameter an die `xml_schema_namespace` -Funktion übergeben, um ein bestimmtes Schema aus der Auflistung abzurufen, wie es in der folgenden Abfrage gezeigt wird:  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Wenn Sie eine XML-Schemaauflistung mithilfe von CREATE XML SCHEMA COLLECTION in der Datenbank erstellen, speichert die Anweisung die Schemakomponenten in den Metadaten. Beachten Sie, dass nur die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpretierbaren Schemakomponenten gespeichert werden. Kommentare, Anmerkungen oder Nicht-XSD-Attribute werden nicht gespeichert. Daher ist das von **xml_schema_namespace** rekonstruierte Schema zwar hinsichtlich seiner Funktionalität mit dem ursprünglichen Schema gleichwertig, sein Erscheinungsbild jedoch nicht unbedingt identisch. Beispielsweise werden Sie die Präfixe des ursprünglichen Schemas nicht wiederfinden. Das von **xml_schema_namespace** zurückgegebene Schema verwendet **t** als Präfix für den Zielnamespace und **ns1**, **ns2**usw. für andere Namespaces.  
  
 Wenn Sie eine identische Kopie des XML-Schemas aufbewahren möchten, sollten Sie das XML-Schema in einer Datei oder in einer Datenbanktabelle in einer Spalte vom Typ **xml** speichern.  
  
 Die [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) -Katalogsicht gibt auch Informationen zu XML-Schemaauflistungen zurück. Zu diesen Informationen gehören der Name der Auflistung, das Erstellungsdatum und der Besitzer der Auflistung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Schemaauflistungen &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
