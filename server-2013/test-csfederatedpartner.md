﻿---
title: Test-CsFederatedPartner
TOCTitle: Test-CsFederatedPartner
ms:assetid: 1f56bf80-37b4-4520-b8a5-da0740a894a2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398281(v=OCS.15)
ms:contentKeyID: 48183584
ms.date: 08/26/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsFederatedPartner

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-25_

Verifies the ability to connect to a federated domain. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsFederatedPartner -Domain <String> -TargetFqdn <String> [-Certificate <X509Certificate2>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-ProxyFqdn <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 verifies the connection between the local access proxy server (accessproxy.litwareinc.com) and the federated domain Fabrikam.com. Note that TargetFqdn must point to the internal edge of the proxy server to which federated SIP traffic is directed.

    Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain fabrikam.com

</div>

<div>

## EXAMPLE 2

Example 2 shows how you can test the connection between your domain and the Lync Server Push Notification Service. You must have configured this service as a hosting provider and must have added push.lync.com to your list of allowed domains for this test to succeed. For more information, see [Configuring for push notifications in Lync Server 2013](lync-server-2013-configuring-for-push-notifications.md).

    Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinco.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com

</div>

<div>

## EXAMPLE 3

In Example 3, connectivity is verified for all the domains on your allowed domains list. To do this, the command first uses the Get-CsAllowedDomain cmdlet to retrieve a collection of all your allowed domains. That collection is then piped to the ForEach-Object cmdlet. In turn, ForEach-Object runs the Test-CsFederatedPartner cmdlet against each domain in the collection.

    Get-CsAllowedDomain | ForEach-Object {Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain $_.Identity}

</div>

</div>

<div>

## Detailed Description

**Test-CsFederatedPartner** verifies your ability to connect to the domain of a federated partner. In order to verify the connectivity to a domain, that domain must be listed in the collection of allowed (federated) domains. Domains can be added to the allowed list by using the **New-CsAllowedDomain** cmdlet. When using the Test-CsFederatedPartner cmdlet, make sure that the TargetFqdn parameter points to the internal edge of the proxy server to which federated SIP traffic is directed.

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsFederatedPartner"}

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
<td><p><em>Domain</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name (FQDN) of the federated domain. For example: -Domain &quot;fabrikam.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>FQDN of the access proxy server used by your organization for federated SIP traffic. The TargetFqdn must point to the internal edge of the proxy server to which federated SIP traffic is directed.</p></td>
</tr>
<tr class="odd">
<td><p><em>Certificate</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Security.Cryptography.X509Certificates.X509Certificate2</p></td>
<td><p>Enables you to provide an X509 certificate for authentication purposes when connecting to the federated domain.</p></td>
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
<p>Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>To save the information stored in the logger variable to an XML file, use a command similar to this:</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>FQDN of the access proxy server used by the federated organization.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. **Test-CsFederatedPartner** does not accept pipelined input.

</div>

<div>

## Return Types

**Test-CsFederatedPartner** returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Get-CsAllowedDomain](get-csalloweddomain.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

