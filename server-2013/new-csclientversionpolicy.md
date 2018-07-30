﻿---
title: New-CsClientVersionPolicy
TOCTitle: New-CsClientVersionPolicy
ms:assetid: 8c95493a-ce18-49eb-937f-7348743fcbb4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398709(v=OCS.15)
ms:contentKeyID: 48184752
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsClientVersionPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Creates a new client version policy. Client version policies enable you to specify which versions of clients (such as Microsoft Office Communicator 2007 R2) will be able to log on to your Lync Server system. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsClientVersionPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Rules <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, a new client version policy is created for the Redmond site. Because no parameters are specified (other than the mandatory Identity parameter), the new policy will contain all of the default values for a client version policy.

    New-CsClientVersionPolicy -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 creates a new client version policy for each site in the organization. To accomplish this task, the command first calls the **Get-CsSite** cmdlet without any additional parameters; that returns a collection of all the sites in the topology. This collection of sites is then then piped to the **Select-Object** cmdlet, which extracts the Identity property for each site. Those Identities are then piped to the **ForEach-Object** cmdlet, which takes each site in the collection and creates a new client version policy for that site.

    Get-CsSite | Select-Object Identity | ForEach-Object {New-CsClientVersionPolicy -Identity ("site:" + $_.Identity)}

</div>

</div>

<div>

## Detailed Description

Client version policies represent a collection of client version rules; in turn, client version rules are used to determine which client applications are allowed to log on to Lync Server. When a user attempts to log on to Lync Server, his or her client application sends a SIP header to the server; this header includes detailed information about the application itself, including the software’s major version, minor version, and build number. The version information included in the SIP header is then checked against a collection of client version rules to see if any rules apply to that particular application. If such a rule exists, Lync Server will then take the action specified by the rule. For example, the rule might tell Lync Server to allow the logon, to block it, or to allow the logon but then silently upgrade the client application to the latest version (for example, upgrade Communicator 2007 R2 to Lync 2013).

Client version policies, which can be applied at the global scope, the site scope, the service scope (Registrar service only), or the per-user scope, give you flexibility in determining which client applications can be used to access the system. For example, as a general rule you might want to prevent users from logging on to Lync Server by using Communicator 2007 R2; you might want to do that because the older client application does not support the same features and capabilities as Lync. However, due to hardware or software conflicts, you might also have a group of users who cannot upgrade to Lync Server. In that case, you can create a separate rule -- and a separate client version policy -- that allows those users to log on from within Communicator 2007 R2.

Note, however, that anonymous users are only affected by global policies. That’s because anonymous users are not associated with a site or service, and cannot be assigned a per-user policy.

New client version policies are created by using the **New-CsClientVersionPolicy** cmdlet. These new policies can be created at the site scope, the service scope (Registrar service only), or at the per-user scope.

It’s important to note that client version policies do not apply to federated users; instead, federated users are bound by the client version policies used in their own organization. For example, suppose a federated user uses client A, a client allowed by the federated organization. As long as the federated organization allows the use of client A, this user will be able to communicate with your organization using that client. This will be true even if your client version policy blocks the use of client A. Client version policies enforced in your organization do not override the client version policies used in a federated organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsClientVersionPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientVersionPolicy\\b"}

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
<td><p>Unique identifier for the policy to be created. To create a policy at the site scope, use syntax similar to this: -Identity &quot;site:Redmond&quot;. To create a policy at the service scope, use syntax similar to this: -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;. The Registrar service is the only service that can host a client version policy.</p>
<p>Policies can also be created at the per-user scope. To create a per-user policy, use syntax similar to this: -Identity &quot;SalesDepartmentPolicy&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to provide explanatory text about the policy. For example, you might include information about the users that the policy should be assigned to.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Rules</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Collection of client version policy rules. You can add and remove rules from a policy by using the <strong>New-CsClientVersionPolicyRule</strong> cmdlet and the <strong>Remove-CsClientVersionPolicyRule</strong> cmdlet. To add a rule at the time you create the new policy, create the rule and store the value in a variable (for example, $x). You can then use syntax similar to this when creating the new policy:</p>
<p>New-CsClientVersionPolicy –Identity &quot;RedmondClientVersionPolicy&quot; –Rules @{Add=$x}</p></td>
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

<div>

## Input Types

None. The **Get-CsClientVersionPolicy** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **New-CsClientVersionPolicy** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionPolicy object.

</div>

<div>

## See Also


[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)  
[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

