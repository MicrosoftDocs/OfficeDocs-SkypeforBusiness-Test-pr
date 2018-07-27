﻿---
title: Test-CsTrunkConfiguration
TOCTitle: Test-CsTrunkConfiguration
ms:assetid: 07f2ef04-49aa-4857-b213-fa98506c0427
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398137(v=OCS.15)
ms:contentKeyID: 48183330
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsTrunkConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Validates a trunk configuration against a phone number. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsTrunkConfiguration -TrunkConfiguration <TrunkConfiguration> [-CallingNumber <PhoneNumber>] [-DialedNumber <PhoneNumber>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example runs a test against the trunk configuration defined for the Redmond site. The first line in this example calls the **Get-CsTrunkConfiguration** cmdlet to retrieve the configuration for the Redmond site (the configuration with the Identity site:Redmond). The trunk configuration object retrieved is assigned to the variable $tc.

In line 2 we call the **Test-CsTrunkConfiguration** cmdlet, passing the phone number to test to the DialedNumber parameter, and the trunk configuration we retrieved in line 1 (stored in $tc) to the TrunkConfiguration parameter.

    $tc = Get-CsTrunkConfiguration -Identity Site:Redmond
    Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $tc

</div>

</div>

<div>

## Detailed Description

Use this cmdlet to verify that a trunking configuration performs as expected against a dialed phone number. Each configuration contains specific settings defining the relationship and capabilities between the Mediation Server and the public switched telephone network (PSTN) gateway, IP-public branch exchange (PBX), or Session Border Controller (SBC) at the service provider. These settings configure such things as whether media bypass is enabled on this trunk, whether real-time transport control protocol (RTCP) packets are sent under certain conditions, and whether to require secure real-time protocol (SRTP) encryption.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsTrunkConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsTrunkConfiguration"}

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
<td><p><em>TrunkConfiguration</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration</p></td>
<td><p>A reference to a trunk configuration object against which to run the test. Trunk configuration objects can be retrieved by calling the <strong>Get-CsTrunkConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>CallingNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>When specified, returns the matched outbound translation rules for the specified phone number. For example:</p>
<p>-CallingNumber &quot;tel:+14255551219&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>DialedNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>The phone number against which to test the configuration.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration object. Accepts pipelined input of a trunk configuration object.

</div>

<div>

## Return Types

Returns a value of type Microsoft.Rtc.Management.Voice.TrunkConfigurationTestResult.

</div>

<div>

## See Also


[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

