﻿---
title: Remove-CsUserAcp
TOCTitle: Remove-CsUserAcp
ms:assetid: dec450bb-d523-468d-aee4-07fdc3d567c4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398982(v=OCS.15)
ms:contentKeyID: 48185610
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsUserAcp

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes one or more audio conferencing providers assigned to a user or group of users. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsUserAcp -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Name <String>] [-ParticipantPasscode <String>] [-PassThru <SwitchParameter>] [-TollNumber <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 removes all the audio conferencing providers that have been assigned to the user Ken Myer.

    Remove-CsUserAcp -Identity "Ken Myer"

</div>

<div>

## EXAMPLE 2

Example 2 shows how you can remove all of the audio conferencing providers that have been assigned to all the users enabled for Lync Server. To do this, the command first uses the **Get-CsUser** cmdlet to retrieve a collection of all the users who have been enabled for Lync Server. That collection is then piped to the **Remove-CsUserAcp** cmdlet, which removes all the audio conferencing providers that have been assigned to each user in the collection.

    Get-CsUser | Remove-CsUserAcp

</div>

<div>

## EXAMPLE 3

In Example 3, all the audio conferencing providers that have the Name "Fabrikam ACP" are removed from Ken Myer’s user account.

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

</div>

<div>

## EXAMPLE 4

Example 4 removes the audio conferencing provider that has the toll number "14255551298" from all the user accounts that have been assigned an audio conferencing provider. To carry out this task, the command first uses the **Get-CsUserAcp** cmdlet to return information about all the audio conferencing providers assigned to all your users. This information is then piped to the **Where-Object** cmdlet, which selects only those accounts where the AcpInfo property includes (-match) the telephone number "14255551298". This filtered collection is then piped to the **Remove-CsUserAcp** cmdlet, which removes the corresponding audio conferencing provider from each account in the filtered collection.

    Get-CsUserAcp | Where-Object {$_.AcpInfo -match "14255551298"} | Remove-CsUserAcp

</div>

</div>

<div>

## Detailed Description

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers provide a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.

Lync Server does not allow for complete integration with audio conferencing providers. The **CsUserAcp** cmdlets do enable administrators to set a phone number and passcode, and to configure other information that can be used for audio conferencing provider integration any time a user schedules a meeting. However, because these cmdlets were not designed for the on-premises version of Lync Server (instead, they are primarily intended for use with Lync Online) no additional audio conferencing provider integration is provided beyond assigning property values.

Any audio conferencing provider assigned to a user can later be removed by using the **Remove-CsUserAcp** cmdlet. Calling the **Remove-CsUserAcp** cmdlet without any parameters (other than the Identity parameter, which indicates the user account to be modified) removes all the audio conferencing providers assigned to a user. Alternatively, you can use the optional parameters included with the **Remove-CsUserAcp** cmdlet to remove selected providers from a user account. For example, this command finds the Ken Myer user account and removes all the audio conferencing providers that have a Name equal to “Fabrikam ACP”:

Remove-CsUserAcp –Identity "Ken Myer" –Name "Fabrikam ACP"

To provide finer-grained removal of audio conferencing providers, simply include additional parameters. For example this command removes any audio conferencing providers that have the Name “Fabrikam ACP” and also have a TollNumber equal to "14255551298" as follows:

Remove-CsUserAcp –Identity "Ken Myer" –Name "Fabrikam ACP" –TollNumber "14255551298"

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsUserAcp** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserAcp"}

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
<td><p>Indicates the Identity of the user account from which the audio conferencing provider is to be removed. You can specify a user's identity using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory Domain Services display name (for example, Ken Myer). User Identities can also be reference by using the user’s Active Directory distinguished name.</p>
<p>You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity &quot;* Smith&quot; returns all the users with a display name that ends with the string value &quot; Smith&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the audio conferencing provider. For example: -Name &quot;Fabrikam Conference Services&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>ParticipantPasscode</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Passcode required when connecting to a conference by using the audio conferencing provider. For example: -PassCode &quot;0712&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to pass a user object through the pipeline that represents the user who is having the audio conferencing provider removed. By default, the <strong>Remove-CsUserAcp</strong> cmdlet does not pass objects through the pipeline.</p></td>
</tr>
<tr class="even">
<td><p><em>TollNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Non-toll-free phone number used for audio conferences. For example: -TollNumber &quot;14255551298&quot;.</p></td>
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

String or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Remove-CsUserAcp** cmdlet accepts a pipelined string value representing the Identity of a user account that has been enabled for Lync Server. The cmdlet also accepts pipelined instances of the Active Directory user object.

</div>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Get-CsUserAcp](get-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

