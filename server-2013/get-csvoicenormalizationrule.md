﻿---
title: Get-CsVoiceNormalizationRule
TOCTitle: Get-CsVoiceNormalizationRule
ms:assetid: 59fe1370-1cec-4cf9-8f65-029a7c2454d1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398393(v=OCS.15)
ms:contentKeyID: 48184219
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsVoiceNormalizationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the voice normalization rules used in your organization. Voice normalization rules convert telephone dialing requirements (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceNormalizationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example retrieves all voice normalization rules defined for the organization.

    Get-CsVoiceNormalizationRule

</div>

<div>

## EXAMPLE 2

Example 2 retrieves all voice normalization rules specified for all sites.

    Get-CsVoiceNormalizationRule -Filter site*

</div>

<div>

## EXAMPLE 3

Example 3 retrieves all voice normalization rules with the letter s anywhere in the scope. For example, this will return all site- and service-level rules, as well as per-user rules with an s in the scope name, such as RedmondEastUsers.

    Get-CsVoiceNormalizationRule -Filter *s*

</div>

<div>

## EXAMPLE 4

The Filter parameter used in Examples 2 and 3 matches only on the scope portion of the Identity. This example performs a match on the name portion to return all rules with a Name containing the string "seattle". To do this, we first call the **Get-CsVoiceNormalizationRule** cmdlet to retrieve all the normalization rules for the organization. We then pipe this collection to the **Where-Object** cmdlet to find all the items in the collection where the Name property matches the string "seattle".

    Get-CsVoiceNormalizationRule | Where-Object {$_.Name -match "seattle"}

</div>

</div>

<div>

## Detailed Description

This cmdlet returns a named voice normalization rule or a collection of voice normalization rules. These rules are a required part of phone authorization and call routing. They define the requirements for converting--or translating--numbers from an internal Lync Server format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.

The same rules accessed by this cmdlet can also be accessed through the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoiceNormalizationRule** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceNormalizationRule"}

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
<td><p>Uses wildcard strings to return a collection of normalization rules based on Identity. Note that Filter works only on the scope portion of the Identity, not on the name. For example, the filter value *lob* will return all rules at the global scope (scopes that contain the letters lob), but not a rule with the identity site:Redmond/lobby, where lob is only in the name portion of the identity, not the scope.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>A unique identifier for the rule. If a value is specified for this parameter, it must be in the format scope/name; for example, site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the voice normalization rule from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

The **Get-CsVoiceNormalizationRule** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object.

</div>

<div>

## See Also


[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Get-CsDialPlan](get-csdialplan.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

