﻿---
title: Revoke-CsClientCertificate
TOCTitle: Revoke-CsClientCertificate
ms:assetid: 27d6d4d9-f8ed-4942-b7cf-dd308dafb5bc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425748(v=OCS.15)
ms:contentKeyID: 48183683
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Revoke-CsClientCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Client certificates provide a way for users to be authenticated when logging on to Lync Server. Certificates are particularly useful for telephones and other devices running Lync Mobile where it is difficult to enter a user name and/or password. The **Revoke-CsClientCertificate** cmdlet provides a way for administrators to revoke client certificates that have been issued to a user. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Revoke-CsClientCertificate -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 revokes all the client certificates currently assigned to Ken Myer; this is done by calling the **Revoke-CsClientCertificate** cmdlet followed by the Identity of the user whose certificates are to be revoked.

    Revoke-CsClientCertificate -Identity "Ken Myer"

</div>

<div>

## EXAMPLE 2

Example 2 revokes all the client certificates that have been issued in your organization. To do this, the **Get-CsUser** cmdlet is first called in order to return a collection of all the users in your organization who have been enabled for Lync Server. This collection is then piped to the **Revoke-CsClientCertificate** cmdlet, which deletes the certificates for each user in the collection.

    Get-CsUser | Revoke-CsClientCertificate

</div>

</div>

<div>

## Detailed Description

Client certificates provide an alternate way for users to be authenticated by Lync Server. Instead of providing a user name and password, users present the system with an X.509 certificate. (This certificate must have a subject name or subject alternative name that identifies the user.) To be authenticated, users only need to type in a personal identification number (PIN); it’s typically easier for a mobile phone user to type in a PIN than to type in an alphanumeric user name and/or password.

At any time administrators can revoke the client certificates that have been issued to a user by using the **Revoke-CsClientCertificate** cmdlet. The **Revoke-CsClientCertificate** cmdlet revokes all the client certificates issued to the user in question from the server.

The **Revoke-CsClientCertificate** cmdlet does not delete certificates from the client device itself; certificates are only deleted from the server. However, this is sufficient to prevent a client from using certificates for authentication purposes: if a certificate cannot be found on the server than the authentication request will be denied.

Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Lync Server. In turn, that means that you will not be able to run the **Revoke-CsClientCertificate** cmdlet from a remote instance of Windows PowerShell; that’s because your command will not be able to traverse the firewall and access the SQL Server Express database. (However, you can still run the cmdlet locally; that is, on the Standard Edition server itself.) If you are using Standard Edition and need to run the **Revoke-CsClientCertificate** cmdlet remotely you must manually enable the firewall exceptions for SQL Server Express.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Revoke-CsClientCertificate** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Revoke-CsClientCertificate"}

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
<td><p>Indicates the Identity of the user account for which certificates are to be revoked. User Identities can be specified by using one of four formats: 1) the user's Session Initiation Protocol (SIP) address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be referenced by using the user’s Active Directory distinguished name.</p></td>
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

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Revoke-CsClientCertificate** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.

</div>

<div>

## Return Types

None. Instead, the **Revoke-CsClientCertificate** cmdlet revokes instances of the Microsoft.Rtc.Management.UserPinService.CertInfoDetails object.

</div>

<div>

## See Also


[Get-CsClientCertificate](get-csclientcertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

