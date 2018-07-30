﻿---
title: New-CsClsProvider
TOCTitle: New-CsClsProvider
ms:assetid: 9b0a90c1-27ab-49c8-88f2-a381cf14625e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619187(v=OCS.15)
ms:contentKeyID: 49733752
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsClsProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-10_

Creates a new centralized logging trace provider. Trace providers are application components that generate trace messages or trace events useful in troubleshooting problems with Lync Server. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsClsProvider -Flags <String> -Level <All | Fatal | Error | Warning | Info | Verbose | Debug> -Name <String> -Type <WPP | EventLog | IISLog> [-Guid <String>] [-Role <String>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 create a new centralized logging scenario provider and then add that provider to the WAC scenario configured for the Redmond site. To do this, the first command in the example uses the **New-CsClsProvider** cmdlet to create a new provider with the name WebInfrastructure; this new provider is stored in a variable named $provider. The second command in the example then adds this new provider to the scenario site:Redmond/WAC. Because the command uses the syntax @{Add=$provider} the new provider will be added to the WAC scenario in addition to any other providers already configured for that

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Add=$provider}

</div>

<div>

## Example 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the new provider will replace any (and all) the existing providers configured for the WAC scenario. This is done by using the syntax @{Replace=$provider}.

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Replace=$provider}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.

Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Lync Server. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.

Each centralized logging scenario requires one or more trace providers to generate the messages and events that are logged in the trace logs. Lync Server 2013 ships with a large number of these providers predefined for you. The **New-CsClsProvider** cmdlet provides a way for developers who are extending Lync Server to take advantage of centralized logging for custom new application/component.

It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClsProvider"}

Lync Server Control Panel: The functions carried out by the **New-CsClsProvider** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Flags</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Specifies individual protocols and subcomponents involved in the trace. For example, the SipStack provider includes the following flags: TF_COMPONENT, TF_RTCHTTP, TF_CONNECTION, TF_DIAG.</p>
<p>Most providers are configured to use all available flags.</p></td>
</tr>
<tr class="even">
<td><p><em>Level</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderLevel</p></td>
<td><p>Tracing level for events recorded by the provider: Allowed values are:</p>
<p>* Fatal</p>
<p>* Error</p>
<p>* Warning</p>
<p>* Info</p>
<p>* Verbose</p>
<p>* Debug</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Unique name for the new provider.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderType</p></td>
<td><p>Type of tracing used by the provider. Allowed values are:</p>
<p>* WPP (Windows software trace preprocessor)</p>
<p>* EventLog</p>
<p>* IISLog</p></td>
</tr>
<tr class="odd">
<td><p><em>Guid</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Globally unique identifier assigned to the provider.</p></td>
</tr>
<tr class="even">
<td><p><em>Role</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server server role for the provider. For example, FE for Front End server or Edge for Edge Server.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The New-CsClsProvider cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The New-CsClsProvider cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Provider object.

</div>

<div>

## See Also


[New-CsClsScenario](new-csclsscenario.md)  
[Set-CsClsScenario](set-csclsscenario.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

