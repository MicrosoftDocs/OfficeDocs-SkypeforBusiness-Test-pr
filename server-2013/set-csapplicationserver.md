﻿---
title: Set-CsApplicationServer
TOCTitle: Set-CsApplicationServer
ms:assetid: 74b3f941-df06-4fde-9487-eba081233723
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398562(v=OCS.15)
ms:contentKeyID: 48184502
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsApplicationServer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

Enables you to modify configuration properties of one or more servers running the Application service. These servers (also known as Application Servers) host software programs, such as the Call Park application, that were developed using the Microsoft Unified Communications Managed API (UCMA) set. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsApplicationServer [-Identity <XdsGlobalRelativeIdentity>] [-ApplicationDatabase <String>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AtsSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-CaaSipPort <UInt16>] [-CasSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-CpsSipPort <UInt16>] [-Force <SwitchParameter>] [-PdpSipPort <UInt16>] [-PdpTurnPort <UInt16>] [-Registrar <String>] [-RgsSipPort <UInt16>] [-RgsWcfMtlsPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 configures the SIP port for the Conferencing Announcement application on the Application Server ApplicationServer:atl-cs-001.litwareinc.com to 5074.

    Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -CasSipPort 5074 

</div>

<div>

## EXAMPLE 2

Example 2 configures audio ports for the Application Server ApplicationServer:atl-cs-001.litwareinc.com. In this example, the starting audio port is set to 49500 and a total of 5500 ports are set aside for audio traffic.

    Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -AudioPortStart 49500 -AudioPortCount 5500 

</div>

<div>

## EXAMPLE 3

In Example 3, the SIP port for the Conferencing Announcement application is set to 5074 for all of the Application Servers in the organization. To do this, the command first uses the **Get-CsService** cmdlet to return a collection of all the Application Servers currently in use. This collection is then piped to the **ForEach-Object** cmdlet, which takes each server in the collection, and uses the **Set-CsApplicationServer** cmdlet to set the Conferencing Announcement application SIP port to 5074.

    Get-CsService -ApplicationServer | ForEach-Object {Set-CsApplicationServer -Identity $_.Identity -CasSipPort 5074} 

</div>

</div>

<div>

## Detailed Description

The Application service hosts a number of Lync Server programs that are not part of the core server components; these programs include the Response Group application, the Conferencing Attendant application, and the Conferencing Announcement application. The Application service takes these programs and fully integrates them into the Lync Server environment.

The **Set-CsApplicationServer** cmdlet enables administrators to modify the configuration settings for any (or all) of the Application Servers deployed in their organization. For example, you can modify the ports used for audio, video, or application sharing traffic, or assign new values to ports used by individual applications such as the Conferencing Attendant application or the Conferencing Announcement application. Note that any time you change ports you will then need to restart the corresponding service.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsApplicationServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsApplicationServer"}

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
<td><p><em>ApplicationDatabase</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Application database. For example: -ApplicationDatabase &quot;ApplicationDatabase:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for application sharing. The actual ports to be opened will start with the value configured for AppSharingPortStart and continue through the number of ports specified for AppSharingPortCount. For example, if the AppSharingPortStart is set to 60000 and the AppSharingPortCount is set to 100 then ports 60000 through 60099 will be used for application sharing.</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of ports allocated for application sharing. For example: –AppSharingPortStart 60000.</p></td>
</tr>
<tr class="even">
<td><p><em>AtsSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for the Audio Test service.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 will be used for audio traffic.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of ports allocated for sending and receiving audio traffic. For example: –AudioPortStart 60000.</p></td>
</tr>
<tr class="odd">
<td><p><em>CaaSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used by the Conferencing Attendant application, used when connecting users to a dial-in conference.</p></td>
</tr>
<tr class="even">
<td><p><em>CasSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used by the Conferencing Announcement application, used to play announcements (for example, &quot;Ken Myer is now exiting&quot;) during a conference.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>CpsSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used by the Call Park service. The Call Park service enables you to place a call on hold from one telephone, then have that call retrieved from a different phone.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Service location of the Application Server to be modified. For example: -Identity &quot;ApplicationServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;ApplicationServer:&quot; when specifying an Application server. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>PdpSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used by the Policy Decision Point Server. The Policy Decision Point Server is used for bandwidth management.</p></td>
</tr>
<tr class="even">
<td><p><em>PdpTurnPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Turn traffic port used by the Policy Decision Point Server.</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of the Registrar associated with the Policy Decision Point Server.</p></td>
</tr>
<tr class="even">
<td><p><em>RgsSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used by the Response Group application. The Response Group application provides a way to direct incoming phone calls to a specific group of people, such as an organization’s support team.</p></td>
</tr>
<tr class="odd">
<td><p><em>RgsWcfMtlsPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for Windows Communication Foundation (WCF) mutual TLS (MTLS) traffic used by the Response Group application.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for sending and receiving video traffic. The actual ports to be opened will start with the value configured for VideoPortStart and continue through the number of ports specified for VideoPortCount. For example, if the VideoPortStart is set to 60000 and the VideoPortCount is set to 100, then ports 60000 through 60099 will be used for video traffic.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of ports allocated for sending and receiving video traffic. For example –VideoPortStart 60000.</p></td>
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

None. The **Set-CsApplicationServer** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Set-CsApplicationServer** cmdlet does not return any values or objects. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayApplicationServer object.

</div>

<div>

## See Also


[Get-CsServerApplication](get-csserverapplication.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

