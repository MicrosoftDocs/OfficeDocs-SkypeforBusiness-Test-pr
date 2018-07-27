﻿---
title: Remove-CsConferencingConfiguration
TOCTitle: Remove-CsConferencingConfiguration
ms:assetid: a3dff4b0-100b-46fa-9078-d3b0d4914d87
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412767(v=OCS.15)
ms:contentKeyID: 48184967
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsConferencingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes the specified collection of conference configuration settings. Conference settings determine such things as the maximum-allowed size for conference content and handouts; the content grace period; and the URLs for the internal and external downloads of the supported client. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 deletes the conferencing configuration settings applied to the Redmond site. When site settings such as these are deleted, users in the site will automatically inherit the settings found in the global conferencing configuration settings.

    Remove-CsConferencingConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In Example 2, the command deletes all the conferencing configuration settings applied to the site scope. To do this, the command first calls the **Get-CsConferencingConfiguration** cmdlet along with the Filter parameter; the filter value "site:" ensures that only those settings that have an Identity that begins with the characters "site:" are returned. This filtered collection is then piped to the **Remove-CsConferencingConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsConferencingConfiguration -Filter site:* | Remove-CsConferencingConfiguration

</div>

<div>

## EXAMPLE 3

Example 3 deletes all the conferencing configuration settings where the organization is not set to Litwareinc. To do this, the command first calls the **Get-CsConferencingConfiguration** cmdlet without any parameters; that returns a collection of all the conferencing configuration settings used in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the Organization property is not equal to Litwareinc. Finally, the filtered collection is piped to the **Remove-CsConferencingConfiguration** cmdlet, which deletes all the settings in the collection.

    Get-CsConferencingConfiguration | Where-Object {$_.Organization -ne "Litwareinc"} | Remove-CsConferencingConfiguration

</div>

</div>

<div>

## Detailed Description

For conferences, management and administration is split between two sets of cmdlets. If you want to manage the things users can and cannot do (for example, can users invite anonymous participants to join a conference, are users allowed to offer application sharing in a conference, are users allowed to transfer files within a conference), then you need to use the **CsConferencingPolicy** cmdlets.

In addition to user activities, administrators need to manage the Web Conferencing service. For example, administrators need to be able to do such things as specify the maximum amount of content storage allotted to a single conference and to specify the grace period before that conference content is automatically deleted. They also need to be able to specify the ports used for activities such as application sharing and file transfer.

These latter activities can be managed by using the **CsConferencingConfiguration** cmdlets. These cmdlets enable you to manage the actual servers themselves. The **CsConferencingConfiguration** cmdlets (which can be applied to the global, the site, and the service scopes) aren’t used to specify whether or not a user can share applications during a conference; however, if application sharing is allowed these cmdlets enable you to indicate which ports should be used for that activity. Likewise, the cmdlets enable you to specify such things as storage limits and expiration periods, as well as pointers to internal and external URLs where users can obtain conferencing help and resources.

The **Remove-CsConferencingConfiguration** cmdlet provides a way for you to delete any of the custom collections of conferencing configuration settings created for use in your organization. When you delete a collection of settings, any server previously affected by those settings will automatically come under the jurisdiction of the next collection in the hierarchy (service – site – scope). If the deleted settings were applied at the service scope, then the servers will be managed by the site settings. If there are no settings at the site scope then the servers will be managed by the global settings. Likewise, if you delete settings at the site scope, then servers previously managed by those site settings will be managed by the global settings.

Note that you can also run the **Remove-CsConferencingConfiguration** cmdlet against the global settings. In that case, however, the global settings will not be removed because Lync Server does not allow you to remove global settings. Instead, all the properties in the global collection will be reset to their default values. For example, if you previously changed the maximum content storage value to 200 megabytes, this property will revert to the default value of 100 megabytes.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsConferencingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferencingConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier of the collection of conferencing configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this: -Identity &quot;site:Redmond&quot;. To remove settings configured at the service scope, use syntax similar to this: -Identity &quot;service:ConferencingServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>The <strong>Remove-CsConferencingConfiguration</strong> cmdlet can also be run against the global settings. In that case, however, those settings will not be removed; instead, all the properties will simply be reset to their default values.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings object. The **Remove-CsConferencingConfiguration** cmdlet accepts pipelined instances of the conferencing configuration object.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsConferencingConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConfSettings object.

</div>

<div>

## See Also


[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[New-CsConferencingConfiguration](new-csconferencingconfiguration.md)  
[Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

