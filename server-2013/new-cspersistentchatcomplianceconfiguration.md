﻿---
title: New-CsPersistentChatComplianceConfiguration
TOCTitle: New-CsPersistentChatComplianceConfiguration
ms:assetid: a61b76a9-0e2b-4f64-b2fa-cddadc15451c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205163(v=OCS.15)
ms:contentKeyID: 48185076
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsPersistentChatComplianceConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Creates a new collection of Persistent Chat compliance configuration settings at the site or the service scope. Persistent Chat compliance enables administrators to maintain an archive of Persistent Chat items and activities including: new messages; new events (for example, a user entering or existing a chat room); file uploads and downloads; and searches run against the chat history. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-AdapterName <String>] [-AdapterOutputDirectory <String>] [-AdapterType <String>] [-AddChatRoomDetails <$true | $false>] [-AddUserDetails <$true | $false>] [-Confirm [<SwitchParameter>]] [-CreateFileAttachmentsManifest <$true | $false>] [-CustomConfiguration <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-OneChatRoomPerOutputFile <$true | $false>] [-RunInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new collection of Persistent Chat compliance configuration settings for the Redmond site. In this example, both the AddUserDetails and the AddChatRoomDetails properties are set to True ($True).

    New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -AddUserDetails $True -AddChatRoomDetails $True

</div>

<div>

## Example 2

Example 2 also demonstrates how to create a new collection of Persistent Chat compliance configuration settings for the Redmond site. In this example, the RunInterval property is set to 30 minutes; that is, 00 hours : 30 minutes : 00 seconds.

    New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -RunInterval "00:30:00"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

Many organizations (including organizations involved in health care and organizations involved in the financial industry) are required to maintain archives of all their electronic communications; this includes conversations that might take place using the Persistent Chat service. Lync Server 2013 allows you to create a separate compliance database that keeps a detailed of archive of everything that happens in your Persistent Chat chat rooms. Persistent Chat compliance can be enabled or disabled at the site scope or at the service scope (that is, compliance can be enabled or disabled for a given Persistent Chat pool). In addition, Persistent Chat compliance can only be managed using the Windows PowerShell command-line interface; there are no options available in the Lync Server 2013 Control Panel for managing Persistent Chat compliance.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatComplianceConfiguration"}

Lync Server Control Panel: The functions carried out by the **New-CsPersistentChatComplianceConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>XdsIdentity</p></td>
<td><p>Unique identifier for the new Persistent Chat compliance settings being created. New compliance settings can be created at either the site or the service scope (for the Persistent Chat Server service, only). To create new settings at the site scope, use syntax similar to this:</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>To create new settings at the service scope, use syntax like this:</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>AdapterName</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Name of the Persistent Chat adapters used by the compliance settings. Adapters are third-party products that convert the data in the compliance database to a specific format.</p></td>
</tr>
<tr class="odd">
<td><p><em>AdapterOutputDirectory</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Full path to the folder where adapter data is stored. You must have a separate folder for each adapter.</p></td>
</tr>
<tr class="even">
<td><p><em>AdapterType</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Specifies the fully qualified name of a .Net managed type that implements the Microsoft.Rtc.Internal.Chat.Server.Compliance.IComplianceAdapter interface. This adapter is supplied by a third-party or can be set to the internal XML adapter, “Microsoft.Rtc.Internal.Chat.Server.Compliance.XmlAdapter,compliance”.</p>
<p>If you do not specify an adapter type Persistent Chat will not save compliance data.</p></td>
</tr>
<tr class="odd">
<td><p><em>AddChatRoomDetails</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, additional details about each chat room are provided to the adapter. This has the potential to greatly increase the size of the compliance data.</p>
<p>The default value is False.</p></td>
</tr>
<tr class="even">
<td><p><em>AddUserDetails</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, additional details about each chat room user are provided to the adapter. This has the potential to greatly increase the size of the compliance data.</p>
<p>The default value is False.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>CreateFileAttachmentsManifest</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, additional output files will be created to track file transfers within chat rooms. These files will have the file extension .ATTACH and are placed in the location specified by the AdapterOutputDirectory.</p></td>
</tr>
<tr class="odd">
<td><p><em>CustomConfiguration</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>XSLT transform script that enables Persistent Chat to save compliance data in a custom format of your design.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>OneChatRoomPerOutputFile</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, separate reports are created for each chat room. The default value is False.</p></td>
</tr>
<tr class="odd">
<td><p><em>RunInterval</em></p></td>
<td><p>Optional</p></td>
<td><p>TimeSpan</p></td>
<td><p>Amount of time that the server waits before generating the next output file. The RunInterval must be specified using the format days.hours:minutes:seconds. For example, to specify a RunInterval of 30 minutes (the default value) use this syntax:</p>
<p>-RunInterval 00:30:00</p>
<p>The RunInterval can be set to any value between 1 minute (00:01.00) and 30 days (30.00:00:00), inclusive. The default value is 15 minutes (00:15:00).</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **New-CsPersistentChatComplianceConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsPersistentChatComplianceConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration object.

</div>

<div>

## See Also


[Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)  
[Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)  
[Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

