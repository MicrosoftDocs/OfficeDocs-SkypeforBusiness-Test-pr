﻿---
title: New-CsNetworkInterRegionRoute
TOCTitle: New-CsNetworkInterRegionRoute
ms:assetid: 97deeba5-b49f-4078-9843-fee7b2d1e72e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398779(v=OCS.15)
ms:contentKeyID: 48184869
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkInterRegionRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Creates a new route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkInterRegionRoute -InterNetworkRegionRouteID <String> <COMMON PARAMETERS>

    New-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID1 <String> -NetworkRegionID2 <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-NetworkRegionLinkIDs <String>] [-NetworkRegionLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 creates a new network region route between the NorthAmerica region and the APAC region. We give the new route the Identity NA\_APAC\_Route. (This will automatically be assigned as the InterNetworkRegionRouteID.) The regions being connected are NorthAmerica, which is passed as the value to the NetworkRegionID1 parameter, and APAC, which is passed as the value to the NetworkRegionID2 parameter. In this example we’re assuming there is no region link configured to link NorthAmerica directly to APAC. However, there are links from NorthAmerica to EMEA (NA\_EMEA), and from EMEA to APAC (EMEA\_APAC). We use both those links, separated by commas, as the value of the NetworkRegionLinkIDs parameter. This will route connections from NorthAmerica to APAC through EMEA and apply any bandwidth limitations to audio and video connections associated with those links.

    New-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA_EMEA,EMEA_APAC"

</div>

</div>

<div>

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet creates that route association.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkInterRegionRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkInterRegionRoute"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>A unique identifier for the newly created network region route. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkRegionRouteID</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>This value is the same as the Identity. You cannot specify both an Identity and an InterNetworkRegionRouteID; a value entered for one will be automatically used for both.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID2 parameter. (In other words, you can’t route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can’t have two routes defined that connect NorthAmerica and EMEA).</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID1 parameter. (In other words, you can’t route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can’t have two routes defined that connect NorthAmerica and EMEA).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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
<td><p><em>NetworkRegionLinkIDs</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Allows you to specify all the links for this route as a string of comma-separated values. The values are the identities (NetworkRegionLinkIDs) of the region links. If you enter values for both NetworkRegionLinkIDs and NetworkRegionLinks, NetworkRegionLinkIDs will be ignored. This parameter provides a convenient way to specify the list of links without having to construct a list object and pass it to the NetworkRegionLinks parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>A list object containing the identities (NetworkRegionLinkIDs) of the region links that apply to this route. For this cmdlet, this parameter differs from the NetworkRegionLinkIDs parameter only in the format if you enter more than one link. The NetworkRegionLinkIDs parameter is the recommended method for defining the initial list with this cmdlet.</p></td>
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

None.

</div>

<div>

## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

</div>

<div>

## See Also


[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

