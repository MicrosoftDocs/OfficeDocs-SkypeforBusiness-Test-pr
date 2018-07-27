﻿---
title: New-CsExUmContact
TOCTitle: New-CsExUmContact
ms:assetid: 085d0a0f-0efb-4c65-b742-2c1cb7a5ae8f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398139(v=OCS.15)
ms:contentKeyID: 48183335
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsExUmContact

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Creates a new Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsExUmContact -DisplayNumber <String> -OU <OUIdParameter> -RegistrarPool <Fqdn> -SipAddress <String> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example calls the **New-CsExUmContact** cmdlet to create a new Exchange UM Active Directory contact object. To create a new contact you must supply the SIP address (in this example, sip:exumsa1@fabrikam.com) of the Auto Attendant or Subscriber Access. In addition, you must supply the name of the pool where the Lync Server Registrar service is running (RedmondPool.litwareinc.com), the OU where this information will be stored (OU=ExUmContacts,DC=litwareinc,DC=com), and the phone number of the Auto Attendant or Subscriber Access (2065554567). Because we didn’t specifically set the AutoAttendant parameter, the default of False will be applied and this contact object will be assumed to be a Subscriber Access contact.

    New-CsExUmContact -SipAddress sip:exumsa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065554567

</div>

<div>

## EXAMPLE 2

This example is similar to Example 1 in that it calls the **New-CsExUmContact** cmdlet to create a new Exchange UM contact. We again create a new Auto Attendant or Subscriber Access contact, this time with the SIP address sip:exumaa1@fabrikam.com. We then supply the name of the pool where the Lync Server Registrar service is running (RedmondPool.litwareinc.com), the OU where this information will be stored (OU=ExUmContacts,DC=litwareinc,DC=com), and the phone number of the Auto Attendant or Subscriber Access (2065554567). The difference in this example is that we set the optional parameter AutoAttendant to True ($True) to show that this object is, in fact, an Auto Attendant contact.

    New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True

</div>

</div>

<div>

## Detailed Description

Lync Server works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on-premises), contact objects must be created with this cmdlet to apply the Auto Attendant and Subscriber Access functionality. These objects are created by calling the **New-CsExUmContact** cmdlet.

A contact object created with this cmdlet will not be available for use within the system until a hosted voice mail policy has been applied that configures routing for the contact. You can retrieve hosted voice mail policies by calling the **Get-CsHostedVoicemailPolicy** cmdlet. From the policies retrieved you can determine whether an appropriate global or site policy exists, or if a per-user policy exists that needs to be granted to this contact.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsExUmContact** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsExUmContact"}

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
<td><p><em>DisplayNumber</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The telephone number of the contact. Display numbers for each contact must be unique (for instance, no two Exchange UM contacts can have the same display number).</p>
<p>This value may begin with a plus sign (+) and may contain any number of digits. The first digit cannot be zero.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>The organizational unit (OU) where this contact will be located in Active Directory.</p>
<p>Full data type: Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPool</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>The fully qualified domain name (FQDN) of the pool on which the Registrar service is running.</p>
<p>Note that an Exchange UM contact in Lync Server cannot be moved to pools that are part of Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2 deployments.</p>
<p>Full data type: Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The SIP address of the contact. This must be a new address that does not already exist as a user or contact in Active Directory Domain Services. This value must begin with the string sip: followed by the SIP address.</p></td>
</tr>
<tr class="odd">
<td><p><em>AutoAttendant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Specifies whether this contact object is an Auto Attendant. (Auto Attendant provides a set of voice prompts that allow callers to navigate the phone system and reach the intended party.)</p>
<p>Default: False</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A description of this contact. The description is for use by administrators to identify the type of contact (Auto Attendant or Subscriber Access), the location, provider, or any other information that will identify the purpose of each Exchange UM contact.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns the results of this command. Running this cmdlet will display the newly created object; including this parameter will simply repeat that output, making the use of this parameter redundant.</p></td>
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

None.

</div>

<div>

## Return Types

Creates an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.

</div>

<div>

## See Also


[Remove-CsExUmContact](remove-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

