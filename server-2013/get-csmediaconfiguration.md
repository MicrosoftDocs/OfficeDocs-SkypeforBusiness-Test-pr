﻿---
title: Get-CsMediaConfiguration
TOCTitle: Get-CsMediaConfiguration
ms:assetid: 071c1733-07c3-4075-8745-367634e37941
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398128(v=OCS.15)
ms:contentKeyID: 48183321
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsMediaConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information regarding media settings, including the supported level of encryption, whether Siren can be used as a voice codec by the Mediation Server in its interactions with Lync Server clients, and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsMediaConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns all the media configurations in use in your organization; this is done simply by invoking the **Get-CsMediaConfiguration** cmdlet without any additional parameters.

    Get-CsMediaConfiguration

</div>

<div>

## EXAMPLE 2

Example 2 returns only the media configuration that has the Identity site:Redmond1. Because identities must be unique, specifying an Identity ensures that you will never retrieve more than one item.

    Get-CsMediaConfiguration -Identity site:Redmond1

</div>

<div>

## EXAMPLE 3

In Example 3, the Filter parameter is used to return all the media configurations at the site scope. The wildcard string site:\* ensures that Windows PowerShell will return only those media configurations that have identities beginning with the string value site:.

    Get-CsMediaConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

In this example, the **Get-CsMediaConfiguration** cmdlet and the **Where-Object** cmdlet are used to return all the media configurations that support (but do not require) encryption. To do this, the command first uses the **Get-CsMediaConfiguration** cmdlet to retrieve all the media configurations in use in your organization. This information is then piped to the **Where-Object** cmdlet, which applies a filter that restricts the returned data to those configurations where the EncryptionLevel property is equal to (-eq) SupportEncryption.

    Get-CsMediaConfiguration | Where-Object {$_.EncryptionLevel -eq "SupportEncryption"}

</div>

<div>

## EXAMPLE 5

This example retrieves all media configurations defined for sites and services with names that contain the string "med". For example, this command will retrieve media configuration settings defined for the site medford1, the site TwoMedfordPlace, and the service MediationServer:redmond.litwareinc.com.

    Get-CsMediaConfiguration -Filter *:*med*

</div>

</div>

<div>

## Detailed Description

This cmdlet retrieves one or more collections of settings that define media interactions.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsMediaConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsMediaConfiguration"}

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
<td><p>This parameter filters the results of the Get operation based on the wildcard value passed to this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the media configuration you want to retrieve. This identifier specifies the scope at which this configuration is applied (global, site, or service).</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the media configuration information from the local replica of the Central Management store, rather than from the Central Management store itself.</p></td>
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

The **Get-CsMediaConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object.

</div>

<div>

## See Also


[New-CsMediaConfiguration](new-csmediaconfiguration.md)  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

