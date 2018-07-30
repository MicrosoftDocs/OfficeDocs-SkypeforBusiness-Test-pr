﻿---
title: Remove-CsLisSwitch
TOCTitle: Remove-CsLisSwitch
ms:assetid: 53456988-4b37-4f34-825d-bebee5124856
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398352(v=OCS.15)
ms:contentKeyID: 48184170
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsLisSwitch

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Removes a Location Information Server (LIS) network switch. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsLisSwitch -ChassisID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 removes the LIS switch with the MAC address (ChassisID) 99-99-99-99-99-99.

This command will not succeed if the ChassisID is referenced by a port. Also, if this switch was associated with a location, that location will not be removed, only the switch will be removed from the location mapping.

    Remove-CsLisSwitch -ChassisID 99-99-99-99-99-99

</div>

<div>

## EXAMPLE 2

This example removes all switches that do not have a city. The example begins with a call to the **Get-CsLisSwitch** cmdlet, which returns a collection of all switches. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a City property that is empty; in other words, a City that is equal to (-eq) an empty string (“”). Finally, we pipe this collection of switches that don’t have cities to the **Remove-CsLisSwitch** cmdlet, which removes everything in that collection.

Note that, as in Example 1, no locations are removed from the location database, only the switches that reference those locations are removed. In this case that means there will be invalid locations (they’re invalid because City is a required property for a location) in the location database that should also be removed. You can remove locations by calling the **Remove-CsLisLocation** cmdlet.

    Get-CsLisSwitch | Where-Object {$_.City -eq ""} | Remove-CsLisSwitch

</div>

</div>

<div>

## Detailed Description

Enhanced 9-1-1 (E9-1-1) allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller’s location. This cmdlet removes a switch from the location configuration database. Removing a switch will not remove the actual location; it removes only the switch. To remove the location, call the **Remove-CsLisLocation** cmdlet.

You cannot remove a switch if the ChassisID of the switch is in use by a port. (Run the following command to find out which ChassisIDs are in use by ports: Get-CsLisPort | Select-Object ChassisID.) You must first remove all ports with the given ChassisID before you can remove the switch.

If you attempt to remove a switch that does not exist, no action will be taken and you will not receive an error or a warning message.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisSwitch** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisSwitch"}

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
<td><p><em>ChassisID</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Media Access Control (MAC) address of the network switch. This value will be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.</p></td>
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

Accepts pipelined input of LIS switch objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Set-CsLisSwitch](set-cslisswitch.md)  
[Get-CsLisSwitch](get-cslisswitch.md)  
[Remove-CsLisLocation](remove-cslislocation.md)  
[Get-CsLisPort](get-cslisport.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

