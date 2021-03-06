---
title: Angeben der Feldlänge mithilfe von bcp (SQL Server) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abb451611f7e102e9167561ef2c3a4b64e00fb12
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011842"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a>Angeben der Feldlänge mithilfe von bcp (SQL Server)
  Die Feldlänge weist auf die maximale Anzahl von Zeichen hin, die zum Darstellen der Daten im Zeichenformat benötigt werden. Die Feldlänge ist bereits bekannt, wenn die Daten im systemeigenen Format gespeichert werden (z. B. der `int`-Datentyp, der 4 Bytes benötigt). Wenn Sie für die Präfix Länge 0 angegeben haben, werden Sie vom **bcp** -Befehl zur Eingabe der Feldlänge, der Standardfeld Längen und der Auswirkung der Feldlänge auf die Datenspeicherung in Daten `char` Dateien aufgefordert, die Daten enthalten.  
  
## <a name="the-bcp-prompt-for-field-length"></a>Die bcp-Eingabeaufforderung für die Feldlänge  
 Wenn ein interaktiver **bcp**-Befehl die Option **in** oder **out**, jedoch keinen Formatdateischalter ( **-f**) bzw. keinen Datenformatschalter ( **-n**, **-c**, **-w** oder **-N**) enthält, fordert der Befehl wie folgt zur Eingabe der Feldlänge für jedes Datenfeld auf:  
  
 `Enter length of field <field_name> [<default>]:`  
  
 Ein Beispiel, das die Verwendung der Aufforderung im Kontext veranschaulicht, finden Sie unter [ Angeben von Datenformaten für die Kompatibilität bei Verwendung von „bcp“ &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).  
  
> [!NOTE]  
>  Nachdem Sie interaktiv alle Felder in einem **bcp**-Befehl angegeben haben, werden Sie vom Befehl dazu aufgefordert, Ihre Antworten für die einzelnen Felder in einer Nicht-XML-Formatdatei zu speichern. Weitere Informationen zu Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
 Ob Sie vom **bcp** -Befehl zur Eingabe der Feldlänge aufgefordert werden, hängt von verschiedenen Faktoren ab, die im Folgenden aufgeführt werden:  
  
-   Wenn Sie Datentypen ohne feste Länge kopieren und eine Präfixlänge von 0 angeben, werden Sie von **bcp** zur Eingabe einer Feldlänge aufgefordert.  
  
-   Wenn **bcp** Daten, die nicht auf Zeichen basieren, in Zeichen konvertiert, schlägt das Hilfsprogramm eine Standardfeldlänge vor, die groß genug zum Speichern der Daten ist.  
  
-   Wenn der Dateispeichertyp Daten enthält, die nicht auf Zeichen basieren, fordert **bcp** nicht zur Eingabe einer Feldlänge auf. Die Daten werden in der nativen Datendarstellung (natives Format) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert.  
  
## <a name="using-default-field-lengths"></a>Verwenden der Standardfeldlängen  
 Im Allgemeinen empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , dass Sie die von **bcp**für die Feldlänge vorgeschlagenen Standardwerte übernehmen. Wenn Sie beim Erstellen einer Datendatei im Zeichenmodus die Standardfeldlänge verwenden, können Sie sicherstellen, dass die Daten nicht abgeschnitten werden und auch keine numerischen Überlauffehler auftreten.  
  
 Die Angabe falscher Feldlängen kann zu Problemen führen. Wenn Sie beispielsweise numerische Daten kopieren und eine Feldlänge angeben, die für die Daten nicht ausreicht, druckt das Hilfsprogramm **bcp** eine Überlaufmeldung und kopiert die Daten nicht. Wenn Sie Daten exportieren `datetime` und für die Zeichenfolge eine Feldlänge von weniger als 26 Bytes angeben, werden die Daten vom Hilfsprogramm **bcp** ohne Fehlermeldung abgeschnitten.  
  
> [!IMPORTANT]  
>  Bei Verwendung der Standardgrößenoption wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine vollständige Zeichenfolge erwartet. In bestimmten Situationen kann die Verwendung der Standardfeldlänge zu einem Fehler des Typs "unerwartetes Dateiende" führen. Dieser Fehler tritt in der Regel mit `money` den `datetime` Datentypen und auf, wenn nur ein Teil des erwarteten Felds in der Datendatei vorkommt. Wenn z. b. `datetime` ein Wert von *mm*/*DD*/*yy* ohne die Zeitkomponente angegeben wird und daher kürzer ist als die erwartete 24-Zeichen-Länge eines `datetime` Werts im `char` -Format. Zur Vermeidung dieses Fehlertyps sollten Sie Feldabschlusszeichen oder Datenfelder mit fester Länge verwenden oder die Standardfeldlänge auf einen anderen Wert ändern.  
  
