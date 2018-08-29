---
title: 'Lync Server 2013: Server roles and services cmdlets'
TOCTitle: Server roles and services cmdlets
ms:assetid: ff3561de-043e-4071-88f7-8de3cded52f6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415683(v=OCS.15)
ms:contentKeyID: 48185971
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server roles and services cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

Many Microsoft Lync Server 2013 components run as server roles or as services. Lync Server 2013 ships with a number of cmdlets that enable you to manage these server roles and services.

<div>

## Server Roles and Services Cmdlets

Many (but not all) of the management tasks that apply to servers and service roles can be performed from the Lync Server Control Panel. For example, you can manage Archiving Server settings but not Address Book Server settings by using Lync Server Control Panel. However, all these tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing server roles and services:

**[Address Book Server cmdlets in Lync Server 2013](lync-server-2013-address-book-server-cmdlets.md)**

  - <span></span>  
    [Get-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398132(v=OCS.15))

  - <span></span>  
    [New-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398395(v=OCS.15))

  - <span></span>  
    [Remove-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398934(v=OCS.15))

  - <span></span>  
    [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Update-CsAddressBook](update-csaddressbook.md)

<!-- end list -->

  - <span></span>  
    [Debug-CsAddressBookReplication](https://technet.microsoft.com/en-us/library/JJ205232(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Test-CsAddressBookService](test-csaddressbookservice.md)

<!-- end list -->

  - <span></span>  
    [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

**[Archiving and Monitoring cmdlets in Lync Server 2013](lync-server-2013-archiving-and-monitoring-cmdlets.md)**

  - <span></span>  
    [Get-CsArchivingConfiguration](https://technet.microsoft.com/en-us/library/Gg399012(v=OCS.15))

  - <span></span>  
    [New-CsArchivingConfiguration](https://technet.microsoft.com/en-us/library/Gg398471(v=OCS.15))

  - <span></span>  
    [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)

  - <span></span>  
    [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Export-CsArchivingData](https://technet.microsoft.com/en-us/library/Gg398452(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Invoke-CsArchivingDatabasePurge](https://technet.microsoft.com/en-us/library/JJ204627(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg425731(v=OCS.15))

  - <span></span>  
    [Grant-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg398475(v=OCS.15))

  - <span></span>  
    [New-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg399032(v=OCS.15))

  - <span></span>  
    [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

  - <span></span>  
    [Set-CsArchivingPolicy](set-csarchivingpolicy.md)

<!-- end list -->

  - <span></span>  
    [Set-CsArchivingServer](set-csarchivingserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsCdrConfiguration](https://technet.microsoft.com/en-us/library/Gg398298(v=OCS.15))

  - <span></span>  
    [New-CsCdrConfiguration](https://technet.microsoft.com/en-us/library/Gg399018(v=OCS.15))

  - <span></span>  
    [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

  - <span></span>  
    [Set-CsCdrConfiguration](set-cscdrconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Set-CsMonitoringServer](set-csmonitoringserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsQoEConfiguration](https://technet.microsoft.com/en-us/library/Gg399004(v=OCS.15))

  - <span></span>  
    [New-CsQoEConfiguration](https://technet.microsoft.com/en-us/library/Gg398325(v=OCS.15))

  - <span></span>  
    [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)

  - <span></span>  
    [Set-CsQoEConfiguration](set-csqoeconfiguration.md)

[Invoke-CsCdrDatabasePurge](https://technet.microsoft.com/en-us/library/JJ205113(v=OCS.15))

  - <span></span>  
    [Export-CsArchivingData](https://technet.microsoft.com/en-us/library/Gg398452(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Invoke-CsQoEDatabasePurge](https://technet.microsoft.com/en-us/library/JJ205247(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsReportingConfiguration](https://technet.microsoft.com/en-us/library/JJ205356(v=OCS.15))

  - <span></span>  
    [New-CsReportingConfiguration](https://technet.microsoft.com/en-us/library/JJ204787(v=OCS.15))

  - <span></span>  
    [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)

  - <span></span>  
    [Set-CsReportingConfiguration](set-csreportingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsTestUserCredential](https://technet.microsoft.com/en-us/library/JJ204759(v=OCS.15))

  - <span></span>  
    [Remove-CsTestUserCredential](remove-cstestusercredential.md)

  - <span></span>  
    [Set-CsTestUserCredential](set-cstestusercredential.md)

<!-- end list -->

  - <span></span>  
    [Get-CsWatcherNodeConfiguration](https://technet.microsoft.com/en-us/library/JJ204739(v=OCS.15))

  - <span></span>  
    [New-CsWatcherNodeConfiguration](https://technet.microsoft.com/en-us/library/JJ205254(v=OCS.15))

  - <span></span>  
    [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)

  - <span></span>  
    [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

  - <span></span>  
    [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsExtendedTest](https://technet.microsoft.com/en-us/library/JJ205275(v=OCS.15))

**[Database and Management Server cmdlets in Lync Server 2013](lync-server-2013-database-and-management-server-cmdlets.md)**

  - <span></span>  
    [Get-CsConfigurationStoreLocation](https://technet.microsoft.com/en-us/library/Gg412814(v=OCS.15))

  - <span></span>  
    [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

  - <span></span>  
    [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

<!-- end list -->

  - <span></span>  
    [Install-CsDatabase](https://technet.microsoft.com/en-us/library/Gg399044(v=OCS.15))

  - <span></span>  
    [Test-CsDatabase](test-csdatabase.md)

  - <span></span>  
    [Uninstall-CsDatabase](unhttps://technet.microsoft.com/en-us/library/Gg399044(v=OCS.15))

<!-- end list -->

  - [Invoke-CsDatabaseFailover](https://technet.microsoft.com/en-us/library/JJ204744(v=OCS.15))

<!-- end list -->

  - [Get-CsDatabaseMirrorState](https://technet.microsoft.com/en-us/library/JJ204845(v=OCS.15))

<!-- end list -->

  - [Install-CsMirrorDatabase](https://technet.microsoft.com/en-us/library/JJ204986(v=OCS.15))

  - [Uninstall-CsMirrorDatabase](unhttps://technet.microsoft.com/en-us/library/JJ204986(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsUserDatabaseState](https://technet.microsoft.com/en-us/library/Gg398831(v=OCS.15))

  - <span></span>  
    [Set-CsUserDatabaseState](set-csuserdatabasestate.md)

<!-- end list -->

  - <span></span>  
    [Update-CsUserDatabase](update-csuserdatabase.md)

<!-- end list -->

  - <span></span>  
    [Move-CsManagementServer](https://technet.microsoft.com/en-us/library/Gg412921(v=OCS.15))

  - <span></span>  
    [Set-CsManagementServer](set-csmanagementserver.md)

<!-- end list -->

  - [Invoke-CsManagementServerFailover](https://technet.microsoft.com/en-us/library/JJ204647(v=OCS.15))

**[Edge Server cmdlets in Lync Server 2013](lync-server-2013-edge-server-cmdlets.md)**

  - <span></span>  
    [Get-CsAccessEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg398574(v=OCS.15))

  - <span></span>  
    [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg413008(v=OCS.15))

  - <span></span>  
    [New-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg412884(v=OCS.15))

  - <span></span>  
    [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  - <span></span>  
    [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

<!-- end list -->

  - <span></span>  
    [Set-CsEdgeServer](set-csedgeserver.md)

**[Other server role cmdlets in Lync Server 2013](lync-server-2013-other-server-role-cmdlets.md)**

  - <span></span>  
    [Set-CsConferenceServer](set-csconferenceserver.md)

<!-- end list -->

  - <span></span>  
    [Set-CsUserServer](set-csuserserver.md)

**[Registrar and Director cmdlets in Lync Server 2013](lync-server-2013-registrar-and-director-cmdlets.md)**

  - <span></span>  
    [Set-CsDirector](set-csdirector.md)

<!-- end list -->

  - <span></span>  
    [Reset-CsPoolRegistrarState](reset-cspoolregistrarstate.md)

<!-- end list -->

  - <span></span>  
    [Set-CsRegistrar](set-csregistrar.md)

<!-- end list -->

  - <span></span>  
    [Get-CsRegistrarConfiguration](https://technet.microsoft.com/en-us/library/Gg398483(v=OCS.15))

  - <span></span>  
    [New-CsRegistrarConfiguration](https://technet.microsoft.com/en-us/library/Gg425893(v=OCS.15))

  - <span></span>  
    [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

  - <span></span>  
    [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Test-CsRegistration](test-csregistration.md)

**[Services cmdlets in Lync Server 2013](lync-server-2013-services-cmdlets.md)**

  - <span></span>  
    [Get-CsService](https://technet.microsoft.com/en-us/library/Gg413038(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsWindowsService](https://technet.microsoft.com/en-us/library/Gg398803(v=OCS.15))

  - <span></span>  
    [Start-CsWindowsService](start-cswindowsservice.md)

  - <span></span>  
    [Stop-CsWindowsService](stop-cswindowsservice.md)

**[Troubleshooting server roles and services cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-server-roles-and-services-cmdlets.md)**

  - <span></span>  
    [Get-CsAudioTestServiceApplication](https://technet.microsoft.com/en-us/library/Gg412984(v=OCS.15))

  - <span></span>  
    [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

<!-- end list -->

  - <span></span>  
    [Get-CsHealthMonitoringConfiguration](https://technet.microsoft.com/en-us/library/Gg398667(v=OCS.15))

  - <span></span>  
    [New-CsHealthMonitoringConfiguration](https://technet.microsoft.com/en-us/library/Gg398718(v=OCS.15))

  - <span></span>  
    [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)

  - <span></span>  
    [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDiagnosticConfiguration](https://technet.microsoft.com/en-us/library/Gg413034(v=OCS.15))

  - <span></span>  
    [New-CsDiagnosticConfiguration](https://technet.microsoft.com/en-us/library/Gg398733(v=OCS.15))

  - <span></span>  
    [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

  - <span></span>  
    [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsDiagnosticsFilter](https://technet.microsoft.com/en-us/library/Gg413009(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsDiagnosticHeaderConfiguration](https://technet.microsoft.com/en-us/library/Gg412774(v=OCS.15))

  - <span></span>  
    [New-CsDiagnosticHeaderConfiguration](https://technet.microsoft.com/en-us/library/Gg398350(v=OCS.15))

  - <span></span>  
    [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)

  - <span></span>  
    [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

**[Web server and services cmdlets in Lync Server 2013](lync-server-2013-web-server-and-services-cmdlets.md)**

  - <span></span>  
    [New-CsSimpleUrl](https://technet.microsoft.com/en-us/library/Gg398180(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsSimpleUrlConfiguration](https://technet.microsoft.com/en-us/library/Gg398392(v=OCS.15))

  - <span></span>  
    [New-CsSimpleUrlConfiguration](https://technet.microsoft.com/en-us/library/Gg425813(v=OCS.15))

  - <span></span>  
    [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)

  - <span></span>  
    [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsSimpleUrlEntry](https://technet.microsoft.com/en-us/library/Gg425902(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Set-CsWebServer](set-cswebserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsWebServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg425751(v=OCS.15))

  - <span></span>  
    [New-CsWebServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398440(v=OCS.15))

  - <span></span>  
    [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

  - <span></span>  
    [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsWebTrustedCACertificate](https://technet.microsoft.com/en-us/library/Gg412746(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [New-CsKerberosAccount](https://technet.microsoft.com/en-us/library/Gg398485(v=OCS.15))

<!-- end list -->

  - <span></span>  
    [Get-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398526(v=OCS.15))

  - <span></span>  
    [New-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398074(v=OCS.15))

  - <span></span>  
    [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  - <span></span>  
    [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  - <span></span>  
    [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

<!-- end list -->

  - <span></span>  
    [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

<!-- end list -->

  - [Test-CsWebApp](test-cswebapp.md)

  - [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

