﻿---
title: Remove-CsVoiceConfiguration
TOCTitle: Remove-CsVoiceConfiguration
ms:assetid: 9b173dde-fa8e-4966-aa58-deff34625560
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398804(v=OCS.15)
ms:contentKeyID: 48184974
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsVoiceConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Resets the voice configuration to its default values. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsVoiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example resets the Global (and only) voice configuration to the default values. This action deletes all defined voice test configurations, so we added the Confirm parameter in order to receive a prompt asking whether we really want to perform this action before the removal takes place.

    Remove-CsVoiceConfiguration -Identity Global -Confirm

</div>

</div>

<div>

## Detailed Description

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet removes the global (and only) voice configuration, which is a container for all voice test configurations defined for a Lync Server deployment. "Removing" the voice configuration doesn’t actually remove it; the global instance is still there. However, it does set the list of voice test configurations to the default, which is empty.

WARNING: Removing the voice configuration (which sets the list of voice test configurations to empty) deletes all defined voice test configurations for a Lync Server deployment. After calling this cmdlet, a call to the **Get-CsVoiceTestConfiguration** cmdlet will return no results.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceConfiguration"}

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
<td><p>The scope of the voice configuration to remove. This value must be Global.</p></td>
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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object. Accepts pipelined input of a voice configuration object.

</div>

<div>

## Return Types

This cmdlet removes (resets) an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration.

</div>

<div>

## See Also


[Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

