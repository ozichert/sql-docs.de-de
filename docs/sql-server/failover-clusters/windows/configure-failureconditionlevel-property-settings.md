---
title: Konfigurieren von FailureConditionLevel-Eigenschafteneinstellungen
describes: 'Use the FailureConditionLevel property to set the conditions for the Always On Failover Cluster Instance (FCI) to fail over or restart. '
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be3b4fee27dccddc3ae3dc2d240304014a698af5
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925108"
---
# <a name="configure-failureconditionlevel-property-settings"></a>Konfigurieren von FailureConditionLevel-Eigenschafteneinstellungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit der FailureConditionLevel-Eigenschaft können Sie die Bedingungen für einen Failover oder Neustart der Always On-Failoverclusterinstanz (FCI) festlegen. Änderungen an dieser Eigenschaft werden unmittelbar übernommen, ohne dass ein Neustart des Windows Server-Failoverclusterdiensts (WSFC) oder der FCI-Ressource erforderlich ist.  
  
-   **Vorbereitungen:**  [FailureConditionLevel-Eigenschafteneinstellungen](#Restrictions), [Sicherheit](#Security)  
  
-   **So konfigurieren Sie die FailureConditionLevel-Eigenschafteneinstellungen mithilfe von** [PowerShell](#PowerShellProcedure), dem [Failovercluster-Manager](#WSFC) und [Transact-SQL](#TsqlProcedure).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> FailureConditionLevel-Eigenschafteneinstellungen  
 Die Fehlerbedingungen werden auf einer ansteigenden Skala festgelegt. Auf der Ebene 1-5 enthält jede Ebene die Bedingungen der vorherigen Ebenen sowie die eigenen Bedingungen. Dies bedeutet, dass die Wahrscheinlichkeit eines Failovers oder Neustarts mit jeder Ebene zunimmt.  Weitere Informationen finden Sie im Abschnitt "Bestimmen von Fehlern" des Themas [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) .  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert ALTER SETTINGS- und VIEW SERVER STATE-Berechtigungen.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell  
  
##### <a name="to-configure-failureconditionlevel-settings"></a>So konfigurieren Sie die FailureConditionLevel-Einstellungen  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das **FailoverClusters** -Modul, um die Cluster-Cmdlets zu aktivieren.  
  
3.  Verwenden Sie das **Get-ClusterResource** -Cmdlet, um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource zu suchen, und verwenden Sie dann das **Set-ClusterParameter** -Cmdlet, um die **FailureConditionLevel** -Eigenschaft für eine Failoverclusterinstanz festzulegen.  
  
> [!TIP]  
>  Bei jedem Öffnen eines neuen PowerShell-Fensters müssen Sie das **FailoverClusters** -Modul importieren.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird die FailureConditionLevel-Einstellung auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressource "`SQL Server (INST1)`" in "Failover oder Neustart bei wichtigen Serverfehlern" geändert.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3  
  
```  
  
### <a name="related-content-powershell"></a>Verwandte Inhalte (PowerShell)  
  
-   [Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Clustering und hohe Verfügbarkeit) (Failoverclustering und Netzwerklastenausgleichs-Teamblog)  
  
-   [Erste Schritte mit Windows PowerShell auf einem Failovercluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Clusterressourcenbefehle und entsprechende Windows PowerShell-Cmdlets](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Verwenden des Failovercluster-Manager-Snap-Ins  
 **So konfigurieren Sie FailureConditionLevel-Eigenschafteneinstellungen:**  
  
1.  Öffnen Sie des Failovercluster-Manager-Snap-In.  
  
2.  Erweitern Sie **Dienste und Anwendungen** , und wählen Sie den FCI aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die **SQL Server-Ressource** unter **Sonstige Ressourcen**, und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften** der SQL Server-Ressource wird angezeigt.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus, geben Sie den gewünschten Wert für die **FailureConditionLevel** -Eigenschaft ein, und klicken Sie dann auf **OK** , um die Änderung zu übernehmen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So konfigurieren Sie FailureConditionLevel-Eigenschafteneinstellungen:**  
  
 Mit der Anweisung [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] können Sie den FailureConditionLevel-Eigenschaftswert angeben.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die FailureConditionLevel-Eigenschaft auf 0 gesetzt. Dadurch wird angegeben, dass bei einer Fehlerbedingung nicht automatisch ein Failover oder Neustart ausgelöst wird.  
  
```  
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)   
 [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
