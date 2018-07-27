﻿---
title: Remove-CsVoicemailReroutingConfiguration
TOCTitle: Remove-CsVoicemailReroutingConfiguration
ms:assetid: 758cea84-5979-417c-a0cd-c76748e0da79
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398573(v=OCS.15)
ms:contentKeyID: 48184530
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsVoicemailReroutingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the voice mail rerouting configuration settings for the site Redmond1.

    Remove-CsVoicemailReroutingConfiguration -Identity site:Redmond1

</div>

<div>

## EXAMPLE 2

This example removes all the voice mail rerouting settings for this deployment of Lync Server. The command first retrieves all the voice mail rerouting configuration settings by calling the **Get-CsVoicemailReroutingConfiguration** cmdlet. The settings retrieved by this call are then passed to the **Remove-CsVoicemailReroutingConfiguration** cmdlet to delete each one.

    Get-CsVoicemailReroutingConfiguration | Remove-CsVoicemailReroutingConfiguration

</div>

</div>

<div>

## Detailed Description

This cmdlet allows you to remove settings that determine where Auto Attendant and Subscriber Access calls are rerouted to over PSTN when IP connectivity is lost.

Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company’s phone system to reach the desired department or employee or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).

Note that if you call this cmdlet to remove the Global settings, those settings will simply be reset to their defaults.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoicemailReroutingConfiguration"}

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
<td><p>The unique identifier of the configuration you want to remove. For this cmdlet the Identity will be either Global or Site:&lt;site name&gt;, where &lt;site name&gt; is the name of the site to which the settings are applied.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration object. Accepts pipelined input of voice mail rerouting configuration objects.

</div>

<div>

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.

</div>

<div>

## See Also


[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

