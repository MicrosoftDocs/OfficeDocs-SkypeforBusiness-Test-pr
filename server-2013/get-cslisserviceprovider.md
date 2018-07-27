﻿---
title: Get-CsLisServiceProvider
TOCTitle: Get-CsLisServiceProvider
ms:assetid: 060b0b32-5787-487b-b1d9-7a0c7dd44d80
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398116(v=OCS.15)
ms:contentKeyID: 48183299
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsLisServiceProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Retrieves information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to validate locations. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsLisServiceProvider

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The **Get-CsLisServiceProvider** cmdlet does not have any parameters (other than the Windows PowerShell common parameters, such as Verbose). There will never be more than one service provider for an E9-1-1 implementation, so this cmdlet will retrieve information about the web service provided by that service provider.

    Get-CsLisServiceProvider

</div>

</div>

<div>

## Detailed Description

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet retrieves information about a provider, including the name of the provider and a URL for the web service that the organization will use to send the locations.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisServiceProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisServiceProvider"}

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
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>This cmdlet provides only common Windows PowerShell parameters.</p></td>
<td></td>
<td></td>
<td> </td>
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

This cmdlet retrieves an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)  
[Set-CsLisServiceProvider](set-cslisserviceprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

