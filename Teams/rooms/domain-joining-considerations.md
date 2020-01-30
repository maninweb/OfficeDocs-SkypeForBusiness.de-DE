---
title: Überlegungen zur Domänenzusammenführung in Skype Room System
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
localization_priority: Normal
ms.assetid: 3034fdcb-7c89-42c4-9c5e-13400e82d88f
ms.collection:
- M365-collaboration
description: Lesen Sie dieses Thema und erfahren Sie, wie Sie Ihrer Domäne einen Skype Room System-Anwendungs-PC hinzufügen.
ms.openlocfilehash: d6002174e067152b1aefee45899e291063f19853
ms.sourcegitcommit: 9bead87a7f4c4e71f19f8980e9dce2b979735055
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "41268962"
---
<!-- This asset missed in the rebrand, and honestly not sure if it's worth keeping.   -->

# <a name="skype-room-system-domain-joining-considerations"></a><span data-ttu-id="3b71c-103">Überlegungen zur Domänenzusammenführung in Skype Room System</span><span class="sxs-lookup"><span data-stu-id="3b71c-103">Skype Room System domain joining considerations</span></span>
 
<span data-ttu-id="3b71c-104">Lesen Sie dieses Thema und erfahren Sie, wie Sie Ihrer Domäne einen Skype Room System-Anwendungs-PC hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3b71c-104">Read this topic to learn how to join a Skype Room System appliance PC to your domain.</span></span>
  
## <a name="domain-joining-considerations"></a><span data-ttu-id="3b71c-105">Überlegungen zur Domänenteilnahme</span><span class="sxs-lookup"><span data-stu-id="3b71c-105">Domain joining considerations</span></span>

<span data-ttu-id="3b71c-106">Sie können den PC der Skype Room-System Einheit an die Active Directory-Domäne anschließen oder in einer Arbeitsgruppe belassen.</span><span class="sxs-lookup"><span data-stu-id="3b71c-106">You can join the Skype Room System appliance PC to the Active Directory domain or leave it in a Workgroup.</span></span> <span data-ttu-id="3b71c-107">Berücksichtigen Sie die folgenden Punkte, bevor Sie diese Entscheidung treffen:</span><span class="sxs-lookup"><span data-stu-id="3b71c-107">Consider the following points before making this decision:</span></span>
  
