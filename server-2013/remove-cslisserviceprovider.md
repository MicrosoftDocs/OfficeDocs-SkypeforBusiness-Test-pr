﻿---
title: Remove-CsLisServiceProvider
TOCTitle: Remove-CsLisServiceProvider
ms:assetid: d26302bf-7794-4125-af80-ba7c92096b6d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398904(v=OCS.15)
ms:contentKeyID: 48185405
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsLisServiceProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Removes an object containing information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsLisServiceProvider [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the service provider web service from the E9-1-1 implementation. There will only be, at most, one service provider defined, which will be removed by this cmdlet.

    Remove-CsLisServiceProvider

</div>

</div>

<div>

## Detailed Description

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet removes an entry for a provider; after running this cmdlet there will be no web service access to the provider.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisServiceProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisServiceProvider"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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

Accepts pipelined input of a Location Information Server (LIS) service provider object.

</div>

<div>

## Return Types

This cmdlet does not return an object or a value. It removes an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Set-CsLisServiceProvider](set-cslisserviceprovider.md)  
[Get-CsLisServiceProvider](get-cslisserviceprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

