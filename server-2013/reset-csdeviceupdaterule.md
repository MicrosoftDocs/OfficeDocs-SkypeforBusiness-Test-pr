﻿---
title: Reset-CsDeviceUpdateRule
TOCTitle: Reset-CsDeviceUpdateRule
ms:assetid: 0de47bcf-da8f-4dae-b293-3adac3c1acdb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398181(v=OCS.15)
ms:contentKeyID: 48183406
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Reset-CsDeviceUpdateRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Rejects a device update rule that has been imported to the system. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Reset-CsDeviceUpdateRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Reset-CsDeviceUpdateRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 resets the device update rule d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 found on the service WebServer:atl-cs-001.litwareinc.com.

    Reset-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

</div>

<div>

## EXAMPLE 2

Example 2 resets all the device update rules that have been configured for the service WebServer:atl-cs-001.litwareinc.com. This is done by first calling the **Get-CsDeviceUpdateRule** cmdlet along with the Filter parameter; the filter value "WebServer:atl-cs-001.litwareinc.com\*" ensures that only rules that have an Identity that begins with the characters "WebServer:atl-cs-001.litwareinc.com" will be returned. (By definition, these are all the device update rules that have been assigned to the service WebServer:atl-cs-001.litwareinc.com.) The filtered collection is then piped to the **Reset-CsDeviceUpdateRule** cmdlet, which resets each rule in the collection.

    Get-CsDeviceUpdateRule -Filter service:WebServer:atl-cs-001.litwareinc.com*  | Reset-CsDeviceUpdateRule

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 resets all the device update rules for the brand LG-Nortel. To do this, the command first calls the **Get-CsDeviceUpdateRule** cmdlet without any parameters in order to return a collection of all the device update rules currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those rules where the Brand property is equal to LG-Nortel. After that the filtered collection is piped to the **Reset-CsDeviceUpdateRule** cmdlet, which resets all the rules in the filtered collection.

    Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "LG-Nortel"} | Reset-CsDeviceUpdateRule

</div>

</div>

<div>

## Detailed Description

Lync Server uses device update rules as a way to provide firmware updates to devices that run Lync Phone Edition. Periodically, administrators upload a set of device update rules to Lync Server. After those rules have been tested and approved, they are automatically downloaded and applied to the appropriate devices as those devices connect to the system. By default devices check for new update rules each time they turn on and connect to Lync Server. Devices also check for updates every 24 hours after that initial sign on.

Each new device update rule added to the system is marked as "Pending." That means that the update will be downloaded and installed by the appropriate test devices; however, it will not be downloaded and installed by client devices in general. This gives you an opportunity to test the updates and ensure that there are no adverse effects before you make this update widely available. As soon as you are convinced that the update has passed your tests and will work for your organization, you can then use the **Approve-CsDeviceUpdateRule** cmdlet to approve the update.

On the other hand, administrators might conclude that a given update should not be used in the organization (for example, the update might cause a conflict with in-house software). In that case, administrators can use the **Reset-CsDeviceUpdateRule** cmdlet to reject the update. When that happens, the PendingVersion of the update rule is set to a null value. In turn, that means that test devices that log on to the system will uninstall the update and reinstall the approved version of that update. And because the update was never approved, that means that the update will never be installed by anything other than those test devices. As a result, there will be no impact on the general user population.

The **Reset-CsDeviceUpdateRule** cmdlet can only be used for device update rules in the Pending state. If a rule has already been approved, you will need to use the **Restore-CsDeviceUpdateRule** cmdlet to roll back the deployment of the device update.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Reset-CsDeviceUpdateRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Reset-CsDeviceUpdateRule"}

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
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the device update rule being reset. The Identity for a device update rule consists of a two parts: the service where the device update rule has been assigned (for example, service:WebServer:atl-cs-001.litwareinc.com) and a globally unique identifier (GUID). Consequently, a device update rule configured for the Redmond site will have an Identity similar to this: &quot;service:WebServer:atl-cs-oo1.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>DeviceUpdate.Rule</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule object. The **Reset-CsDeviceUpdateRule** cmdlet accepts pipelined instances of the device update rule object.

</div>

<div>

## Return Types

None. Instead, the **Reset-CsDeviceUpdateRule** cmdlet resets instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdate.Rule object.

</div>

<div>

## See Also


[Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)  
[Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)  
[Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)  
[Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

