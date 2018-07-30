﻿---
title: Set-CsMediationServer
TOCTitle: Set-CsMediationServer
ms:assetid: 13efdd9d-ba26-4c93-b0b9-b6e4739bb630
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398213(v=OCS.15)
ms:contentKeyID: 48183476
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsMediationServer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Enables you to modify the properties of one or more Mediation Servers. Mediation Servers are used to route traffic between your internal Enterprise Voice infrastructure and a public switched telephone network (PSTN) gateway or a SIP trunk. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsMediationServer [-Identity <XdsGlobalRelativeIdentity>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-Registrar <String>] [-SipClientTcpPort <UInt16>] [-SipClientTlsPort <UInt16>] [-SipServerPort <UInt16>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 sets the SIP gateway TCP listening port to 5072 for the Mediation Server MediationServer:atl-cs-001.litwareinc.com. After changing the port you will need to restart the Lync Server Mediation service.

    Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -SipClientTcpPort 5072

</div>

<div>

## EXAMPLE 2

Example 2 configures audio port settings for the Mediation Server MediationServer:atl-cs-001.litwareinc.com. In this example the starting audio port is set to 60000 and the total number of ports allocated for audio is 1000.

    Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -AudioPortStart 60000 -AudioPortCount 1000

</div>

</div>

<div>

## Detailed Description

Mediation Servers act as a bridge between your internal Enterprise Voice configuration and either a PSTN gateway, IP-PBX, or a SIP trunk; in turn, this provides a way for your Enterprise Voice users (who are using Voice over Internet Protocol (VoIP) devices) to communicate with people using standard land-line telephones or mobile phones. The **Set-CsMediationServer** cmdlet provides a way for you to make changes to an existing Mediation Server. In particular, you can modify the ports used for communicating with client devices, Front End Servers, and gateways peers. If necessary, the **Set-CsMediationServer** cmdlet can also be used to associate a Mediation Server with a new Registrar or a new Edge Server.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsMediationServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMediationServer"}

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
<td><p><em>AudioPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 inclusive will be used for audio traffic.</p>
<p>A minimum of seven media ports are needed for relaying a single audio call:</p>
<p>Two gateway ports. One port is needed for real-time transport protocol (RTP) traffic and one for real-time transport control protocol (RTCP) traffic.</p>
<p>Two User Datagram Protocol (UDP) relay ports, one for RTP traffic and one for RTCP traffic.</p>
<p>One Transmission Control Protocol (TCP) relay port. A single TCP relay port can handle both RTP and RTCP traffic.</p>
<p>Two local ports per network interface, one for RTP traffic and one for RTCP traffic</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of ports allocated for sending and receiving audio traffic. For example: –AudioPortStart 60000.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>EdgeServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service identity of the Edge Server to be associated with the Mediation Server. For example: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;.</p></td>
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
<td><p>Service location of the Mediation Server to be modified. For example: -Identity &quot;MediationServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;MediationServer:&quot; when specifying a Mediation Server. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service identity of the Registrar to be associated with the Mediation Server. For example: -Registrar &quot;Registrar:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>SipClientTcpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Listening port used for communicating with gateway peers using TCP. By default, no TCP port is defined; however, a TCP port with the port number 5068 will automatically be created when a PSTN gateway is created. If you change the SipClientTcpPort you will need to restart the Mediation Server service before the new port will actually be used.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipClientTlsPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Listening port used for communicating with gateway peers using the Transport Layer Security (TLS) protocol. By default, SipClientTlsPort is configured to use port 5067. If you change the SipClientTlsPort you will need to restart the Mediation Server service before the new port will actually be used.</p></td>
</tr>
<tr class="even">
<td><p><em>SipServerPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Listening port used for communicating with Front End Servers. By default, SipServerPort is configured to use port 5070. If you change the SipServerPort, you will need to restart the Mediation Server service before the new port will actually be used.</p></td>
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

<div>

## Input Types

None. The **Set-CsMediationServer** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Set-CsMediationServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayMediationServer object.

</div>

<div>

## See Also


[Get-CsService](get-csservice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

