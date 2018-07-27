﻿---
title: Convert-CsUserData
TOCTitle: Convert-CsUserData
ms:assetid: e52f8037-19f3-49c9-8dfc-79b0c27d8b94
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205337(v=OCS.15)
ms:contentKeyID: 48185649
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Convert-CsUserData

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Converts exported user data to the data format used by either Microsoft Lync Server 2010 or Lync Server 2013. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Convert-CsUserData -InputFile <String> -OutputFile <String> -TargetVersion <Lync2010 | Current> [-ConfDirectoryFilter <String>] [-Force <SwitchParameter>] [-UserFilter <String>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 converts the user data stored in the file C:\\Logs\\Lync2013Data.zip to the user data format used in Lync Server 2010. The converted data is stored in the XML file C:\\Logs\\Lync2010Data.xml.

    Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010Data.xml" -TargetVersion Lync2010

</div>

<div>

## Example 2

Example 2 shows how you can convert data for a single user; in this example, the user with the SIP address kenmyer@litwareinc.com. This is done by including the UserFilter parameter followed by the user’s SIP address (minus the sip: prefix).

    Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010data.xml" -TargetVersion Lync2010 -UserFilter "kenmyer@litwareinc.com"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Convert-CsUserData** cmdlet takes data exported by using the [Export-CsUserData](export-csuserdata.md) cmdlet and then converts that data to the user data format used by either Microsoft Lync Server 2010 or Lync Server 2013. In turn, that enables the **Import-CsUserData** cmdlet to import that data to the appropriate version of Lync Server.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Convert-CsUserData"}

**Lync Server Control Panel:** The functions carried out by the **Convert-CsUserData** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>InputFile</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Full path to the .ZIP file or .XML file containing the user data to be converted. For example:</p>
<p>-InputFile “C:\Data\Lync2010.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>OutputFile</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Full path to the file that will store the converted data. If you are outputting the data using the Microsoft Lync Server 2010 format then the output file must use a .XML file extension; for example:</p>
<p>-OutputFile &quot;C:\Data\ConvertedLync2010Data.xml&quot;</p>
<p>If you are using the Lync Server 2013 format, the output file must use a .ZIP file extension:</p>
<p>-OutputFile &quot;C:\Data\ConvertedLyncData.zip&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetVersion</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.BlobStore.Cmdlets.ConvertTarget</p></td>
<td><p>Indicates the format for the converted data. Allowed values are:</p>
<p>Lync2010</p>
<p>Current</p></td>
</tr>
<tr class="even">
<td><p><em>ConfDirectoryFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to convert conference directory data. To do this, include the ConfDirectoryFilter parameter and specify the Identity of the conference directory:</p>
<p>-ConfDirectoryFilter 13</p>
<p>You can retrieve conference directory Identities by using this command:</p>
<p>Get-CsConferenceDirectory | Select-Object Identity, ServiceId</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>UserFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to convert data for a single user. That user specified by using his or her SIP address, minus the sip: prefix. For example:</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Convert-CsUserData** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Convert-CsUserData** cmdlet creates either XML or ZIP files, depending on whether the converted data is to be used with Lync Server 2010 or with Lync Server 2013.

</div>

<div>

## See Also


[Export-CsUserData](export-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)  
[Update-CsUserData](update-csuserdata.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

