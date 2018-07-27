﻿---
title: Set-CsTestUserCredential
TOCTitle: Set-CsTestUserCredential
ms:assetid: e613fad9-e91b-4bce-a67d-b1c9860ab34d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205341(v=OCS.15)
ms:contentKeyID: 48185679
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTestUserCredential

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Creates a new watcher node test user. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Set-CsTestUserCredential -Credential <PSCredential> <COMMON PARAMETERS>

    Set-CsTestUserCredential -Password <String> -UserName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -SipAddress <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 configures the user with the SIP address sip:kenmyer@litwareinc.com to be a watcher node test user. Note that you must also supply the user name (in the form domain name\\user name) and the user's password when you configure an account as a watcher node test user.

    Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -UserName "litwareinc\kenmyer" -Password "07Apples"

</div>

<div>

## Example 2

The commands shown in the preceding example also configure the user with the SIP address sip:kenmyer@litwareinc.com to be a watcher node test user; in this case, however, the Credential parameter is used instead of the UserName and Password parameters. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the account litwareinc\\kenmyer; that credentials object is then stored in a variable named $x. (Note that you must supply the password for the litwareinc\\kenmyer account when creating the credentials object.) The second command in the example then uses the Credential parameter and the parameter value $x to configure the test credentials.

    $x = Get-Credential "litwareinc\kenmyer"
    
    Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -Credential $x

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

If you are using System Center Operations Manager in conjunction with Lync Server 2013, you have the option of configuring "watcher node" computers. Watcher nodes are computers that periodically (and automatically) run synthetic transactions. Synthetic transactions are cmdlets that test various features of Lync Server; for example, there are synthetic transactions that verify that users can register with Lync Server; that users can exchange instant messages and presence information using Lync Server; that users can conduct data collaboration and application sharing conferences; and that users can make phone calls across the public switched telephone network. As noted, these synthetic transactions run periodically and, if they fail, issue alerts notifying administrators that the system might be experiencing difficulties.

Many synthetic transactions require test users; for example, you cannot test the ability of two users to exchange instant messages unless you have a pair of user accounts and you attempt to exchange instant messages using those accounts. When you configure a watcher node you must assign at least two test users to that node. These test users can be any valid Active Directory user accounts that have been enabled for Lync Server 2013 and have been registered as test accounts. Accounts are registered as test accounts by using the **Set-CsTestUserCredential** cmdlet. If you later decide not to use an account as a test account you can unregister the by using the [Remove-CsTestUserCredential](remove-cstestusercredential.md) cmdlet. This cmdlet simply prevents the account from being used as a watcher node test account; it does not delete, disable, or otherwise modify the account.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTestUserCredential"}

**Lync Server Control Panel:** The functions carried out by the **Set-CsTestUserCredential** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Credential</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Enables you to configure test credentials by using a Windows PowerShell credentials object rather than the Password and UserName parameters; this has the advantage of ensuring that the user password is masked when you type it onscreen.</p>
<p>To use the Credential parameter you must first create a PSCredential object using the <strong>Get-Credential</strong> cmdlet and then store the resulting object in a variable. For example:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>That variable is then used as the parameter value for the Credential parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Password</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Password for the account whose test user credentials are being set. (Note that this password will be displayed onscreen in plain text.) For example:</p>
<p>-Password &quot;p@ssw0rd&quot;</p>
<p>You do not need to use the Password or the UserName parameters if you use the Credential parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>SIP address of the account whose test user credentials are being set. For example:</p>
<p>-SipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>UserName</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>User name of the account being configured for test credentials. The user name can be the SamAccountName or Active Directory DisplayName; for example:</p>
<p>-UserName &quot;Ken Myer&quot;</p>
<p>You can also specify the UserName by using the format domain name\user name. For example:</p>
<p>-UserName &quot;litwareinc\kenmyer&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Set-CsTestUserCredential** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsTestUserCredential** cmdlet modifies existing instances of the System.Management.Automation.PSCredential object.

</div>

<div>

## See Also


[Get-CsTestUserCredential](get-cstestusercredential.md)  
[Remove-CsTestUserCredential](remove-cstestusercredential.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

