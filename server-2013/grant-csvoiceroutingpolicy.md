﻿---
title: Grant-CsVoiceRoutingPolicy
TOCTitle: Grant-CsVoiceRoutingPolicy
ms:assetid: a7c7b6c4-925a-464c-a3ee-8373f4eb46b2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205141(v=OCS.15)
ms:contentKeyID: 48185022
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Grant-CsVoiceRoutingPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Assigns a per-user voice routing policy to one or more users. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Lync Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Lync Server 2013. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Grant-CsVoiceRoutingPolicy -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-PolicyName <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to the user with the Active Directory display name "Ken Myer".

    Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName "RedmondVoiceRoutingPolicy"

</div>

<div>

## Example 2

In Example 2, any per-user voice routing policy previously assigned to the user Ken Myer is unassigned from that user; as a result, Ken Myer will be managed by the global voice routing policy. To unassign a per-user policy, set the PolicyName to a null value ($Null).

    Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName $Null

</div>

<div>

## Example 3

Example 3 assigns the per-user voice routing policy RedmondVoiceRoutingPolicy to all the users in the Redmond OU in Active Directory. To do this, the command first calls the **Get-CsUser** cmdlet long with the OU parameter; the parameter value "OU=Redmond,dc=litwareinc,dc=com" limits the returned data to user accounts in the Redmond OU. Those user accounts are then piped to the **Grant-CsVoiceRoutingPolicy** cmdlet, which assigns each user the voice routing policy RedmondVoiceRoutingPolicy.

    Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsVoiceRoutingPolicy -PolicyName "RedmondVoiceRoutingPolicy"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Lync Server and other users are homed on Lync Online. Assigning your Lync Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.

Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Lync Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsVoiceRoutingPolicy"}

**Lync Server Control Panel:** The functions carried out by the Grant-CsVoiceRoutingPolicy cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Indicates the Identity of the user account to be assigned the per-user voice routing policy. User Identities are typically specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (four example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).</p>
<p>User Identities can also be specified by using the user’s Active Directory distinguished name.</p>
<p>In addition, you can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity &quot;* Smith&quot; returns all the users who have a display name that ends with the string value &quot; Smith&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to retrieve user information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to pass a user object through the pipeline that represents the user account being assigned the voice routing policy. By default, the <strong>Grant-CsVoiceRoutingPolicy</strong> cmdlet does not pass objects through the pipeline.</p></td>
</tr>
<tr class="odd">
<td><p><em>PolicyName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>&quot;Name&quot; of the policy to be assigned. The PolicyName is simply the policy Identity minus the policy scope (the &quot;tag:&quot; prefix). For example, a policy with the Identity tag:Redmond has a PolicyName equal to Redmond; likewise, a policy with the Identity tag:RedmondVoiceRoutingPolicy has a PolicyName equal to RedmondVoiceRoutingPolicy.</p>
<p>To unassign a per-user policy previously assigned to a user, set the PolicyName to a null value ($Null).</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Grant-CsVoiceRoutingPolicy** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

By default, the **Grant-CsVoiceRoutingPolicy** cmdlet does not return a value or object. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact.

</div>

<div>

## See Also


[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

