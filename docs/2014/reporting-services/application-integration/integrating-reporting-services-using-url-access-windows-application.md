---
title: Verwenden des URL-Zugriffs in einer Windows-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb841d187385724ea31b5a7db86fcb323bf10663
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63126238"
---
# <a name="using-url-access-in-a-windows-application"></a>Verwenden des URL-Zugriffs in einer Windows-Anwendung
  Obwohl der URL-Zugriff auf einen Berichtsserver für eine Webumgebung optimiert ist, können Sie mit dem URL-Zugriff auch [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichte in eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendung integrieren. Aber der URL-Zugriff, der auch Windows Forms umfasst, erfordert trotzdem die Verwendung der Webbrowsertechnologie. Sie können folgende Integrationsszenarien mit dem URL-Zugriff und Windows Forms verwenden:  
  
-   Zeigen Sie einen Bericht in einer Windows Forms-Anwendung an, indem Sie einen Webbrowser programmgesteuert starten.  
  
-   Verwenden Sie das <xref:System.Windows.Forms.WebBrowser>-Steuerelement auf einer Windows Form, um einen Bericht anzuzeigen.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Starten von Internet Explorer von einer Windows Form  
 Sie können über die <xref:System.Diagnostics.Process>-Klasse auf einen Prozess zugreifen, der auf einem Computer ausgeführt wird. Die <xref:System.Diagnostics.Process> -Klasse ist ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] nützliches Konstrukt zum Starten, beenden, Steuern und Überwachen von Anwendungen. Um einen bestimmten Bericht in der Berichtsserver-Datenbank anzuzeigen, können Sie den Prozess **IExplore** starten, indem Sie die URL an den Bericht übergeben. Folgendes Codebeispiel kann verwendet werden, um [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer zu starten und eine spezielle URL zu übergeben, wenn ein Benutzer auf eine Schaltfläche in einer Windows Form klickt.  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Integrieren eines Browsersteuerelements auf einer Windows Form  
 Wenn Sie den Bericht nicht in einem externen Webbrowser anzeigen möchten, können Sie einen Webbrowser nahtlos als Teil der Windows Form integrieren, indem Sie das <xref:System.Windows.Forms.WebBrowser>-Steuerelement verwenden.  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>So fügen Sie der Windows Form das Webbrowser-Steuerelement hinzu  
  
1.  Erstellen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Sie entweder in oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]in eine neue Windows-Anwendung.  
  
2.  Suchen Sie im Dialogfeld **Toolbox** das <xref:System.Windows.Forms.WebBrowser>-Steuerelement.  
  
     Wenn **Toolbox** nicht sichtbar ist, können Sie darauf zugreifen, indem Sie im Menüelement **Ansicht** auf **Toolbox** klicken.  
  
3.  Ziehen Sie das <xref:System.Windows.Forms.WebBrowser>-Steuerelement auf die Entwurfsoberfläche des Windows Form.  
  
     Das als webBrowser1 bezeichnete <xref:System.Windows.Forms.WebBrowser>-Steuerelement wird zum Formular hinzugefügt.  
  
 Sie leiten das <xref:System.Windows.Forms.WebBrowser>-Steuerelement an eine URL weiter, indem Sie seine **Navigate**-Methode aufrufen. Sie können dem <xref:System.Windows.Forms.WebBrowser>-Steuerelement zur Laufzeit eine bestimmte URL-Zugriffszeichenfolge zuordnen, wie in folgendem Beispiel gezeigt.  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integrieren von Reporting Services in Anwendungen](../application-integration/integrating-reporting-services-into-applications.md)   
 [Integrieren von Reporting Services mithilfe des URL-Zugriffs](integrating-reporting-services-using-url-access.md)   
 [Integrieren von Reporting Services mithilfe von SOAP](integrating-reporting-services-using-soap.md)   
 [Integrieren von Reporting Services mithilfe der Report Viewer-Steuerelemente](integrating-reporting-services-using-reportviewer-controls.md)   
 [URL-Zugriff &#40;SSRS&#41;](../url-access-ssrs.md)  
  
  