### <a name="default-field-lengths-for-character-file-storage"></a>Standardfeldlänge zum Speichern von Dateien im Zeichenformat  
 In der folgenden Tabelle werden die Standardfeldlängen für Daten aufgeführt, die als Dateien im Zeichenformat gespeichert werden. Daten, die NULL zulassen, besitzen die gleiche Länge wie Daten ohne NULL-Werte.  
  
|Datentyp|Standardlänge (Zeichen)|  
|---------------|-----------------------------------|  
|`char`|Für die Spalte definierte Länge|  
|`varchar`|Für die Spalte definierte Länge|  
|`nchar`|Zweifaches der für die Spalte definierten Länge|  
|`nvarchar`|Zweifaches der für die Spalte definierten Länge|  
|`Text`|0|  
|`ntext`|0|  
|`bit`|1|  
|`binary`|Das Doppelte der für die Spalte definierten Länge + 1|  
|`varbinary`|Das Doppelte der für die Spalte definierten Länge + 1|  
|`image`|0|  
|`datetime`|24|  
|`smalldatetime`|24|  
|`float`|30|  
|`real`|30|  
|`int`|12|  
|`bigint`|19|  
|`smallint`|7|  
|`tinyint`|5|  
|`money`|30|  
|`smallmoney`|30|  
|`decimal`|41*|  
|`numeric`|41*|  
|`uniqueidentifier`|37|  
|`timestamp`|17|  
|`varchar(max)`|0|  
|`varbinary(max)`|0|  
|`nvarchar(max)`|0|  
|UDT|Länge der UDT-Spalte (User-defined Term)|  
|XML|0|  
  
 \*Weitere Informationen zu den `decimal` Datentypen `numeric` und finden Sie unter [Decimal und numeric &#40;Transact-SQL-&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
> [!NOTE]  
>  Eine Spalte des Typs `tinyint` kann Werte von 0 bis 255 aufweisen. Zum Darstellen einer beliebigen Zahl in diesem Bereich werden maximal drei Zeichen (bei den Werten von 100 bis 255) benötigt.  
  
### <a name="default-field-lengths-for-native-file-storage"></a>Standardfeldlänge zum Speichern systemeigener Dateien  
 In der folgenden Tabelle werden die Standardfeldlängen für Daten aufgeführt, die als Dateien im systemeigenen Format gespeichert werden. Daten, die NULL zulassen, weisen die gleiche Länge auf wie Daten ohne NULL-Werte. Zeichendaten werden immer im Zeichenformat gespeichert.  
  
|Datentyp|Standardlänge (Zeichen)|  
|---------------|-----------------------------------|  
|`bit`|1|  
|`binary`|Für die Spalte definierte Länge|  
|`varbinary`|Für die Spalte definierte Länge|  
|`image`|0|  
|`datetime`|8|  
|`smalldatetime`|4|  
|`float`|8|  
|`real`|4|  
|`int`|4|  
|`bigint`|8|  
|`smallint`|2|  
|`tinyint`|1|  
|`money`|8|  
|`smallmoney`|4|  
|`decimal`<sup>1</sup>|<sup>*</sup>|  
|`numeric`<sup>1</sup>|<sup>*</sup>|  
|`uniqueidentifier`|16|  
|`timestamp`|8|  
  
 <sup>1</sup> Weitere Informationen zu den `decimal` Datentypen `numeric` und finden Sie unter [Decimal und numeric &#40;Transact-SQL-&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).  
  
 Wenn Sie eine Datendatei erstellen, die später erneut in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen werden soll, und dabei den Speicherplatz auf ein Minimum begrenzen möchten, sollten Sie ein Längenpräfix mit dem Standard-Dateispeichertyp und der Standardfeldlänge verwenden. Dies gilt für jeden der vorangegangenen Fälle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Angeben der Präfixlänge in Datendateien mittels bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)   
 [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)   
 [Beibehalten von NULL-Werten oder Verwenden von Standardwerten während des Massenimports &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
