﻿---
title: New-CsClsScenario
TOCTitle: New-CsClsScenario
ms:assetid: 79ff443f-82ff-4b49-bde5-98e51e8b1ed2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205022(v=OCS.15)
ms:contentKeyID: 48184575
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsClsScenario

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new centralized logging configuration scenario. A scenario represents a particular Lync Server 2013 component or situation (such as IM and presence) that administrators can enable or disable for tracing. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsClsScenario -Identity <XdsIdentity> <COMMON PARAMETERS>

    New-CsClsScenario -Name <String> -Parent <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Provider <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 create a new centralized logging scenario with the Identity global/RedmondHybridVoice. In order to carry out this task, the first command in the example uses the **New-CsClsProvider** cmdlet to create a provider to be assigned to the scenario; this new provider is stored in the variable $provider.

After the description and the provider have been created, the final command in the example calls the **New-CsClsScenario** cmdlet in order to create the scenario, using the data stored in $provider to assign a value to the Provider property.

    $provider = New-CsClsProvider -Name "RedmondHybridVoice" -Type "WPP" -Level "Info" -Flags "All"
    
    New-CsClsScenario -Identity "global/RedmondHybridVoice"-Provider $provider

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.

Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Lync Server. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.

Custom scenarios can be created by using the New-CsClsScenario cmdlet and then adding the new scenario to a collection of centralized logging configuration settings.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClsScenario"}

**Lync Server Control Panel:** The functions carried out by the **New-CsClsScenario** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Unique identifier for the new scenario. A scenario consists of two parts: the scope where the scenario is configured (that is, the collection of centralized logging configuration settings where the scenario can be found) and the scenario name. For example:</p>
<p>-Identity &quot;site:Redmond/AddressBook&quot;</p>
<p>If you use the Identity parameter then you cannot use either the name parameter or the Parent parameter in that same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Unique name for the new scenario. For example:</p>
<p>-Name &quot;RedmondHybridVoice&quot;</p>
<p>If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Scope of the centralized logging configuration settings where the new scenario will be located. For example, to add the new scenario to the global settings, use this syntax:</p>
<p>-Parent &quot;global&quot;</p>
<p>You can return identities for all your centralizing logging &quot;parents&quot; by using this command:</p>
<p>Get-CsClsConfiguration | Select-Object Identity</p>
<p>If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.</p></td>
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
<td><p><em>Provider</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Logging provider for the scenario. New providers must be created using the New-CsClsProvider cmdlet. For example:</p>
<p>$provider = New-CsClsProvider –Name &quot;UserServices&quot; –Type &quot;WPP&quot; –Level &quot;Info&quot; –Flags &quot;All&quot;</p></td>
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

None. The **New-CsClsScenario** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsClsScenario** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario\#Decorated object.

</div>

</div>

<span> </span>

</div>

</div>

</div>

