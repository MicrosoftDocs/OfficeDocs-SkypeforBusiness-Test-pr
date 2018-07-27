﻿---
title: Get-CsClientVersionConfiguration
TOCTitle: Get-CsClientVersionConfiguration
ms:assetid: ed39feda-ebcf-4ed6-a970-64543f150b16
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399072(v=OCS.15)
ms:contentKeyID: 48185744
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsClientVersionConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Retrieves information about the specified collection of client version configuration settings in use in your organization. Client version configuration settings determine whether or not Lync Server checks the version number of each client application that logs on to the system. If client version filtering is enabled the ability of that client application to access the system will be based on settings configured in the relevant client version policy. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClientVersionConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In the first example, the **Get-CsClientVersionConfiguration** cmdlet is called without specifying any additional parameters. This causes the **Get-CsClientVersionConfiguration** cmdlet to return a collection of all the client version configuration settings currently in use in your organization.

    Get-CsClientVersionConfiguration

</div>

<div>

## EXAMPLE 2

In this example, the **Get-CsClientVersionConfiguration** cmdlet returns all the client version configuration settings that have the Identity site:Redmond. Because Identities must be unique, this command will never return more than one item.

    Get-CsClientVersionConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

Example 3 returns all the client version configuration settings that have been applied at the site scope. This is done by including the Filter parameter and the filter value "site:\*". That filter value instructs the **Get-CsClientVersionConfiguration** cmdlet to return only the settings that have an Identity that begins with the string value "site:".

    Get-CsClientVersionConfiguration -Filter "site:*"

</div>

<div>

## EXAMPLE 4

Example 4 returns all the client version configuration settings that are currently disabled. To carry out this task, the command first uses the **Get-CsClientVersionConfiguration** cmdlet to return a collection of all the client version settings configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the collection to those settings where the Enabled property is equal to False.

    Get-CsClientVersionConfiguration | Where-Object {$_.Enabled -eq $False}

</div>

</div>

<div>

## Detailed Description

Lync Server gives administrators considerable leeway when it comes to specifying the client software (and, equally important, the version number of that software) that users can use to log on to the system. For example, there is no technical reason that requires users to log on to Lync Server by using Lync; there are no technical limitations that would prevent users from logging on by using Microsoft Office Communicator 2007 R2.

However, there might be some non-technical reasons why you would prefer that your users do not log on by using Office Communicator 2007 R2. For example, Office Communicator 2007 R2 does not support all of the features and capabilities found in Lync; as a result, users who log on with Office Communicator 2007 R2 will have a different experience than users who log on by using Lync. This can create difficulties for your users; it can also create difficulties for help desk personnel, who must provide support for a number of different client applications.

If this could be a problem for your organization you can employ client version filtering in order to specify which client applications can be used to log on to Lync Server. When you install Lync Server, a global set of client version configuration settings is installed and enabled. These settings are used to determine whether or not client version filtering is enabled. In addition to the global settings, client version configuration settings can also be applied at the site scope; in those instances, the site settings will have precedence over the global settings.

The **Get-CsClientVersionConfiguration** cmdlet enables you to retrieve information about the client version configuration settings currently in use in your organization. Note that this cmdlet does not return information about which client applications are allowed or are not allowed. To retrieve that information, use the **Get-CsClientVersionPolicy** cmdlet.

Note, too that client version configuration is not a security feature. The technology relies on self-reporting from client applications, and does not attempt to verify that an application is really the application and the version number of that application that it claims to be.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsClientVersionConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientVersionConfiguration"}

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
<td><p>Enables you to use wildcard characters in order to return a collection (or collections) of client version configuration settings. To return a collection of all the settings configured at the site scope, use this syntax: -Filter site:*. To return a collection of all the settings that have the string value &quot;EMEA&quot; somewhere in their Identity (the only property you can filter for) use this syntax: -Filter *EMEA*.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indicates the unique identifier for the collection of client version configuration settings you want to return. To refer to the global settings, use this syntax: -Identity global. To refer to a collection configured at the site scope, use syntax similar to this: -Identity site:Redmond. You cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.</p>
<p>If this parameter is not specified then the <strong>Get-CsClientVersionConfiguration</strong> cmdlet returns a collection of all the client version configuration settings in use in the organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the client version configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsClientVersionConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsClientVersionConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object.

</div>

<div>

## See Also


[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

