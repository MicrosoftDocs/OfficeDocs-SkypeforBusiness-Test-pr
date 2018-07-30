﻿---
title: Invoke-CsManagementServerFailover
TOCTitle: Invoke-CsManagementServerFailover
ms:assetid: 060ab02a-1267-4b35-bc2b-6a4a35616be0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204647(v=OCS.15)
ms:contentKeyID: 48183312
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Invoke-CsManagementServerFailover

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Invokes the process by which the Lync Server 2013 Central Management store is failed over. When the Central Management store is failed over the primary database will be replaced by either a pre-assigned mirror database or a specified backup database. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Fqdn> -Force <SwitchParameter> [-BackupMirrorSqlInstanceName <String>] [-BackupMirrorSqlServerFqdn <Fqdn>] [-BackupSqlInstanceName <String>] <COMMON PARAMETERS>

    Invoke-CsManagementServerFailover [-Restore <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 fails over the Central Management store for Lync Server 2013. In this case, the existing management store will be replaced by the RTC database instance found on the computer redmond-cs-001.litwareinc.com.

    Invoke-CsManagementServerFailover -BackupSqlServerFqdn "redmond-cs-001.litwareinc.com" - BackupSqlInstanceName "RTC" -Force

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Invoke-CsManagementServerFailover** cmdlet enables administrators to "failover" the Central Managament Server (CMS). The **Invoke-CsManagementServerFailover** cmdlet provides two different methods for failing over the CMS: 1) you can failover to a specified backup instance of SQL Server, or, 2) you can failover to a preassigned mirror database. To failover to a specified backup instance, use the BackupSqlServerFqdn and BackupSqlInstanceName parameters. To failover to the mirror database, use the BackupMirrorSqlServerFqdn and BackupMirrorSqlInstanceName parameters.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsManagementServerFailover"}

**Lync Server Control Panel:** The functions carried out by the **Invoke-CsManagementServerFailover** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>BackupSqlServerFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the computer hosting the SQL Server backup database. This parameter is required if you are running the <strong>Invoke-CsManagementServerFailover</strong> cmdlet in disaster recovery mode.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command. This parameter is required if you are running the <strong>Invoke-CsManagementServerFailover</strong> cmdlet in disaster recovery mode.</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupMirrorSqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SQL Server instance for the mirror database.</p></td>
</tr>
<tr class="even">
<td><p><em>BackupMirrorSqlServerFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the computer hosting the SQL Server mirror database.</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupSqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SQL Server instance for the backup database.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\CMSFailover.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Restore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When specified, restores the existing Central Management Server database.</p></td>
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

None. The **Invoke-CsManagementServerFailover** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

