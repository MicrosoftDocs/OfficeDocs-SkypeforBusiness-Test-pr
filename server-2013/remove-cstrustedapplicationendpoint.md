﻿---
title: Remove-CsTrustedApplicationEndpoint
TOCTitle: Remove-CsTrustedApplicationEndpoint
ms:assetid: c9b96690-d8c2-47f7-bff3-706dbf68d75a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398837(v=OCS.15)
ms:contentKeyID: 48185432
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsTrustedApplicationEndpoint

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes a trusted application endpoint. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsTrustedApplicationEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the endpoint contact with the Identity (in this case the display name) Endpoint 1. Because identities must be unique, this command will remove, at most, one endpoint.

    Remove-CsTrustedApplicationEndpoint -Identity "Endpoint 1"

</div>

<div>

## EXAMPLE 2

This example removes all trusted application endpoints associated with the application tapp2. This is accomplished by first calling the **Get-CsTrustedApplicationEndpoint** cmdlet and passing the ID tapp2 to the ApplicationId parameter. This will return a collection of endpoints that are associated with the tapp2 trusted application. This collection is then piped to the **Remove-CsTrustedApplicationEndpoint** cmdlet, which removes each endpoint in the collection. Keep in mind that this call to the **Get-CsTrustedApplicationEndpoint** cmdlet could retrieve endpoints with the application ID tapp2 from multiple pools, which would result in this command removing trusted application endpoints from multiple pools.

    Get-CsTrustedApplicationEndpoint -ApplicationId tapp2 | Remove-CsTrustedApplicationEndpoint

</div>

</div>

<div>

## Detailed Description

A trusted application endpoint is an Active Directory contact object that enables routing of calls to a trusted application. This cmdlet removes an existing endpoint contact object from Active Directory Domain Services.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrustedApplicationEndpoint** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrustedApplicationEndpoint"}

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
<td><p>The Identity (the distinguished name of the contact), SIP address, or display name of the application endpoint to be removed.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact object. Accepts pipelined input of trusted application endpoint objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.

</div>

<div>

## See Also


[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

