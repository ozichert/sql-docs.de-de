---
title: Keys-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Keys
- Keys
helpviewer_keywords:
- Keys collection [ADOX]
ms.assetid: cdb31c76-e559-475c-b33a-aac24f73e70e
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a7bebc1c05ab195d3b23c5c0894d4fcce967625
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82746543"
---
# <a name="keys-collection-adox"></a>Keys-Collection (ADOX)
Enthält alle [Schlüssel](../../../ado/reference/adox-api/key-object-adox.md) Objekte einer [Tabelle](../../../ado/reference/adox-api/table-object-adox.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-keys.md) -Methode für eine [Keys](../../../ado/reference/adox-api/keys-collection-adox.md) -Auflistung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Auflistung mithilfe der [Append](../../../ado/reference/adox-api/append-method-adox-keys.md) -Methode einen neuen Schlüssel hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf einen Schlüssel in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Schlüssel mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernt einen Schlüssel aus der Auflistung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das Schema der aktuellen Datenbank mit [der Aktualisierungs Methode](../../../ado/reference/ado-api/refresh-method-ado.md) widerzuspiegeln.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Indizes Auflistungseigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Eigenschaften, Methoden und Ereignisse der Schlüssel Sammlung](../../../ado/reference/adox-api/keys-collection-properties-methods-and-events.md)   
 [Key-Objekt (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)
