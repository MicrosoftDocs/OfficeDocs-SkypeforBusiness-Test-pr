﻿---
title: Get-CsClsSearchTerm
TOCTitle: Get-CsClsSearchTerm
ms:assetid: 89a6cc1d-5cbe-42ef-b5a0-127068a0f78a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205061(v=OCS.15)
ms:contentKeyID: 48184736
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsClsSearchTerm

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the centralized logging search terms available for use in the organization. Search terms help define the personally identifiable information available to technical support personnel who are searching the centralized trace logs. Search terms are intended for use with Lync Online.

This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsClsSearchTerm [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClsSearchTerm [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information about all the search terms currently in use in the organization.

    Get-CsClsSearchTerm

</div>

<div>

## Example 2

In Example 2, information is returned for a single search term: the Phone search term found in the global collection of centralized logging configuration settings.

    Get-CsClsSearchTerm -Identity "global/Phone"

</div>

<div>

## Example 3

The command shown in Example 3 returns information for all the URI search terms. To do this, the command first calls the **Get-CsClsSearchTerm** cmdlet without any parameters; this returns a collection of all the available search terms. That collection is then piped to the **Where-Object** cmdlet, which picks out only those terms where the Type property is equal to (-eq) URI.

    Get-CsClsSearchTerm | Where-Object {$_.Type -eq "URI"}

</div>

<div>

## Example 4

In Example 4 information is returned for all the search terms where the Inserts property includes the string value "ItemE164". To carry out this task, the command first uses the **Get-CsClsSearchTerm** cmdlet to return a collection of all the available search terms. That collection is then piped to the **Where-Object** cmdlet, which selects any term for which the Inserts property includes (-match) the string value "ItemE164".

    Get-CsClsSearchTerm | Where-Object {$_.Inserts -match "ItemE164"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.

In Lync Server 2013, administrators can use search terms to mask personally identifiable information from support personnel who are viewing the log files. For example, a user’s name, such as Ken Myer, would not appear when viewed using the support console; instead, the name might appear as FIRST1 LAST1. Likewise, the phone number +12065551219 might be displayed as PHONE1.

The **Get-CsClsSearchTerm** cmdlet returns information about the search terms currently available for use. These search terms are based on the Inserts property, which specifies the information that will be masked as well as the mask that will be substituted for the personally-identifiable information.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClsSearchTerm"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsClsSearchTerm** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcards in order to return one or search terms. For example, to return all the CallID search terms, regardless of the scope where these terms have been configured, use this syntax:</p>
<p>-Filter &quot;*CallID*&quot;</p>
<p>You cannot use both the Identity parameter and the Filter parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier of the search term to be returned. A search term consists of two parts: the scope where the term is configured (that is, the collection of centralized logging configuration settings where the term can be found) and the term name. For example:</p>
<p>-Identity &quot;site:Redmond/CallID&quot;</p>
<p>You can also specify just the search term scope; for example:</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>In that case, all the search terms configured for use on the Redmond site will be returned.</p>
<p>If this parameter is not specified then the <strong>Get-CsSearchTerm</strong> cmdlet will return information about all your centralized logging search terms.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the search term data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsClsSearchTerm** cmdlet does not support pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsClsSearchTerm** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SearchTerm\#Decorated object.

</div>

<div>

## See Also


[Set-CsClsSearchTerm](set-csclssearchterm.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

