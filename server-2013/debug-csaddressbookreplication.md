﻿---
title: Debug-CsAddressBookReplication
TOCTitle: Debug-CsAddressBookReplication
ms:assetid: c138f274-7a1f-4074-b6a2-548274af5199
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205232(v=OCS.15)
ms:contentKeyID: 48185302
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Debug-CsAddressBookReplication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Verifies replication between Active Directory and the Lync Server 2013 Address book service. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Debug-CsAddressBookReplication [-DomainController <String>] [-User <String>] [-VerifyReplication <SwitchParameter>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PoolFqdn <Fqdn>] [-VerifyNormalization <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 verifies Address book replication for the current pool. To verify replication for a specified pool, include the PoolFqdn parameter followed by the fully qualified domain name of the pool to be verified.

    Debug-CsAddressBookReplication

</div>

<div>

## Example 2

In Example 2, the User parameter is included when verifying Address book replication for the current pool. When the User parameter is included, additional related information is returned for the specified user.

    Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com"

</div>

<div>

## Example 3

Example 3 uses the VerifyReplication parameter to make a change to the specified user account and then verify that this change can be successfully replicated to the Address Book.

    Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com" -VerifyReplication 

</div>

<div>

## Example 4

The command shown in Example 4 uses the VerifyNormalization parameter to return information about user accounts where Address Book normalization rules could not be applied.

    Debug-CsAddressBookReplication -VerifyNormalization

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Address Book servers are intermediaries between Active Directory Domain Services (AD DS) and Microsoft Lync Server. The Address Book server ensures that the user information stored in Lync Server is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database.

The **Debug-CsAddressBookReplication** cmdlet enables administrators to verify that data is being replicated between Active Directory and Lync Server. Fully testing replication between Active Directory and the Address Book server can potentially be time-consuming and resource-intensive; because of that, it is recommended that **Debug-CsAddressBookReplication** only be used in troubleshooting scenarios. If you want to periodically "spot check" the functioning of your Address Book server you should use the **Test-CsAddressBookService** cmdlet and/or the **Test-CsAddressBookWebQuery** cmdlet instead.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsAddressBookReplication"}

**Lync Server Control Panel:** The functions carried out by the D**ebug-CsAddressBookReplication** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a domain controller to connect to when verifying Address book replication. If this parameter is not included then the cmdlet will use the first available domain controller.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods – ToHTML and ToXML – that can then be used to save that output to either an HTML or an XML file.</p>
<p>To store output in a logger variable named $TestOutput use the following syntax:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Note: Do not prepend a $ character when specifying the variable name.</p>
<p>To save the information stored in the logger variable to an HTML file, use a command similar to this:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>To save the information stored in the logger variable to an XML file, use a command similar to this:</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the pool being checked. If this parameter is not included then the <strong>Debug-CsAddressBookReplication</strong> cmdlet will verify the current pool.</p></td>
</tr>
<tr class="even">
<td><p><em>User</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When included, returns detailed replication information for the specified user accounts. The user account to be verified can be specified by using the user’s SIP address, email address, or SamAccountName.</p></td>
</tr>
<tr class="odd">
<td><p><em>VerifyNormalization</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>If specified, detailed information will be returned for any user accounts where Address book normalization failed. Normalization rules are used to convert phone numbers to the E.164 format used by Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><em>VerifyReplication</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When specified, the <strong>Debug-CsAddressBookReplication</strong> cmdlet will modify the specified user account in Active Directory and then verify that the changes are replicated to the Address book. Note that the user account modification is for testing purposes only, and will not actually change the property values of that account.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Debug-CsAddressBookReplication** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Debug-CsAddressBookReplication** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.Activities.Database.AddressBookReplicationTaskOutput object.

</div>

<div>

## See Also


[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

