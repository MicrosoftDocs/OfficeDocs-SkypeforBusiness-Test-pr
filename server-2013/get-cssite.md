﻿---
title: Get-CsSite
TOCTitle: Get-CsSite
ms:assetid: 0e5fd5b8-17aa-433d-9915-3b88281fa2c2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398185(v=OCS.15)
ms:contentKeyID: 48183413
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsSite

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-21_

Returns information about the sites created as part of your Lync Server infrastructure. Sites represent a collection of Lync Server pools and are typically designed around geographic regions. Lync Server includes two types of sites: data center sites and remote sites (branch sites). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsSite [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 retrieves information for all your Lync Server sites.

    Get-CsSite

</div>

<div>

## EXAMPLE 2

In Example 2, information is returned for a single site: the site with the Identity Redmond.

    Get-CsSite -Identity "Redmond"

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 returns information for your central site. To carry out this task, the command first calls the **Get-CsSite** cmdlet in order to return a collection of all the sites configured for use in your organization. This collection is then piped to the **Where-Object** cmdlet, which picks out the one site where the SiteType property is equal to "CentralSite".

    Get-CsSite | Where-Object {$_.SiteType -eq "CentralSite"}

</div>

<div>

## EXAMPLE 4

Example 4 displays the list of pools found in the Redmond site. To do this, the command first retrieves complete information for the Redmond site, and then pipes that data to the **Select-Object** cmdlet. In turn, the **Select-Object** cmdlet uses the ExpandProperty parameter to "expand" the value of the Pools property. Expanding a property value means that all the values stored in that property will be displayed on the screen in an easy-to-read format.

    Get-CsSite -Identity "Redmond" | Select-Object -ExpandProperty Pools

</div>

</div>

<div>

## Detailed Description

Lync Server 2010 introduced a new concept to the Lync Server topology: sites. Sites (which should not be confused with Active Directory sites or Microsoft Exchange Server sites) are a collection of Lync Server pools and servers that are typically organized according to geography and network bandwidth. For example, if all your computers in Redmond are located on the same local area network with high-speed, low-latency connections, you might designate a Redmond site that encompasses those computers. If your computers in Dublin are located on their own local area network, and share high-speed, low-latency connections, then you might create a separate Dublin site as well. Sites play a key role in Lync Server management: most policies and settings can be configured at the site scope, making it easy to do such things as apply one set of dial plans to users in Redmond and a completely different set of dial plans to users in Dublin.

The **Get-CsSite** cmdlet enables you to return information about all the sites in your organization, including information about the pools that make up each of those sites.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsSite** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsSite"}

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
<td><p>Enables you to use wildcards when specifying the Identity of the site (or sites) to be returned. For example, this syntax returns all the pools that have an Identity that include the string value &quot;Dublin&quot;: -Filter &quot;*Dublin*&quot;.</p>
<p>Note that you cannot use both Filter and Identity in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Name of the site to be returned. Note that you should specify just the site name; for example: -Identity &quot;Redmond&quot;. Do not use the format &quot;site:Redmond&quot; when specifying the Identity.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsSite** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsSite** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Site+CentralSite object.

</div>

<div>

## See Also


[Set-CsSite](set-cssite.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

