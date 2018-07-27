﻿---
title: Get-CsHealthMonitoringConfiguration
TOCTitle: Get-CsHealthMonitoringConfiguration
ms:assetid: 843876f1-8aa6-4324-a981-8eded4d3b16d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398667(v=OCS.15)
ms:contentKeyID: 48184696
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsHealthMonitoringConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Returns information about the health monitoring configuration settings currently in use in your organization. These settings enable administrators to run quality assurance tests without having to supply user names and passwords for the required test accounts. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsHealthMonitoringConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsHealthMonitoringConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns all the health monitoring configuration settings currently in use in your organization.

    Get-CsHealthMonitoringConfiguration

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 returns a single collection of health monitoring configuration settings: the settings that have the Identity atl-cs-001.litwareinc.com.

    Get-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 3

Example 3 returns all the health monitoring configuration settings that have been created for the domain litwareinc.com. To do this, the **Get-CsHealthMonitoringConfiguration** cmdlet is called along with the Filter parameter; the filter value "\*.litwareinc.com" ensures that only those settings that have an Identity that ends with the string value ".litwareinc.com" will be returned.

    Get-CsHealthMonitoringConfiguration -Filter *.litwareinc.com

</div>

<div>

## EXAMPLE 4

The command shown in Example 4 returns all the health monitoring configuration settings that include the user with the SIP address sip:kenmyer@litwareinc.com as one of the test users. To carry out this task, the command first calls the **Get-CsHealthMonitoringConfiguration** cmdlet without any additional parameters; this returns a collection of all the health monitoring configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the FirstTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com" or where the SecondTestUserSipUri property is equal to "sip:kenmyer@litwareinc.com". As a result, any collection of settings where Ken Myer’s SIP address is used for either the first or the second test user will be returned.

    Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:kenmyer@litwareinc.com" -or $_.SecondTestUserSipUri -eq " sip:kenmyer@litwareinc.com"}

</div>

</div>

<div>

## Detailed Description

Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted "manually" by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).

Synthetic transactions can be conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test accounts for each of their Registrar or Director pools. These test accounts are a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) When test accounts have been configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test. Instead, the synthetic transaction will automatically use the preconfigured test accounts when performing its checks.

Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator can run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts). If you decide to conduct a synthetic transaction using actual user accounts you will have to supply the credentials for each user.

The **Get-CsHealthMonitoringConfiguration** cmdlet provides a way for you to retrieve information about the health monitoring configuration settings currently in use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsHealthMonitoringConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsHealthMonitoringConfiguration"}

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
<td><p>Enables you to use wildcard characters when specifying the health monitoring configuration settings to be retrieved. For example, this syntax returns all the settings configured for the litwareinc.com domain: -Filter &quot;*.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Fully qualified domain name (FQDN) of the pool where the health monitoring configuration settings have been assigned. For example: -Identity atl-cs-001.litwareinc.com.</p>
<p>If this parameter is not included, then the <strong>Get-CsHealthMonitoringConfiguration</strong> cmdlet will return information about all the health monitoring configuration settings currently in use.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the health monitoring configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsHealthMonitoringConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsHealthMonitoringConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings object.

</div>

<div>

## See Also


[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)  
[Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

