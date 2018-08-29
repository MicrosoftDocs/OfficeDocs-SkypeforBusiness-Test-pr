---
title: 'Lync Server 2013: Call admission control cmdlets'
TOCTitle: Call admission control cmdlets
ms:assetid: dd9d3912-b562-4839-a337-bfc5277cfb62
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415676(v=OCS.15)
ms:contentKeyID: 48185602
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call admission control cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-03-21_

Call admission control (CAC) determines whether there is sufficient network bandwidth to establish a real-time audio or video session of acceptable quality. You manage CAC by configuraing limitations and settings for networks, sites, and subnets and the interactions between them.

<div>

## Call Admission Control Cmdlets

Use the following cmdlets to manage CAC from the Lync Server Management Shell.

**Call Admission Control**

  - <span></span>  
    [Get-CsBandwidthPolicyServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg412727(v=OCS.15))

  - <span></span>  
    [New-CsBandwidthPolicyServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398175(v=OCS.15))

  - <span></span>  
    [Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)

  - <span></span>  
    [Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkBandwidthPolicyProfile](https://technet.microsoft.com/en-us/library/Gg425815(v=OCS.15))

  - <span></span>  
    [New-CsNetworkBandwidthPolicyProfile](https://technet.microsoft.com/en-us/library/Gg398675(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)

  - <span></span>  
    [Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

<!-- end list -->

  - <span></span>  
    [New-CsNetworkBWAlternatePath](https://technet.microsoft.com/en-us/library/Gg398732(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [New-CsNetworkBWPolicy](https://technet.microsoft.com/en-us/library/Gg412916(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkConfiguration](https://technet.microsoft.com/en-us/library/Gg398140(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)

  - <span></span>  
    [Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkInterRegionRoute](https://technet.microsoft.com/en-us/library/Gg425817(v=OCS.15))

  - <span></span>  
    [New-CsNetworkInterRegionRoute](https://technet.microsoft.com/en-us/library/Gg398779(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)

  - <span></span>  
    [Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkInterSitePolicy](https://technet.microsoft.com/en-us/library/Gg412769(v=OCS.15))

  - <span></span>  
    [New-CsNetworkInterSitePolicy](https://technet.microsoft.com/en-us/library/Gg398994(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)

  - <span></span>  
    [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkRegion](https://technet.microsoft.com/en-us/library/Gg398406(v=OCS.15))

  - <span></span>  
    [New-CsNetworkRegion](https://technet.microsoft.com/en-us/library/Gg425829(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkRegion](remove-csnetworkregion.md)

  - <span></span>  
    [Set-CsNetworkRegion](set-csnetworkregion.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkRegionLink](https://technet.microsoft.com/en-us/library/Gg398972(v=OCS.15))

  - <span></span>  
    [New-CsNetworkRegionLink](https://technet.microsoft.com/en-us/library/Gg398437(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)

  - <span></span>  
    [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398766(v=OCS.15))

  - <span></span>  
    [New-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398365(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkSite](remove-csnetworksite.md)

  - <span></span>  
    [Set-CsNetworkSite](set-csnetworksite.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkSubnet](https://technet.microsoft.com/en-us/library/Gg412825(v=OCS.15))

  - <span></span>  
    [New-CsNetworkSubnet](https://technet.microsoft.com/en-us/library/Gg398226(v=OCS.15))

  - <span></span>  
    [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)

  - <span></span>  
    [Set-CsNetworkSubnet](set-csnetworksubnet.md)

</div>

<div>

## See Also


[Overview of call admission control in Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md)  


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

