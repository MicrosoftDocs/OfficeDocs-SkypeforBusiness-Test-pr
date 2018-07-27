﻿---
title: New-CsOutboundCallingNumberTranslationRule
TOCTitle: New-CsOutboundCallingNumberTranslationRule
ms:assetid: 959591bb-4a6b-4b7f-9666-da1fa0f9cd43
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205097(v=OCS.15)
ms:contentKeyID: 48184842
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsOutboundCallingNumberTranslationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Creates a new outbound calling number translation rule. An outbound calling number translation rule converts the E.164 phone numbers used by Lync Server 2013 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsOutboundCallingNumberTranslationRule -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsOutboundCallingNumberTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new outbound calling number translation rule that converts an E.164 number that begins with the string value +1206 (for example, +12065551219) to a seven-digit value (for example, 5551219, stripping off the +1206).

    New-CsOutboundCallingNumberTranslationRule -Parent "site:Redmond" -Name SevenDigit -Description "Converts a dialed number to seven digits" -Pattern '^\+1206(\d{7})$' -Translation '$1'

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Outbound calling number translation rules convert the E.164 phone numbers used by Lync 2013 to a format that can be used by trunking peers that do not support E.164 numbers; when you create a translation rule you supply a regular expression representing the outbound E.164 number (the Pattern) as well as a regular expression representing the converted number (the Translation).

Outbound calling number translation rules must be bound to a collection of trunk configuration settings; when you create a new translation rule you must specify both the Identity of the trunking configuration settings and a name for the new rule (for example, site:Redmond/RedmondTranslationRule). Note that the trunking configuration settings do not necessarily have to exist at the time you create a new rule. For example, suppose you create the rule site:Redmond/RedmondTranslationRule but no trunk configuration settings have been created for the Redmond site. If the Redmond site is a valid site, trunk configuration settings will automatically be created for the site and the new translation rule will be assigned to that collection of settings. However, your command will fail if the Redmond site does not exist.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsOutboundCallingNumberTranslationRule"}

**Lync Server Control Panel:** To create a new outbound calling number translation rule using the Lync Server Control Panel, click Voice Routing then click Trunk Configuration, and then double-click the appropriate item in the Name column. In the Edit Trunk Configuration dialog box scroll down to the section labeled Calling number translation rules and then click New.

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
<td><p>Unique identifier for the new translation rule. Names are composed of the scope (parent), a &quot;/&quot; character, and a unique name within that scope. For example, a rule named RedmondDialing created for the Redmond site would have an Identity that looked like this:</p>
<p>-Identity &quot;site:Redmond/RedmondDialing&quot;</p>
<p>If you use the Identity parameter then your command cannot contain either the Parent or the Name parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Name for the new translation rule; names must be unique for the given scope. For example:</p>
<p>-Name &quot;RedmondDialing&quot;</p>
<p>Any time you use the Name parameter you must also use the Parent parameter. The Name parameter cannot be used in the same command as the Identity parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Scope at which the new translation rule will be configured. To configure a rule at the global scope, use this syntax:</p>
<p>-Parent &quot;global&quot;</p>
<p>To configure a rule at the site scope, use syntax similar to this:</p>
<p>-Parent &quot;site:Redmond&quot;</p>
<p>To configure a rule at the service scope (for the PstnGateway service only) use syntax like this:</p>
<p>-Parent &quot;service:PstnGateway:192.168.0.100&quot;</p>
<p>Any time you use the Parent parameter you must also use the Name parameter. The Parent parameter cannot be used in the same command as the Identity parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables administrators to provide additional text to accompany a translation rule. This description can be used to help administrators clearly identify the purpose of the rule.</p></td>
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
<td><p><em>Pattern</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A regular expression representing the number pattern to which the Translation will be applied.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>Priority assigned to the rule. If a number matches the Pattern of more than one outbound translation rule, rules are applied in priority order. Rules are processed in order of their assigned priority; the first rule to be processed has a priority of 0; the second rule to be processed has a priority of 1; and so on.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A regular expression that will be applied to the number matching the Pattern to prepare that number for outbound calling.</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

None. The **New-CsOutboundCallingNumberTranslationRule** cmdlet does not accept pipelined data.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsOutboundCallingNumberTranslationRule** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated object.

</div>

<div>

## See Also


[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

