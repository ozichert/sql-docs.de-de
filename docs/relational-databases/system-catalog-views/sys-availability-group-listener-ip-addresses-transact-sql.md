---
title: sys. availability_group_listener_ip_addresses (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listener_ip_addresses
- sys.availability_group_listener_ip_addresses
- availability_group_listener_ip_addresses_TSQL
- sys.availability_group_listener_ip_addresses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.availability_group_listener_ip_addresses catalog view
ms.assetid: e515fa6b-1354-4110-9b70-ab2e6164c992
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 49f7322dc32634631a991d76bab58394a26c491e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829126"
---
# <a name="sysavailability_group_listener_ip_addresses-transact-sql"></a>sys.availability_group_listener_ip_addresses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede IP-Adresse zurück, die einem beliebigen Always On-Verfügbarkeitsgruppenlistener im WSFC-Cluster (Windows Server-Failoverclustering) zugeordnet ist.  
  
 Primärschlüssel: **listener_id**  +  **ip_address**  +  **ip_sub_mask**  
  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**listener_id**|**nvarchar (36)**|Ressourcen-GUID des WSFC-Clusters (Windows Server-Failoverclustering).|  
|**ip_address**|**nvarchar (48)**|Konfigurierte virtuelle IP-Adresse des Verfügbarkeitsgruppenlisteners. Gibt eine einzelne IPv4- oder IPv6-Adresse zurück.|  
|**ip_subnet_mask**|**nvarchar (15)**|Konfigurierte IP-Subnetzmaske für die IPv4-Adresse, falls vorhanden, die für den Verfügbarkeitsgruppenlistener konfiguriert ist.<br /><br /> NULL = IPv6-Subnetz|  
|**is_dhcp**|**bit**|Gibt an, ob die IP-Adresse von DHCP konfiguriert wird. Folgende Werte sind möglich:<br /><br /> 0 = IP-Adresse wird nicht von DHCP konfiguriert.<br /><br /> 1 = IP-Adresse wird von DHCP konfiguriert.|  
|**network_subnet_ip**|**nvarchar (48)**|Die Netzwerksubnetz-IP-Adresse, die das Subnetz angibt, zu dem die IP-Adresse gehört.|  
|**network_subnet_prefix_length**|**int**|Die Netzwerksubnetz-Präfixlänge des Subnetzes, zu der die IP-Adresse gehört.|  
|**network_subnet_ipv4_mask**|**nvarchar (45)**|Die Netzwerksubnetz-Maske des Subnetzes, zu der die IP-Adresse gehört. **network_subnet_ipv4_mask** , um die DHCP-<network_subnet_option> Optionen in einer With DHCP-Klausel der [Create Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) -oder [Alter Availability Group](../../t-sql/statements/alter-availability-group-transact-sql.md) - [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung anzugeben.<br /><br /> NULL = IPv6-Subnetz|  
|**state**|**tinyint**|Der IP-Ressourcen-ONLINE/OFFLINE-Status aus dem WSFC-Cluster. Folgende Werte sind möglich:<br /><br /> 1 = Online. Die IP-Ressource ist online.<br /><br /> 0 = Offline Die IP-Ressource ist offline.<br /><br /> 2 = Online ausstehend Die IP-Ressource ist offline, wird aber online geschaltet.<br /><br /> 3 = fehlgeschlagen. Die IP-Ressource wurde online geschaltet, aber ein Fehler ist aufgetreten.|  
|**state_desc**|**nvarchar(60)**|Beschreibung des **Zustands**, eine der folgenden:<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> ONLINE_PENDING<br /><br /> FAILED|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
