﻿---
title: Move-CsApplicationEndpoint
TOCTitle: Move-CsApplicationEndpoint
ms:assetid: 0f5a5b7a-aca5-4672-b712-d47683e28caf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398188(v=OCS.15)
ms:contentKeyID: 48183423
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move-CsApplicationEndpoint

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

Moves an endpoint to a different Registrar pool. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Move-CsApplicationEndpoint -Identity <UserIdParameter> -TargetApplicationPool <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example moves the application endpoint contact object with the SIP address endpoint1@litwareinc.com to the trusted Registrar pool TrustPoolA.litwareinc.com. Use this command to upgrade a UCMA 2.0 application to a Lync Server application after coexistence.

    Move-CsApplicationEndpoint -Identity sip:endpoint1@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com

</div>

<div>

## EXAMPLE 2

This example moves the application endpoint contact object with the SIP address endpoint2@litwareinc.com to the trusted Registrar pool TrustPoolA.litwareinc.com. This example differs from Example 1 in that this command includes the Force parameter. Use this command for an in-place migration of a UCMA 2.0 application or for direct deployment of a UCMA 2.0 application against a pure Lync Server deployment. This will update an existing object in Active Directory with the necessary attributes so that routing can occur through the Lync Server Registrar.

    Move-CsApplicationEndpoint -Identity sip:endpoint2@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com -Force

</div>

</div>

<div>

## Detailed Description

This cmdlet moves an existing endpoint contact object in Active Directory Domain Services from a Microsoft Office Communications Server 2007 R2 application pool to a Lync Server application pool, or from one Lync Server application pool to another. The application associated with the given endpoint must exist on the target pool. To determine which application is associated with the endpoint, run the **Get-CsTrustedApplicationEndpoint** cmdlet or the **Get-CsDialInConferencingAccessNumber** cmdlet.

This cmdlet is also used to upgrade the Active Directory contact object properties when an application deployed against Office Communications Server 2007 R2 is retargeted against Lync Server. Note that the source and target application pool will be the same in that case. Also, if an application originally designed to work against Office Communications Server 2007 R2 is directly deployed against Lync Server, then this cmdlet must be used with the Force flag to upgrade the Active Directory contact object properties.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Move-CsApplicationEndpoint** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsApplicationEndpoint"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>The SIP address or distinguished name (DN) of the endpoint contact you want to move.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetApplicationPool</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>The fully qualified domain name (FQDN) of the pool to which the endpoint is moving. The target pool must have a Registrar service dependency.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>This flag is required if you are moving a Microsoft Unified Communications Managed API (UCMA) 2.0 contact object to the same pool but on a Lync Server deployment. This will force routing to occur through the Lync Server Registrar.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the application endpoint despite those errors.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Specifying this parameter will return the application endpoint object after the object has been moved.</p></td>
</tr>
<tr class="even">
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

String. Accepts a pipelined string value representing the Identity of an application endpoint.

</div>

<div>

## Return Types

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.

</div>

<div>

## See Also


[Get-CsApplicationEndpoint](get-csapplicationendpoint.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

