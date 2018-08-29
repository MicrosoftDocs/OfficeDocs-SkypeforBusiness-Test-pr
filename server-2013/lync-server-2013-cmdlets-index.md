---
title: 'Lync Server 2013:  cmdlets index'
TOCTitle: Lync Server 2013 cmdlets index
ms:assetid: cd37aba7-3d27-4db9-b69f-3a6da1fb4b4a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398867(v=OCS.15)
ms:contentKeyID: 48185661
ms.date: 04/12/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync Server 2013 cmdlets index

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-04-12_

Microsoft Lync Server 2013 ships with more than 700 cmdlets that enable administrators to manage Lync Server 2013 from the command line. The Lync Server cmdlets are typically used with the Lync Server Management Shell. One way to use the Lync Server Management Shell is to log on to a computer running a Lync Server service or server role, click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**. After the Management Shell is open you can retrieve help for a cmdlet directly from the command line by typing a command similar to the following:

    Get-Help New-CsVoicePolicy -Full

The preceding command retrieves the complete help available for the **New-CsVoicePolicy** cmdlet. To view help for a different cmdlet, substitute **New-CsVoicePolicy** with the name of the cmdlet for which you want to retrieve help.

To retrieve a full list of cmdlets available for managing Lync Server, type the following at the Lync Server Management Shell command prompt:

    Get-Command * -Module Lync -CommandType cmdlet

