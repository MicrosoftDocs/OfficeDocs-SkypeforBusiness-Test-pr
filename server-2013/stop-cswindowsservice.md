﻿---
title: Stop-CsWindowsService
TOCTitle: Stop-CsWindowsService
ms:assetid: 60318b9f-2291-4b99-a271-d206e4074b70
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398426(v=OCS.15)
ms:contentKeyID: 48184272
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Stop-CsWindowsService

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

**Stop-CsWindowsService** enables you to stop a Lync Server service. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Stop-CsWindowsService [-ComputerName <String>] [-Name <String>] <COMMON PARAMETERS>

    Stop-CsWindowsService [-InputObject <NTService>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Graceful <SwitchParameter>] [-LeaveClsAgentRunning <SwitchParameter>] [-LeaveWebServerRunning <SwitchParameter>] [-NoWait <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 stops the Response Group application service on the local computer. The Response Group application service is identified by including the Name parameter and the name of that service: RTCRGS.

    Stop-CsWindowsService -Name "RTCRGS"

</div>

<div>

## EXAMPLE 2

Example 2 also stops the Response Group application service; in this example, however, that service is located on the remote computer atl-cs-001.litwareinc.com. To stop a service on a remote computer, include the ComputerName parameter followed by the FQDN of the remote computer.

    Stop-CsWindowsService -Name "RTCRGS" -ComputerName atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 3

Example 3 demonstrates how you can stop a service even if you do not know the service name (in this example, RTCCPS). To do this, the command first calls the **Get-CsWindowsService** cmdlet without any parameters in order to return a collection of all the Lync Server services on the local computer. This complete collection is then piped to the **Where-Object** cmdlet, which selects only those services where the DisplayName property includes the string value "Call Park". The filtered collection is then piped to the **Stop-CsWindowsService** cmdlet, which stops the Call Park application service.

    Get-CsWindowsService | Where-Object {$_.DisplayName -like "*Call Park*"} | Stop-CsWindowsService

</div>

</div>

<div>

## Detailed Description

Many Lync Server components run as standard Windows services; for example, the Conferencing Attendant application is actually a service named RTCCAA. If you need to stop a Lync Server service, you can do so by using the **Stop-CsWindowsService** cmdlet.

Keep in mind that the **Stop-CsWindowsService** cmdlet can only stop Lync Server services; an error will occur if you attempt to stop a non-Lync Server service (such as the print spooler) using this cmdlet.

Functionally, the **Stop-CsWindowsService** cmdlet is very similar to the generic Windows PowerShell **Stop-Service**cmdlet; if you wanted to, you could use the **Stop-Service** cmdlet to stop a Lync Server service. However, the **Stop-CsWindowsService** cmdlet includes a ComputerName parameter that makes it easy to stop a service on a remote computer: you simply include the ComputerName parameter followed by the fully qualified domain name (FQDN) of the remote computer. The **Stop-Service** cmdlet does not have a comparable parameter. In addition, the **Stop-CsWindowsService** cmdlet has a Report parameter that enables you to keep a log of any errors that might occur when calling that cmdlet.

The **Stop-CsWindowsService** cmdlet does exactly what the name implies: it stops any service you ask it to stop. This includes services that have dependent services (services that can only run if the service you are attempting to stop is running). By default, if you try to stop a service that has dependent services, the **Stop-CsWindowsService** cmdlet will not only stop the service in question, but will stop all those dependent services as well. Because that could result in unexpected consequences, you can include the Graceful parameter when calling the **Stop-CsWindowsService** cmdlet. When you include the Graceful parameter, the **Stop-CsWindowsService** cmdlet will prevent the service from accepting any new requests. All existing service requests will remain as is; however, new requests will be rejected. As existing requests finish, those requests will not be replaced. Eventually, all the existing requests will be filled and the service will then shut down.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Stop-CsWindowsService** cmdlet locally: RTCUniversalServerAdmins. In addition, you must also have local administrator rights on the destination computer in order to run this cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Stop-CsWindowsService"}

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
<td><p><em>ComputerName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the remote computer running the service to be stopped; if this parameter is not included, then the <strong>Stop-CsWindowsService</strong> cmdlet will stop the specified service on the local computer. The remote computer should be referenced using its FQDN; for example, atl-mcs-001.litwareinc.com.</p></td>
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
<td><p><em>Graceful</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Instead of immediately shutting down a service, waits until all existing service requests have been filled. (However, all new service requests will be rejected.) The service will not completely shut down until all the existing requests have been filled.</p></td>
</tr>
<tr class="odd">
<td><p><em>InputObject</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.Core.NTService</p></td>
<td><p>Enables you to stop a service using an object reference rather than a service name. For example, if you use the <strong>Get-CsWindowsService</strong> cmdlet to return information about a service, and if you store the returned object in a variable named $x, you can then stop the service using this command:</p>
<p>$x = Get-CsWindowsService –Name &quot;RTCCPS&quot;</p>
<p>Stop-CsWindowsService -InputObject $x.Name</p></td>
</tr>
<tr class="even">
<td><p><em>LeaveClsAgentRunning</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When specified, stops all the Lync Server services except for the centralized logging agent service.</p></td>
</tr>
<tr class="odd">
<td><p><em>LeaveWebServerRunning</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, shuts down all services except the Web Server service on the specified computer.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the Lync Server service you want to stop. Note that you must use the service name (for example, RTCCAA) and not the service display name. You can only pass a single service name to the Name parameter, and you cannot use wildcards in the service name. You can use the <strong>Get-CsWindowsService</strong> cmdlet to retrieve service names.</p>
<p>Keep in mind that the <strong>Stop-CsWindowsService</strong> cmdlet can only stop Lync Server services; you cannot use this cmdlet to stop other Windows services. For those services, you might be able to use the Windows PowerShell  <strong>Stop-Service</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>NoWait</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, causes the command to run and then immediately return control to the Windows PowerShell prompt. If not present, control will not be returned until the command has completed and a status report has been written to the screen.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Path to an HTML file where error information can be written. If this parameter is included, any errors that occur during the running of this cmdlet will be logged to the specified file (for example, C:\Logs\Service_report.html).</p></td>
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

Microsoft.Rtc.Management.Deployment.Core.NTService object. The **Stop-CsWindowsService** cmdlet accepts pipelined instances of the Windows service object.

</div>

<div>

## Return Types

None. Instead, the **Stop-CsWindowsService** cmdlet stops instances of the Microsoft.Rtc.Management.Deployment.Core.NTService object.

</div>

<div>

## See Also


[Get-CsWindowsService](get-cswindowsservice.md)  
[Start-CsWindowsService](start-cswindowsservice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

