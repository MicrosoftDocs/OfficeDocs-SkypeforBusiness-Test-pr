﻿---
title: Set-CsDiagnosticHeaderConfiguration
TOCTitle: Set-CsDiagnosticHeaderConfiguration
ms:assetid: e9243b84-63c7-4ee1-8568-6b4417e10b0c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399045(v=OCS.15)
ms:contentKeyID: 48185900
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsDiagnosticHeaderConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Modifies an existing diagnostic header configuration setting collection currently in use in your organization. Diagnostic header configuration settings determine whether SIP messages are accompanied by header information that can be useful in troubleshooting and error reporting. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsDiagnosticHeaderConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDiagnosticHeaderConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-SendToExternalNetworks <$true | $false>] [-SendToOutsideUnauthenticatedUsers <$true | $false>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 modifies the diagnostic header configuration settings that have the Identity site:Redmond. In this example, the value of the SendToOutsideUnauthenticatedUsers property is set to True.

    Set-CsDiagnosticHeaderConfiguration -Identity site:Redmond -SendToOutsideUnauthenticatedUsers $True

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1; in this case, however, the SendToOutsideUnauthenticatedUsers property is modified for all the diagnostic header configuration settings in use. To do this, the **Get-CsDiagnosticHeaderConfiguration** cmdlet is first called without any parameters; this returns a collection of all the diagnostic header settings currently in use. This collection is then piped to the **Set-CsDiagnosticHeaderConfiguration** cmdlet, which sets the SendToOutsideUnauthenticatedUsers property of each item in the collection to True.

    Get-CsDiagnosticHeaderConfiguration | Set-CsDiagnosticHeaderConfiguration -SendToOutsideUnauthenticatedUsers $True

</div>

<div>

## EXAMPLE 3

In Example 3, the SendToOutsideUnauthenticatedUsers property is modified again, but this time only for those diagnostic header settings where the SendToExternalNetworks property is True. To carry out this task, the command first uses the **Get-CsDiagnosticHeaderConfiguration** cmdlet to return a collection of all the diagnostic header configuration settings currently in use. That collection is piped to the **Where-Object** cmdlet, which selects only those settings where the SendToExternalNetworks property is equal to True. That filtered collection is then piped to the **Set-CsDiagnosticHeaderConfiguration** cmdlet, which sets the value of the SendToOutsideUnauthenticatedUsers property for each item in the collection to True.

    Get-CsDiagnosticHeaderConfiguration | Where-Object {$_.SendToExternalNetworks -eq $True} | Set-CsDiagnosticHeaderConfiguration -SendToOutsideUnauthenticatedUsers $True

</div>

</div>

<div>

## Detailed Description

Administrators have the option of attaching an ms-diagnostic header to each SIP message sent in their organization. This message (which is not visible to end users) contains information that might be useful in troubleshooting connection problems or in reporting errors. For example, the diagnostic header might contain error codes that enable the client application (for example, Lync Server) to take a predetermined course of action should a specific situation arise.

For SIP messages sent within your internal network, there’s little reason not to include these diagnostic headers: they have a minimal impact on message size and can be an invaluable tool for administrators trying to troubleshoot connectivity problems. However, diagnostic headers also contain information -- such as the fully qualified domain names (FQDNs) of your SIP servers -- that you might not want to make available to people outside the internal network. Because of this, the diagnostic header configuration settings enable you to decide whether you want diagnostic headers sent to users on external networks (such as users in a federated domain) and/or to outside users. (Outside users are users who have connected from outside the internal network and have not yet been authenticated.)

By default, headers are not included in messages sent either to external networks or to unauthenticated users. However, you can modify the global diagnostic header settings to include headers to external networks and/or unauthenticated users. Alternatively, you can create custom settings at the site scope or at the service scope (for the Edge Server or Registrar service). That way, you can choose to include diagnostic headers on messages sent from one site, or through one Edge Server, while disallowing headers on messages sent from other sites or through other Edge Servers.

The **Set-CsDiagnosticHeaderConfiguration** cmdlet provides a way for you to modify an existing diagnostic header configuration setting collection. You can use this cmdlet to enable (or disable) the transmission of diagnostic headers to external networks and/or to outside users.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsDiagnosticHeaderConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDiagnosticHeaderConfiguration"}

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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the diagnostic header configuration settings to be modified. To modify settings configured at the site scope, use syntax similar to this: -Identity &quot;site:Redmond&quot;. To modify settings configured at the service scope, use syntax like this: -Identity &quot;service:EdgeServer:atl-cs-001.litwareinc.com&quot;. To modify the global settings, use this syntax: -Identity global.</p>
<p>If this parameter is not specified, then the <strong>Set-CsDiagnosticHeaderConfiguration</strong> cmdlet will automatically modify the global settings.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>DiagnosticHeaderSettings object</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>SendToExternalNetworks</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, diagnostic headers will be attached to messages sent to users on external networks (such as users in a federated domain). The default value is False.</p></td>
</tr>
<tr class="even">
<td><p><em>SendToOutsideUnauthenticatedUsers</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, diagnostic headers will be attached to messages sent to outside users. Outside users are users who have connected from outside the internal network (for example, through a proxy server) and have not yet been authenticated.</p>
<p>The default value is False.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings object. The **Set-CsDiagnosticHeaderConfiguration** cmdlet accepts pipelined instances of the diagnostic header settings object.

</div>

<div>

## Return Types

The **Set-CsDiagnosticHeaderConfiguration** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings object.

</div>

<div>

## See Also


[Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)  
[New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)  
[Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