For details about using the Lync Server Management Shell, see the Lync Server Windows PowerShell blog at [http://go.microsoft.com/fwlink/p/?linkId=203150](http://go.microsoft.com/fwlink/p/?linkid=203150).

<div>

## Lync Server 2013 Cmdlets

Following is a list of the cmdlets that ship with Lync Server 2013:

  - [Add-CsSlaDelegates](https://technet.microsoft.com/en-us/library/Mt703199(v=OCS.15))

  - [Approve-CsDeviceUpdateRule](https://technet.microsoft.com/en-us/library/Gg398949(v=OCS.15))

  - [Backup-CsPool](https://technet.microsoft.com/en-us/library/JJ204955(v=OCS.15))

  - [Clear-CsDeviceUpdateFile](https://technet.microsoft.com/en-us/library/Gg425835(v=OCS.15))

  - [Clear-CsDeviceUpdateLog](https://technet.microsoft.com/en-us/library/Gg412738(v=OCS.15))

  - [Clear-CsPersistentChatRoom](https://technet.microsoft.com/en-us/library/JJ204976(v=OCS.15))

  - [Convert-CsUserData](https://technet.microsoft.com/en-us/library/JJ205337(v=OCS.15))

  - [Debug-CsAddressBookReplication](https://technet.microsoft.com/en-us/library/JJ205232(v=OCS.15))

  - [Debug-CsIntraPoolReplication](https://technet.microsoft.com/en-us/library/JJ205103(v=OCS.15))

  - [Debug-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398710(v=OCS.15))

  - [Disable-CsAdDomain](https://technet.microsoft.com/en-us/library/Gg398785(v=OCS.15))

  - [Disable-CsAdForest](https://technet.microsoft.com/en-us/library/Gg398122(v=OCS.15))

  - [Disable-CsComputer](https://technet.microsoft.com/en-us/library/Gg399023(v=OCS.15))

  - [Disable-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398481(v=OCS.15))

  - [Disable-CsMeetingRoom](https://technet.microsoft.com/en-us/library/JJ204723(v=OCS.15))

  - [Disable-CsPublicProvider](https://technet.microsoft.com/en-us/library/Gg398984(v=OCS.15))

  - [Disable-CsUser](https://technet.microsoft.com/en-us/library/Gg398747(v=OCS.15))

  - [Enable-CsAdDomain](https://technet.microsoft.com/en-us/library/Gg412764(v=OCS.15))

  - [Enable-CsAdForest](https://technet.microsoft.com/en-us/library/Gg425713(v=OCS.15))

  - [Enable-CsComputer](https://technet.microsoft.com/en-us/library/Gg412815(v=OCS.15))

  - [Enable-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398166(v=OCS.15))

  - [Enable-CsMeetingRoom](https://technet.microsoft.com/en-us/library/JJ205062(v=OCS.15))

  - [Enable-CsPublicProvider](https://technet.microsoft.com/en-us/library/Gg398780(v=OCS.15))

  - [Enable-CsReplica](https://technet.microsoft.com/en-us/library/Gg425965(v=OCS.15))

  - [Enable-CsTopology](https://technet.microsoft.com/en-us/library/Gg398398(v=OCS.15))

  - [Enable-CsUser](https://technet.microsoft.com/en-us/library/Gg398711(v=OCS.15))

  - [Export-CsArchivingData](https://technet.microsoft.com/en-us/library/Gg398452(v=OCS.15))

  - [Export-CsConfiguration](https://technet.microsoft.com/en-us/library/Gg398627(v=OCS.15))

  - [Export-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398539(v=OCS.15))

  - [Export-CsPersistentChatData](https://technet.microsoft.com/en-us/library/JJ205378(v=OCS.15))

  - [Export-CsRgsConfiguration](https://technet.microsoft.com/en-us/library/JJ205011(v=OCS.15))

  - [Export-CsUserData](https://technet.microsoft.com/en-us/library/JJ204897(v=OCS.15))

  - [Get-CsAccessEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg398574(v=OCS.15))

  - [Get-CsAdContact](https://technet.microsoft.com/en-us/library/Gg412776(v=OCS.15))

  - [Get-CsAdDomain](https://technet.microsoft.com/en-us/library/Gg398453(v=OCS.15))

  - [Get-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398132(v=OCS.15))

  - [Get-CsAdForest](https://technet.microsoft.com/en-us/library/Gg412995(v=OCS.15))

  - [Get-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg399050(v=OCS.15))

  - [Get-CsAdminRoleAssignment](https://technet.microsoft.com/en-us/library/Gg398434(v=OCS.15))

  - [Get-CsAdPrincipal](https://technet.microsoft.com/en-us/library/JJ205326(v=OCS.15))

  - [Get-CsAdServerSchema](https://technet.microsoft.com/en-us/library/Gg413070(v=OCS.15))

  - [Get-CsAdUser](https://technet.microsoft.com/en-us/library/Gg398592(v=OCS.15))

  - [Get-CsAllowedDomain](https://technet.microsoft.com/en-us/library/Gg398164(v=OCS.15))

  - [Get-CsAnalogDevice](https://technet.microsoft.com/en-us/library/Gg398748(v=OCS.15))

  - [Get-CsAnnouncement](https://technet.microsoft.com/en-us/library/Gg398937(v=OCS.15))

  - [Get-CsApplicationEndpoint](https://technet.microsoft.com/en-us/library/Gg398655(v=OCS.15))

  - [Get-CsArchivingConfiguration](https://technet.microsoft.com/en-us/library/Gg399012(v=OCS.15))

  - [Get-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg425731(v=OCS.15))

  - [Get-CsAudioTestServiceApplication](https://technet.microsoft.com/en-us/library/Gg412984(v=OCS.15))

  - [Get-CsAutodiscoverConfiguration](https://technet.microsoft.com/en-us/library/Hh690014(v=OCS.15))

  - [Get-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg413008(v=OCS.15))

  - [Get-CsBackupServiceConfiguration](https://technet.microsoft.com/en-us/library/JJ205087(v=OCS.15))

  - [Get-CsBackupServiceStatus](https://technet.microsoft.com/en-us/library/JJ205032(v=OCS.15))

  - [Get-CsBandwidthPolicyServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg412727(v=OCS.15))

  - [Get-CsBlockedDomain](https://technet.microsoft.com/en-us/library/Gg398424(v=OCS.15))

  - [Get-CsCallParkOrbit](https://technet.microsoft.com/en-us/library/Gg398554(v=OCS.15))

  - [Get-CsCdrConfiguration](https://technet.microsoft.com/en-us/library/Gg398298(v=OCS.15))

  - [Get-CsCertificate](https://technet.microsoft.com/en-us/library/Gg398227(v=OCS.15))

  - [Get-CsClientAccessLicense](https://technet.microsoft.com/en-us/library/JJ204853(v=OCS.15))

  - [Get-CsClientCertificate](https://technet.microsoft.com/en-us/library/Gg398143(v=OCS.15))

  - [Get-CsClientPinInfo](https://technet.microsoft.com/en-us/library/Gg425947(v=OCS.15))

  - [Get-CsClientPolicy](https://technet.microsoft.com/en-us/library/Gg398830(v=OCS.15))

  - [Get-CsClientVersionConfiguration](https://technet.microsoft.com/en-us/library/Gg399072(v=OCS.15))

  - [Get-CsClientVersionPolicy](https://technet.microsoft.com/en-us/library/Gg398957(v=OCS.15))

  - [Get-CsClientVersionPolicyRule](https://technet.microsoft.com/en-us/library/Gg413048(v=OCS.15))

  - [Get-CsClsRegion](https://technet.microsoft.com/en-us/library/JJ204879(v=OCS.15))

  - [Get-CsClsSearchTerm](https://technet.microsoft.com/en-us/library/JJ205061(v=OCS.15))

  - [Get-CsClsScenario](https://technet.microsoft.com/en-us/library/JJ205091(v=OCS.15))

  - [Get-CsClsSecurityGroup](https://technet.microsoft.com/en-us/library/JJ205285(v=OCS.15))

  - [Get-CsCommonAreaPhone](https://technet.microsoft.com/en-us/library/Gg412934(v=OCS.15))

  - [Get-CsComputer](https://technet.microsoft.com/en-us/library/Gg425959(v=OCS.15))

  - [Get-CsConferenceDirectory](https://technet.microsoft.com/en-us/library/Gg425771(v=OCS.15))

  - [Get-CsConferenceDisclaimer](https://technet.microsoft.com/en-us/library/Gg425714(v=OCS.15))

  - [Get-CsConferencingConfiguration](https://technet.microsoft.com/en-us/library/Gg398965(v=OCS.15))

  - [Get-CsConferencingPolicy](https://technet.microsoft.com/en-us/library/Gg398293(v=OCS.15))

  - [Get-CsConfigurationStoreLocation](https://technet.microsoft.com/en-us/library/Gg412814(v=OCS.15))

  - [Get-CsCpsConfiguration](https://technet.microsoft.com/en-us/library/Gg398948(v=OCS.15))

  - [Get-CsDatabaseMirrorState](https://technet.microsoft.com/en-us/library/JJ204845(v=OCS.15))

  - [Get-CsDeviceUpdateConfiguration](https://technet.microsoft.com/en-us/library/Gg399030(v=OCS.15))

  - [Get-CsDeviceUpdateRule](https://technet.microsoft.com/en-us/library/Gg398215(v=OCS.15))

  - [Get-CsDiagnosticConfiguration](https://technet.microsoft.com/en-us/library/Gg413034(v=OCS.15))

  - [Get-CsDiagnosticHeaderConfiguration](https://technet.microsoft.com/en-us/library/Gg412774(v=OCS.15))

  - [Get-CsDialInConferencingAccessNumber](https://technet.microsoft.com/en-us/library/Gg413015(v=OCS.15))

  - [Get-CsDialInConferencingConfiguration](https://technet.microsoft.com/en-us/library/Gg398575(v=OCS.15))

  - [Get-CsDialInConferencingDtmfConfiguration](https://technet.microsoft.com/en-us/library/Gg398578(v=OCS.15))

  - [Get-CsDialInConferencingLanguageList](https://technet.microsoft.com/en-us/library/Gg425869(v=OCS.15))

  - [Get-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg413043(v=OCS.15))

  - [Get-CsEffectivePolicy](https://technet.microsoft.com/en-us/library/JJ204636(v=OCS.15))

  - [Get-CsEnhancedEmergencyServiceDisclaimer](https://technet.microsoft.com/en-us/library/Gg412877(v=OCS.15))

  - [Get-CsExternalAccessPolicy](https://technet.microsoft.com/en-us/library/Gg425805(v=OCS.15))

  - [Get-CsExUmContact](https://technet.microsoft.com/en-us/library/Gg412725(v=OCS.15))

  - [Get-CsFileTransferFilterConfiguration](https://technet.microsoft.com/en-us/library/Gg398527(v=OCS.15))

  - [Get-CsFIPSConfiguration](https://technet.microsoft.com/en-us/library/JJ204904(v=OCS.15))

  - [Get-CsHealthMonitoringConfiguration](https://technet.microsoft.com/en-us/library/Gg398667(v=OCS.15))

  - [Get-CsHostedVoicemailPolicy](https://technet.microsoft.com/en-us/library/Gg398348(v=OCS.15))

  - [Get-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg413078(v=OCS.15))

  - [Get-CsImFilterConfiguration](https://technet.microsoft.com/en-us/library/Gg398980(v=OCS.15))

  - [Get-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398526(v=OCS.15))

  - [Get-CsLisCivicAddress](https://technet.microsoft.com/en-us/library/Gg398459(v=OCS.15))

  - [Get-CsLisLocation](https://technet.microsoft.com/en-us/library/Gg412834(v=OCS.15))

  - [Get-CsLisPort](https://technet.microsoft.com/en-us/library/Gg398820(v=OCS.15))

  - [Get-CsLisServiceProvider](https://technet.microsoft.com/en-us/library/Gg398116(v=OCS.15))

  - [Get-CsLisSubnet](https://technet.microsoft.com/en-us/library/Gg398473(v=OCS.15))

  - [Get-CsLisSwitch](https://technet.microsoft.com/en-us/library/Gg425769(v=OCS.15))

  - [Get-CsLisWirelessAccessPoint](https://technet.microsoft.com/en-us/library/Gg398117(v=OCS.15))

  - [Get-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg398911(v=OCS.15))

  - [Get-CsManagementConnection](https://technet.microsoft.com/en-us/library/Gg412849(v=OCS.15))

  - [Get-CsManagementStoreReplicationStatus](https://technet.microsoft.com/en-us/library/Gg399052(v=OCS.15))

  - [Get-CsMcxConfiguration](https://technet.microsoft.com/en-us/library/Hh690031(v=OCS.15))

  - [Get-CsMediaConfiguration](https://technet.microsoft.com/en-us/library/Gg398128(v=OCS.15))

  - [Get-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/Gg425875(v=OCS.15))

  - [Get-CsMeetingRoom](https://technet.microsoft.com/en-us/library/JJ205277(v=OCS.15))

  - [Get-CsMobilityPolicy](https://technet.microsoft.com/en-us/library/Hh690017(v=OCS.15))

  - [Get-CsNetworkBandwidthPolicyProfile](https://technet.microsoft.com/en-us/library/Gg425815(v=OCS.15))

  - [Get-CsNetworkConfiguration](https://technet.microsoft.com/en-us/library/Gg398140(v=OCS.15))

  - [Get-CsNetworkInterface](https://technet.microsoft.com/en-us/library/Gg398121(v=OCS.15))

  - [Get-CsNetworkInterRegionRoute](https://technet.microsoft.com/en-us/library/Gg425817(v=OCS.15))

  - [Get-CsNetworkInterSitePolicy](https://technet.microsoft.com/en-us/library/Gg412769(v=OCS.15))

  - [Get-CsNetworkRegion](https://technet.microsoft.com/en-us/library/Gg398406(v=OCS.15))

  - [Get-CsNetworkRegionLink](https://technet.microsoft.com/en-us/library/Gg398972(v=OCS.15))

  - [Get-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398766(v=OCS.15))

  - [Get-CsNetworkSubnet](https://technet.microsoft.com/en-us/library/Gg412825(v=OCS.15))

  - [Get-CsOAuthConfiguration](https://technet.microsoft.com/en-us/library/JJ205155(v=OCS.15))

  - [Get-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ205238(v=OCS.15))

  - [Get-CsOutboundCallingNumberTranslationRule](https://technet.microsoft.com/en-us/library/JJ204962(v=OCS.15))

  - [Get-CsOutboundTranslationRule](https://technet.microsoft.com/en-us/library/Gg398104(v=OCS.15))

  - [Get-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ205128(v=OCS.15))

  - [Get-CsPersistentChatAddin](https://technet.microsoft.com/en-us/library/JJ204670(v=OCS.15))

  - [Get-CsPersistentChatCategory](https://technet.microsoft.com/en-us/library/JJ204771(v=OCS.15))

  - [Get-CsPersistentChatComplianceConfiguration](https://technet.microsoft.com/en-us/library/JJ204625(v=OCS.15))

  - [Get-CsPersistentChatConfiguration](https://technet.microsoft.com/en-us/library/JJ205140(v=OCS.15))

  - [Get-CsPersistentChatEligiblePrincipal](https://technet.microsoft.com/en-us/library/JJ204891(v=OCS.15))

  - [Get-CsPersistentChatEndpoint](https://technet.microsoft.com/en-us/library/JJ204764(v=OCS.15))

  - [Get-CsPersistentChatPolicy](https://technet.microsoft.com/en-us/library/JJ204673(v=OCS.15))

  - [Get-CsPersistentChatRoom](https://technet.microsoft.com/en-us/library/JJ205123(v=OCS.15))

  - [Get-CsPersistentChatState](https://technet.microsoft.com/en-us/library/JJ204915(v=OCS.15))

  - [Get-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398262(v=OCS.15))

  - [Get-CsPool](https://technet.microsoft.com/en-us/library/Gg398992(v=OCS.15))

  - [Get-CsPoolBackupRelationship](https://technet.microsoft.com/en-us/library/JJ204745(v=OCS.15))

  - [Get-CsPoolUpgradeReadinessState](https://technet.microsoft.com/en-us/library/JJ204689(v=OCS.15))

  - [Get-CsPresencePolicy](https://technet.microsoft.com/en-us/library/Gg398463(v=OCS.15))

  - [Get-CsPresenceProvider](https://technet.microsoft.com/en-us/library/JJ204705(v=OCS.15))

  - [Get-CsPrivacyConfiguration](https://technet.microsoft.com/en-us/library/Gg413002(v=OCS.15))

  - [Get-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg399011(v=OCS.15))

  - [Get-CsPstnUsage](https://technet.microsoft.com/en-us/library/Gg412734(v=OCS.15))

  - [Get-CsPublicProvider](https://technet.microsoft.com/en-us/library/Gg412945(v=OCS.15))

  - [Get-CsPushNotificationConfiguration](https://technet.microsoft.com/en-us/library/Hh690049(v=OCS.15))

  - [Get-CsQoEConfiguration](https://technet.microsoft.com/en-us/library/Gg399004(v=OCS.15))

  - [Get-CsRegistrarConfiguration](https://technet.microsoft.com/en-us/library/Gg398483(v=OCS.15))

  - [Get-CsReportingConfiguration](https://technet.microsoft.com/en-us/library/JJ205356(v=OCS.15))

  - [Get-CsRgsAgentGroup](https://technet.microsoft.com/en-us/library/Gg425793(v=OCS.15))

  - [Get-CsRgsConfiguration](https://technet.microsoft.com/en-us/library/Gg412762(v=OCS.15))

  - [Get-CsRgsHolidaySet](https://technet.microsoft.com/en-us/library/Gg412983(v=OCS.15))

  - [Get-CsRgsHoursOfBusiness](https://technet.microsoft.com/en-us/library/Gg398284(v=OCS.15))

  - [Get-CsRgsQueue](https://technet.microsoft.com/en-us/library/Gg412759(v=OCS.15))

  - [Get-CsRgsWorkflow](https://technet.microsoft.com/en-us/library/Gg425766(v=OCS.15))

  - [Get-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg425851(v=OCS.15))

  - [Get-CsServerApplication](https://technet.microsoft.com/en-us/library/Gg425948(v=OCS.15))

  - [Get-CsServerVersion](https://technet.microsoft.com/en-us/library/Gg398470(v=OCS.15))

  - [Get-CsService](https://technet.microsoft.com/en-us/library/Gg413038(v=OCS.15))

  - [Get-CsSimpleUrlConfiguration](https://technet.microsoft.com/en-us/library/Gg398392(v=OCS.15))

  - [Get-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg398701(v=OCS.15))

  - [Get-CsSipResponseCodeTranslationRule](https://technet.microsoft.com/en-us/library/Gg398130(v=OCS.15))

  - [Get-CsSlaConfiguration](https://technet.microsoft.com/en-us/library/Mt703200(v=OCS.15))

  - [Get-CsSite](https://technet.microsoft.com/en-us/library/Gg398185(v=OCS.15))

  - [Get-CsStaticRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg398754(v=OCS.15))

  - [Get-CsTestDevice](https://technet.microsoft.com/en-us/library/Gg398304(v=OCS.15))

  - [Get-CsTestUserCredential](https://technet.microsoft.com/en-us/library/JJ204759(v=OCS.15))

  - [Get-CsTopology](https://technet.microsoft.com/en-us/library/Gg412824(v=OCS.15))

  - [Get-CsTrunk](https://technet.microsoft.com/en-us/library/JJ205244(v=OCS.15))

  - [Get-CsTrunkConfiguration](https://technet.microsoft.com/en-us/library/Gg398224(v=OCS.15))

  - [Get-CsTrustedApplication](https://technet.microsoft.com/en-us/library/Gg399025(v=OCS.15))

  - [Get-CsTrustedApplicationComputer](https://technet.microsoft.com/en-us/library/Gg425843(v=OCS.15))

  - [Get-CsTrustedApplicationEndpoint](https://technet.microsoft.com/en-us/library/Gg413035(v=OCS.15))

  - [Get-CsTrustedApplicationPool](https://technet.microsoft.com/en-us/library/Gg413055(v=OCS.15))

  - [Get-CsUCPhoneConfiguration](https://technet.microsoft.com/en-us/library/Gg398070(v=OCS.15))

  - [Get-CsUICulture](https://technet.microsoft.com/en-us/library/Gg412900(v=OCS.15))

  - [Get-CsUnassignedNumber](https://technet.microsoft.com/en-us/library/Gg412792(v=OCS.15))

  - [Get-CsUser](https://technet.microsoft.com/en-us/library/Gg398125(v=OCS.15))

  - [Get-CsUserAcp](https://technet.microsoft.com/en-us/library/Gg398978(v=OCS.15))

  - [Get-CsUserDatabaseState](https://technet.microsoft.com/en-us/library/Gg398831(v=OCS.15))

  - [Get-CsUserPoolInfo](https://technet.microsoft.com/en-us/library/Gg398615(v=OCS.15))

  - [Get-CsUserReplicatorConfiguration](https://technet.microsoft.com/en-us/library/Gg398548(v=OCS.15))

  - [Get-CsUserServicesConfiguration](https://technet.microsoft.com/en-us/library/Gg398133(v=OCS.15))

  - [Get-CsUserServicesPolicy](https://technet.microsoft.com/en-us/library/JJ204838(v=OCS.15))

  - [Get-CsVoiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398815(v=OCS.15))

  - [Get-CsVoicemailReroutingConfiguration](https://technet.microsoft.com/en-us/library/Gg425732(v=OCS.15))

  - [Get-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398393(v=OCS.15))

  - [Get-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398101(v=OCS.15))

  - [Get-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg425926(v=OCS.15))

  - [Get-CsVoiceRoutingPolicy](https://technet.microsoft.com/en-us/library/JJ204940(v=OCS.15))

  - [Get-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg412957(v=OCS.15))

  - [Get-CsWatcherNodeConfiguration](https://technet.microsoft.com/en-us/library/JJ204739(v=OCS.15))

  - [Get-CsWebServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg425751(v=OCS.15))

  - [Get-CsWindowsService](https://technet.microsoft.com/en-us/library/Gg398803(v=OCS.15))

  - [Get-CsXmppAllowedPartner](https://technet.microsoft.com/en-us/library/JJ204981(v=OCS.15))

  - [Get-CsXmppGatewayConfiguration](https://technet.microsoft.com/en-us/library/JJ204869(v=OCS.15))

  - [Grant-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg398475(v=OCS.15))

  - [Grant-CsClientPolicy](https://technet.microsoft.com/en-us/library/Gg412942(v=OCS.15))

  - [Grant-CsClientVersionPolicy](https://technet.microsoft.com/en-us/library/Gg412903(v=OCS.15))

  - [Grant-CsConferencingPolicy](https://technet.microsoft.com/en-us/library/Gg425937(v=OCS.15))

  - [Grant-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg398547(v=OCS.15))

  - [Grant-CsExternalAccessPolicy](https://technet.microsoft.com/en-us/library/Gg425942(v=OCS.15))

  - [Grant-CsHostedVoicemailPolicy](https://technet.microsoft.com/en-us/library/Gg412829(v=OCS.15))

  - [Grant-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg413049(v=OCS.15))

  - [Grant-CsMobilityPolicy](https://technet.microsoft.com/en-us/library/Hh690038(v=OCS.15))

  - [Grant-CsOUPermission](https://technet.microsoft.com/en-us/library/Gg425739(v=OCS.15))

  - [Grant-CsPersistentChatPolicy](https://technet.microsoft.com/en-us/library/JJ204907(v=OCS.15))

  - [Grant-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398871(v=OCS.15))

  - [Grant-CsPresencePolicy](https://technet.microsoft.com/en-us/library/Gg398571(v=OCS.15))

  - [Grant-CsSetupPermission](https://technet.microsoft.com/en-us/library/Gg398569(v=OCS.15))

  - [Grant-CsUserServicesPolicy](https://technet.microsoft.com/en-us/library/JJ205388(v=OCS.15))

  - [Grant-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg398828(v=OCS.15))

  - [Grant-CsVoiceRoutingPolicy](https://technet.microsoft.com/en-us/library/JJ205141(v=OCS.15))

  - [Import-CsAnnouncementFile](https://technet.microsoft.com/en-us/library/Gg398472(v=OCS.15))

  - [Import-CsCertificate](https://technet.microsoft.com/en-us/library/Gg398688(v=OCS.15))

  - [Import-CsConfiguration](https://technet.microsoft.com/en-us/library/Gg398800(v=OCS.15))

  - [Import-CsDeviceUpdate](https://technet.microsoft.com/en-us/library/Gg398861(v=OCS.15))

  - [Import-CsLegacyConferenceDirectory](https://technet.microsoft.com/en-us/library/Gg398418(v=OCS.15))

  - [Import-CsLegacyConfiguration](https://technet.microsoft.com/en-us/library/Gg412923(v=OCS.15))

  - [Import-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398380(v=OCS.15))

  - [Import-CsPersistentChatData](https://technet.microsoft.com/en-us/library/JJ204709(v=OCS.15))

  - [Import-CsRgsAudioFile](https://technet.microsoft.com/en-us/library/Gg412830(v=OCS.15))

  - [Import-CsRgsConfiguration](https://technet.microsoft.com/en-us/library/JJ205245(v=OCS.15))

  - [Import-CsUserData](https://technet.microsoft.com/en-us/library/JJ205373(v=OCS.15))

  - [Install-CsAdServerSchema](https://technet.microsoft.com/en-us/library/Gg398681(v=OCS.15))

  - [Install-CsDatabase](https://technet.microsoft.com/en-us/library/Gg399044(v=OCS.15))

  - [Install-CsMirrorDatabase](https://technet.microsoft.com/en-us/library/JJ204986(v=OCS.15))

  - [Invoke-CsArchivingDatabasePurge](https://technet.microsoft.com/en-us/library/JJ204627(v=OCS.15))

  - [Invoke-CsBackupServiceSync](https://technet.microsoft.com/en-us/library/JJ205374(v=OCS.15))

  - [Invoke-CsCdrDatabasePurge](https://technet.microsoft.com/en-us/library/JJ205113(v=OCS.15))

  - [Invoke-CsDatabaseFailover](https://technet.microsoft.com/en-us/library/JJ204744(v=OCS.15))

  - [Invoke-CsManagementServerFailover](https://technet.microsoft.com/en-us/library/JJ204647(v=OCS.15))

  - [Invoke-CsManagementStoreReplication](https://technet.microsoft.com/en-us/library/Gg413060(v=OCS.15))

  - [Invoke-CsPoolFailBack](https://technet.microsoft.com/en-us/library/JJ204873(v=OCS.15))

  - [Invoke-CsPoolFailOver](https://technet.microsoft.com/en-us/library/JJ205189(v=OCS.15))

  - [Invoke-CsQoEDatabasePurge](https://technet.microsoft.com/en-us/library/JJ205247(v=OCS.15))

  - [Invoke-CsUcsRollback](https://technet.microsoft.com/en-us/library/JJ204661(v=OCS.15))

  - [Lock-CsClientPin](https://technet.microsoft.com/en-us/library/Gg398650(v=OCS.15))

  - [Merge-CsLegacyTopology](https://technet.microsoft.com/en-us/library/Gg425870(v=OCS.15))

  - [Move-CsAnalogDevice](https://technet.microsoft.com/en-us/library/Gg398816(v=OCS.15))

  - [Move-CsApplicationEndpoint](https://technet.microsoft.com/en-us/library/Gg398188(v=OCS.15))

  - [Move-CsCommonAreaPhone](https://technet.microsoft.com/en-us/library/Gg412837(v=OCS.15))

  - [Move-CsConferenceDirectory](https://technet.microsoft.com/en-us/library/Gg412968(v=OCS.15))

  - [Move-CsExUmContact](https://technet.microsoft.com/en-us/library/Gg425842(v=OCS.15))

  - [Move-CsLegacyUser](https://technet.microsoft.com/en-us/library/Gg413025(v=OCS.15))

  - [Move-CsManagementServer](https://technet.microsoft.com/en-us/library/Gg412921(v=OCS.15))

  - [Move-CsMeetingRoom](https://technet.microsoft.com/en-us/library/JJ204889(v=OCS.15))

  - [Move-CsRgsConfiguration](https://technet.microsoft.com/en-us/library/Gg398782(v=OCS.15))

  - [Move-CsUser](https://technet.microsoft.com/en-us/library/Gg398528(v=OCS.15))

  - [New-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398395(v=OCS.15))

  - [New-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg398271(v=OCS.15))

  - [New-CsAllowedDomain](https://technet.microsoft.com/en-us/library/Gg398628(v=OCS.15))

  - [New-CsAnalogDevice](https://technet.microsoft.com/en-us/library/Gg412937(v=OCS.15))

  - [New-CsAnnouncement](https://technet.microsoft.com/en-us/library/Gg398522(v=OCS.15))

  - [New-CsArchivingConfiguration](https://technet.microsoft.com/en-us/library/Gg398471(v=OCS.15))

  - [New-CsArchivingPolicy](https://technet.microsoft.com/en-us/library/Gg399032(v=OCS.15))

  - [New-CsAutodiscoverConfiguration](https://technet.microsoft.com/en-us/library/Hh690022(v=OCS.15))

  - [New-CsAVEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg412884(v=OCS.15))

  - [New-CsBandwidthPolicyServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398175(v=OCS.15))

  - [New-CsBlockedDomain](https://technet.microsoft.com/en-us/library/Gg398822(v=OCS.15))

  - [New-CsCallParkOrbit](https://technet.microsoft.com/en-us/library/Gg398936(v=OCS.15))

  - [New-CsCdrConfiguration](https://technet.microsoft.com/en-us/library/Gg399018(v=OCS.15))

  - [New-CsClientPolicy](https://technet.microsoft.com/en-us/library/Gg425949(v=OCS.15))

  - [New-CsClientPolicyEntry](https://technet.microsoft.com/en-us/library/Gg399046(v=OCS.15))

  - [New-CsClientVersionConfiguration](https://technet.microsoft.com/en-us/library/Gg399029(v=OCS.15))

  - [New-CsClientVersionPolicy](https://technet.microsoft.com/en-us/library/Gg398709(v=OCS.15))

  - [New-CsClientVersionPolicyRule](https://technet.microsoft.com/en-us/library/Gg398905(v=OCS.15))

  - [New-CsClsRegion](https://technet.microsoft.com/en-us/library/JJ204658(v=OCS.15))

  - [New-CsClsScenario](https://technet.microsoft.com/en-us/library/JJ205022(v=OCS.15))

  - [New-CsClsSecurityGroup](https://technet.microsoft.com/en-us/library/JJ205359(v=OCS.15))

  - [New-CsCommonAreaPhone](https://technet.microsoft.com/en-us/library/Gg398430(v=OCS.15))

  - [New-CsConferenceDirectory](https://technet.microsoft.com/en-us/library/Gg413080(v=OCS.15))

  - [New-CsConferencingConfiguration](https://technet.microsoft.com/en-us/library/Gg412967(v=OCS.15))

  - [New-CsConferencingPolicy](https://technet.microsoft.com/en-us/library/Gg413019(v=OCS.15))

  - [New-CsCpsConfiguration](https://technet.microsoft.com/en-us/library/Gg412919(v=OCS.15))

  - [New-CsDeviceUpdateConfiguration](https://technet.microsoft.com/en-us/library/Gg425761(v=OCS.15))

  - [New-CsDiagnosticConfiguration](https://technet.microsoft.com/en-us/library/Gg398733(v=OCS.15))

  - [New-CsDiagnosticHeaderConfiguration](https://technet.microsoft.com/en-us/library/Gg398350(v=OCS.15))

  - [New-CsDiagnosticsFilter](https://technet.microsoft.com/en-us/library/Gg413009(v=OCS.15))

  - [New-CsDialInConferencingAccessNumber](https://technet.microsoft.com/en-us/library/Gg398818(v=OCS.15))

  - [New-CsDialInConferencingConfiguration](https://technet.microsoft.com/en-us/library/Gg412816(v=OCS.15))

  - [New-CsDialInConferencingDtmfConfiguration](https://technet.microsoft.com/en-us/library/Gg425792(v=OCS.15))

  - [New-CsDialPlan](https://technet.microsoft.com/en-us/library/Gg425860(v=OCS.15))

  - [New-CsExtendedTest](https://technet.microsoft.com/en-us/library/JJ205275(v=OCS.15))

  - [New-CsExternalAccessPolicy](https://technet.microsoft.com/en-us/library/Gg398441(v=OCS.15))

  - [New-CsExUmContact](https://technet.microsoft.com/en-us/library/Gg398139(v=OCS.15))

  - [New-CsFileTransferFilterConfiguration](https://technet.microsoft.com/en-us/library/Gg425897(v=OCS.15))

  - [New-CsFIPSConfiguration](https://technet.microsoft.com/en-us/library/JJ205114(v=OCS.15))

  - [New-CsHealthMonitoringConfiguration](https://technet.microsoft.com/en-us/library/Gg398718(v=OCS.15))

  - [New-CsHostedVoicemailPolicy](https://technet.microsoft.com/en-us/library/Gg398653(v=OCS.15))

  - [New-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398490(v=OCS.15))

  - [New-CsImFilterConfiguration](https://technet.microsoft.com/en-us/library/Gg398244(v=OCS.15))

  - [New-CsIssuedCertId](https://technet.microsoft.com/en-us/library/Gg425814(v=OCS.15))

  - [New-CsKerberosAccount](https://technet.microsoft.com/en-us/library/Gg398485(v=OCS.15))

  - [New-CsKerberosAccountAssignment](https://technet.microsoft.com/en-us/library/Gg398074(v=OCS.15))

  - [New-CsLocationPolicy](https://technet.microsoft.com/en-us/library/Gg398231(v=OCS.15))

  - [New-CsMcxConfiguration](https://technet.microsoft.com/en-us/library/Hh690035(v=OCS.15))

  - [New-CsMediaConfiguration](https://technet.microsoft.com/en-us/library/Gg425881(v=OCS.15))

  - [New-CsMeetingConfiguration](https://technet.microsoft.com/en-us/library/Gg398065(v=OCS.15))

  - [New-CsMobilityPolicy](https://technet.microsoft.com/en-us/library/Hh689987(v=OCS.15))

  - [New-CsNetworkBandwidthPolicyProfile](https://technet.microsoft.com/en-us/library/Gg398675(v=OCS.15))

  - [New-CsNetworkBWAlternatePath](https://technet.microsoft.com/en-us/library/Gg398732(v=OCS.15))

  - [New-CsNetworkBWPolicy](https://technet.microsoft.com/en-us/library/Gg412916(v=OCS.15))

  - [New-CsNetworkInterRegionRoute](https://technet.microsoft.com/en-us/library/Gg398779(v=OCS.15))

  - [New-CsNetworkInterSitePolicy](https://technet.microsoft.com/en-us/library/Gg398994(v=OCS.15))

  - [New-CsNetworkMediaBypassConfiguration](https://technet.microsoft.com/en-us/library/Gg425718(v=OCS.15))

  - [New-CsNetworkRegion](https://technet.microsoft.com/en-us/library/Gg425829(v=OCS.15))

  - [New-CsNetworkRegionLink](https://technet.microsoft.com/en-us/library/Gg398437(v=OCS.15))

  - [New-CsNetworkSite](https://technet.microsoft.com/en-us/library/Gg398365(v=OCS.15))

  - [New-CsNetworkSubnet](https://technet.microsoft.com/en-us/library/Gg398226(v=OCS.15))

  - [New-CsOAuthServer](https://technet.microsoft.com/en-us/library/JJ205206(v=OCS.15))

  - [New-CsOutboundCallingNumberTranslationRule](https://technet.microsoft.com/en-us/library/JJ205097(v=OCS.15))

  - [New-CsOutboundTranslationRule](https://technet.microsoft.com/en-us/library/Gg412803(v=OCS.15))

  - [New-CsPartnerApplication](https://technet.microsoft.com/en-us/library/JJ204628(v=OCS.15))

  - [New-CsPersistentChatAddin](https://technet.microsoft.com/en-us/library/JJ204641(v=OCS.15))

  - [New-CsPersistentChatCategory](https://technet.microsoft.com/en-us/library/JJ204803(v=OCS.15))

  - [New-CsPersistentChatComplianceConfiguration](https://technet.microsoft.com/en-us/library/JJ205163(v=OCS.15))

  - [New-CsPersistentChatConfiguration](https://technet.microsoft.com/en-us/library/JJ205330(v=OCS.15))

  - [New-CsPersistentChatEndpoint](https://technet.microsoft.com/en-us/library/JJ204811(v=OCS.15))

  - [New-CsPersistentChatPolicy](https://technet.microsoft.com/en-us/library/JJ205396(v=OCS.15))

  - [New-CsPersistentChatRoom](https://technet.microsoft.com/en-us/library/JJ205166(v=OCS.15))

  - [New-CsPinPolicy](https://technet.microsoft.com/en-us/library/Gg398935(v=OCS.15))

  - [New-CsPresencePolicy](https://technet.microsoft.com/en-us/library/Gg412747(v=OCS.15))

  - [New-CsPresenceProvider](https://technet.microsoft.com/en-us/library/JJ204895(v=OCS.15))

  - [New-CsPrivacyConfiguration](https://technet.microsoft.com/en-us/library/Gg398807(v=OCS.15))

  - [New-CsProxyConfiguration](https://technet.microsoft.com/en-us/library/Gg398335(v=OCS.15))

  - [New-CsPublicProvider](https://technet.microsoft.com/en-us/library/Gg398161(v=OCS.15))

  - [New-CsPushNotificationConfiguration](https://technet.microsoft.com/en-us/library/Hh690027(v=OCS.15))

  - [New-CsQoEConfiguration](https://technet.microsoft.com/en-us/library/Gg398325(v=OCS.15))

  - [New-CsRegistrarConfiguration](https://technet.microsoft.com/en-us/library/Gg425893(v=OCS.15))

  - [New-CsReportingConfiguration](https://technet.microsoft.com/en-us/library/JJ204787(v=OCS.15))

  - [New-CsRgsAgentGroup](https://technet.microsoft.com/en-us/library/Gg413065(v=OCS.15))

  - [New-CsRgsAnswer](https://technet.microsoft.com/en-us/library/Gg412812(v=OCS.15))

  - [New-CsRgsCallAction](https://technet.microsoft.com/en-us/library/Gg398136(v=OCS.15))

  - [New-CsRgsHoliday](https://technet.microsoft.com/en-us/library/Gg398075(v=OCS.15))

  - [New-CsRgsHolidaySet](https://technet.microsoft.com/en-us/library/Gg398403(v=OCS.15))

  - [New-CsRgsHoursOfBusiness](https://technet.microsoft.com/en-us/library/Gg398291(v=OCS.15))

  - [New-CsRgsPrompt](https://technet.microsoft.com/en-us/library/Gg398486(v=OCS.15))

  - [New-CsRgsQuestion](https://technet.microsoft.com/en-us/library/Gg398186(v=OCS.15))

  - [New-CsRgsQueue](https://technet.microsoft.com/en-us/library/Gg398989(v=OCS.15))

  - [New-CsRgsTimeRange](https://technet.microsoft.com/en-us/library/Gg399040(v=OCS.15))

  - [New-CsRgsWorkflow](https://technet.microsoft.com/en-us/library/Gg398246(v=OCS.15))

  - [New-CsRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg399056(v=OCS.15))

  - [New-CsServerApplication](https://technet.microsoft.com/en-us/library/Gg398096(v=OCS.15))

  - [New-CsSimpleUrl](https://technet.microsoft.com/en-us/library/Gg398180(v=OCS.15))

  - [New-CsSimpleUrlConfiguration](https://technet.microsoft.com/en-us/library/Gg425813(v=OCS.15))

  - [New-CsSimpleUrlEntry](https://technet.microsoft.com/en-us/library/Gg425902(v=OCS.15))

  - [New-CsSipDomain](https://technet.microsoft.com/en-us/library/Gg425857(v=OCS.15))

  - [New-CsSipProxyCustom](https://technet.microsoft.com/en-us/library/Gg425904(v=OCS.15))

  - [New-CsSipProxyRealm](https://technet.microsoft.com/en-us/library/Gg413084(v=OCS.15))

  - [New-CsSipProxyTCP](https://technet.microsoft.com/en-us/library/Gg425745(v=OCS.15))

  - [New-CsSipProxyTLS](https://technet.microsoft.com/en-us/library/Gg398629(v=OCS.15))

  - [New-CsSipProxyTransport](https://technet.microsoft.com/en-us/library/Gg398489(v=OCS.15))

  - [New-CsSipProxyUseDefault](https://technet.microsoft.com/en-us/library/Gg398274(v=OCS.15))

  - [New-CsSipProxyUseDefaultCert](https://technet.microsoft.com/en-us/library/Gg425858(v=OCS.15))

  - [New-CsSipResponseCodeTranslationRule](https://technet.microsoft.com/en-us/library/Gg413041(v=OCS.15))

  - [New-CsStaticRoute](https://technet.microsoft.com/en-us/library/Gg398265(v=OCS.15))

  - [New-CsStaticRoutingConfiguration](https://technet.microsoft.com/en-us/library/Gg425811(v=OCS.15))

  - [New-CsTestDevice](https://technet.microsoft.com/en-us/library/Gg425899(v=OCS.15))

  - [New-CsTrunkConfiguration](https://technet.microsoft.com/en-us/library/Gg413021(v=OCS.15))

  - [New-CsTrustedApplication](https://technet.microsoft.com/en-us/library/Gg398259(v=OCS.15))

  - [New-CsTrustedApplicationComputer](https://technet.microsoft.com/en-us/library/Gg398405(v=OCS.15))

  - [New-CsTrustedApplicationEndpoint](https://technet.microsoft.com/en-us/library/Gg398594(v=OCS.15))

  - [New-CsTrustedApplicationPool](https://technet.microsoft.com/en-us/library/Gg425804(v=OCS.15))

  - [New-CsUCPhoneConfiguration](https://technet.microsoft.com/en-us/library/Gg398445(v=OCS.15))

  - [New-CsUnassignedNumber](https://technet.microsoft.com/en-us/library/Gg398651(v=OCS.15))

  - [New-CsUserReplicatorConfiguration](https://technet.microsoft.com/en-us/library/Gg399059(v=OCS.15))

  - [New-CsUserServicesConfiguration](https://technet.microsoft.com/en-us/library/Gg412926(v=OCS.15))

  - [New-CsUserServicesPolicy](https://technet.microsoft.com/en-us/library/JJ205072(v=OCS.15))

  - [New-CsVoicemailReroutingConfiguration](https://technet.microsoft.com/en-us/library/Gg425849(v=OCS.15))

  - [New-CsVoiceNormalizationRule](https://technet.microsoft.com/en-us/library/Gg398240(v=OCS.15))

  - [New-CsVoicePolicy](https://technet.microsoft.com/en-us/library/Gg425856(v=OCS.15))

  - [New-CsVoiceRegex](https://technet.microsoft.com/en-us/library/Gg412751(v=OCS.15))

  - [New-CsVoiceRoute](https://technet.microsoft.com/en-us/library/Gg398197(v=OCS.15))

  - [New-CsVoiceRoutingPolicy](https://technet.microsoft.com/en-us/library/JJ205135(v=OCS.15))

  - [New-CsVoiceTestConfiguration](https://technet.microsoft.com/en-us/library/Gg398961(v=OCS.15))

  - [New-CsWatcherNodeConfiguration](https://technet.microsoft.com/en-us/library/JJ205254(v=OCS.15))

  - [New-CsWebLink](https://technet.microsoft.com/en-us/library/Hh690053(v=OCS.15))

  - [New-CsWebServiceConfiguration](https://technet.microsoft.com/en-us/library/Gg398440(v=OCS.15))

  - [New-CsWebTrustedCACertificate](https://technet.microsoft.com/en-us/library/Gg412746(v=OCS.15))

  - [New-CsXmppAllowedPartner](https://technet.microsoft.com/en-us/library/JJ204631(v=OCS.15))

  - [Publish-CsLisConfiguration](https://technet.microsoft.com/en-us/library/Gg398364(v=OCS.15))

  - [Publish-CsTopology](https://technet.microsoft.com/en-us/library/Gg398953(v=OCS.15))

  - [Remove-CsAddressBookConfiguration](https://technet.microsoft.com/en-us/library/Gg398934(v=OCS.15))

  - [Remove-CsAdminRole](https://technet.microsoft.com/en-us/library/Gg413036(v=OCS.15))

  - [Remove-CsAllowedDomain](https://technet.microsoft.com/en-us/library/Gg398913(v=OCS.15))

  - [Remove-CsAnalogDevice](rehttps://technet.microsoft.com/en-us/library/Gg398816(v=OCS.15))

  - [Remove-CsAnnouncement](remove-csannouncement.md)

  - [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)

  - [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

  - [Remove-CsAutodiscoverConfiguration](remove-csautodiscoverconfiguration.md)

  - [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  - [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

  - [Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)

  - [Remove-CsBlockedDomain](remove-csblockeddomain.md)

  - [Remove-CsCallParkOrbit](remove-cscallparkorbit.md)

  - [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

  - [Remove-CsCertificate](remove-cscertificate.md)

  - [Remove-CsClientPolicy](remove-csclientpolicy.md)

  - [Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)

  - [Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)

  - [Remove-CsClientVersionPolicyRule](remove-csclientversionpolicyrule.md)

  - [Remove-CsClsRegion](remove-csclsregion.md)

  - [Remove-CsClsScenario](remove-csclsscenario.md)

  - [Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)

  - [Remove-CsCommonAreaPhone](rehttps://technet.microsoft.com/en-us/library/Gg412837(v=OCS.15))

  - [Remove-CsConferenceDirectory](rehttps://technet.microsoft.com/en-us/library/Gg412968(v=OCS.15))

  - [Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

  - [Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)

  - [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)

  - [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

  - [Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)

  - [Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)

  - [Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)

  - [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

  - [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)

  - [Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)

  - [Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)

  - [Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)

  - [Remove-CsDialPlan](remove-csdialplan.md)

  - [Remove-CsEnhancedEmergencyServiceDisclaimer](remove-csenhancedemergencyservicedisclaimer.md)

  - [Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)

  - [Remove-CsExUmContact](rehttps://technet.microsoft.com/en-us/library/Gg425842(v=OCS.15))

  - [Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)

  - [Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)

  - [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)

  - [Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)

  - [Remove-CsHostingProvider](remove-cshostingprovider.md)

  - [Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)

  - [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  - [Remove-CsLisLocation](remove-cslislocation.md)

  - [Remove-CsLisPort](remove-cslisport.md)

  - [Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)

  - [Remove-CsLisSubnet](remove-cslissubnet.md)

  - [Remove-CsLisSwitch](remove-cslisswitch.md)

  - [Remove-CsLisWirelessAccessPoint](remove-csliswirelessaccesspoint.md)

  - [Remove-CsLocationPolicy](remove-cslocationpolicy.md)

  - [Remove-CsManagementConnection](remove-csmanagementconnection.md)

  - [Remove-CsMcxConfiguration](remove-csmcxconfiguration.md)

  - [Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)

  - [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)

  - [Remove-CsMobilityPolicy](remove-csmobilitypolicy.md)

  - [Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)

  - [Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)

  - [Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)

  - [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)

  - [Remove-CsNetworkRegion](remove-csnetworkregion.md)

  - [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)

  - [Remove-CsNetworkSite](remove-csnetworksite.md)

  - [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)

  - [Remove-CsOAuthServer](remove-csoauthserver.md)

  - [Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)

  - [Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)

  - [Remove-CsPartnerApplication](remove-cspartnerapplication.md)

  - [Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)

  - [Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)

  - [Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)

  - [Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)

  - [Remove-CsPersistentChatEndpoint](remove-cspersistentchatendpoint.md)

  - [Remove-CsPersistentChatMessage](remove-cspersistentchatmessage.md)

  - [Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)

  - [Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)

  - [Remove-CsPinPolicy](remove-cspinpolicy.md)

  - [Remove-CsPresencePolicy](remove-cspresencepolicy.md)

  - [Remove-CsPresenceProvider](remove-cspresenceprovider.md)

  - [Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)

  - [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

  - [Remove-CsPublicProvider](remove-cspublicprovider.md)

  - [Remove-CsPushNotificationConfiguration](remove-cspushnotificationconfiguration.md)

  - [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)

  - [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

  - [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)

  - [Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)

  - [Remove-CsRgsHolidaySet](remove-csrgsholidayset.md)

  - [Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)

  - [Remove-CsRgsQueue](remove-csrgsqueue.md)

  - [Remove-CsRgsWorkflow](remove-csrgsworkflow.md)

  - [Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)

  - [Remove-CsServerApplication](remove-csserverapplication.md)

  - [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)

  - [Remove-CsSipDomain](remove-cssipdomain.md)

  - [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)

  - [Remove-CsSlaConfiguration](remove-csslaconfiguration.md)

  - [Remove-CsSlaDelegates](remove-cssladelegates.md)

  - [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

  - [Remove-CsTestDevice](remove-cstestdevice.md)

  - [Remove-CsTestUserCredential](remove-cstestusercredential.md)

  - [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)

  - [Remove-CsTrustedApplication](remove-cstrustedapplication.md)

  - [Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)

  - [Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)

  - [Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)

  - [Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)

  - [Remove-CsUnassignedNumber](remove-csunassignednumber.md)

  - [Remove-CsUserAcp](remove-csuseracp.md)

  - [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)

  - [Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)

  - [Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)

  - [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)

  - [Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)

  - [Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)

  - [Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)

  - [Remove-CsVoicePolicy](remove-csvoicepolicy.md)

  - [Remove-CsVoiceRoute](remove-csvoiceroute.md)

  - [Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)

  - [Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)

  - [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)

  - [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

  - [Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)

  - [Request-CsCertificate](request-cscertificate.md)

  - [Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md)

  - [Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)

  - [Revoke-CsClientCertificate](revoke-csclientcertificate.md)

  - [Revoke-CsOUPermission](revoke-csoupermission.md)

  - [Revoke-CsSetupPermission](revoke-cssetuppermission.md)

  - [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

  - [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

  - [Set-CsAdminRole](set-csadminrole.md)

  - [Set-CsAllowedDomain](set-csalloweddomain.md)

  - [Set-CsAnalogDevice](set-csanalogdevice.md)

  - [Set-CsAnnouncement](set-csannouncement.md)

  - [Set-CsApplicationServer](set-csapplicationserver.md)

  - [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)

  - [Set-CsArchivingPolicy](set-csarchivingpolicy.md)

  - [Set-CsArchivingServer](set-csarchivingserver.md)

  - [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

  - [Set-CsAutodiscoverConfiguration](set-csautodiscoverconfiguration.md)

  - [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

  - [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

  - [Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)

  - [Set-CsBlockedDomain](set-csblockeddomain.md)

  - [Set-CsCallParkOrbit](set-cscallparkorbit.md)

  - [Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

  - [Set-CsCdrConfiguration](set-cscdrconfiguration.md)

  - [Set-CsCertificate](set-cscertificate.md)

  - [Set-CsClientPin](set-csclientpin.md)

  - [Set-CsClientPolicy](set-csclientpolicy.md)

  - [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

  - [Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

  - [Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)

  - [Set-CsClsRegion](set-csclsregion.md)

  - [Set-CsClsScenario](set-csclsscenario.md)

  - [Set-CsClsSearchTerm](set-csclssearchterm.md)

  - [Set-CsClsSecurityGroup](set-csclssecuritygroup.md)

  - [Set-CsCommonAreaPhone](set-cscommonareaphone.md)

  - [Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

  - [Set-CsConferenceServer](set-csconferenceserver.md)

  - [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

  - [Set-CsConferencingPolicy](set-csconferencingpolicy.md)

  - [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

  - [Set-CsCpsConfiguration](set-cscpsconfiguration.md)

  - [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

  - [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

  - [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

  - [Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

  - [Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

  - [Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

  - [Set-CsDialPlan](set-csdialplan.md)Set-CsDialPlan

  - [Set-CsDirector](set-csdirector.md)

  - [Set-CsEdgeServer](set-csedgeserver.md)

  - [Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)

  - [Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)

  - [Set-CsExUmContact](set-csexumcontact.md)

  - [Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)

  - [Set-CsFIPSConfiguration](set-csfipsconfiguration.md)

  - [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

  - [Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)

  - [Set-CsHostingProvider](set-cshostingprovider.md)

  - [Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)

  - [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  - [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

  - [Set-CsLisLocation](set-cslislocation.md)

  - [Set-CsLisPort](set-cslisport.md)

  - [Set-CsLisServiceProvider](set-cslisserviceprovider.md)

  - [Set-CsLisSubnet](set-cslissubnet.md)

  - [Set-CsLisSwitch](set-cslisswitch.md)

  - [Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)

  - [Set-CsLocationPolicy](set-cslocationpolicy.md)

  - [Set-CsManagementConnection](set-csmanagementconnection.md)

  - [Set-CsMcxConfiguration](set-csmcxconfiguration.md)

  - [Set-CsManagementServer](set-csmanagementserver.md)

  - [Set-CsMediaConfiguration](set-csmediaconfiguration.md)

  - [Set-CsMediationServer](set-csmediationserver.md)

  - [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

  - [Set-CsMeetingRoom](set-csmeetingroom.md)

  - [Set-CsMobilityPolicy](set-csmobilitypolicy.md)

  - [Set-CsMonitoringServer](set-csmonitoringserver.md)

  - [Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

  - [Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)

  - [Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)

  - [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

  - [Set-CsNetworkRegion](set-csnetworkregion.md)

  - [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)

  - [Set-CsNetworkSite](set-csnetworksite.md)

  - [Set-CsNetworkSubnet](set-csnetworksubnet.md)

  - [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

  - [Set-CsOAuthServer](set-csoauthserver.md)

  - [Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

  - [Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)

  - [Set-CsPartnerApplication](set-cspartnerapplication.md)

  - [Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md)

  - [Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

  - [Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

  - [Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)

  - [Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)

  - [Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

  - [Set-CsPersistentChatRoom](set-cspersistentchatroom.md)

  - [Set-CsPersistentChatState](set-cspersistentchatstate.md)

  - [Set-CsPinPolicy](set-cspinpolicy.md)

  - [Set-CsPresencePolicy](set-cspresencepolicy.md)

  - [Set-CsPresenceProvider](set-cspresenceprovider.md)

  - [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

  - [Set-CsProxyConfiguration](set-csproxyconfiguration.md)

  - [Set-CsPstnGateway](set-cspstngateway.md)

  - [Set-CsPstnUsage](set-cspstnusage.md)

  - [Set-CsPublicProvider](set-cspublicprovider.md)

  - [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md)

  - [Set-CsQoEConfiguration](set-csqoeconfiguration.md)

  - [Set-CsRegistrar](set-csregistrar.md)

  - [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

  - [Set-CsReportingConfiguration](set-csreportingconfiguration.md)

  - [Set-CsRgsAgentGroup](set-csrgsagentgroup.md)

  - [Set-CsRgsConfiguration](set-csrgsconfiguration.md)

  - [Set-CsRgsHolidaySet](set-csrgsholidayset.md)

  - [Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)

  - [Set-CsRgsQueue](set-csrgsqueue.md)

  - [Set-CsRgsWorkflow](set-csrgsworkflow.md)

  - [Set-CsRoutingConfiguration](set-csroutingconfiguration.md)

  - [Set-CsServerApplication](set-csserverapplication.md)

  - [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

  - [Set-CsSipDomain](set-cssipdomain.md)

  - [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

  - [Set-CsSite](set-cssite.md)

  - [Set-CsSlaConfiguration](set-csslaconfiguration.md)

  - [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

  - [Set-CsTestDevice](set-cstestdevice.md)

  - [Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)

  - [Set-CsTrustedApplication](set-cstrustedapplication.md)

  - [Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)

  - [Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)

  - [Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)

  - [Set-CsUICulture](set-csuiculture.md)

  - [Set-CsUnassignedNumber](set-csunassignednumber.md)

  - [Set-CsUser](set-csuser.md)

  - [Set-CsUserAcp](set-csuseracp.md)

  - [Set-CsUserDatabaseState](set-csuserdatabasestate.md)

  - [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

  - [Set-CsUserServer](set-csuserserver.md)

  - [Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

  - [Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

  - [Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)

  - [Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)

  - [Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)

  - [Set-CsVoicePolicy](set-csvoicepolicy.md)

  - [Set-CsVoiceRoute](set-csvoiceroute.md)

  - [Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

  - [Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)

  - [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

  - [Set-CsWebServer](set-cswebserver.md)

  - [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

  - [Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

  - [Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)

  - [Start-CsWindowsService](start-cswindowsservice.md)

  - [Stop-CsWindowsService](stop-cswindowsservice.md)

  - [Sync-CsUserData](sync-csuserdata.md)

  - [Test-CsAddressBookService](test-csaddressbookservice.md)

  - [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

  - [Test-CsASConference](test-csasconference.md)

  - [Test-CsAudioConferencingProvider](test-csaudioconferencingprovider.md)

  - [Test-CsAVConference](test-csavconference.md)

  - [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

  - [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)

  - [Test-CsComputer](test-cscomputer.md)

  - [Test-CsDatabase](test-csdatabase.md)

  - [Test-CsDataConference](test-csdataconference.md)

  - [Test-CsDialInConferencing](test-csdialinconferencing.md)

  - [Test-CsDialPlan](test-csdialplan.md)

  - [Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)

  - [Test-CsExStorageNotification](test-csexstoragenotification.md)

  - [Test-CsExUMConnectivity](test-csexumconnectivity.md)

  - [Test-CsExUMVoiceMail](test-csexumvoicemail.md)

  - [Test-CsFederatedPartner](test-csfederatedpartner.md)

  - [Test-CsGroupExpansion](test-csgroupexpansion.md)

  - [Test-CsGroupIM](test-csgroupim.md)

  - [Test-CsIM](test-csim.md)

  - [Test-CsInterTrunkRouting](test-csintertrunkrouting.md)

  - [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

  - [Test-CsLisCivicAddress](test-csliscivicaddress.md)

  - [Test-CsLisConfiguration](test-cslisconfiguration.md)

  - [Test-CsLocationPolicy](test-cslocationpolicy.md)

  - [Test-CsMcxConference](test-csmcxconference.md)

  - [Test-CsMcxP2PIM](test-csmcxp2pim.md)

  - [Test-CsMcxPushNotification](test-csmcxpushnotification.md)

  - [Test-CsOUPermission](test-csoupermission.md)

  - [Test-CsP2PAV](test-csp2pav.md)

  - [Test-CsPersistentChatMessage](test-cspersistentchatmessage.md)

  - [Test-CsPhoneBootstrap](test-csphonebootstrap.md)

  - [Test-CsPresence](test-cspresence.md)

  - [Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)

  - [Test-CsPstnPeerToPeerCall](test-cspstnpeertopeercall.md)

  - [Test-CsRegistration](test-csregistration.md)

  - [Test-CsReplica](test-csreplica.md)

  - [Test-CsSetupPermission](test-cssetuppermission.md)

  - [Test-CsTopology](test-cstopology.md)

  - [Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

  - [Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)

  - [Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)

  - [Test-CsVoicePolicy](test-csvoicepolicy.md)

  - [Test-CsVoiceRoute](test-csvoiceroute.md)

  - [Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

  - [Test-CsVoiceUser](test-csvoiceuser.md)

  - [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

  - [Test-CsWebApp](test-cswebapp.md)

  - [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

  - [Test-CsWebScheduler](test-cswebscheduler.md)

  - [Test-CsXmppIM](test-csxmppim.md)

  - [Uninstall-CsDatabase](unhttps://technet.microsoft.com/en-us/library/Gg399044(v=OCS.15))

  - [Uninstall-CsMirrorDatabase](unhttps://technet.microsoft.com/en-us/library/JJ204986(v=OCS.15))

  - [Unlock-CsClientPin](unhttps://technet.microsoft.com/en-us/library/Gg398650(v=OCS.15))

  - [Unpublish-CsLisConfiguration](unhttps://technet.microsoft.com/en-us/library/Gg398364(v=OCS.15))

  - [Update-CsAddressBook](update-csaddressbook.md)

  - [Update-CsAdminRole](update-csadminrole.md)

  - [Update-CsTenantMeetingUrl](update-cstenantmeetingurl.md)

  - [Update-CsUserData](update-csuserdata.md)

  - [Update-CsUserDatabase](update-csuserdatabase.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

