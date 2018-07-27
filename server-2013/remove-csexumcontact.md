﻿---
title: Remove-CsExUmContact
TOCTitle: Remove-CsExUmContact
ms:assetid: d79f7082-f58b-4cc3-a90d-230111e32850
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398946(v=OCS.15)
ms:contentKeyID: 48185654
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsExUmContact

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-06_

Removes an Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsExUmContact -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the Exchange UM contact with the SIP address exumsa1@fabrikam.com.

    Remove-CsExUmContact -Identity sip:exumsa1@fabrikam.com

</div>

<div>

## EXAMPLE 2

This example removes all Exchange UM contacts with LineURI values beginning with tel:425. The first part of this command calls the **Get-CsExUmContact** cmdlet with the Filter parameter, using this expression as the filter: LineURI -like "tel:425\*". That filter specifies that we want to retrieve the Exchange UM contact objects that have a LineURI matching the wildcard string tel:425\*. In other words, all line URIs that start with the string tel:425 and end with any set of characters. Once we have that collection of objects, we pipe the collection to the **Remove-CsExUmContact** cmdlet, which removes all the items in the collection.

    Get-CsExUmContact -Filter {LineURI -like "tel:425*"} | Remove-CsExUmContact

</div>

</div>

<div>

## Detailed Description

Lync Server works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on-premises), contact objects must be created by using Windows PowerShell to apply the Auto Attendant and Subscriber Access functionality. Any of the objects that are created can be removed with the **Remove-CsExUmContact** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsExUmContact** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsExUmContact"}

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
<td><p>The unique identifier of the contact object you want to remove. Contact identities can be specified using one of four formats: 1) The contact’s SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).</p>
<p>Full data type: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact object. Accepts pipelined input of Exchange UM contact objects.

</div>

<div>

## Return Types

This cmdlet does not return an object. It removes an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.

</div>

<div>

## See Also


[New-CsExUmContact](new-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

