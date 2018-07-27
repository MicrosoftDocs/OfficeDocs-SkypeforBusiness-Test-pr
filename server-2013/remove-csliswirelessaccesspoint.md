﻿---
title: Remove-CsLisWirelessAccessPoint
TOCTitle: Remove-CsLisWirelessAccessPoint
ms:assetid: 656190b0-bde0-4a92-a6b5-b96a389c4863
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398461(v=OCS.15)
ms:contentKeyID: 48184326
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsLisWirelessAccessPoint

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Removes a Location Information Server (LIS) wireless access point (WAP). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsLisWirelessAccessPoint -BSSID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 removes the LIS WAP location with the BSSID 99-99-99-99-99-99.

If this WAP was associated with a location, that location will not be removed, only the WAP will be removed from the location mapping.

    Remove-CsLisWirelessAccessPoint -BSSID 99-99-99-99-99-99

</div>

<div>

## EXAMPLE 2

This example removes all WAPs in building 30. The example begins with a call to the **Get-CsLisWirelessAccessPoint** cmdlet, which returns a collection of all WAPs. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a Location property that contains the string Bldg30 anywhere in the value; in other words, a Location that is like (-like) Bldg30. Finally, we pipe this collection of WAPs in building 30 to the **Remove-CsLisWirelessAccessPoint** cmdlet, which removes everything in that collection.

Note that, as in Example 1, no locations are removed from the location configuration database, only the WAPs that reference those locations are removed.

    Get-CsLisWirelessAccessPoint | Where-Object {$_.Location -like "*Bldg30*"} | Remove-CsLisWirelessAccessPoint

</div>

</div>

<div>

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller’s location. This cmdlet removes a WAP from the location configuration database. Removing the WAP will not remove the location associated with that WAP. Use the **Remove-CsLisLocation** cmdlet to remove a location.

If you attempt to remove a WAP that does not exist, no action will be taken and you will not receive an error or a warning message.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisWirelessAccessPoint** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisWirelessAccessPoint"}

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
<td><p><em>BSSID</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Basic Service Set Identifier (BSSID) of the wireless access point you want to remove. This value will be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.</p></td>
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

Accepts pipelined input of LIS wireless access point objects.

</div>

<div>

## Return Types

This cmdlet removes an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)  
[Get-CsLisWirelessAccessPoint](get-csliswirelessaccesspoint.md)  
[Remove-CsLisLocation](remove-cslislocation.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

