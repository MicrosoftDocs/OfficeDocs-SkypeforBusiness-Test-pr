﻿---
title: Install-CsAdServerSchema
TOCTitle: Install-CsAdServerSchema
ms:assetid: 86e13601-7e80-4276-b176-77d9c6e7d55a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398681(v=OCS.15)
ms:contentKeyID: 48184722
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Install-CsAdServerSchema

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Extends the Active Directory schema to allow for the installation of Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Install-CsAdServerSchema [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Ldf <String>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 determines the location of the .LDF file by reading information from the registry, then uses that file to update the Active Directory schema.

    Install-CsAdServerSchema

</div>

<div>

## EXAMPLE 2

In Example 2, the Active Directory schema is updated with information taken from a schema update file located in the folder C:\\Schemas. This folder location is specified by using the Ldf parameter.

    Install-CsAdServerSchema -Ldf "C:\Schemas"

</div>

</div>

<div>

## Detailed Description

Although Lync Server stores most of its configuration information in its own database, the software also relies on Active Directory Domain Services as a storage location; for example, user-related information is stored as part of the user’s Active Directory account. In order to do this, Lync Server must store these values in attributes that are not part of the typical Active Directory user account. In turn, that means you must "extend" your Active Directory schema: the schema must be modified to add custom attributes (and other items) required by Lync Server.

The easiest way to extend the Active Directory schema is to use the **Install-CsAdServerSchema** cmdlet. The **Install-CsAdServerSchema** cmdlet is typically run as part of the Lync Server setup process but, if need be, administrators can run the cmdlet at any time. After the cmdlet finishes running, you can then use the **Get-CsAdServerSchema** cmdlet to verify that the schema has been updated and that Active Directory is ready for the next step in the installation process.

Note that, when the **Install-CsAdServerSchema** cmdlet runs, the cmdlet must have access to the schema master, the operations master role that manages Active Directory object and attribute definitions. If you are running the **Install-CsAdServerSchema** cmdlet on a computer other than the schema master, the computer that hosts the schema master must allow remote access to the registry. If it does not, then you must run the **Install-CsAdServerSchema** cmdlet on the schema master itself.

The functions carried out by the **Install-CsAdServerSchema** cmdlet are similar to those carried out by the following Microsoft Office Communications Server 2007 R2 command:

Lcscmd.exe /forest /action:SchemaPrep /SchemaType:Server

Who can run this cmdlet: You must be an Active Directory schema administrator in the root domain and a local administrator on the schema master computer in order to run the **Install-CsAdServerSchema** cmdlet locally.

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the <strong>Install-CsAdServerSchema</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a domain controller in your domain. This parameter is not required if you are running the <strong>Install-CsAdServerSchema</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="odd">
<td><p><em>Ldf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Path to the folder containing the .LDF file to be imported; the .LDF (LDAP Data Interchange Format) file contains the required updates for the Active Directory schema. If this parameter is not included, the <strong>Install-CsAdServerSchema</strong> cmdlet will look for the file in the Lync Server installation path recorded in the registry. The installation path will typically be C:\Program Files\Microsoft Lync Server 2010\Deployment\Setup.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\ServerSchema.html&quot;</p></td>
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

<div>

## Input Types

None. The **Install-CsAdServerSchema** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Install-CsAdServerSchema** cmdlet does not return any values or objects.

</div>

<div>

## See Also


[Get-CsAdServerSchema](get-csadserverschema.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

