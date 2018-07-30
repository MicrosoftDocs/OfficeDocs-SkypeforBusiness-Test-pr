﻿---
title: Import-CsAnnouncementFile
TOCTitle: Import-CsAnnouncementFile
ms:assetid: 66da2361-e325-4085-8b6f-47a8423edaab
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398472(v=OCS.15)
ms:contentKeyID: 48184341
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsAnnouncementFile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-11_

Imports an announcement file to the Announcement service audio library. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Import-CSAnnouncementFile -Content <Byte[]> -FileName <String> -Parent <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

These commands import an audio file into the Announcement service File Store. Because audio files must be imported as byte arrays, we first need to call the **Get-Content** cmdlet to retrieve the audio file as an array of individual bytes. **Get-Content** is a Windows PowerShell built-in cmdlet to which we pass the name (including path) of the file we want to use for our announcement. Next we pass a value of 0 to the ReadCount parameter, meaning we want to read the whole file at once. We then pass a value of Byte to the Encoding parameter, which tells **Get-Content** that we want the contents of the file as an array of bytes. We assign that array to the variable $a.

In the second line we call the **Import-CsAnnouncementFile** cmdlet to actually import the file. We pass the service Identity ApplicationServer:redmond.litwareinc.com to the Parent parameter, then we pass a name to the FileName parameter (WelcomeMessage.wav). This can be any valid Windows operating system file name, but it should end with a .wav or .wma extension. Finally, we pass the variable $a as the value to the Content parameter to read in our byte array.

    $a = Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte
    Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content $a

</div>

<div>

## EXAMPLE 2

Example 2 is identical to Example 1 except that we included the **Get-Content** command inside parentheses as a value to the Content parameter rather than calling that command on its own and assigning it to a variable.

    Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content (Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte)

</div>

<div>

## EXAMPLE 3

Example 3 is yet another variation of Example 1. The difference in this example is that rather than use the Content parameter, we first call the **Get-Content** cmdlet, then pipe the results to **Import-CsAnnouncementFile**. This is the most reliable way of importing an announcement file from a remote session.

    Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte | Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav"

</div>

</div>

<div>

## Detailed Description

This cmdlet imports an audio file as a byte array to the Announcement service audio library. This makes the file available for playback as an announcement for unassigned numbers.

Running this cmdlet imports the audio file to the library. After the file has been imported, the file can be used in an announcement by calling the **New-CsAnnouncement** cmdlet or the **Set-CsAnnouncement** cmdlet and passing the file name and associated service as parameters. At that point the **New-CsUnassignedNumber** or **Set-CsUnassignedNumber** cmdlet can be called to assign the announcement to a specific range of numbers.

Imported files must be WAV or WMA files.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsAnnouncementFile** cmdlet locally: RTCUniversalServerAdmins. However, the cmdlet can also be run by anyone with write access to the destination computer File Store. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsAnnouncementFile"}

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
<td><p><em>Content</em></p></td>
<td><p>Required</p></td>
<td><p>System.Byte[]</p></td>
<td><p>The contents of the audio file as a byte array.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The name that you want the file to have in the File Store. You will use this name in the AudioFilePrompt parameter in the call to the <strong>New-CsAnnouncement</strong> or <strong>Set-CsAnnouncement</strong> cmdlet to assign the file to an announcement.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The service ID of the Application Server on which the associated Announcement service is running.</p></td>
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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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

<div>

## Input Types

Byte\[\]. Accepts a byte array from an audio file. Byte array must be piped as a single record. See Example 3.

</div>

<div>

## Return Types

This cmdlet does not return a value.

</div>

</div>

<span> </span>

</div>

</div>

</div>

