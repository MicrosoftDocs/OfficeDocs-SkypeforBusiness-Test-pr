﻿---
title: Get-CsImFilterConfiguration
TOCTitle: Get-CsImFilterConfiguration
ms:assetid: de9b24a1-8d17-4da1-89c2-db5b532674eb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398980(v=OCS.15)
ms:contentKeyID: 48185608
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsImFilterConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Returns the instant messaging (IM) link filters configured in your organization. These filters are used to prevent users from sending instant messages that contain hyperlinks with specific prefixes (for example, links with an http or telnet prefix). Depending on your settings, this means that any Uniform Resource Identifier (URI) prefaced with one of these schemes will be converted to a non-clickable hyperlink or removed altogether. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsImFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsImFilterConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the IM hyperlink filters configured for use in your organization. This is the behavior any time you call the **Get-CsImFilterConfiguration** cmdlet without any additional parameters.

    Get-CsImFilterConfiguration

</div>

<div>

## EXAMPLE 2

Example 2 returns settings for one IM filter: the settings that have the Identity site:Redmond. Because identities must be unique, this command can never return more than one configuration.

    Get-CsImFilterConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

Example 3 uses the Filter parameter to return a collection of all the IM filters that have been configured at the site level. The wildcard string site:\* instructs the **Get-CsImFilterConfiguration** cmdlet to return only those IM filter configurations that have an Identity that begins with the string value site:.

    Get-CsImFilterConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

In Example 4 the value of the global IM filter configuration’s Prefixes property is "expanded" when displayed on the screen; this simply means that the property and its values are shown in a more user-friendly and readable format. To perform this task, the **Get-CsImFilterConfiguration** cmdlet is first used to retrieve the global IM filter configuration. (Note that the call to the **Get-CsImFilterConfiguration** cmdlet is enclosed in parentheses. That tells Windows PowerShell to first carry out the command enclosed in parentheses, and then continue on from there.) After the configuration has been retrieved, the value of the Prefixes property is displayed with one prefix on each line.

    (Get-CsImFilterConfiguration -Identity Global).Prefixes

</div>

</div>

<div>

## Detailed Description

When sending instant messages, users can embed a URI within the text of that message to refer other participants in the conversation to a particular web site or share. Lync Server can be configured so that hyperlinks with certain prefixes are blocked or are not active. (In other words, the participants can’t simply click the link and go to the site the URI refers to; they must copy and paste the link manually into a browser.)

The **Get-CsImFilterConfiguration** cmdlet retrieves all the settings for filtering URIs from instant messages. Called by itself (with no parameters), the **Get-CsImFilterConfiguration** cmdlet returns all URI IM filter settings, globally and for all sites. You can also specify an Identity to show the settings for a specific site (or the global settings).

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsImFilterConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsImFilterConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Performs a wildcard search for configurations matching a given Identity pattern. For example, returns all settings with identities beginning with site* (all site-specific settings).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the settings you want to retrieve. This will be either global or site:&lt;site name&gt;, where &lt;site name&gt; is the name of the site to which these settings apply, such as site:Redmond.</p>
<p>Full Data Type: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the IM filter configuration from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

The **Get-CsImFilterConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration object.

</div>

<div>

## See Also


[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

