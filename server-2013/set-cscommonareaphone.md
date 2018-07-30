﻿---
title: Set-CsCommonAreaPhone
TOCTitle: Set-CsCommonAreaPhone
ms:assetid: 765ab74c-33ca-4b17-ba15-edb2fe559ebb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398579(v=OCS.15)
ms:contentKeyID: 48184539
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsCommonAreaPhone

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies the property values of a common area phone managed by Lync Server. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 modifies the Active Directory display name for the common area phone with the phone number 1-425-555-6710. To do this, the **Get-CsCommonAreaPhone** cmdlet is first called along with the Filter parameter; the filter value {LineUri -eq "tel:+14255556710"} limits the returned data to the common area phone where the LineUri property is equal to tel:+14255556710. The returned object is then piped to the **Set-CsCommonAreaPhone** cmdlet, which sets the value of the DisplayName property to "Employee Lounge".

    Get-CsCommonAreaPhone -Filter {LineUri -eq "tel:+14255556710"} | Set-CsCommonAreaPhone -DisplayName "Employee Lounge"

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 enables all the common area phones currently configured for use in the organization. To carry out this task, the command calls the **Get-CsCommonAreaPhone** cmdlet without any parameters in order to return a collection of all the common area phones. This collection is then piped to the **Set-CsCommonAreaPhone** cmdlet, which takes each item in the collection and sets the Enabled property to True.

    Get-CsCommonAreaPhone | Set-CsCommonAreaPhone -Enabled $True

</div>

<div>

## EXAMPLE 3

Example 3 adds a generic description to all the common area phones that do not have a value assigned to the Description property. To do this, the **Get-CsCommonAreaPhone** cmdlet is called along with the Filter parameter; the filter value {Description -eq $Null} ensures that the only items returned are common area phones where the Description property is equal to a null value. This filtered collection is then piped to the **Set-CsCommonAreaPhone** cmdlet, which assigns the generic description "Common area phone" to each item in the collection.

    Get-CsCommonAreaPhone -Filter {Description -eq $Null} | Set-CsCommonAreaPhone -Description "Common area phone"

</div>

</div>

<div>

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone’s office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that’s because phone use in Lync Server is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.

One solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) This command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

The **Set-CsCommonAreaPhone** cmdlet provides a way for you to modify the properties of the contact objects associated with common area phones. Among other things, you can change the contact’s Active Directory display name or the line Uniform Resource Identifier (URI) associated with the phone. You can also use the Enabled parameter to enable and disable the account for use with Lync Server.

In addition, you can configure "hotdesking" for common area phones by using the CsClientPolicy cmdlets. When a phone is hotdesked, users can log on to the phone using their Lync Server credentials. Among other things, this gives users easy access to their contacts. See the help topic for the [Set-CsClientPolicy](set-csclientpolicy.md) cmdlet for more information.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsCommonAreaPhone** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational units (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCommonAreaPhone"}

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
<td><p>UserIdParameter</p></td>
<td><p>Unique identifier for the common area phone. Common area phones are identified using the Active Directory distinguished name of the associated contact object. By default, common area phones use a globally unique identifier (GUID) as their common name; that means phones will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Because of that you might find it easier to retrieve common area phones by using the <strong>Get-CsCommonAreaPhone</strong> cmdlet, and then piping the returned objects to the <strong>Set-CsCommonAreaPhone</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Enables you to modify the Active Directory description attribute for the common area phone. This provides a way to supply additional information about the phone; for example, you might provide details about who to contact in case of problems with the phone.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Enables you to modify the Active Directory display name of the common area phone.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Phone number as displayed in Lync. The DisplayNumber property can be formatted any way you prefer; for example 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; and so on. When choosing a display number, keep in mind that this number will be shown on the display screen of the common area phone only if the number can be normalized. (Normalization is the process of translating number strings into a standard phone number format.) If a normalization rule does not exist for the phone number format used when configuring the display number, the display screen of the common area phone will show the value of the LineUri property rather than the value of the DisplayNumber property.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to modify contact information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-mcs-001) or its fully qualified domain name (FQDN); for example: atl-mcs-001.litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether or not the contact object for the common area phone has been enabled for Lync Server.</p>
<p>If you disable a contact by using the Enabled parameter, the information associated with that account (including assigned policies and whether or not the contact is enabled for Enterprise Voice, remote call control, and/or voice mail integration) is retained. If you later re-enable the account by using the Enabled parameter, the associated account information will be restored.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether the contact object for the common area phone has been enabled for Enterprise Voice, the Voice over Internet Protocol (VoIP) solution offered by Microsoft. With Enterprise Voice, telephone calls can be made using the Internet rather than using the standard telephone network.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>ExchangeArchivingPolicyOptionsEnum</p></td>
<td><p>Indicates where the contact's instant messaging sessions are archived. Allowed values are:</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="even">
<td><p><em>LineURI</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Phone number for the common area phone. The line Uniform Resource Identifier (URI) should be specified using the E.164 format, and be prefixed by the &quot;TEL:&quot; prefix. For example: TEL:+14255551297. Any extension number should be added to the end of the line URI; for example: TEL:+14255551297;ext=51297.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Returns an object representing the common area phone.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Unique identifier that allows the common area phone to communicate with SIP devices such as Lync. The SIP address must be prefaced by the prefix sip: and include a valid SIP domain. For example: sip:bldg14lobby@litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

</div>

<div>

## Return Types

By default, the **Set-CsCommonAreaPhone** cmdlet does not return any objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

</div>

<div>

## See Also


[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