- <span data-ttu-id="3b71c-108">Domain-Beitritt zum Skype Room System Appliance PC hilft beim automatischen Importieren der privaten root-Zertifikatkette Ihres Unternehmens.</span><span class="sxs-lookup"><span data-stu-id="3b71c-108">Domain-joining the Skype Room System appliance PC helps in importing your organization's private root certificate chain automatically.</span></span>
- <span data-ttu-id="3b71c-109">Domain-Beitritt zum Skype Room System Appliance PC können Sie Domänenbenutzern und Gruppenadministrator Rechte erteilen.</span><span class="sxs-lookup"><span data-stu-id="3b71c-109">Domain-joining the Skype Room System appliance PC enables you to grant domain users and groups administrative rights.</span></span> <span data-ttu-id="3b71c-110">Dadurch müssten Sie sich das Kennwort für das Administratorkonto auf Computerebene nicht merken.</span><span class="sxs-lookup"><span data-stu-id="3b71c-110">By doing so, you will not have to remember the local machine level administrator account password.</span></span>
- <span data-ttu-id="3b71c-111">Wenn Sie der Domäne einen Skype Room-systemappliance-PC beitreten, ist es erforderlich, dass Sie eine separate Organisationseinheit (Organizational Unit, OU) erstellen, damit Sie der Organisationseinheit, in der sich alle Skype Room-System Computerobjekte befinden, Gruppenrichtlinienobjekt-Ausschlüsse bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="3b71c-111">When you join an Skype Room System appliance PC to the domain, it is required that you create a separate Organizational Unit (OU), so that you can provide Group Policy Object (GPO) exclusions to the OU where all the Skype Room System machine objects reside.</span></span> <span data-ttu-id="3b71c-112">Wenn Sie dies tun, erstellen Sie in der Organisationseinheit Computerobjekte, bevor Sie dem PC der Skype Room-System Einheit zur Domäne beitreten.</span><span class="sxs-lookup"><span data-stu-id="3b71c-112">When you do this, create machine objects in the OU before joining the Skype Room System appliance PC to the domain.</span></span>
- <span data-ttu-id="3b71c-113">Viele Organisationen verfügen über die folgenden GPOs, die sich auf die PC-Funktionen der Skype Room-System Einheit auswirken.</span><span class="sxs-lookup"><span data-stu-id="3b71c-113">Many organizations have the following GPOs, which affect Skype Room System appliance PC functions.</span></span> <span data-ttu-id="3b71c-114">Stellen Sie sicher, dass Sie die Vererbung dieser GPOs in der Skype Room System ou außer Kraft setzen oder blockieren:</span><span class="sxs-lookup"><span data-stu-id="3b71c-114">Ensure that you override or block the inheritance of these GPOs in the Skype Room System OU:</span></span>

  - <span data-ttu-id="3b71c-115">Timeout von Anmeldesitzungen (automatische Sperre)</span><span class="sxs-lookup"><span data-stu-id="3b71c-115">Timeout of logon sessions (auto lockout)</span></span>
  - <span data-ttu-id="3b71c-116">Richtlinien in Bezug auf die Energieverwaltung</span><span class="sxs-lookup"><span data-stu-id="3b71c-116">Power management related policies</span></span>
  - <span data-ttu-id="3b71c-117">Notwendigkeit zusätzlicher Authentifizierungsschritte</span><span class="sxs-lookup"><span data-stu-id="3b71c-117">Requiring additional authentication steps</span></span>
  - <span data-ttu-id="3b71c-118">Verweigern des Zugriffs auf lokale Laufwerke</span><span class="sxs-lookup"><span data-stu-id="3b71c-118">Denying access to local drives</span></span>
  - <span data-ttu-id="3b71c-119">Benutzeraufforderungen bei langsamen Netzwerkverbindungen</span><span class="sxs-lookup"><span data-stu-id="3b71c-119">Prompting users for slow network connections</span></span>
  - <span data-ttu-id="3b71c-120">Starten eines bestimmten Programms bei der Anmeldung</span><span class="sxs-lookup"><span data-stu-id="3b71c-120">Start a certain program at logon</span></span>
  - <span data-ttu-id="3b71c-121">Erstellen eines weiteren Domänennutzerkontos auf allen Computern in der Domäne.</span><span class="sxs-lookup"><span data-stu-id="3b71c-121">Create another domain user account on all domain-joined machines.</span></span>
  - <span data-ttu-id="3b71c-122">Windows Update auf das Skype Room-System pushen</span><span class="sxs-lookup"><span data-stu-id="3b71c-122">Push Windows Update to Skype Room System</span></span>
    
- <span data-ttu-id="3b71c-123">Alternativ könnten Sie sich dazu entschließen, den Anwendungs-PC in der Arbeitsgruppe zu belassen.</span><span class="sxs-lookup"><span data-stu-id="3b71c-123">Alternatively, you might decide to leave the appliance PC in the workgroup.</span></span> <span data-ttu-id="3b71c-124">Wie bei den Desktop-Microsoft Teams oder dem Skype for Business-Client müssen Sie die Root-Zertifikatkette manuell auf dem PC der Skype Room-System Einheit importieren.</span><span class="sxs-lookup"><span data-stu-id="3b71c-124">As with the desktop Microsoft Teams or Skype for Business client, this requires you to manually import the root certificate chain on the Skype Room System appliance PC.</span></span> <span data-ttu-id="3b71c-125">Sie müssen die Stammzertifikatkette nicht importieren, wenn Ihre Bereitstellung ein öffentliches Zertifikat verwendet (beispielsweise Entrust, VeriSign usw.).</span><span class="sxs-lookup"><span data-stu-id="3b71c-125">You're not required to import the root certificate chain if your deployment is using a public certificate (for example, Entrust, VeriSign, and so on).</span></span> 
    
