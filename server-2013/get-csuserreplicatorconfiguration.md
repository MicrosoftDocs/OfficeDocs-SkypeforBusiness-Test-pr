﻿---
title: Get-CsUserReplicatorConfiguration
TOCTitle: Get-CsUserReplicatorConfiguration
ms:assetid: 7318ae92-e07b-4817-9ec1-be9c7f35aa26
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398548(v=OCS.15)
ms:contentKeyID: 48184479
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsUserReplicatorConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the User Replicator configuration settings currently employed in your organization. The User Replicator periodically retrieves up-to-date user account information from Active Directory and then synchronizes the new information with the current user data stored by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsUserReplicatorConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsUserReplicatorConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about all the User Replicator configuration settings currently in use in your organization.

    Get-CsUserReplicatorConfiguration

</div>

</div>

<div>

## Detailed Description

Although Lync Server maintains its own database of user accounts and user account data, Lync Server still relies on Active Directory as the ultimate source for user information. For example, when a new Active Directory user account is created, you must supply basic information about the user account (such as the Active Directory display name). When a user is enabled for Lync Server, however, you do not need to specify a new display name for that user. That’s because Lync Server uses the display name already stored in Active Directory Domain Services.

Of course, user account information (including the Active Directory display name) is subject to change over time. For example, a user who gets married might change her last name and, in turn, need to change her display name as well. In order to ensure that the Lync Server database and Active Directory remain in synch, Lync Server must periodically check in with Active Directory, retrieve the latest user account updates, and then modify its own user database accordingly. This synchronization between Active Directory and Lync Server is carried out by the User Replicator.

When you install Lync Server a global set of User Replicator configuration settings is created for you. By default, these settings are used to manage the User Replicator on an organization-wide basis. Management of the User Replicator consists of identifying the domains that Lync Server needs to synch with as well as indicating how often the User Replicator checks Active Directory for user account updates. By default, the User Replicator discovers and synchs with all available domains. However, by using the AdDomainNamingContextList property you can restrict synchronization to a specific set of domains: the domains that appear in the AdDomainNamingContextList property.

If you are working with Lync Server you can also use the CsUserReplicatorConfiguration cmdlets to create and manage configuration settings at the service scope. However, with the on-premises version of Lync Server you are limited to a single collection of configuration settings assigned to the global scope.

The **Get-CsUserReplicatorConfiguration** cmdlet enables administrators to return information about all the User Replicator settings currently employed in their organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUserReplicatorConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserReplicatorConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcards when specifying the collection (or collections) of User Replicator configuration settings to be returned. For example, this command returns all the settings configured at the service scope: -Filter &quot;service:*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier of the User Replicator configuration settings to be returned. To return settings at the service scope, use syntax similar to this: -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;. (Note that service scope settings are available only if you are running Lync Online). To return the global settings, use this syntax: -Identity global. If this parameter is not specified then all the User Replicator configurations settings currently in use in your organization will be returned.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the User Replicator configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsUserReplicatorConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsUserReplicatorConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object.

</div>

<div>

## See Also


[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

