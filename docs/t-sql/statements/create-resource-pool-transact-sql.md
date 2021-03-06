---
title: CREATE RESOURCE POOL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE RESOURCE POOL
- RESOURCE POOL
- CREATE_RESOURCE_POOL_TSQL
- RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE RESOURCE POOL
ms.assetid: 82712505-c6f9-4a65-a469-f029b5a2d6cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d2c0278199684db2355d76c624ed6349e8aefda
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633958"
---
# <a name="create-resource-pool-transact-sql"></a>CREATE RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Erstellt einen Ressourcenpool für die Ressourcenkontrolle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ein Ressourcenpool stellt eine Teilmenge der physischen Ressourcen (Arbeitsspeicher, CPUs und E/A) einer Instanz der Datenbank-Engine dar. Mit der Ressourcenkontrolle kann ein Datenbankadministrator Serverressourcen auf Ressourcenpools verteilen, bis zu maximal 64 Pools. Die Ressourcenkontrolle ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
```syntaxsql
CREATE RESOURCE POOL pool_name  
[ WITH  
    (  
        [ MIN_CPU_PERCENT = value ]  
        [ [ , ] MAX_CPU_PERCENT = value ]   
        [ [ , ] CAP_CPU_PERCENT = value ]   
        [ [ , ] AFFINITY {SCHEDULER =  
                  AUTO 
                | ( <scheduler_range_spec> )   
                | NUMANODE = ( <NUMA_node_range_spec> )
                } ]   
        [ [ , ] MIN_MEMORY_PERCENT = value ]  
        [ [ , ] MAX_MEMORY_PERCENT = value ]  
        [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
        [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
    )   
]  
[;]  
  
<scheduler_range_spec> ::=  
{ SCHED_ID | SCHED_ID TO SCHED_ID }[,...n]  
  
<NUMA_node_range_spec> ::=  
{ NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID }[,...n]  
```  
  
## <a name="arguments"></a>Argumente  
*pool_name*  
Der benutzerdefinierte Name für den Ressourcenpool. *pool_name* ist alphanumerisch, kann bis zu 128 Zeichen enthalten, muss innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig sein und muss den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) entsprechen.  
  
MIN_CPU_PERCENT =*value*  
Gibt die garantierte durchschnittliche CPU-Bandbreite für alle Anforderungen im Ressourcenpool an, wenn CPU-Konflikte bestehen. *value* ist eine ganze Zahl mit dem Standardwert 0. Der zulässige Bereich für *value* liegt zwischen 0 und 100.  
  
MAX_CPU_PERCENT = *value*  
Gibt die maximale durchschnittliche CPU-Bandbreite an, die allen Anforderungen im Ressourcenpool zugewiesen wird, wenn CPU-Konflikte bestehen. *value* ist eine ganze Zahl mit dem Standardwert 100. Der zulässige Bereich für *value* liegt zwischen 1 und 100.  
  
CAP_CPU_PERCENT =*value*   
**Gilt für**:  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.  
  
Legt eine feste Obergrenze für die CPU-Bandbreite fest, die für alle Anforderungen im Ressourcenpool gilt. Beschränkt die maximale CPU-Bandbreitenstufe auf den angegebenen Wert. *value* ist eine ganze Zahl mit dem Standardwert 100. Der zulässige Bereich für *value* liegt zwischen 1 und 100.  
  
AFFINITY {SCHEDULER = AUTO | ( \<scheduler_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)}      
**Gilt für**:  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.  
  
Fügt den Ressourcenpool an bestimmte Zeitplanungsmodule an. Der Standardwert ist AUTO.  
  
AFFINITY SCHEDULER = **(** \<scheduler_range_spec> **)** ordnet den Ressourcenpool den von den angegebenen IDs identifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeitplänen zu. Den Werten in der scheduler_id-Spalte in [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md) werden diese IDs zugeordnet. 
  
Wenn Sie AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** verwenden, wird der Ressourcenpool den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeitplanungsmodulen zugeordnet, die wiederum den physischen CPUs zugeordnet werden, die dem angegebenen NUMA-Knoten oder dem Bereich von Knoten entsprechen. Sie können die Zuordnung zwischen der physischen NUMA-Konfiguration und den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Zeitplanungsmodul-IDs mithilfe der folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrage ermitteln. 
  
```sql  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc   
    ON osn.node_id = sc.parent_node_id   
    AND sc.scheduler_id < 1048576;  
```  
  
MIN_MEMORY_PERCENT =*value*    
Gibt den Mindestarbeitsspeicher an, der für diesen Ressourcenpool reserviert ist und nicht gemeinsam mit anderen Ressourcenpools verwendet werden kann. *value* ist eine ganze Zahl mit dem Standardwert 0. Der zulässige Bereich für *value* liegt zwischen 0 und 100.  
  
MAX_MEMORY_PERCENT =*value*    
Gibt den gesamten Serverspeicher an, der für Anforderungen in diesem Ressourcenpool verwendet werden kann. *value* ist eine ganze Zahl mit dem Standardwert 100. Der zulässige Bereich für *value* liegt zwischen 1 und 100.  
  
