﻿---
title: Remove-CsAVEdgeConfiguration
TOCTitle: Remove-CsAVEdgeConfiguration
ms:assetid: 98bceec5-ed9d-4574-b6bf-f51e0f414ca7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398786(v=OCS.15)
ms:contentKeyID: 48184874
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsAVEdgeConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Enables you to remove an existing collection of configuration settings applied to computers running the Access Edge service (these computers are also known as A/V Edge servers). An A/V Edge server enables internal users to share audio and video data with external users (that is, users who are not logged on to your internal network). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsAVEdgeConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 removes the A/V Edge configuration settings that have the Identity site:Redmond. After the settings are removed, A/V Edge servers in the Redmond site will be governed by the global configuration settings.

    Remove-CsAVEdgeConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In Example 2, all of the A/V Edge configuration settings that have been applied at the service scope are removed. To do this, the command first calls the **Get-CsAVEdgeConfiguration** cmdlet along with the Filter parameter; the filter value "service:\*" ensures that only settings configured at the service scope are returned. This filtered collection is then piped to the **Remove-CsAVEdgeConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsAVEdgeConfiguration -Filter "service:*" | Remove-CsAVEdgeConfiguration

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 deletes all of the A/V Edge configuration settings where the value of the MaxBandwidthPerUserKB property is less than 5,000 kilobits per second. To carry out this task, the command first uses the **Get-CsAVEdgeConfiguration** cmdlet without any additional parameters in order to return a collection of all the A/V Edge settings currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which selects only those settings where the MaxBandwidthPerUserKB property is less than 5000. The filtered collection is then piped to the **Remove-CsAVEdgeConfiguration** cmdlet, which deletes each item in that collection.

    Get-CsAVEdgeConfiguration | Where-Object {$_.MaxBandwidthPerUserKB -lt 5000} | Remove-CsAVEdgeConfiguration

</div>

</div>

<div>

## Detailed Description

An A/V Edge server provides a way for audio and video traffic to be exchanged across an organization’s firewall. Among other things, this enables users to use Lync Server across the Internet, and then exchange audio and video data with users who have logged onto the system from inside the firewall. Edge Server configuration settings can be assigned at the global scope, the site scope, and the service scope. The A/V Edge configuration settings enable administrators to do such things as manage the amount of time that user authentication is valid before it must be renewed, and to limit the amount of bandwidth that can be used by a single user or a single port.

The **Remove-CsAVEdgeConfiguration** cmdlet enables you to delete A/V Edge configuration settings that have been applied to either the site or the service scope. The cmdlet can also be run against the global settings; however, those global settings will not be deleted. Instead, the properties contained within the global collection will all be reset to their default values.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsAVEdgeConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAVEdgeConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the collection of A/V Edge configuration settings to be removed. To &quot;remove&quot; the global collection, use the following syntax: -Identity global. (As noted previously, the global settings cannot be removed; the properties can only be reset to their default values.) To remove a site collection, use syntax similar to this: -Identity site:Redmond. Settings configured at the service scope should be referred to using syntax similar to this:</p>
<p>-Identity service:EdgeServer:atl-cs-001.litwareinc.com</p>
<p>You cannot use wildcards when specifying a policy Identity.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object. The **Remove-CsAVEdgeConfiguration** cmdlet accepts pipelined input of media relay settings objects. These objects retrieved by running the **Get-CsAVEdgeConfiguration** cmdlet.

</div>

<div>

## Return Types

The **Remove-CsAVEdgeConfiguration** cmdlet does not return a value or object. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings object.

</div>

<div>

## See Also


[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

