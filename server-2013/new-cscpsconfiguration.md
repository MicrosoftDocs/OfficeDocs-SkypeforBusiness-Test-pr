﻿---
title: New-CsCpsConfiguration
TOCTitle: New-CsCpsConfiguration
ms:assetid: bc740858-0e00-48ae-883e-67b3b7a03528
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412919(v=OCS.15)
ms:contentKeyID: 48185258
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsCpsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Creates a new collection of Call Park service settings. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone by entering the correct number. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsCpsConfiguration -Identity <XdsIdentity> [-CallPickupTimeoutThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnableMusicOnHold <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxCallPickupAttempts <Int32>] [-OnTimeoutURI <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 uses the **New-CsCpsConfiguration** cmdlet to create a Call Park service configuration for site Redmond. This configuration will be created with default values with the exception of EnableMusicOnHold. This command sets this property to False, meaning the caller whose call has been parked will not hear anything while on hold. (EnableMusicOnHold is set to True by default, assuming Call Park service has been deployed.)

    New-CsCpsConfiguration -Identity site:Redmond -EnableMusicOnHold $False

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 uses the **New-CsCpsConfiguration** cmdlet to create a Call Park service configuration for site Redmond1. By default no OnTimeoutURI is supplied, so this example adds a value for that parameter. In this case the OnTimeoutURI is set to sip:kenmyer@litwareinc.com. The value passed to this parameter must begin with the string "sip:" and should point to a user or Response Group that will receive parked calls that aren’t picked up after a specified number of ringback attempts.

    New-CsCpsConfiguration -Identity site:Redmond -OnTimeoutURI sip:kenmyer@litwareinc.com

</div>

<div>

## EXAMPLE 3

This command uses the **New-CsCpsConfiguration** cmdlet to create a Call Park service configuration for site Redmond1. For this site, the MaxCallPickupAttempts has been set to 2. That means the call rings back up to two times.

    New-CsCpsConfiguration -Identity site:Redmond -MaxCallPickupAttempts 2

</div>

</div>

<div>

## Detailed Description

This cmdlet is used to create a new Call Park service configuration. When Call Park service is installed, global settings are configured by default and can be updated but cannot be removed. ("Removing" the global settings simply resets them to the default values.) Therefore this cmdlet is used to create only site-specific settings.

A Call Park service configuration specifies what happens to a call once it’s parked. For example, if a parked call isn’t answered after a period of time it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can be configured to ring after a certain period of time to ensure the call isn’t forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsCpsConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCpsConfiguration"}

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
<td><p>The site to which the settings are applied. This must be entered in the format site:&lt;sitename&gt;, such as site:Redmond. A configuration will always exist at the global scope and can’t be removed, so a global configuration can’t be re-created with this cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>CallPickupTimeoutThreshold</em></p></td>
<td><p>Optional</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>The amount of time that will elapse after a call has been parked before it will ring back to the phone on which the call was answered.</p>
<p>This must be entered in the format hh:mm:ss (hh = hours, mm = minutes, ss = seconds)</p>
<p>Default: 00:01:30 (90 seconds); Minimum Value: 10 seconds (00:00:10); Maximum Value: 10 minutes (00:10:00)</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMusicOnHold</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Determines whether music plays for the caller while a call is parked.</p>
<p>Lync Server ships with a default Music on Hold file. You can change this file (thereby changing the music the caller hears while parked) with the <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet.</p>
<p>Default: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCallPickupAttempts</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>The number of times a parked call will ring back to the answering phone before giving up and forwarding the call to the fallback Uniform Resource Identifier (URI). The fallback URI is set with the OnTimeoutURI parameter.</p>
<p>Default: 1; Minimum Value: 1; Maximum Value: 10</p></td>
</tr>
<tr class="even">
<td><p><em>OnTimeoutURI</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The SIP address of the user or Response Group to which unanswered parked calls will be routed. The parked call will be routed after the number of ringbacks defined with the MaxCallPickupAttempts parameter. If that parameter is set to Null, the OnTimeoutURI will be ignored and the parked call will be disconnected after unsuccessful ringback attempts.</p>
<p>Values must be SIP URIs, beginning with the string sip:. For example, sip:rgs1@litwareinc.com.</p></td>
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

This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

</div>

<div>

## See Also


[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

