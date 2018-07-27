﻿---
title: Set-CsTrustedApplicationPool
TOCTitle: Set-CsTrustedApplicationPool
ms:assetid: 0f42d12b-d09a-41fd-892f-2b7515a35344
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398187(v=OCS.15)
ms:contentKeyID: 48183421
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTrustedApplicationPool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-13_

Modifies a pool that contains the computers that host trusted applications. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsTrustedApplicationPool [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-OutboundOnly <$true | $false>] [-Registrar <String>] [-RequiresReplication <$true | $false>] [-ThrottleAsServer <$true | $false>] [-TreatAsAuthenticated <$true | $false>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the pool with the FQDN TrustPool.litwareinc.com. We use the Identity parameter to specify the FQDN of the pool we want to modify. This example modifies the OutboundOnly property of the pool by specifying a value of True ($True) for the parameter OutboundOnly. (The default value is False.)

    Set-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com -OutboundOnly $True

</div>

</div>

<div>

## Detailed Description

We recommend that the computers that are running trusted applications within a Lync Server deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. The **Set-CsTrustedApplicationPool** cmdlet modifies the settings for an existing trusted application pool. Note that you can’t modify the computers that are associated with a pool by using this cmdlet; you must use the CsTrustedApplicationComputer cmdlets to do that.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsTrustedApplicationPool** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTrustedApplicationPool"}

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
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of ports available in the port range for application sharing connections.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of the first port in the port range available for application sharing connections.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of ports available in the port range for audio connections.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of the first port in the port range available for audio connections.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The fully qualified domain name (FQDN) or service ID of the pool whose settings you want to modify.</p></td>
</tr>
<tr class="even">
<td><p><em>OutboundOnly</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Specifies whether a trusted application can initiate a connection to a server within the pool. Set this value to True if you want all connections to be initiated by the server rather than the application.</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The service ID or FQDN of the Registrar service for the pool. Note that changing the Registrar will orphan any contacts attached to the application. Those contacts must be moved by calling the <strong>Move-CsApplicationEndpoint</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>RequiresReplication</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Determines whether replication is required for this pool. Set this value to False if replication is not required. You would ordinarily set this parameter to False for Microsoft Outlook Web Access and manually-provisioned applications.</p></td>
</tr>
<tr class="odd">
<td><p><em>ThrottleAsServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Set this parameter to false to throttle connections between the servers within the pool and trusted applications as clients. This places greater restrictions on the connections than the default True, which throttles connections as servers. Throttling a connection simply places restrictions on the number of transactions that can occur simultaneously.</p></td>
</tr>
<tr class="even">
<td><p><em>TreatAsAuthenticated</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Determines whether authentication is required for trusted applications connecting to servers within the pool. Set this parameter to False if you want to require trusted applications to be authenticated. The default value of True allows the trusted applications to connect under the assumption they’ve already been authenticated.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of ports available in the port range for video connections.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>The number of the first port in the port range available for video connections.</p></td>
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

Microsoft.Rtc.Management.Xds.DisplayExternalServer object. Accepts pipelined input of trusted application pool objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.Xds.DisplayExternalServer.

</div>

<div>

## See Also


[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)  
[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

