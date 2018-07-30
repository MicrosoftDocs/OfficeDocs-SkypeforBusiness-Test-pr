﻿---
title: Get-CsPublicProvider
TOCTitle: Get-CsPublicProvider
ms:assetid: c122505d-7209-4dcb-a888-5c73f58fa68a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412945(v=OCS.15)
ms:contentKeyID: 48185312
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPublicProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about the public providers configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. Lync Server ships with three public providers configured but not enabled: Yahoo\!, AIM (AOL), and Messenger (MSN). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPublicProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the public providers that are configured for use in the organization. Calling the **Get-CsPublicProvider** cmdlet without any additional parameters always returns the complete collection of public providers.

    Get-CsPublicProvider

</div>

<div>

## EXAMPLE 2

In Example 2, all the public providers that have the Identity Messenger are returned. Because Identities must be unique among public providers (and among hosting providers), this command will always return, at most, a single item.

    Get-CsPublicProvider -Identity "Messenger"

</div>

<div>

## EXAMPLE 3

Example 3 returns all the public providers that have an Identity that begins with the letter W. This is done by including the Filter parameter and the filter value "W\*".

    Get-CsPublicProvider -Filter W*

</div>

<div>

## EXAMPLE 4

The command shown in Example 4 returns a collection of all the public providers that are currently disabled. To do this, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those providers where the Enabled property is equal to False.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False}

</div>

<div>

## EXAMPLE 5

Example 5 returns all the public providers where the VerificationLevel property is set to either AlwaysUnverifiable or UseSourceVerification. (Verification levels can be set to AlwaysUnverifiable; UseSourceVerification; or AlwaysVerifiable.) To perform this task, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those providers where the VerificationLevel property is not equal to AlwaysVerifiable. The net effect: only providers where the VerificationLevel property is set to either AlwaysUnverifiable or UseSourceVerification will be selected.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"}

</div>

</div>

<div>

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Lync 2013. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.

A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Messenger (MSN), then your users will be able to exchange instant messages and presence information with anyone who has a Messenger instant messaging account.

In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) The **Get-CsPublicProvider** cmdlet enables you to return information about the public providers that have been configured for use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPublicProvider** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPublicProvider"}

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
<td><p>Enables you to use wildcard values in order to return one or more public providers. For example, to return a collection of all the public providers that have an Identity that begins with the letter Y, use this syntax: -Filter &quot;Y*&quot;. To return a collection of all the public providers that include the string value &quot;Windows&quot; anywhere in their Identity, use this syntax: -Filter &quot;*Windows*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique identifier for the public provider to be returned. The Identity is typically the name of the web site providing the services (for example, Yahoo!; AOL; MSN; etc.).</p>
<p>You cannot use wildcards when specifying the Identity. To use wildcards to return one or more public providers, use the Filter parameter instead.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the public provider data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsPublicProvider** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

Returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.

</div>

<div>

## See Also


[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

