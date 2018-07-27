﻿---
title: Invoke-CsStorageServiceFlush
TOCTitle: Invoke-CsStorageServiceFlush
ms:assetid: 3f88a70d-79b0-4614-8604-660bac35a86f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619175(v=OCS.15)
ms:contentKeyID: 49733622
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Invoke-CsStorageServiceFlush

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Flushes the Lync Server Storage Service database on each Front End server in a pool. Flushing a database involves writing all the queued data to disk, and then clearing the database queue. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Invoke-CsStorageServiceFlush -FlushType <FullFlush | SteadyStateFlush> -PoolFqdn <Fqdn> [-Binding <String>] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-WaitTime <TimeSpan>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 performs a “steady state” flush of the Storage Service databases found on the pool atl-cs-011.litwareinc.com. In a steady state flush, the only data removed from the queue (and written to disk) is data that can be removed without affecting the database operation.

    Invoke-CsStorageServiceFlush -PoolFqdn "atl-cs-001.litwareinc.com" -FlushType "SteadyState"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Lync Server Storage Service provides a common interface and infrastructure for managing Lync Server data, including session data for monitoring, archiving, and conversation history, as well as for integrating with the Microsoft Exchange Server 2013 storage system. Like other databases, the Storage Service caches data in memory and then, as system resources permit, periodically writes that data to disk.

As a general rule, administrators do not have to interact with this queued data. However, there could be times when the queue becomes too large or because the Registrar pool associated with the database is being failed over. In cases like that, the **Invoke-CsStorageServiceFlush** cmdlet can be called in order to write all the queued data to disk and then clear the database cache.

The **Invoke-CsStorageServiceFlush** cmdlet is also useful when multiple Front End servers must be shut down at the same time (for example, in order to do a software upgrade). As a general rule, Front End servers in a pool should be shut down, and restarted, one-by-one; that helps prevent data loss that could occur due to routing group rebalancing. However, there might be occasions when you need to shutdown multiple servers at the same time. To help guard against potential loss, you can run the **Invoke-CsStorageServiceFlush** cmdlet before doing the computer shutdowns. This will flush the queue for the pool and write all that data to disk before any of the servers are actually shut down.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsStorageServiceFlush"}

**Lync Server Control Panel:** The functions carried out by the **Invoke-CsStorageServiceFlush** cmdlet are not available in the Lync Server Control Panel.

</div>

<div>

## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>FlushType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.FlushType</p></td>
<td><p>Specifies the type of storage flush to be performed. Allowed values are:</p>
<p>* SteadyState – The only data that will be flushed is data that can be removed from the queue without affecting normal operations of the storage service. This is typically done to remove older data from the queue.</p>
<p>* FullFlush – Flushes all the data from the queue. This is typically used when a pool is being failed over, and when there is no expectation that the queue will be receiving any new data.</p></td>
</tr>
<tr class="even">
<td><p><em>PoolFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the pool containing the storage service to be flushed.</p></td>
</tr>
<tr class="odd">
<td><p><em>Binding</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Windows Communication Foundation (WCF) binding. A WCF binding determines the transport, encoding, and protocol details required for clients and services to communicate with each other. valid values are:</p>
<p>* NetNamedPipe</p>
<p>* NetTCP</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostNameStorageService</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of the server where the Lync Server Storage Service is running. This parameter is required if the Binding is set to NetTCP.</p></td>
</tr>
<tr class="even">
<td><p><em>WaitTime</em></p></td>
<td><p>Optional</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>Specifies the maximum amount of time the cmdlet will wait before assuming that flushing has begun and moving on to the next step in the flushing process.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Invoke-CsStorageServiceFlush** cmdlet does not accept pipelined data.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

String value.

</div>

<div>

## See Also


[Invoke-CsPoolFailOver](invoke-cspoolfailover.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

