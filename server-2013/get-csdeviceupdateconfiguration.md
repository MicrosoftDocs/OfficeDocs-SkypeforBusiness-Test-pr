﻿---
title: Get-CsDeviceUpdateConfiguration
TOCTitle: Get-CsDeviceUpdateConfiguration
ms:assetid: e7adc8a7-616a-41b1-8f4b-5f8778e46f55
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399030(v=OCS.15)
ms:contentKeyID: 48185877
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsDeviceUpdateConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Returns information about the device update configuration settings currently deployed in your organization. These settings help manage the Device Update Web service, a Lync Server component that enables administrators to distribute firmware updates to telephones and other devices running Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsDeviceUpdateConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDeviceUpdateConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the device update configuration settings currently in use in the organization. Calling the **Get-CsDeviceUpdateConfiguration** cmdlet without any additional parameters returns all the device update settings currently in use.

    Get-CsDeviceUpdateConfiguration 

</div>

<div>

## EXAMPLE 2

In Example 2, information is returned for the global device update configuration settings.

    Get-CsDeviceUpdateConfiguration -Identity Global

</div>

<div>

## EXAMPLE 3

Example 3 demonstrates the use of the Filter parameter. The filter value "site:\*" returns a collection of all the device update configuration settings applied at the site scope; that’s because these settings all have an Identity that begins with the string value "site:".

    Get-CsDeviceUpdateConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

Example 4 returns all the device update configuration settings where the MaxLogFileSize property is greater than 2048000 bytes. To do this, the **Get-CsDeviceUpdateConfiguration** cmdlet is used to return a collection of all the device update configuration settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the MaxLogFileSize property is greater than 2048000.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -gt 2048000}

</div>

<div>

## EXAMPLE 5

The command shown in Example 5 returns all the device update configuration settings that include "Watson" as a valid log file type. To accomplish this task, the **Get-CsDeviceUpdateConfiguration** cmdlet is used to return a collection of all the device update configuration settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only the device settings that include "Watson" in their set of valid log file types.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.ValidLogFileTypes -like "*Watson*"}

</div>

</div>

<div>

## Detailed Description

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Lync Server. Periodically, administrators upload a set of device update rules to Lync Server. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices check for updates every 24 hours.

The Device Update Web service is managed by using device configuration settings; these settings can be applied at the global scope or at the site scope. You can use the **Get-CsDeviceUpdateConfiguration** cmdlet to return information about the device update configuration settings currently in use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsDeviceUpdateConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Approve-CsDeviceUpdateRule"}

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
<td><p>Provides a way for you to use wildcard characters when specifying device update configuration settings. For example, to return a collection of all the configuration settings that have been applied at the site scope, use this syntax: -Filter &quot;site:*&quot;. To return all the settings that have the term &quot;EMEA&quot; in their Identity, use this syntax: -Filter &quot;*EMEA*&quot;. Note that the Filter parameter acts only on the Identity of the settings; you cannot filter on other device update configuration properties.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indicates the Identity of the device update configuration settings to be retrieved. To refer to the global settings, use this syntax: -Identity global. To refer to site settings, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, use the Filter parameter instead.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the device update configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsDeviceUpdateConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsDeviceUpdateConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object.

</div>

<div>

## See Also


[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

