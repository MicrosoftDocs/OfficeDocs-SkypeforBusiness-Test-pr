﻿---
title: Invoke-CsQoEDatabasePurge
TOCTitle: Invoke-CsQoEDatabasePurge
ms:assetid: c4cae63a-b9dd-485b-8d53-2d81d353b7c3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205247(v=OCS.15)
ms:contentKeyID: 48185356
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Invoke-CsQoEDatabasePurge

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Manually purges records from the Quality of Experience (QoE) database. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Invoke-CsQoEDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>

    Invoke-CsQoEDatabasePurge -SqlServerFqdn <String> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -PurgeQoEDataOlderThanDays <Int32> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 purges all the QoE records more than 10 days old from the monitoring database on atl-sql-001.litwareinc.com.

    Invoke-CsQoEDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeQoEDataOlderThanDays 10

</div>

<div>

## Example 2

The command shown in Example 2 is a variation of the command shown in Example 1; in this case, however, the Confirm parameter is added using this syntax:

\-Confirm:$False

That syntax suppresses the confirmation prompts that would otherwise appear when purging QoE records.

    Invoke-CsQoEDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeQoEDataOlderThanDays 10 -Confirm:$False

</div>

<div>

## Example 3

Example 3 purges all the QoE records more than 10 days old from all monitoring QoE databases in use in the organization. To do this, the first command in the example uses the **Get-CsService** cmdlet and the MonitoringDatabase parameter to return a collection of all the monitoring databases. This collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet takes each database in the collection and then runs the **Invoke-CsQoEDatabasePurge** cmdlet against that database, purging all the Quality of Experience records more than 10 days old.

    Get-CsService -MonitoringDatabase | Invoke-CsQoEDatabasePurge -PurgeQoEDataOlderThanDays 10 -Confirm:$False

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.

Quality of Experience records are stored in the SQL Server database LcsQoEMetrics. Over time, this database has the potential to grow extremely large. Because of that, Lync Server provides two ways for administrators to purge older records from the database: 1) you can configure Lync Server to automatically delete older QoE records each day; and/or, 2) you can use the **Invoke-CsQoEDatabasePurge** cmdlet at any time to delete Quality of Experience records from the LcsQoEMetrics database. (The **Invoke-CsQoEDatabasePurge** cmdlet does this by calling the SQL Server stored procedure QoePurgeOutdatedReports.)

When you call the **Invoke-CsQoEDatabasePurge** cmdlet you must specify the service location of the monitoring database where the QoE records are stored (for example, MonitoringDatabase:atl-sql-001.litwareinc.com); you must also indicate the minimum age (in days) of the records to be deleted. For example, if you specify a minimum age of 10 days then all QoE records older than 10 days will be deleted from the database.

Note that these records will be deleted even if the purging has been disabled for the specified database. (That is, the EnablePurging property in the QoE configuration settings has been set to False.) The EnablePurging property only controls the automated purging of archiving records; it has no effect on the **Invoke-CsQoEDatabasePurge** cmdlet.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsQoEDatabasePurge"}

**Lync Server Control Panel:** The functions carried out by the **Invoke-CsQoEDatabasePurge** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Service Identity of the monitoring database to be purged. You can retrieve the Identities for your monitoring databases by running this command:</p>
<p>Get-CsService –MonitoringDatabase</p>
<p>Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeQoEDataOlderThanDays</em></p></td>
<td><p>Required</p></td>
<td><p>System.Int32</p></td>
<td><p>Specifies the age (in days) of the QoE records to be purged from the database; any records older than this value will be deleted.</p>
<p>PurgeQoEDataOlderThanHours can be set to any integer value between 1 and 2147483647, inclusive.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of the computer where the QoE database is located. For example:</p>
<p>-SqlServerFqdn &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SQL Server instance name for the QoE database. For example:</p>
<p>-SqlInstanceName &quot;archinst&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

The **Invoke-CsQoEDatabasePurge** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayMonitoringDatabase\#Decorated class.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Invoke-CsQoEDatabasePurge** cmdlet returns instances of the Microsoft.Rtc.Management.Purge.QoEDataPurgeStatistics class.

</div>

<div>

## See Also


[New-CsQoEConfiguration](new-csqoeconfiguration.md)  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

