﻿---
title: New-CsReportingConfiguration
TOCTitle: New-CsReportingConfiguration
ms:assetid: 2f033456-5c1c-4313-ab17-37038a412189
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204787(v=OCS.15)
ms:contentKeyID: 48183775
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsReportingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Creates a new collection of reporting configuration settings at the service scope. Reporting configuration settings are used to specify the URL used to access Lync Server 2013 Monitoring Reports. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsReportingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ReportingUrl <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new collection of reporting configuration settings assigned to the monitoring database with the identity service:MonitoringDatabase:atl-sql-001.litwareinc.com. In this example, the value of the ReportingUrl property is set to "https://atl-sql-001.litwareinc.com/lync\_reports".

    New-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -ReportingUrl "https://atl-sql-001.litwareinc.com/lync_reports"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Reporting configuration settings are used to specify the home page for the Lync Server Monitoring Reports; if you are not using Monitoring Reports then there is no reason for you to modify the reporting configuration settings.

If you do not know the URL for the Monitoring Reports home page you can determine that URL by doing the following:

1.  Open the SQL Server Reporting Services Configuration Manager for the SQL Server instance that contains your monitoring database.

2.  In the Configuration Manager, click **Report Manager URL** and then click the URL for your Monitoring Reports. If you see two URLs, click the one that uses the https protocol.

3.  In SQL Server Reporting Services, click **LyncServerReports**.

4.  On the LyncServerReports page, click **Reports Home Page**. That will take you to the home page for the Monitoring Reports. You can then copy the URL and use that URL in conjunction with the CsReportingConfiguration cmdlets.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsReportingConfiguration"}

**Lync Server Control Panel:** The functions carried out by the **New-CsReportingConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Service Identity of the monitoring database to be associated with the new reporting configuration settings. For example:</p>
<p>-Identity &quot;Service:MonitoringDatabase:atl-sql-001.litwareinc.com&quot;</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReportingUrl</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>URL for the Lync Server 2013 Monitoring Reports.</p></td>
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

None. The **New-CsReportingConfiguration** cmdlet does not accept pipelined data.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsReportingConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration object.

</div>

<div>

## See Also


[Get-CsReportingConfiguration](get-csreportingconfiguration.md)  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