<span data-ttu-id="3b71c-126">Wenn Sie beabsichtigen, an der Domäne an Skype Room-System Computer teilzunehmen, um zu vermeiden, dass Sie versehentlich zu einer unbeabsichtigten ou, die nicht frei von GPOs ist, dem Skype Room-System Computer beitreten, stellen Sie bitte sicher, dass Sie der richtigen ou beitreten.</span><span class="sxs-lookup"><span data-stu-id="3b71c-126">If you plan to join Skype Room System machines to the domain, to avoid joining Skype Room System machine inadvertently to an unintended OU, which may not be free from GPOs, please ensure you join the correct OU.</span></span> <span data-ttu-id="3b71c-127">Sie können das folgende Cmdlet vom Skype Room-System Computer verwenden, um an der richtigen Organisationseinheit teilzunehmen, und es werden keine GPOs empfangen, die die LRS-Funktionalität blockieren könnten.</span><span class="sxs-lookup"><span data-stu-id="3b71c-127">You can use the following cmdlet from the Skype Room System machine to join in the correct OU and does not receive GPOs that might block LRS functionality.</span></span> <span data-ttu-id="3b71c-128">Wenden Sie sich an Ihren Systemadministrator oder OEM-Partner, wenn Sie Fragen zur Ausführung dieses Cmdlets haben:</span><span class="sxs-lookup"><span data-stu-id="3b71c-128">Contact your system administrator or OEM partner to run these cmdlet:</span></span>
  
```
$username = "contso.local\LRS01"
$password = ConvertTo-SecureString "password123" -AsPlainText -Force
$myCred = New-Object System.Management.Automation.PSCredential $username, $password
Add-Computer -DomainName contoso.local -Credential $mycred -OUPath "OU=LyncRoomSystem,OU=Resources,DC=CONTOSO,DC=LOCAL"
```

<span data-ttu-id="3b71c-129">Sogar wenn Sie eine separate OU erstellen und die Vererbung blockieren, gibt es einige Richtlinien, die Probleme auf einer höheren Ebene verursachen könnten.</span><span class="sxs-lookup"><span data-stu-id="3b71c-129">Even if you create a separate OU and block inheritance, there are some policies which could cause issues at a higher level.</span></span> <span data-ttu-id="3b71c-130">Eine Gruppenrichtlinie mit „Nicht aufheben“-Einstellung hat Vorrang gegenüber einer OU mit „Richtlinienvererbung aufheben“-Einstellung.</span><span class="sxs-lookup"><span data-stu-id="3b71c-130">A Group Policy with No Override setting beats an OU with a Block Policy Inheritance setting.</span></span> <span data-ttu-id="3b71c-131">Weitere Informationen finden Sie im Artikel [keine Überschreibung im Vergleich zum Blockieren der Richtlinienvererbung](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc978255(v=technet.10)) in der Gruppenrichtliniendokumentation.</span><span class="sxs-lookup"><span data-stu-id="3b71c-131">For more information, see the article [No Override as Compared to Block Policy Inheritance](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/cc978255(v=technet.10)) in the Group Policy documentation.</span></span>
  
<span data-ttu-id="3b71c-132">Unter Umständen stehen Ihnen mehrere Ansätze zur Lösung dieser Probleme zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3b71c-132">You may have multiple approaches to solving these problems.</span></span> <span data-ttu-id="3b71c-133">Es wird empfohlen, dass Sie sich an Ihre Active Directory-Experten wenden, um sicherzustellen, dass Sie über eine OU mit den angemessenen GPO-Einstellungen oder wenigstens über eine OU verfügen, in der die weiter oben beschriebenen Richtlinien nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="3b71c-133">We advise you to consult with your Active Directory experts to ensure you are provided with an OU that has appropriate GPO settings, or at least an OU in which the previously described policies do not exist.</span></span> <span data-ttu-id="3b71c-134">Es wird empfohlen, Quality of Service (QoS) für Skype Room-System Geräte zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3b71c-134">It is advised to enable Quality of Service (QoS) for Skype Room System devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b71c-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3b71c-135">See also</span></span>
  
[<span data-ttu-id="3b71c-136">Gerätekonfiguration: Erstellen einer neuen oder Bearbeiten einer vorhandenen Gerätekonfiguration</span><span class="sxs-lookup"><span data-stu-id="3b71c-136">Device Configuration: Create New or Edit Existing</span></span>](/skypeforbusiness/help-topics/help-lscp/device-configuration-create-new-or-edit-existing.md)

[<span data-ttu-id="3b71c-137">Verwalten der Dienstqualität (Quality of Service, QoS)</span><span class="sxs-lookup"><span data-stu-id="3b71c-137">Managing Quality of Service</span></span>](/skypeforbusiness/plan-your-deployment/network-requirements/network-requirements.#managing-quality-of-service)