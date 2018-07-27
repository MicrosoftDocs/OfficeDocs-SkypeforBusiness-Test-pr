﻿---
title: Get-CsAdminRoleAssignment
TOCTitle: Get-CsAdminRoleAssignment
ms:assetid: 61374f9b-e85a-4866-91f2-037a862ba0d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398434(v=OCS.15)
ms:contentKeyID: 48184317
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsAdminRoleAssignment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

Returns the role-based access control (RBAC) roles assigned to a user. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsAdminRoleAssignment -Identity <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns all of the RBAC roles assigned to the user kenmyer.

    Get-CsAdminRoleAssignment -Identity "kenmyer"

</div>

<div>

## EXAMPLE 2

Example 2 returns the RBAC roles for all of the users who have been enabled for Lync Server. To do this, the command begins by calling the **Get-CsUser** cmdlet without any parameters; that returns a collection of all the users in the organization who have been enabled for Lync Server or Office Communications Server. This data is then piped to the **ForEach-Object** cmdlet, which loops through each user account in the collection and does the following: 1) echoes the user’s display name to the screen; and 2) uses the **Get-CsAdminRoleAssignment** cmdlet to return the user’s RBAC roles. The user account information must be piped to the **ForEach-Object** cmdlet because the **Get-CsAdminRoleAssignment** cmdlet does not directly accept pipelined data.

    Get-CsUser | ForEach-Object {$_.DisplayName; Get-CsAdminRoleAssignment -Identity $_.SamAccountName}

</div>

</div>

<div>

## Detailed Description

Role-based access control (RBAC) enables administrators to delegate control of specific management tasks for Lync Server. For example, instead of granting your organization’s help desk full administrator privileges you can give these employees very specific rights: the right to manage only user accounts; the right to manage only Enterprise Voice components; and the right to manage only archiving and Archiving Server. In addition, these rights can be limited in scope: one user can be given the right to manage Enterprise Voice, but only in the Redmond site; while another user can be given the right to manage user accounts, but only if those accounts are in the Finance organizational unit (OU).

The **Get-CsAdminRoleAssignment** cmdlet provides a way for you to retrieve a list of the RBAC roles that have been assigned to a user.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsAdminRoleAssignment** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdminRoleAssignment"}

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
<td><p>System.String</p></td>
<td><p>SamAccountName of the user whose RBAC roles are to be returned, You can retrieve the SamAccountName for a user by using a command similar to this:</p>
<p>Get-CsUser &quot;Ken Myer&quot; | Select-Object SamAccountName</p>
<p>Note that you must use the SamAccountName when specifying the user Identity. Other common values used when specifying identities, such as the Active Directory display name or the user’s SIP address, will not work with <strong>Get-CsAdminRoleAssignment</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the RBAC role assignment data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

String. The **Get-CsAdminRoleAssignment** cmdlet accepts a pipelined string value representing the SamAccountName of a user.

</div>

<div>

## Return Types

The **Get-CsAdminRoleAssignment** cmdlet returns string values representing the RBAC roles held by the specified user.

</div>

<div>

## See Also


[Get-CsAdminRole](get-csadminrole.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

