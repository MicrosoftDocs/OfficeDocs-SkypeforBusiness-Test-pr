﻿---
title: Invoke-CsDatabaseFailover
TOCTitle: Invoke-CsDatabaseFailover
ms:assetid: 24b73e8e-948c-4e9c-bf4e-04ec0a229ffa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204744(v=OCS.15)
ms:contentKeyID: 48183629
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Invoke-CsDatabaseFailover

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-21_

Invokes the process in which a Lync Server 2013 database fails over to its mirror database. After failover has been completed, the mirror database will become the principal database and will handle all new database requests. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Invoke-CsDatabaseFailover -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -NewPrincipal <Primary | Mirror> -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-ExcludeDatabaseList <String[]>] [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 invokes failover for the User database found on the pool atl-cs-001.litwareinc.com. The command causes the User database to failover to a previously-assigned mirror database.

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "User" -NewPrincipal "Mirror"

</div>

<div>

## Example 2

In Example 2, all databases on the pool atl-cs-001.litwareinc.com are failed over except for the LcsCDR and LcsLog databases. These databases are exempted from failover by using the ExcludeDatabaseList parameter.

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -ExcludeDatabase -NewPrincipal "Mirror" -ExcludeDatabaseList "LcsCDR", "LcsLog"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Invoke-CsDatabaseFailover** cmdlet provides a way for administrators to "failover" one or more Lync Server 2013 databases. For example, suppose you need to temporarily take down the primary database, perhaps to perform a hardware upgrade. In that case, you can use the **Invoke-CsDatabaseFailover** cmdlet to failover from the primary database to the mirror database; when you do that, all requests for the database in question will be routed to the mirror database. Later, when the hardware upgrade is complete, you can use this same cmdlet to failback to the primary database.

Note that any commands using the **Invoke-CsDatabaseFailover** cmdlet will fail if you have not configured both a primary database and a mirror database for the database in question.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsDatabaseFailover"}

**Lync Server Control Panel:** The functions carried out by the **Invoke-CsDatabaseFailover** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>DatabaseType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>Type of database being failed over. Valid values are:</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Cls</p>
<p>Edge</p>
<p>Lyss</p>
<p>Monitoring</p>
<p>PersistentChat</p>
<p>PersistentChatCompliance</p>
<p>Provision</p>
<p>Registrar</p>
<p>User</p></td>
</tr>
<tr class="even">
<td><p><em>NewPrincipal</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.MirrorRole</p></td>
<td><p>Specifies whether failover will be to the primary database or to the mirror database. Valid values are:</p>
<p>* * Mirror</p>
<p>Primary</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the pool containing the database to be failed over.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeDatabaseList</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String[]</p></td>
<td><p>List of databases that should not be failed over. For example:</p>
<p>-ExcludeDatabaseList &quot;LcsCDR&quot;</p>
<p>To prevent multiple databases from being failed over, separate the database names using commas:</p>
<p>-ExcludeDatabaseList &quot;LcsCDR&quot;, &quot;LcsLog&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command. The Force parameter is also used if the current database is not accessible.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves topology information from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\DatabaseFailover.html&quot;</p></td>
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

None. The **Invoke-CsDatabaseFailover** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

