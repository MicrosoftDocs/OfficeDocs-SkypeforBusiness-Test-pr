﻿---
title: Remove-CsVoiceNormalizationRule
TOCTitle: Remove-CsVoiceNormalizationRule
ms:assetid: 6a1bf26c-d95b-4a03-8d2d-c17159dcb9be
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398501(v=OCS.15)
ms:contentKeyID: 48184391
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsVoiceNormalizationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes a voice normalization rule. Voice normalization rules are used to convert telephone dialing requirements (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsVoiceNormalizationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the voice normalization rule with the Identity site:Redmond/SeattleRule1.

    Remove-CsVoiceNormalizationRule -Identity site:Redmond/SeattleRule1

</div>

<div>

## EXAMPLE 2

This example removes all voice normalization rules from site Redmond.

    Remove-CsVoiceNormalizationRule -Identity site:Redmond

</div>

</div>

<div>

## Detailed Description

This cmdlet removes a named voice normalization rule. These rules are a required part of phone authorization and call routing. They define the requirements for converting (or translating) numbers from an internal Lync Server format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.

Rules that are removed by using this cmdlet will be deleted from the dial plans of the organization, so they won’t be returned by the **Get-CsVoiceNormalizationRule** cmdlet and will not appear in the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet. This means that calling the **Remove-CsVoiceNormalizationRule** cmdlet could leave a dial plan with no normalization rules.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceNormalizationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceNormalizationRule"}

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
<td><p>The unique identity of the rule to be removed. If the Identity specified includes the scope followed by a slash and then the name (for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name), the one rule with that unique Identity will be removed. If the value passed to the Identity contains only the scope (site:Redmond), all normalization rules at that scope will be removed.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object. Accepts pipelined input of voice normalization rule objects.

</div>

<div>

## Return Types

This cmdlet deletes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule.

</div>

<div>

## See Also


[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