MIN_IOPS_PER_VOLUME =*value*    
**Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.  
  
Gibt die minimalen E/A-Vorgänge pro Sekunde (IOPS) pro Datenträgervolume an, die für den Ressourcenpool reserviert werden sollen. Der zulässige Bereich für *value* liegt zwischen 0 und 2^31-1 (2.147.483.647). 0 gibt an, dass kein minimaler Schwellenwert für den Pool gilt. Die Standardeinstellung ist 0.  
  
MAX_IOPS_PER_VOLUME =*value*    
**Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.  
  
Gibt die maximalen E/A-Vorgänge pro Sekunde (IOPS) pro Datenträgervolume an, die für den Ressourcenpool zulässig sein sollen. Der zulässige Bereich für *value* liegt zwischen 0 und 2^31-1 (2.147.483.647). 0 gibt einen unbegrenzten Schwellenwert für den Pool an. Die Standardeinstellung ist 0.  
  
Wenn `MAX_IOPS_PER_VOLUME` für einen Pool auf den Wert 0 festgelegt ist, wird der Pool überhaupt nicht kontrolliert und kann alle IOPS im System annehmen, selbst wenn für andere Pools MIN_IOPS_PER_VOLUME festgelegt ist. Für diesen Fall wird empfohlen, dass Sie den `MAX_IOPS_PER_VOLUME`-Wert für diesen Pool auf eine höhere Zahl festlegen (z. B. auf den Maximalwert 2^31-1), wenn E/A-Vorgänge für diesen Pool kontrolliert werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
`MIN_IOPS_PER_VOLUME` und `MAX_IOPS_PER_VOLUME` geben das Minimum und das Maximum für Lese- und Schreibvorgänge pro Sekunde an. Die Lese- und Schreibvorgänge können eine beliebige Größe haben und geben daher keinen Aufschluss über den minimalen bzw. maximalen Durchsatz.  
  
Die Werte für `MAX_CPU_PERCENT` und `MAX_MEMORY_PERCENT` müssen größer als oder gleich den Werten für `MIN_CPU_PERCENT` bzw. `MIN_MEMORY_PERCENT` sein.  
  
`CAP_CPU_PERCENT` unterscheidet sich von `MAX_CPU_PERCENT` dahingehend, dass die dem Pool zugeordneten Workloads eine CPU-Kapazität nutzen können, die den Wert von `MAX_CPU_PERCENT`, falls vorhanden, übersteigt, aber nicht über den Wert von `CAP_CPU_PERCENT` hinausgeht.  
  
Der gesamte CPU-Prozentsatz für jede zugeordnete Komponente (Zeitplanungsmodul(e) oder NUMA-Knoten) darf 100 % nicht überschreiten.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die `CONTROL SERVER`-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
### <a name="1-shows-how-to-create-a-resource-pool"></a>1. Zeigt, wie Sie einen Ressourcenpool erstellen

In diesem Beispiel wurde ein Ressourcenpool namens „bigPool“ erstellt. Dieser Pool verwendet die Standardeinstellungen der Ressourcenkontrolle.  
  
```sql  
CREATE RESOURCE POOL bigPool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
### <a name="2-set-the-cap_cpu_percent-to-a-hard-cap-and-set-affinity-scheduler"></a>2. CAP_CPU_PERCENT auf eine feste Obergrenze festlegen und AFFINITY SCHEDULER festlegen

Legen Sie die CAP_CPU_PERCENT auf eine feste Obergrenze von 30 % fest, und legen Sie AFFINITY SCHEDULER auf einen Bereich von 0 bis 63, 128 bis 191 fest. 
  
**Gilt für**:  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.  
  
```sql  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
     MIN_CPU_PERCENT = 10,  
     MAX_CPU_PERCENT = 20,  
     CAP_CPU_PERCENT = 30,  
     AFFINITY SCHEDULER = (0 TO 63, 128 TO 191),  
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
      );  
```  
  
### <a name="3-set-min_iops_per_volume-and-max_iops_per_volume"></a>3. MIN_IOPS_PER_VOLUME und MAX_IOPS_PER_VOLUME festlegen   

Legen Sie MIN_IOPS_PER_VOLUME auf 20 und MAX_IOPS_PER_VOLUME auf 100 fest. Diese Werte bestimmen die physischen E/A-Lese- und Schreibvorgänge, die für den Ressourcenpool verfügbar sind.  
  
**Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.  
  
```sql  
CREATE RESOURCE POOL PoolAdmin  
WITH (  
    MIN_IOPS_PER_VOLUME = 20,  
    MAX_IOPS_PER_VOLUME = 100  
      );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)     
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)     
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)     
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)     
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)     
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)     
 [Ressourcenpool für die Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)     
 [Erstellen eines Ressourcenpools](../../relational-databases/resource-governor/create-a-resource-pool.md)    
  
