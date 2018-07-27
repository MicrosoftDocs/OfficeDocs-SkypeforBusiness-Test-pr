﻿---
title: Set-CsMediaConfiguration
TOCTitle: Set-CsMediaConfiguration
ms:assetid: 768bc273-5253-4569-895d-5b1127386b92
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398580(v=OCS.15)
ms:contentKeyID: 48184543
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsMediaConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

Modifies an existing collection of media settings. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsMediaConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableQoS <$true | $false>] [-EnableSiren <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 modifies the media configuration collection with the Identity site:Redmond1; in particular, the command sets the value of the MaxVideoRateAllowed property to Hd720p15M. Note that the value passed to the MaxVideoRateAllowed parameter must be one of the values specified in the parameter description. Also note that the values are not case sensitive; the value entered here as hd720p15m will be automatically converted to the appropriate casing (in this instance, to Hd720p15M).

    Set-CsMediaConfiguration -Identity site:Redmond1 -MaxVideoRateAllowed hd720p15m

</div>

<div>

## EXAMPLE 2

This example modifies the media configuration collection with the Identity site:Redmond1 to have an EncryptionLevel value of DoNotSupportEncryption. Note that this value is not case sensitive; the value was entered as donotsupportencryption, but that value will be accepted as a valid value and will be automatically changed to mixed case (DoNotSupportEncryption).

    Set-CsMediaConfiguration site:Redmond1 -EncryptionLevel donotsupportencryption

</div>

</div>

<div>

## Detailed Description

This cmdlet modifies a collection of settings that define media configuration. These actions relate to audio and video calls between client endpoints.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsMediaConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMediaConfiguration"}

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
<td><p><em>EnableQoS</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoS monitors the quality of voice signals over a network.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSiren</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>By default, the Mediation Server does not negotiate Siren as a possible codec for calls between itself and other Lync clients. If this setting is True, Siren will be included as a possible codec for use between the Mediation Server and other Lync clients.</p></td>
</tr>
<tr class="even">
<td><p><em>EncryptionLevel</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel</p></td>
<td><p>The level of encryption between unified communications devices.</p>
<p>Valid values:</p>
<p>SupportEncryption - secure real-time transport protocol (SRTP) will be used if it can be negotiated.</p>
<p>RequireEncryption - SRTP must be negotiated.</p>
<p>DoNotSupportEncryption - SRTP must not be used.</p>
<p>This value is not case sensitive. (For details, see the Examples in this topic.)</p>
<p>Default: RequireEncryption</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the media configuration settings you want to change. This identifier specifies the scope at which this configuration is applied (global, site, or service).</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>MediaSettings</p></td>
<td><p>An instance of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object. You can retrieve this object by calling the <strong>Get-CsMediaConfiguration</strong> cmdlet with a specific Identity. You can then assign new values to the properties of that object, and then save those changes by passing the object to the <strong>Set-CsMediaConfiguration</strong> cmdlet.</p></td>
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
<p>Note that these values are not case sensitive; values will be converted to appropriate casing when the configuration is created. (For details, see the Examples in this topic.)</p>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object. Accepts pipelined input of media configuration objects.

</div>

<div>

## Return Types

The **Set-CsMediaConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object.

</div>

<div>

## See Also


[New-CsMediaConfiguration](new-csmediaconfiguration.md)  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

