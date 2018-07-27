﻿---
title: Get-CsPoolFabricState
TOCTitle: Get-CsPoolFabricState
ms:assetid: 9fe6cce5-4142-47b3-94ac-4cb8b94ec215
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619188(v=OCS.15)
ms:contentKeyID: 49733759
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPoolFabricState

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Returns the Windows Fabric state for a Lync Server 2013 pool. Windows Fabric is a Microsoft technology used for creating highly reliable, distributable, and scalable applications. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsPoolFabricState -PoolFqdn <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Type <All | MCUFactory | ConferenceDirectory | Routing | LYSS>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns the fabric state for the pool atl-cs-001.litwareinc.com. Because the Type parameter was not included, state information for all the services on the pool will be returned.

    Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

<div>

## Example 2

Example 2 returns the fabric state for a single service on the pool atl-cs-001.litwareinc.com: the MCU factory service. This is done by including the Type parameter and the parameter value "MCU".

    Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com" -Type MCU

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Get-CsPoolFabricState** cmdlet returns the Windows Fabric state for a Lync Server 2013 pool. This includes information about Windows Fabric replica instances for any (or all) of the following services: MCU factory; Conference Directory; Routing; Lync Server Storage Service.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPoolFabricState"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsPoolFabricState** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of the pool being checked. You must supply the FQDN of a pool when calling this cmdlet; for example:</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com”</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.HADR.GetOcsPoolFabricStateCmdlet+FabricEnumerationType</p></td>
<td><p>Specifies the service type to be returned. Allowed values are:</p>
<p>* All (returns information for all services)</p>
<p>* MCUFactory (returns information for the MCU factory service)</p>
<p>* ConferenceDirectory (returns information for the Conference Directory service)</p>
<p>LYSS (returns information for the Lync Server Storage service)</p>
<p>You can only specify a single type per command.</p></td>
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

None. The **Get-CsPoolFabricState** cmdlet does not support pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

String value representing the fabric state. The **Get-CsPoolFabricState** cmdlet does not return objects.

</div>

</div>

<span> </span>

</div>

</div>

</div>

