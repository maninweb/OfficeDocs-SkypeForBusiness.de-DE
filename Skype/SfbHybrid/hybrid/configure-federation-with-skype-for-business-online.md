---
title: Konfigurieren von Skype for Business Hybrid
ms.reviewer: ''
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Hybrid
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom: ''
description: 'Zusammenfassung: Hier erfahren Sie, wie Sie die Interoperabilität zwischen Ihrer lokalen Bereitstellung und Skype for Business Online konfigurieren.'
ms.openlocfilehash: 59f5f752e7a6d9fa4047e736f1a988819525955e
ms.sourcegitcommit: 1336f6c182043016c42660d5f21632d82febb658
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "36160593"
---
# <a name="configure-skype-for-business-hybrid"></a><span data-ttu-id="2001f-103">Konfigurieren von Skype for Business Hybrid</span><span class="sxs-lookup"><span data-stu-id="2001f-103">Configure Skype for Business hybrid</span></span>

<span data-ttu-id="2001f-104">Um Skype for Business Hybrid zu konfigurieren, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="2001f-104">To configure Skype for Business hybrid, you need to:</span></span>

- <span data-ttu-id="2001f-105">[Konfigurieren Sie den lokalen Umgebungs Dienst für die Föderation mit Office 365](#configure-your-on-premises-edge-service-to-federate-with-office-365).</span><span class="sxs-lookup"><span data-stu-id="2001f-105">[Configure your on-premises environment service to federate with Office 365](#configure-your-on-premises-edge-service-to-federate-with-office-365).</span></span>
- <span data-ttu-id="2001f-106">[Konfigurieren Sie Ihre lokale Umgebung, um Office 365 zu Vertrauen und den freigegebenen SIP-Adressraum mit Office 365 zu aktivieren](#configure-your-on-premises-environment-to-enable-shared-sip-address-space-with-office-365).</span><span class="sxs-lookup"><span data-stu-id="2001f-106">[Configure your on-premises environment to trust Office 365 and enable shared SIP address space with Office 365](#configure-your-on-premises-environment-to-enable-shared-sip-address-space-with-office-365).</span></span>
- <span data-ttu-id="2001f-107">[Aktivieren Sie den freigegebenen SIP-Adressraum in Ihrem Office 365 Mandanten](#enable-shared-sip-address-space-in-your-office-365-tenant).</span><span class="sxs-lookup"><span data-stu-id="2001f-107">[Enable shared SIP address space in your Office 365 tenant](#enable-shared-sip-address-space-in-your-office-365-tenant).</span></span>

<span data-ttu-id="2001f-108">Beachten Sie, dass Sie bei einer lokalen Exchange-Organisation möglicherweise OAuth zwischen der lokalen Exchange-Umgebung und Skype for Business Online Umgebungen konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2001f-108">Note that if you have Exchange on-premises, you may want to configure OAuth between your Exchange on-premises and Skype for Business Online environments.</span></span> <span data-ttu-id="2001f-109">Weitere Informationen finden Sie unter [Verwalten der Server-zu-Server-Authentifizierung in Skype for Business Server](https://docs.microsoft.com/en-us/SkypeForBusiness/manage/authentication/server-to-server-and-partner-applications) und [Planen der Integration von Skype for Business und Exchange](https://docs.microsoft.com/en-us/SkypeForBusiness/plan-your-deployment/integrate-with-exchange/integrate-with-exchange#feature_support).</span><span class="sxs-lookup"><span data-stu-id="2001f-109">For more information, see  [Manage server-to-server authentication in Skype for Business Server](https://docs.microsoft.com/en-us/SkypeForBusiness/manage/authentication/server-to-server-and-partner-applications) and [Plan to integrate Skype for Business and Exchange](https://docs.microsoft.com/en-us/SkypeForBusiness/plan-your-deployment/integrate-with-exchange/integrate-with-exchange#feature_support).</span></span> 
  
## <a name="configure-your-on-premises-edge-service-to-federate-with-office-365"></a><span data-ttu-id="2001f-110">Konfigurieren des lokalen Edge-Diensts für die Zusammenlegung mit Office 365</span><span class="sxs-lookup"><span data-stu-id="2001f-110">Configure your on-premises Edge service to federate with Office 365</span></span>

<span data-ttu-id="2001f-111">Mit dem Partnerverbund können Benutzer in Ihrer lokalen Bereitstellung mit Office 365 Benutzern in Ihrer Organisation kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2001f-111">Federation allows users in your on-premises deployment to communicate with Office 365 users in your organization.</span></span> <span data-ttu-id="2001f-112">Führen Sie das folgende Cmdlet in der Skype for Business Server Verwaltungsshell aus, um den Verbund zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="2001f-112">To configure federation, run the following cmdlet in the Skype for Business Server Management Shell:</span></span>
  
```
Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -EnablePartnerDiscovery 1 -UseDnsSrvRouting
```

<span data-ttu-id="2001f-113">Wenn der Wert "-EnablePartnerDiscovery" auf 1 festgelegt ist, verwendet Skype for Business Server DNS-Einträge, um Partnerdomänen zu testen und zu ermitteln, die nicht in der AllowedDomains-Liste aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="2001f-113">If '-EnablePartnerDiscovery' value set to 1, Skype for Business Server will use DNS records to try and discover partner domains not listed in the AllowedDomains list.</span></span> <span data-ttu-id="2001f-114">Wenn der Wert auf 0 festgelegt ist, wird Skype for Business Server nur eine Föderation mit Domänen in der AllowedDomains-Liste haben.</span><span class="sxs-lookup"><span data-stu-id="2001f-114">If the value set to 0, Skype for Business Server will only federate with domains found on the AllowedDomains list.</span></span> <span data-ttu-id="2001f-115">Dieser Parameter ist für die Verwendung von DNS-Dienstrouting erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2001f-115">This parameter is required if you use DNS service routing.</span></span>



## <a name="configure-your-on-premises-environment-to-enable-shared-sip-address-space-with-office-365"></a><span data-ttu-id="2001f-116">Konfigurieren der lokalen Umgebung zur Aktivierung des freigegebenen SIP-Adressraums mit Office 365</span><span class="sxs-lookup"><span data-stu-id="2001f-116">Configure your on-premises environment to enable shared SIP address space with Office 365</span></span>

<span data-ttu-id="2001f-117">Sie müssen auch Ihre lokale Umgebung so konfigurieren, dass Office 365 vertraut und der freigegebene SIP-Adressraum mit Office 365 aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="2001f-117">You must also configure your on-premises environment to trust Office 365 and enable shared SIP address space with Office 365.</span></span> <span data-ttu-id="2001f-118">Dies bedeutet, dass Office 365 potenziell Benutzerkonten für dieselbe Gruppe von SIP-Domänen wie Ihre lokale Umgebung hosten kann und dass Nachrichten zwischen Benutzern, die lokal gehostet werden, und Online weitergeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="2001f-118">This means Office 365 can potentially host user accounts for the same set of SIP domains as your on-premises environment, and messages can be routed between users hosted on premises and online.</span></span>  <span data-ttu-id="2001f-119">Konfigurieren Sie hierzu einen Hostinganbieter mit ProxyFqdn = sipfed. online. lync. com, wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2001f-119">You do this by configuring a hosting provider with ProxyFqdn=sipfed.online.lync.com as described below.</span></span>

<span data-ttu-id="2001f-120">Überprüfen Sie zunächst, ob Sie bereits über einen Hostinganbieter mit ProxyFqdn = sipfed. online. lync. com verfügen.</span><span class="sxs-lookup"><span data-stu-id="2001f-120">First, check if you already have a hosting provider with ProxyFqdn=sipfed.online.lync.com.</span></span> <span data-ttu-id="2001f-121">Wenn eine vorhanden ist, entfernen Sie Sie mithilfe des folgenden Befehls:</span><span class="sxs-lookup"><span data-stu-id="2001f-121">If one exists, then remove it by using the following command:</span></span>

```
Get-CsHostingProvider | ?{ $_.ProxyFqdn -eq "sipfed.online.lync.com" } | Remove-CsHostingProvider
```

<span data-ttu-id="2001f-122">Erstellen Sie dann einen neuen Hostinganbieter, verwenden Sie das New-CsHostingProvider-Cmdlet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2001f-122">Then create a new hosting provider, use the New-CsHostingProvider cmdlet as follows:</span></span> 

```
New-CsHostingProvider -Identity Office365 -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root 
```

 ## <a name="enable-shared-sip-address-space-in-your-office-365-tenant"></a><span data-ttu-id="2001f-123">Aktivieren des freigegebenen SIP-Adressraums in Ihrem Office 365 Mandanten</span><span class="sxs-lookup"><span data-stu-id="2001f-123">Enable shared SIP address space in your Office 365 tenant</span></span>
  
<span data-ttu-id="2001f-124">Zusätzlich zu der Änderung, die Sie in Ihrer lokalen Bereitstellung vorgenommen haben, müssen Sie die entsprechende Änderung in Ihrem Office 365 Mandanten zu aktiviertem freigegebenem SIP-Adressraum mit Ihrer lokalen Bereitstellung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="2001f-124">In addition to the change you made in your on-premises deployment, you'll need to make the corresponding change in your Office 365 tenant to enabled shared SIP address space with your on-premises deployment.</span></span>  

<span data-ttu-id="2001f-125">Um den freigegebenen SIP-Adressraum in Ihrem Office 365 Mandanten zu aktivieren, richten Sie eine Remote-PowerShell-Sitzung mit Skype for Business Online ein, und führen Sie dann das folgende Cmdlet aus:</span><span class="sxs-lookup"><span data-stu-id="2001f-125">To enable shared SIP address space in your Office 365 tenant, establish a remote PowerShell session with Skype for Business Online, and then run the following cmdlet:</span></span>
  
```
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true
```

> [!NOTE]
> <span data-ttu-id="2001f-126">Das SharedSipAddressSpace-Attribut muss "true" bleiben, bis der Wechsel zu Online abgeschlossen ist und keine Benutzer lokal verbleiben.</span><span class="sxs-lookup"><span data-stu-id="2001f-126">The SharedSipAddressSpace attribute needs to remain "True" until moving to online is final, and no users remain on-premises.</span></span> 
  
<span data-ttu-id="2001f-127">Um eine Remote-PowerShell-Sitzung mit Teams oder Skype for Business Online einzurichten, müssen Sie zuerst das Skype for Business Online-Connector-Modul für Windows PowerShell installieren, das Sie [hier](https://go.microsoft.com/fwlink/p/?LinkId=391911)erhalten können.</span><span class="sxs-lookup"><span data-stu-id="2001f-127">To establish a remote PowerShell session with Teams or Skype for Business Online, you first need to install the Skype for Business Online connector module for Windows PowerShell, which you can get [here](https://go.microsoft.com/fwlink/p/?LinkId=391911).</span></span>
  
<span data-ttu-id="2001f-128">Nachdem Sie das Modul installiert haben, können Sie eine Remotesitzung mit den folgenden Cmdlets einrichten:</span><span class="sxs-lookup"><span data-stu-id="2001f-128">After you install the module, you can establish a remote session with the following cmdlets:</span></span>
  
```
$cred = Get-Credential
Import-PSSession (New-CsOnlineSession -Credential $cred) -AllowClobber
```

<span data-ttu-id="2001f-129">Weitere Informationen zum Einrichten einer Remote-PowerShell-Sitzung mit Skype for Business Online und zur Verwendung des Skype for Business Online-Connector-Moduls finden Sie unter [Einrichten Ihres Computers für Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2001f-129">For more information about how to establish a remote PowerShell session with Skype for Business Online, and how to use the Skype for Business Online Connector module, see [Set up your computer for Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).</span></span>
  


## <a name="see-also"></a><span data-ttu-id="2001f-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2001f-130">See also</span></span>

[<span data-ttu-id="2001f-131">New-CsHostingProvider</span><span class="sxs-lookup"><span data-stu-id="2001f-131">New-CsHostingProvider</span></span>](https://docs.microsoft.com/powershell/module/skype/new-cshostingprovider?view=skype-ps)
