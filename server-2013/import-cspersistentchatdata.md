﻿---
title: Import-CsPersistentChatData
TOCTitle: Import-CsPersistentChatData
ms:assetid: 17151a25-5dea-498a-93d5-fed3da7d3fa5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204709(v=OCS.15)
ms:contentKeyID: 48183511
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsPersistentChatData

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Enables administrators to import data exported from a Microsoft Lync Server 2010 Group Chat database into a Lync Server 2013 Persistent Chat database. This data must have previously been exported from the Group Chat database by using the **Export-CsPersistentChatData** cmdlet. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Import-CsPersistentChatData -FileName <String> <COMMON PARAMETERS>

    Import-CsPersistentChatData -ByteInput <Byte[]> <COMMON PARAMETERS>

    COMMON PARAMETERS: -DBInstance <String> [-Confirm [<SwitchParameter>]] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown on Example 1 reads exported Persistent Chat data from the file C:\\Logs\\PersistentChatExport.xml and then adds that data to the Persistent Chat database atl-sql-001.litwareinc.com\\rtc (where "atl-sql-001.litwareinc.com" is the fully qualified domain name of the SQL Server computer and "rtc" is the SQL Server database instance).

    Import-CsPersistentChatData -DBInstance "atl-sql-001.litwareinc.com\rtc" -FileName "C:\Logs\PersistentChatExport.zip"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

If you are currently running Lync Server 2010, you can migrate your current Group Chat implementation by using the E**xport-CsPersistentChatData** cmdlet to export your existing Group Chat configuration settings, then use the **Import-CsPersistentChatData** cmdlet to migrate that information to Lync Server 2013 and the Persistent Chat service. Note that the **Export-CsPersistentChatData** cmdlet gives you the option of importing all your Group Chat settings and data or only a portion of your Group Chat settings and data; for example, you can export (and then import) your Group Chat categories and chat rooms without exporting all the content associated with those categories and chat rooms.

Although primarily intended for migration purposes, the **CsPersistentChatData** cmdlets can also be used to manage Persistent Chat data on Lync Server 2013.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsPersistentChatData"}

**Lync Server Control Panel:** The functions carried out by the **Import-CsPersistentChatData** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>ByteInput</em></p></td>
<td><p>Required</p></td>
<td><p>System.Byte[]</p></td>
<td><p>When specified, data is imported as a byte array rather than an XML file.</p></td>
</tr>
<tr class="even">
<td><p><em>DBInstance</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name and name of the SQL Server instance where the Lync Server 2013 Persistent Chat database is located. For example, this syntax specifies the database found in the RTC database instance on the server atl-sql-001.litwareinc.com:</p>
<p>-DBInstance &quot;atl-sql-001.litwareinc.com\rtc&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>FileName</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Full path to the XML file being imported. For example:</p>
<p>-FileName &quot;C:\Logs\PersistentChatExport.xml&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example:</p>
<p>-Report &quot;C:\Logs\PersistentChatExport.html&quot;</p>
<p>If this file already exists, it will be overwritten when you run the cmdlet.</p></td>
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

None. The **Import-CsPersistentChatData** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None.

</div>

</div>

<span> </span>

</div>

</div>

</div>

