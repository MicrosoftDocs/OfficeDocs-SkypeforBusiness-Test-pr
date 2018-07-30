﻿---
title: Get-CsXmppAllowedPartner
TOCTitle: Get-CsXmppAllowedPartner
ms:assetid: 6d031b38-325a-4196-998f-c473390f2055
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204981(v=OCS.15)
ms:contentKeyID: 48184427
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsXmppAllowedPartner

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Returns information about XMPP partners authorized to communicate with your organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. Allowed partners are IM and presence providers that have been authorized to exchange instant messages and presence information with your Lync Server 2013 users. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsXmppAllowedPartner [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsXmppAllowedPartner [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information about all the XMPP allowed partners configured for use in the organization.

    Get-CsXmppAllowedPartner

</div>

<div>

## Example 2

In Example 2, information is returned for a single XMPP allowed partner: the partner with the Identity xmpp.contoso.com.

    Get-CsXmppAllowedPartner -Identity "xmpp.contoso.com"

</div>

<div>

## Example 3

Example 3 returns information for all the XMPP allowed partners that have an Identity that ends in the string value ".org" (for example, xmpp.contoso.org and xmpp.fabrikam.org).

    Get-CsXmppAllowedPartner - Filter "*.org"

</div>

<div>

## Example 4

The command shown in Example 4 returns information about all the XMPP allowed partners where Simple Authentication and Security Layer negotiation is required. In order to do this, the command first uses the **Get-CsXmppAllowedPartner** cmdlet to return information about all the allowed XMPP allowed partners. The returned partners are then piped to the **Where-Object** cmdlet, which selects only those partners where the SaslNegotiation property is equal to Required.

    Get-CsXmppAllowedPartner | Where-Object {$_.SaslNegotiation -eq "Required"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.

In order for your users to be able to exchange instant messages and presence information with users on an XMPP network, that network must be configured as an XMPP allowed partner. (You must also assign your users an external access policy that allows XMPP access.) By design, your users will be allowed to communicate with users on any XMPP network that is listed on the allowed partners list. If you do not want users communicating with users from a given network then you must delete that network from the allowed partners list.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsXmppAllowedPartner"}

**Lync Server Control Panel:** To view information about your XMPP allowed partners in the Lync Server Control Panel, click External User Access and then click XMPP Federated Partners.

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
<td><p>Enables you to use wildcards when specifying the Identities of the XMPP allowed partner (or partners) to be returned. For example the filter value &quot;*.org&quot; returns a collection of all the XMPP allowed partners that have an Identity that ends with the string value &quot;.org&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Fully qualified domain name (FQDN) of the XMPP allowed partner to be returned (for example, fabrikam.com). If neither this parameter nor the Filter parameter is specified, then all the XMPP partners configured for use in your organization are returned.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the XMPP allowed partner data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsXmppAllowedPartner** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsXmppAllowedPartner** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner\#Decorated object.

</div>

<div>

## See Also


[New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

