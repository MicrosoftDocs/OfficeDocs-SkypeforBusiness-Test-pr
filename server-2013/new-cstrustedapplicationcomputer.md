﻿---
title: New-CsTrustedApplicationComputer
TOCTitle: New-CsTrustedApplicationComputer
ms:assetid: 5c44a596-7fca-49d3-a7cf-e22656698a28
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398405(v=OCS.15)
ms:contentKeyID: 48184277
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsTrustedApplicationComputer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Adds a computer that hosts trusted applications to an existing pool. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> -Pool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example adds a new computer with the FQDN Trust1.litwareinc.com to the pool TrustPool.litwareinc.com. We use the Identity parameter to specify the FQDN of the new computer, and the Pool parameter to specify the FQDN of the pool. The pool must exist and must be a trusted application pool. (Note: To create a trusted application pool, call the **New-CsTrustedApplicationPool** cmdlet.)

    New-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com -Pool TrustPool.litwareinc.com

</div>

</div>

<div>

## Detailed Description

We recommend that the computers that are running trusted applications within a Lync Server deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. By default, when you create a pool, a computer with the same fully qualified domain name (FQDN) as the pool is also created. Use this cmdlet to create a new computer and add it to a pool.

The trusted application pool must already exist in order for this cmdlet to succeed. In addition, you can’t add an additional trusted application computer to a pool that contains service roles other than the ExternalServer role. For example, if the pool also supports Registrar or CentralMgmt roles, the pool can contain only one trusted application computer. In addition, if you did not specify a computer FQDN for the default computer when you created the pool (by calling the **New-CsTrustedApplicationPool**) cmdlet, the computer will have the same FQDN as the pool and you cannot add another computer.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsTrustedApplicationComputer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrustedApplicationComputer"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The FQDN of the computer that hosts the trusted application.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The FQDN of the pool hosting the trusted application computer. You can find available pools by running the <strong>Get-CsTrustedApplicationPool</strong> cmdlet.</p></td>
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

None.

</div>

<div>

## Return Types

Creates an object of type Microsoft.Rtc.Management.Xds.DisplayComputer.

</div>

<div>

## See Also


[Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)  
[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

