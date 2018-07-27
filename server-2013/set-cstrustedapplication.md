﻿---
title: Set-CsTrustedApplication
TOCTitle: Set-CsTrustedApplication
ms:assetid: 35b2812b-43da-4a0a-88dc-960f3cab0dfc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425840(v=OCS.15)
ms:contentKeyID: 48183842
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTrustedApplication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Modifies the settings for a trusted application. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsTrustedApplication [-Identity <ExternalApplicationIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Port <Int32>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the port for the trusted application with the Identity TrustPool.litwareinc.com/tapp2 to port 6200. This is accomplished by passing the **Set-CsTrustedApplication** cmdlet an Identity of TrustPool.litwareinc.com/tapp2. This Identity consists of the name of the pool on which the application resides followed by the name (or ID) of the application. We then include the Port parameter, giving it a value of 6200 to modify that value.

    Set-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2 -Port 6200

</div>

</div>

<div>

## Detailed Description

A trusted application is an application developed by a third party that is given trusted status to run as part of Lync Server but that is not a built-in part of the product. This cmdlet allows you to modify the port number that the external service that runs the application is using.

When you use this cmdlet to modify a trusted application, you must supply a value for the Identity parameter. The Identity is the fully qualified domain name (FQDN) of the pool on which the application is homed followed by a slash (/) followed by the application ID. For example, TrustPool.litwareinc.com/tapp2, where TrustPool.litwareinc.com is the pool FQDN and tapp2 is the application ID. Note that if you view an existing application by calling the **Get-CsTrustedApplication** cmdlet, you’ll see an ID that looks more like this: TrustPool.litwareinc.com/urn:application:tapp2. Notice the prefix urn:application: before the application name (tapp2). While this prefix is part of the Identity, it’s not required when you specify the value for the Identity parameter.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsTrustedApplication** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –matches "Set-CsTrustedApplication\\b"}

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
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity</p></td>
<td><p>The unique identifier of the trusted application you want to modify. Identity values must be entered in the format &lt;pool FQDN&gt;/&lt;application ID&gt;, where pool FQDN is the FQDN of the pool on which the application resides, and application ID is the name of the application.</p></td>
</tr>
<tr class="even">
<td><p><em>Port</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>The port number on which the application will run.</p></td>
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

Microsoft.Rtc.Management.Xds.DisplayTrustedApplication object. Accepts pipelined input of trusted application objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.Xds.DisplayTrustedApplication.

</div>

<div>

## See Also


[New-CsTrustedApplication](new-cstrustedapplication.md)  
[Remove-CsTrustedApplication](remove-cstrustedapplication.md)  
[Get-CsTrustedApplication](get-cstrustedapplication.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

