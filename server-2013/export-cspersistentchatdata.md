﻿---
title: Export-CsPersistentChatData
TOCTitle: Export-CsPersistentChatData
ms:assetid: f4855109-26e0-41b8-8a9f-890f8d892645
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205378(v=OCS.15)
ms:contentKeyID: 48185814
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Export-CsPersistentChatData

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-08_

Exports data from a Persistent Chat database. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Export-CsPersistentChatData [-FileName <String>] <COMMON PARAMETERS>

    Export-CsPersistentChatData [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -DBInstance <String> [-DBName <String>] [-DisableExportedNodes <SwitchParameter>] [-Level <User | Category | RoomDirectory | Content | All>] [-Report <String>] [-Scope <List>] [-StartDate <DateTime>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 exports Persistent Chat data from the Persistent Chat database located on the server atl-sql-001.litwareinc.com; the exported data will be stored in the file C:\\Logs\\PersistentChatData.zip. Because the Level parameter was not specified, the **Export-CsPersistentChatData** cmdlet will do a full export of the Persistent Chat information.

    Export-CsPersistentChatData -DBInstance "atl-sql-001.litwareinc.com\rtc" -FileName "C:\Logs\PersistentChatData.zip"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

If you are currently running Lync Server 2010, you can migrate your current Group Chat implementation by using the **Export-CsPersistentChatData** cmdlet to export your existing Group Chat configuration settings, then use the **Import-CsPersistentChatData** cmdlet to migrate that information to Lync Server 2013 and the Persistent Chat service. Note that the **Export-CsPersistentChatData** cmdlet gives you the option of importing all your Group Chat settings and data or only a portion of your Group Chat settings and data; for example, you can export (and then import) your Group Chat categories and chat rooms without exporting all the content associated with those categories and chat rooms.

Although primarily intended for migration purposes, the **CsPersistentChatData** cmdlets can also be used to manage Persistent Chat data on Lync Server 2013.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsPersistentChatData"}

Lync Server Control Panel: The functions carried out by the **Export-CsPersistentChatData** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>DBInstance</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name and name of the SQL Server instance where the Lync Server 2013 Persistent Chat database is located. For example, this syntax specifies the database found in the RTC database instance on the server atl-sql-001.litwareinc.com:</p>
<p>-DBInstance &quot;atl-sql-001.litwareinc.com\rtc&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns Persistent Chat information as a byte array; the returned data must then be stored in a variable in order to be used by the <strong>Import-CsPersistentChatData</strong> cmdlet. You cannot use both AsBytes and FileName in the same command.</p></td>
</tr>
<tr class="odd">
<td><p><em>DBName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SQL instance name of the Persistent Chat database.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableExportedNodes</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, all exported categories and chat rooms will be disabled when the export is complete.</p></td>
</tr>
<tr class="odd">
<td><p><em>FileName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Full path to the .ZIP file that the <strong>Export-CsPersistentChatData</strong> cmdlet will create; this file will contain the exported user data. For example:</p>
<p>-FileName &quot;C:\Logs\PersistentChatData.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Level</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ExportLevel</p></td>
<td><p>Enables you to specify which Persistent Chat information will be exported. Allowed values are:</p>
<p>* All</p>
<p>* User</p>
<p>* Category</p>
<p>* RoomDirectory</p>
<p>* Content</p>
<p>The default value is All, which means that all the Persistent Chat information will be exported.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Full path for the log file created when the cmdlet runs. For example:</p>
<p>-Report &quot;C:\Logs\ExportPersistentChat.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Scope</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Collections.Generic.List</p></td>
<td><p>Enables you to export data for a specified set of categories (and their corresponding chat rooms). By default all Categories are exported.</p></td>
</tr>
<tr class="odd">
<td><p><em>StartDate</em></p></td>
<td><p>Optional</p></td>
<td><p>System.DateTime</p></td>
<td><p>Beginning date for the time period for which Persistent Chat chat room content should be exported. For example:</p>
<p>-StartDate &quot;1/1/2012&quot;</p>
<p>This parameter is valid only when they Level is set to RoomDirectory.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Export-CsPersistentChatData** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Export-CsPersistentChatData** cmdlet creates .ZIP files.

</div>

</div>

<span> </span>

</div>

</div>

</div>

