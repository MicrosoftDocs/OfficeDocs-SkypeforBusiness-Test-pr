﻿---
title: Move-CsCommonAreaPhone
TOCTitle: Move-CsCommonAreaPhone
ms:assetid: af5f832c-1be9-4495-ba1a-c10ca50d7b29
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412837(v=OCS.15)
ms:contentKeyID: 48185082
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move-CsCommonAreaPhone

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Moves one or more common area phones to a new Registrar pool. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Move-CsCommonAreaPhone -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 moves the common area phone with the Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com to the Registrar pool atl-cs-001.litwareinc.com.

    Move-CsCommonAreaPhone -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 2

In Example 2, the common area phone with the Active Directory display name "Building 31 Cafeteria" is moved to the Registrar pool atl-cs-001.litwareinc.com. To do this, the **Get-CsCommonAreaPhone** cmdlet is first called without any parameters in order to return a collection of all the common area phones currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those phones where the DisplayName attribute is equal to "Building 31 Cafeteria." That filtered collection is then piped to the **Move-CsCommonAreaPhone** cmdlet, which moves each phone in the collection to atl-cs-001.litwareinc.com.

    Get-CsCommonAreaPhone | Where-Object {$_.DisplayName -eq "Building 31 Cafeteria"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 3

Example 3 moves all the common area phones currently homed on the Registrar pool dublin-cs-001.litwareinc.com to the Registrar pool atl-cs-001.litwareinc.com. To carry out this task, the command first calls the **Get-CsCommonAreaPhone** cmdlet without any parameters; that returns a collection of all the common area phones configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out all the common area phones where the RegistrarPool is equal to dublin-cs-001.litwareinc.com. This collection is then piped to the **Move-CsCommonAreaPhone** cmdlet, which moves each phone in the collection to the new Registrar pool atl-cs-001.litwareinc.com.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 4

Example 4 is a variation of the command shown in Example 3; in this case, however, the common area phones are not only moved to a new Registrar pool, but are also assigned a new per-user voice policy. To do this, the PassThru parameter is included when calling the **Move-CsCommonAreaPhone** cmdlet; this is required in order to pass the common area phone objects through the pipeline. (By default, the **Move-CsCommonAreaPhone** cmdlet does not pass objects through the pipeline.) After the phones have been moved, the phone objects are piped to the **Grant-CsVoicePolicy** cmdlet, which assigns the voice policy AtlantaVoicePolicy to each of the newly-moved phones.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com -PassThru | Grant-CsVoicePolicy -PolicyName AtlantaVoicePolicy

</div>

</div>

<div>

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone’s office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that’s because phone use in Lync Server is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.

The solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.)

The **Move-CsCommonAreaPhone** cmdlet enables you to move an existing common area phone to a new Registrar pool.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Move-CsCommonAreaPhone** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational units (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsCommonAreaPhone"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Unique identifier for the common area phone. Common area phones are identified using the Active Directory distinguished name of the associated contact object. By default, common area phones use a globally unique identifier (GUID) as their common name, which means that phones will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>The fully qualified domain name (FQDN) of the Registrar pool where the common area phone should be moved; for example: atl-cs-001.litwareinc.com. In addition to a Registrar pool, the Target can also be the FQDN of a hosting provider.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to move the common area phone. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-cs-001) or its FQDN (for example, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>If present, moves the common area phone but deletes any associated data (such as policies that were assigned to the device). If not present, the phone is moved along with any associated data.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the common area phone despite those errors.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to pass a user object through the pipeline that represents the user account being moved. By default, the <strong>Move-CsCommonAreaPhone</strong> cmdlet does not pass objects through the pipeline.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>This parameter is used only for Lync Online. It should not be used with an on-premises implementation of Lync Server.</p></td>
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

String. The **Move-CsCommonAreaPhone** cmdlet accepts a pipelined string value that represents the Identity of the common area phone.

</div>

<div>

## Return Types

By default, the **Move-CsCommonAreaPhone** cmdlet does not return any objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

</div>

<div>

## See Also


[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

