﻿---
title: Test-CsOUPermission
TOCTitle: Test-CsOUPermission
ms:assetid: 9908eac9-765e-4406-bb6b-0e4dd07f85f8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398787(v=OCS.15)
ms:contentKeyID: 48184945
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsOUPermission

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Verifies that the required permissions needed to manage users, computers, and other objects have been set on the specified Active Directory container. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 verifies that user permissions have been set on the Redmond OU in the litwareinc.com domain.

    Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"

</div>

</div>

<div>

## Detailed Description

If you have locked down your Active Directory domain (that is, if you have disabled permission inheritance), then the domain preparation that takes place when you install Lync Server will not be able to add the permissions needed to manage users, computers, contacts, application contacts, and InetOrg persons. (Domain administrators will still be able to manage these objects, but no one else, including members of the RTCUniversalServerAdmins group, will have management permissions.) In that case, you will need to use the [Grant-CsOUPermission](grant-csoupermission.md) cmdlet to grant the RTCUniversalServerAdmins group the appropriate permissions. In addition, you will need to do this on a container-by-container basis.

The **Test-CsOUPermission** cmdlet enables you to determine whether or not the required permissions have been added to a specified Active Directory container. The **Test-CsOUPermission** cmdlet returns True if the correct permissions have been applied, and returns False if the correct permissions have not been applied. If the cmdlet returns False, you will then need to run the [Grant-CsOUPermission](grant-csoupermission.md) cmdlet in order to make the necessary changes.

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsOUPermission"}

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
<td><p><em>ObjectType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.ObjectType</p></td>
<td><p>Type of object to be checked. Valid values are:</p>
<p>User</p>
<p>Computer</p>
<p>Contact</p>
<p>AppContact</p>
<p>InetOrgPerson</p>
<p>To check multiple objects in the same kind, separate the object types by using commas: -ObjectType &quot;user&quot;,&quot;computer&quot;,&quot;contact&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Distinguished name of the organizational unit (OU) to be checked. For example: -OU &quot;ou=Redmond,dc=litwareinc,dc=com&quot;.</p>
<p>Note that you can only check a single OU per command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Domain</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Name of the domain where the OU to be checked is located. If this parameter is not included, then the <strong>Test-CsOUPermission</strong> cmdlet will look for the OU on the current domain.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a domain controller in your domain. This parameter is not required if you are running the <strong>Test-CsOUPermission</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a global catalog server in your domain. This parameter is not required if you are running the <strong>Test-CsOUPermission</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\OUPermissions.html&quot;. If this file already exists, it will be overwritten when you run the cmdlet.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Test-CsOUPermission** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsOUPermission** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Grant-CsOUPermission](grant-csoupermission.md)  
[Revoke-CsOUPermission](revoke-csoupermission.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

