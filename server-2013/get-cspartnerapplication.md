﻿---
title: Get-CsPartnerApplication
TOCTitle: Get-CsPartnerApplication
ms:assetid: a20738b5-d9e7-4da4-bcac-e967f73c4bdc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205128(v=OCS.15)
ms:contentKeyID: 48184950
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPartnerApplication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about all the partner applications configured for use in the organization. A partner application is any application that Lync Server 2013 can directly exchange security tokens with, without having to exchange those tokens by using a third-party security token server. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsPartnerApplication [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPartnerApplication [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information about all the partner applications configured for use in the organization

    Get-CsPartnerApplication

</div>

<div>

## Example 2

Example 2 returns information for the partner application that has the Identity MicrosoftExchange.

    Get-CsPartnerApplication -Identity "MicrosoftExchange"

</div>

<div>

## Example 3

In Example 3, information is returned for all the partner applications that have an application identifier equal to "microsoft.exchange." In order to do this, the command first calls the **Get-CsPartnerApplication** cmdlet without any parameters; that returns a collection of all the configured partner applications. That collection is then piped to the Where-Object cmdlet, which picks out only those partner applications where the ApplicationIdentifier property is equal to "microsoft.exchange."

    Get-CsPartnerApplication | Where-Object {$_.ApplicationIdentifier -eq "microsoft.exchange"}

</div>

<div>

## Example 4

In Example 4, information is returned for all the partner applications that are currently disabled. To do this, the command first calls the **Get-CsPartnerApplication** cmdlet in order to return a collection of all the partner applications, both enabled and disabled. That collection is then piped to the **Where-Object** cmdlet, which selects only those applications where the Enabled property is equal to False.

    Get-CsPartnerApplication | Where-Object {$_.Enabled -eq $False}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

In Lync Server 2013, server-to-server authentication (for example, the authentication that enables Lync Server 2013 and Exchange 2013 to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.

If you are using an on-premises version of Lync Server 2013 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange 2013 or Microsoft SharePoint 2013) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, you will need to configure the other server product (e.g., Exchange 2013) as a partner application. (You will also need to configure Lync Server 2013 as a partner application for the other server product.) In Lync Server 2013, partner applications are managed by using the **CsPartnerApplication** cmdlets.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPartnerApplication"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsPartnerApplication** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Enables you to use wildcard values to return one or more partner applications. For example, to return all the partner applications that have an Identity that includes the string value &quot;Microsoft&quot; use this syntax:</p>
<p>-Filter &quot;*Microsoft*&quot;</p>
<p>You cannot use both the Filter parameter and the Identity parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique identifier for the partner application. For example:</p>
<p>-Identity &quot;MicrosoftExchange&quot;</p>
<p>If neither the identity parameter nor the Filter parameter are included in the command then the <strong>Get-CsPartnerApplication</strong> cmdlet will return information for all your partner applications.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the partner application data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account where whose partner application settings are to be retrieved.</p>
<p>For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsPartnerApplication** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsPartnerApplication** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication\#Decorated object.

</div>

<div>

## See Also


[New-CsPartnerApplication](new-cspartnerapplication.md)  
[Remove-CsPartnerApplication](remove-cspartnerapplication.md)  
[Set-CsPartnerApplication](set-cspartnerapplication.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

