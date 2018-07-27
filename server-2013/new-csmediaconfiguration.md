﻿---
title: New-CsMediaConfiguration
TOCTitle: New-CsMediaConfiguration
ms:assetid: 3b60c36f-f824-4948-aa46-6745b40b9641
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425881(v=OCS.15)
ms:contentKeyID: 48183867
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsMediaConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

Creates a new collection of media settings. These settings can be used to specify such things as the supported level of encryption and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableQoS <$true | $false>] [-EnableSiren <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 uses the **New-CsMediaConfiguration** cmdlet to create a new media configuration with the Identity site:Redmond1. This new configuration requires both parties involved in a multimedia conversation to use encryption. That requirement is put in place by adding the EncryptionLevel parameter and setting the parameter value to RequireEncryption.

    New-CsMediaConfiguration -Identity site:Redmond1 -EncryptionLevel RequireEncryption

</div>

<div>

## EXAMPLE 2

This example uses the **New-CsMediaConfiguration** cmdlet to create a new media configuration with the Identity MediationServer:pool0.litwareinc.com. This new configuration will have an EnableSiren value of True, which means that Siren is enabled for calls involving this Mediation Server.

    New-CsMediaConfiguration -Identity MediationServer:pool0.litwareinc.com -EnableSiren $True

</div>

</div>

<div>

## Detailed Description

This cmdlet creates a new collection of settings that define behaviors for specific media actions.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsMediaConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsMediaConfiguration"}

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
<td><p>A unique identifier specifying the scope at which this configuration is applied (site or service). A configuration at the site scope would be entered as site:&lt;site name&gt;, such as site:Redmond. A service would be entered as &lt;server role&gt;:&lt;fqdn&gt;, such as MediationServer:pool0.litwareinc.com. A media configuration at the global scope will always exist and cannot be removed, so a new global configuration cannot be created.</p>
<p>Media configurations created at the service scope can be created only for the A/V Conferencing service, Mediation Server, and Application Server.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableQoS</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoS monitors the quality of voice signals over a network.</p>
<p>Default: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableSiren</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>By default, the Mediation Server does not negotiate Siren as a possible codec for calls between itself and other Lync clients. If this setting is True, Siren will be included as a possible codec for use between the Mediation Server and other Lync clients.</p>
<p>Default: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EncryptionLevel</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel</p></td>
<td><p>The level of encryption between unified communications devices.</p>
<p>Valid values:</p>
<p>SupportEncryption - secure real-time transport protocol (SRTP) will be used if it can be negotiated.</p>
<p>RequireEncryption - SRTP must be negotiated.</p>
<p>DoNotSupportEncryption - SRTP must not be used.</p>
<p>Default: RequireEncryption</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxVideoRateAllowed</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.MaxVideoRateAllowed</p></td>
<td><p>The maximum rate at which video signals will be transferred at the client endpoints.</p>
<p>Valid values: Hd720p15M, VGA600K, CIF250K</p>
<p>Hd720p15M - High definition, with a resolution of 1280 x 720 and aspect ratio 16:9.</p>
<p>VGA600K - VGA, with a resolution of 640 x 480, 25 fps with the aspect ratio 4:3.</p>
<p>CIF250K - Common Intermediate Format (CIF) video format, 15 fps with a resolution of 352 x 288.</p>
<p>Note that these values are not case sensitive; values will be converted to appropriate casing when the configuration is created.</p>
<p>Default: VGA600K</p></td>
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

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings.

</div>

<div>

## See Also


[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

