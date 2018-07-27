﻿---
title: Move-CsExUmContact
TOCTitle: Move-CsExUmContact
ms:assetid: 35ed6bdc-95ea-4bf8-84ce-c4256dc2c4e5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425842(v=OCS.15)
ms:contentKeyID: 48183844
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move-CsExUmContact

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Moves one or more Exchange Unified Messaging (UM) contacts to a new Registrar pool. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Move-CsExUmContact -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 moves the Exchange UM contact object with the SIP address exum1@fabrikam.com to the Registrar pool with the FQDN atl-cs-001.litwareinc.com. Note that a confirmation prompt will be displayed when you run this command, even though we didn’t include the Confirm parameter. This prompt will appear even if you include the Force parameter.

    Move-CsExUmContact -Identity "sip:exum1@fabrikam.com" -Target atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 2

This example moves all Exchange UM contact objects that are Auto Attendants to the Registrar pool with the FQDN atl-cs-001.litwareinc.com. The example begins with a call to the **Get-CsExUmContact** cmdlet, which retrieves all Exchange UM contacts that have been defined. This collection of contacts is then piped to the **Where-Object** cmdlet, which finds all the contacts in the collection that have an AutoAttendant property value of True ($True), meaning the contact is an Auto Attendant.

Finally, the collection of contacts where AutoAttendant is True is piped to the **Move-CsExUmContact** cmdlet, which moves those contacts to the Registrar pool specified in the Target parameter.

As in Example 1, you will be prompted for confirmation when running this command.

    Get-CsExUmContact | Where-Object {$_.AutoAttendant -eq $True} | Move-CsExUmContact -Target atl-cs-001.litwareinc.com

</div>

</div>

<div>

## Detailed Description

Lync Server works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. The **Move-CsExUmContact** cmdlet provides a way for you to move an existing Exchange UM contact object to a new Registrar pool.

When an Exchange UM contact object is moved, the AutoAttendant and IsSubscriberAccess properties will be set appropriately based on the value of the OtherIpPhone property of the object.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Move-CsExUmContact** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsExUmContact"}

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
<td><p>The unique identifier of the contact object you want to move. Contact identities can be specified by using one of four formats: 1) the contact's SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>The fully qualified domain name (FQDN) of the Registrar pool to which the contact is being moved.</p></td>
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
<td><p>Enables you to connect to the specified domain controller. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-mcs-001) or its FQDN (for example, atl-mcs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the contact despite those errors.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to pass a contact object through the pipeline that represents the contact account being moved. By default, the <strong>Move-CsExUmContact</strong> cmdlet does not pass objects through the pipeline.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>This parameter is used only for hosted instances of Lync Server. It should not be used with an on-premises implementation of Lync Server.</p></td>
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

String. Accepts a pipelined string value representing the Identity of an Exchange UM object to be moved.

</div>

<div>

## Return Types

When called with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact.

</div>

<div>

## See Also


[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

