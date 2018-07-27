﻿---
title: Get-CsUserDatabaseState
TOCTitle: Get-CsUserDatabaseState
ms:assetid: c90150cd-fdb0-4c79-af58-c9ad884cb043
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398831(v=OCS.15)
ms:contentKeyID: 48185400
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsUserDatabaseState

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the online status (True or False) of one or more Lync Server user databases. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsUserDatabaseState [-RegistrarPool <Fqdn>] <COMMON PARAMETERS>

    Get-CsUserDatabaseState [-Identity <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns the online status of each user database configured for use in your organization.

    Get-CsUserDatabaseState

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 returns the online status of a single user database: the database with the Identity UserDatabase:atl-sql-001.litwareinc.com.

    Get-CsUserDatabaseState -Identity "UserDatabase:atl-sql-001.litwareinc.com"

</div>

<div>

## EXAMPLE 3

In Example 3, status information is returned for all the user databases located in the Registrar pool atl-cs-001.litwareinc.com.

    Get-CsUserDatabaseState -RegistrarPool "atl-cs-001.litwareinc.com"\

</div>

<div>

## EXAMPLE 4

In Example 4, information is returned for all the user databases that are currently online. To do this, the command first calls the **Get-CsUserDatabaseState** cmdlet without any parameters. That returns a collection of all the user databases in use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those databases where the Online property is equal to True.

    Get-CsUserDatabaseState | Where-Object {$_.Online -eq $True}

</div>

</div>

<div>

## Detailed Description

Lync Server employs the user database (also known as the user store) to maintain presence and routing information for Lync Server users. The **Get-CsUserDatabaseState** cmdlet provides a way to verify the current status (either online or offline) for any of the user databases currently in use in your organization.

Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Lync Server. In turn, that means that you will not be able to run the **Get-CsUserDatabaseState** cmdlet from a remote instance of Windows PowerShell. That’s because your command will not be able to traverse the firewall and access the SQL Server Express database. You can still run the cmdlet locally (that is, on the Standard Edition server itself). However, to run the **Get-CsUserDatabaseState** cmdlet remotely you will need to manually enable the firewall exceptions for SQL Server Express.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUserDatabaseState** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserDatabaseState"}

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
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Unique identifier of the user database whose online status is to be returned. For example: -Identity &quot;UserDatabase:atl-sql-001.litwareinc.com&quot;.</p>
<p>You cannot use both Identity and RegistrarPool in the same command, nor can you use wildcards with either parameter. If both parameters are omitted the <strong>Get-CsUserDatabaseState</strong> cmdlet returns information about all the user databases currently in use.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPool</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the Registrar pool hosting the user databases whose online status is to be returned. For example: -RegistrarPool &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>You cannot use both Identity and RegistrarPool in the same command, nor can you use wildcards with either parameter. If both parameters are omitted the <strong>Get-CsUserDatabaseState</strong> cmdlet returns information about all of the user databases currently in use.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsUserDatabaseState** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsUserDatabaseState** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.UserStoreState object.

</div>

<div>

## See Also


[Set-CsUserDatabaseState](set-csuserdatabasestate.md)  
[Update-CsUserDatabase](update-csuserdatabase.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

