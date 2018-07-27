﻿---
title: Remove-CsPersistentChatAddin
TOCTitle: Remove-CsPersistentChatAddin
ms:assetid: e218e88a-326e-4405-ba58-4d34b41191b4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205350(v=OCS.15)
ms:contentKeyID: 48185705
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsPersistentChatAddin

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-19_

Removes an existing Persistent Chat add-in. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Remove-CsPersistentChatAddin -Identity <String> <COMMON PARAMETERS>

    Remove-CsPersistentChatAddin -Instance <Addin> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

Example 1 removes the Persistent Chat add-in ITChatAddin found on the pool atl-cs-001.litwareinc.com.

    Remove-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\ITChatAddin"

</div>

<div>

## Example 2

The command shown in Example 2 removes all the Persistent Chat add-ins currently in use in the organization. To do this, the command first uses the **Get-CsPersistentChatAddin** cmdlet to return a collection of all the Persistent Chat add-ins currently in use. This collection is piped to the **Remove-CsPersistentChatAddin** cmdlet, which then deletes each add-in in the collection.

    Get-CsPersistentChatAddin | Remove-CsPersistentChatAddin

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

Add-ins serve as extensions to a Persistent Chat chat room. Add-ins are external applications (that is, items not built into Persistent Chat itself) that are associated with a particular chat room. For example, a help desk chat room might include a URL that links to a Web page or to a Silverlight application that shows the status of the day's help requests. The Lync Server Windows PowerShell command-line interface cmdlets do not provide the ability to create these add-ins. Instead, the **CsPersistentChatAddin** cmdlets are used to associate (or disassociate) an add-in from a chat room.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatAddin"}

**Lync Server Control Panel:** To remove a Persistent Chat add-in using the Lync Server Control Panel, click **Persistent Chat** and then click **Add-in**. Select the add-in to be removed, click **Edit**, and then click **Delete**.

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
<td><p>System.String</p></td>
<td><p>Unique identifier for the Persistent Chat add-in to be removed. The Identity is composed of the fully qualified domain name of the Persistent Chat pool where the add-in is located, a &quot;\&quot; character, and the add-in name. For example:</p>
<p>-Identity &quot;atl-gc-001.litwareincom\ITPersistentChatAddin&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.Addin</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command; for example, attempting to remove an add-in that is currently associated with one or more chat rooms.</p></td>
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

The **Remove-CsPersistentChatAddin** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object. The cmdlet will also accept a string value representing the Identity of an existing add-in.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Remove-CsPersistentChatAddin** cmdlet deletes existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object.

</div>

<div>

## See Also


[Get-CsPersistentChatAddin](get-cspersistentchataddin.md)  
[New-CsPersistentChatAddin](new-cspersistentchataddin.md)  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

