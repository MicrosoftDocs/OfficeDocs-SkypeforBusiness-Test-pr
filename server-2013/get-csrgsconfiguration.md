﻿---
title: Get-CsRgsConfiguration
TOCTitle: Get-CsRgsConfiguration
ms:assetid: a3667917-cfbf-47c1-8b48-e936594b5357
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412762(v=OCS.15)
ms:contentKeyID: 48184964
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsRgsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-11_

Returns information about configuration settings for the Response Group application. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsRgsConfiguration -Identity <RgsIdentity>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns the Response Group configuration settings for the service ApplicationServer:atl-cs-001.litwareinc.com. Because there can only be one collection of settings per service, this command will never return more than a single item.

    Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 returns the value of a single property -- DisableCallContext -- for the Response Group configuration settings found on the service ApplicationServer:atl-cs-001.litwareinc.com. To accomplish this task, **Get-CsRgsConfiguration** is first used to retrieve all the property values for the Response Group configuration settings for ApplicationServer:atl-cs-001.litwareinc.com. Note that this command is enclosed in parentheses; that ensures that Windows PowerShell returns all the property values before doing anything else.

After all the property values have been returned, standard "dot notation" is used to display the value of the property DisableCallContext (and only the value of that property). Standard dot notation consists of the object followed by a period (dot) followed by the name of the property to be displayed. For example, to display the value of the AgentRingbackGracePeriod property (and only the value of that property), you can use this command:

(Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com").AgentRingbackGracePeriod.

    (Get-CsRgsConfiguration -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com").DisableCallContext

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 demonstrates how you can return Response Group configuration information from all the computers running the Application service that host an instance of the Response Group application. To do this, the command first uses the **Get-CsService** cmdlet and the ApplicationServer parameter to return information about all the servers in the organization that are running the Application service. This collection is then piped to the **Where-Object** cmdlet, which picks out only those servers where the Applications property contains the application "urn:application:RGS"; that value indicates that the Response Group application is running on the server.

In turn, those servers are piped to the **ForEach-Object** cmdlet. **ForEach-Object** then takes each server in the collection and uses **Get-CsRgsConfiguration** to return Response Group configuration information from each server.

    Get-CsService -ApplicationServer | Where-Object {$_.Applications -contains "urn:application:RGS"} | ForEach-Object {Get-CsRgsConfiguration -Identity $_.Identity}

</div>

</div>

<div>

## Detailed Description

The Response Group application provides a way for you to automatically route phone calls to entities such as a help desk or customer support line. When someone calls a designated phone number, that call can be directly routed to the appropriate set of Response Group agents. Alternatively, the call might first be routed to an interactive voice response (IVR) queue. In that queue, the caller will be asked a series of questions (for example, "Are you calling about an existing order?") and then, based on the answers to those questions, be routed to the appropriate Response Group queue.

The **Get-CsRgsConfiguration** cmdlet provides a way for you to return information about how the Response Group application has been configured. Note that, by default, this cmdlet only returns information from one instance of the Response Group application at a time. For example, if you have separate installations of the Response Group application -- one on ApplicationServer:atl-cs-001.litwareinc.com and one on ApplicationServer:dublin-cs-001.litwareinc.com -- you will typically need to make separate calls to **Get-CsRgsConfiguration** in order to return information for each of these Response Group instances. However, the Examples section in this topic shows a way to work around this issue.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsRgsConfiguration** cmdlet locally: RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsConfiguration"}

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
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>Name of the service hosting the Response Group configuration settings; for example: -Identity &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;. If you do not include this parameter, <strong>Get-CsRgsConfiguration</strong> will prompt you to supply an Identity.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

String. **Get-CsRgsConfiguration** accepts a string value representing the Identity of the Response Group configuration settings.

</div>

<div>

## Return Types

**Get-CsRgsConfiguration** returns instances of the Microsoft.Rtc.Rgs.Management.WritableSettings.ServiceSettings object.

</div>

<div>

## See Also


[Move-CsRgsConfiguration](move-csrgsconfiguration.md)  
[Set-CsRgsConfiguration](set-csrgsconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

