﻿---
title: New-CsCommonAreaPhone
TOCTitle: New-CsCommonAreaPhone
ms:assetid: 6082d24d-de92-4a3c-8639-5d28341cbc84
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398430(v=OCS.15)
ms:contentKeyID: 48184311
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsCommonAreaPhone

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new common area phone that can be managed by using Lync Server. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsCommonAreaPhone -DN <ADObjectId> <COMMON PARAMETERS>

    New-CsCommonAreaPhone -OU <OUIdParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS: -LineUri <String> -RegistrarPool <Fqdn> [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayName <String>] [-DisplayNumber <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 creates a new common area phone for the phone number 1-425-555-6710. (Note that the LineUri must be specified using the E.164 format.) In addition to specifying the phone number, the command also specifies the Registrar pool (RegistrarPool); the Active Directory display name (DisplayName); and the distinguished name of the OU where the corresponding contact object should be created (OU).

    New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DisplayName "Building 14 Lobby" -OU "ou=Telecommunications,dc=litwareinc,dc=com"

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In Example 2, however, the new common area phone is associated with an existing Active Directory contact object. To do this, the command employs the DN parameter instead of the OU parameter, using the distinguished name of the existing contact object (cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com) as the parameter value. In this command the DisplayName is also left out, which means that the new common area phone will use the display name already assigned to the existing contact object.

    New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DN "cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com"

</div>

</div>

<div>

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone’s office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that’s because phone use in Lync Server is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.

One solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) This command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

As noted, new common area phones can be created by using the **New-CsCommonAreaPhone** cmdlet. The **New-CsCommonAreaPhone** cmdlet can either create new contact objects for use with common area phones or it can associate existing contact objects with a new common area phone. For more details, see the OU and the DN parameter descriptions in this topic.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsCommonAreaPhone** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational units (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCommonAreaPhone"}

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
<td><p><em>DN</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.ADObjectId</p></td>
<td><p>Enables you to associate an existing Active Directory contact object with the new common area phone. If you have a contact object you want to associate with a common area phone, use the DN parameter followed by the distinguished name of that contact. For example: -DN &quot;cn=Building 14 Lobby,dc=litwareinc,dc=com&quot;. Note that your command will fail if the specified contact does not exist. Your command will also fail if the specified contact has already been enabled for Lync Server. In that case, you must first disable the contact using the <strong>Disable-CsUser</strong> and cmdlet then run the <strong>New-CsCommonAreaPhone</strong> cmdlet.</p>
<p>The DN parameter is particularly useful in organizations that have already created contact objects for conference rooms and other entities. These contacts are often used for scheduling purposes. By using the DN parameter you can create a new common area phone using one of these pre-existing contact objects.</p>
<p>You cannot use the OU and the DN parameters in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>LineUri</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Phone number for the common area phone. The line Uniform Resource Identifier (URI) should be specified using the E.164 format, and be prefixed by the &quot;TEL:&quot; prefix. For example: TEL:+14255551297. Any extension number should be added to the end of the line URI, for example: TEL:+14255551297;ext=51297.</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Distinguished name of the Active Directory organizational unit (OU) where the contact object should be located. For example: -OU &quot;ou=Redmond,dc=litwareinc,dc=com”.</p>
<p>If you include the OU parameter, a new contact will be created in the specified OU, and the contact will automatically be assigned a globally unique identifier (GUID) as its common name. As a result, the contact object will have a name similar to this: {ce84964a-c4da-4622-ad34-c54ff3ed361f}.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPool</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool where the contact object should be homed. For example: -RegistrarPool &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to set the Active Directory Description attribute for the common area phone. In turn, this provides a way for you to supply additional information about the phone; for example, you might want to provide details about who to contact in case of problems with the phone.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to set the Active Directory display name of the common area phone.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Phone number as displayed in Lync. The DisplayNumber property can be formatted any way you prefer; for example 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; and so on. When choosing a display number, keep in mind that this number will be shown on the display screen of the common area phone only if the number can be normalized. (Normalization is the process of translating number strings into a standard phone number format.) If a normalization rule does not exist for the phone number format used when configuring the display number, the display screen of the common area phone will show the value of the LineUri property rather than the value of the DisplayNumber property.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns an object representing the common area phone.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Unique identifier that allows the common area phone to communicate with SIP devices such as Lync. The SIP address must be prefaced by the prefix &quot;sip:&quot; and must include a valid SIP domain. For example: sip:bldg14lobby@litwareinc.com.</p></td>
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

None. The **New-CsCommonAreaPhone** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **New-CsCommonAreaPhone** cmdlet creates new instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

</div>

<div>

## See Also


[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

