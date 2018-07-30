﻿---
title: New-CsUserServicesPolicy
TOCTitle: New-CsUserServicesPolicy
ms:assetid: 8d7b7f79-f72e-4057-a0d1-188a87af5023
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205072(v=OCS.15)
ms:contentKeyID: 48184761
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsUserServicesPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Creates a new User Services policy. User Services policies determine whether or not a user's contacts are stored in Lync Server 2013 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Lync 2013, Microsoft Outlook, and/or Microsoft Outlook Web Access. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsUserServicesPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-UcsAllowed <$true | $false>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new User Services policy for the Redmond site. Users managed by this policy will not have their contacts moved to the Unified Contact Store; that's because the UcsAllowed parameter has been set to False ($False).

    New-CsUserServicesPolicy -Identity "site:Redmond" -UcsAllowed $False

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Microsoft Exchange Server 2013 instead of in Lync Server; in turn that allows the user to access the same set of contacts in Microsoft Outlook and Outlook Web Access as well as in Lync 2013. (Alternatively, you can continue to store contacts in Lync Server 2013. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Lync 2013.)

In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store. User service policies (which can be configured at the global, site, or the per-user scope) contain only a single property: UcsAllowed. When this property is set to True then (assuming all the other prerequisites have been met) the next time a user logs on to Lync Server 2013 his or her contacts will automatically be migrated to the unified contact store.

If this property is set to False this automatic migration will not take place. However, simply setting UcsAllowed will not cause a user's contacts to be moved from the unified contact store back to Lync Server. In order to do that, you must first assign the user a user services policy that does not allow the use of the unified contact store. After that, you must then use the **Invoke-UcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Lync Server.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUserServicesPolicy"}

**Lync Server Control Panel:** The functions carried out by the **New-CsUserServicesPolicy** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the policy to be created. To create a policy at the site scope, use syntax similar to this:</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>To create a policy at the service scope, use syntax similar to this: -Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot;</p>
<p>Note that the User Server service is the only service that can host a user services policy.</p>
<p>Policies can also be created at the per-user scope. To create a per-user policy, use syntax similar to this:</p>
<p>-Identity &quot;RedmondUserServicesPolicy&quot;</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account for which the new user services policy is being created. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>UcsAllowed</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True (the default value) users affected by the policy will automatically be migrated to the unified contact store (assuming that they have an account on Microsoft Exchange Server 2013 and that they log on using Lync 2013). When set to False, users can be removed from the unified contact store, but only if they are &quot;manually&quot; removed by the <strong>Invoke-CsUcsRollback</strong> cmdlet.</p></td>
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

None. The **New-CsUserServicesPolicy** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsUserServicesPolicy** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.

</div>

<div>

## See Also


[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)  
[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

