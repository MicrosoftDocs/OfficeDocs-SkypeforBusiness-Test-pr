﻿---
title: Get-CsCallParkOrbit
TOCTitle: Get-CsCallParkOrbit
ms:assetid: 73bbb09a-7966-4af1-aff3-001f5cc56df1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398554(v=OCS.15)
ms:contentKeyID: 48184492
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsCallParkOrbit

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Gets the call park orbit range settings for the organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsCallParkOrbit [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsCallParkOrbit [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Type <CallPark | GroupPickup>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In this example, the **Get-CsCallParkOrbit** cmdlet is called without specifying any additional parameters. When called like this, the **Get-CsCallParkOrbit** cmdlet returns a collection of all the call park orbit ranges configured for use in your organization.

    Get-CsCallParkOrbit

</div>

<div>

## EXAMPLE 2

In Example 2, the **Get-CsCallParkOrbit** cmdlet is used to return information about the call park orbit range with the name "Redmond CPO 1".

    Get-CsCallParkOrbit -Identity "Redmond CPO 1"

</div>

<div>

## EXAMPLE 3

The command in this example returns all call park orbit ranges with the string "Redmond" in their Identity. For example, this command will return call park orbits with identities such as "Redmond 501", "CP Redmond 1", and "ARedmond". The command uses the Filter parameter with the wildcard character (\*) to designate what to search for. (This search is not case sensitive.)

    Get-CsCallParkOrbit -Filter *Redmond*

</div>

<div>

## EXAMPLE 4

This command returns all call park orbit ranges assigned to the call park service with the ID ApplicationServer:pool0.litwareinc.com. The **Get-CsCallParkOrbit** cmdlet retrieves a collection of all call park orbit ranges, and then pipes that collection to the **Where-Object** cmdlet. This call to the **Where-Object** cmdlet finds all call park orbits in that collection with a value of ApplicationServer:pool0.litwareinc.com in their CallParkServiceId properties. Notice that we add the toString method to the end of the CallParkServiceId parameter name. The CallParkServiceId is of type WritableServiceId. In order to compare that value to the supplied string, we must first turn it into a string by calling the toString method.

    Get-CsCallParkOrbit | Where-Object {$_.CallParkServiceId.toString() -eq "ApplicationServer:pool0.litwareinc.com"}

</div>

<div>

## EXAMPLE 5

The command in this example returns all call park orbit ranges where the range of numbers starts with an \* prefix. After the **Get-CsCallParkOrbit** cmdlet retrieves a collection of all the call park orbit ranges, the collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows the collection to only those call park orbit ranges that have a call park location starting with a \*. It does this by checking the StartsWith property of the NumberRangeStart object for the string "\*".

    Get-CsCallParkOrbit | Where-Object {$_.NumberRangeStart.StartsWith("*")}

</div>

<div>

## EXAMPLE 6

The command in this example returns all call park orbit ranges where no prefix has been assigned to the numbers in the range. (A prefix is the value \* or \# placed at the beginning of the number.) All call park orbits returned by this command will have ranges that consist only of numbers with no other characters included. The **Get-CsCallParkOrbit** cmdlet retrieves a collection of all the call park orbit ranges, and then that collection is piped to the **Where-Object** cmdlet. Looking at the criteria in the call to the **Where-Object** cmdlet, we see this: $\_.NumberRangeStart\[0\]). This returns the first character in the number at the start of the range. (Note that we need to check only the start of the range--if the starting number in the range doesn’t have a prefix, neither will the ending number.) This character is passed to the IsDigit function to determine whether it is a numeric character. If it is, the call park orbit information for the corresponding collection item will be returned.

    Get-CsCallParkOrbit | Where-Object {[Char]::IsDigit($_.NumberRangeStart[0])}

</div>

</div>

<div>

## Detailed Description

This cmdlet retrieves the settings for the call park orbits defined for an organization. You can retrieve a single call park orbit range (specified by the Identity parameter) or you can call the **Get-CsCallParkOrbit** cmdlet with no parameters to retrieve all the call park orbit ranges defined for an organization. Call park orbits are composed of settings that specify a range of numbers at which a user can park a call and the servers associated with those number ranges.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCallParkOrbit** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmin. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCallParkOrbit"}

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
<td><p>This parameter accepts a wildcard string and returns all call park orbit ranges with identities matching that string. For example, a Filter value of Redmond* will return all call park orbit ranges with names beginning with the string Redmond, such as Redmond 1, Redmond 2, RedmondCPO, etc.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique name of the call park orbit range. This name was assigned by the administrator when the call park orbit range was defined.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the call park orbit information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Core.OrbitType</p></td>
<td><p>Specifies the type of call park orbit to be retrieved. Lync Server 2013 allows for two different types of call park orbits:</p>
<p>CallPark. This is the standard call park orbit, in which a user places a call on hold and then can retrieve that call from any phone by dialing the specified call park number.</p>
<p>GroupPickup. With group pickup, users can answer any incoming call that is made to any member of their call pickup group. Call pickup groups are configured by administrators.</p>
<p>To return a specified type of a call park orbit, use syntax similar to this:</p>
<p>-Type GroupPickup</p>
<p>To return all call park orbit, regardless of type, simply omit the Type parameter.</p>
<p>This parameter was introduced in the February 2013 release of Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None.

</div>

<div>

## Return Types

This cmdlet returns an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbits.

</div>

<div>

## See Also


[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Remove-CsCallParkOrbit](remove-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

