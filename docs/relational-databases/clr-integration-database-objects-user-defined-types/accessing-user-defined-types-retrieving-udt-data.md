---
title: Abrufen von UDT-Daten | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie auf UDTs in einer SQL Server Datenbank zugreifen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d14c6d24d6db5d27b12bcc3f28c1b6ba383442
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488221"
---
# <a name="accessing-user-defined-types---retrieving-udt-data"></a>Zugreifen auf benutzerdefinierte Typen: Abrufen von UDT-Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Zum Erstellen eines benutzerdefinierten Typs (User-Defined Type, UDT) auf dem Client muss die zuvor in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank als UDT registrierte Assembly für die Clientanwendung verfügbar sein. Die UDT-Assembly kann in dasselbe Verzeichnis gelegt werden wie die Anwendung oder in den globalen Assemblycache (GAC). Sie können auch in Ihrem Projekt einen Verweis auf die Assembly festlegen.  
  
## <a name="requirements-for-using-udts-in-adonet"></a>Anforderungen zum Verwenden von UDTs in ADO.NET  
 Die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladene Assembly und die Assembly auf dem Client müssen kompatibel sein, damit der UDT auf dem Client erstellt werden kann. Für UDTs **, die mit dem System** eigenen Serialisierungsformat definiert sind, müssen die Assemblys strukturell kompatibel sein. Bei Assemblys, die mit dem **benutzerdefinierten** Format definiert sind, muss die Assembly auf dem Client verfügbar sein.  
  
 Sie brauchen keine Kopie der UDT-Assembly auf dem Client, um die Rohdaten aus einer UDT-Spalte einer Tabelle abzurufen.  
  
> [!NOTE]  
>  **SqlClient** kann beim Laden eines UDTs im Fall von nicht übereinstimmenden UDT-Versionen oder anderen Problemen einen UDT möglicherweise nicht laden. Wenden Sie in diesem Fall die üblichen Maßnahmen zur Problembehandlung an, um zu ermitteln, aus welchem Grund die Assembly, die den UDT enthält, nicht von der aufrufenden Anwendung gefunden werden kann. Weitere Informationen finden Sie im Thema "Diagnostizieren von Fehlern mit Assistenten für verwaltetes Debuggen" in der .NET Framework-Dokumentation.  
  
## <a name="accessing-udts-with-a-sqldatareader"></a>UDT-Zugriff über SqlDataReader  
 Ein **System. Data. SqlClient. SqlDataReader** -Objekt kann im Client Code verwendet werden, um ein Resultset abzurufen, das eine UDT-Spalte enthält, die als Instanz des-Objekts verfügbar gemacht wird.  
  
### <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie die **Main** -Methode zum Erstellen eines neuen **SqlDataReader** -Objekts verwendet wird. In diesem Codebeispiel werden die folgenden Aktionen ausgeführt:  
  
1.  Die Main-Methode erstellt ein neues **SqlDataReader** -Objekt und ruft die Werte aus der Points-Tabelle ab, die über eine UDT-Spalte mit dem Namen "Point" verfügt.  
  
2.  Der Point-UDT macht die als ganze Zahlen definierten X- und Y-Koordinaten verfügbar.  
  
3.  Der UDT definiert eine **Entfernungs** Methode und eine **GetDistanceFromXY** -Methode.  
  
4.  Der Beispielcode ruft die Werte des Primärschlüssels und der UDT-Spalten ab, um die Möglichkeiten des UDT darzustellen.  
  
5.  Der Beispielcode ruft die Methoden **Point. Distance** und **Point. GetDistanceFromXY** auf.  
  
6.  Die Ergebnisse werden im Konsolenfenster angezeigt.  
  
> [!NOTE]  
>  Die Anwendung muss bereits einen Verweis auf die UDT-Assembly aufweisen.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a>Bindung von UDTs als Bytes  
 In bestimmten Situationen bietet es sich an, Rohdaten aus der UDT-Spalte abzurufen. Möglicherweise ist der Typ lokal nicht verfügbar, oder Sie möchten keine Instanz des UDT instanziieren. Sie können die Rohbytes in ein Bytearray lesen, indem Sie die **GetBytes** -Methode von **SqlDataReader**verwenden. Diese Methode liest, beginnend am angegeben Pufferoffset, einen Datenstrom von Bytes aus dem angegebenen Spaltenoffset in den Puffer eines Arrays. Eine andere Möglichkeit besteht darin, eine der **GetSqlBytes** -oder **GetSqlBinary** -Methoden zu verwenden und den gesamten Inhalt in einem einzelnen Vorgang zu lesen. In keinem der beiden Fälle wird das UDT-Objekt instanziiert. Daher brauchen Sie in der Client-Assembly keinen Verweis auf den UDT festzulegen.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie die **Punkt** Daten als Rohdaten Bytes mithilfe von **SqlDataReader**als Rohdaten Bytes in ein Bytearray abgerufen werden. Der Code verwendet einen **System. Text. StringBuilder** , um die Rohdaten Bytes in eine Zeichen folgen Darstellung zu konvertieren, die im Konsolenfenster angezeigt werden soll.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a>Beispiel: Verwenden von GetSqlBytes  
 In diesem Beispiel wird gezeigt, wie die **Punkt** Daten als Rohdaten Bytes in einem einzelnen Vorgang mithilfe der **gezqlbytes** -Methode abgerufen werden. Im Code wird ein **StringBuilder** -Zeichen verwendet, um die Rohdaten Bytes in eine Zeichen folgen Darstellung zu konvertieren, die im Konsolenfenster angezeigt werden soll.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a>Arbeiten mit UDT-Parametern  
 UDTs können im ADO.NET-Code sowohl als Eingabe- als auch als Ausgabeparameter verwendet werden.  
  
## <a name="using-udts-in-query-parameters"></a>Verwenden von UDTs in Abfrageparametern  
 UDTs können beim Einrichten eines **SqlParameter** -Objekts für ein **System. Data. SqlClient. SqlCommand** -Objekt als Parameterwerte verwendet werden. Die **SqlDbType. UDT** -Enumeration eines **SqlParameter** -Objekts wird verwendet, um anzugeben, dass der-Parameter ein UDT ist, wenn die **Add** -Methode für die **Parameter** Auflistung aufgerufen wird. Die **udttypame** -Eigenschaft eines **SqlCommand** -Objekts wird verwendet, um den voll qualifizierten Namen des UDT in der Datenbank mithilfe der *Database. schema_name. object_name* -Syntax anzugeben. Die Angabe des vollqualifizierten Namens ist zwar nicht erforderlich, macht den Code jedoch klarer.  
  
> [!NOTE]  
>  Eine lokale Kopie der UDT-Assembly muss dem Clientprojekt zur Verfügung stehen.  
  
### <a name="example"></a>Beispiel  
 Der Code in diesem Beispiel erstellt die Objekte **SqlCommand** und **SqlParameter** , um Daten in eine UDT-Spalte in einer Tabelle einzufügen. Der Code verwendet die **SqlDbType. UDT** -Enumeration, um den Datentyp anzugeben, und die **udttykname** -Eigenschaft des **SqlParameter** -Objekts, um den voll qualifizierten Namen des UDT in der Datenbank anzugeben.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      
      param.UdtTypeName = "TestPoint.dbo.Point"      
      param.Direction = ParameterDirection.Input      
      param.Value = New Point(5, 6)      
      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf benutzerdefinierte Typen in ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
