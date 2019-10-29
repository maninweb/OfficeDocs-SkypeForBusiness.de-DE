---
title: Direktes Routing für Telefonsysteme
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 10/17/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:
- Teams_ITAdmin_Help
- M365-voice
ms.reviewer: nmurav
search.appverid: MET150
description: Benachrichtigung über direkten Routing Anruf
appliesto:
- Microsoft Teams
localization_priority: Normal
ms.openlocfilehash: 07efe11d304107a5a8606a07f5d1c2a7a130bc0b
ms.sourcegitcommit: 9fd23cf0e03dd8fcf7ed04ef09dcdac048ebb44a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "37595345"
---
# <a name="manage-call-notifications"></a><span data-ttu-id="c28b6-103">Verwalten von Anrufbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c28b6-103">Manage call notifications</span></span>

<span data-ttu-id="c28b6-104">In diesem Artikel wird beschrieben, wie Sie Anrufbenachrichtigungen für Ihre Benutzer verwalten.</span><span class="sxs-lookup"><span data-stu-id="c28b6-104">This article describes how to manage call notifications for your users.</span></span> <span data-ttu-id="c28b6-105">Sie können Anruf Endpunkte sowohl für Teams als auch für eine Drittpartei (Private Branch Exchange, PBX) oder einen Session Border Controller (SBC) konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c28b6-105">You can configure call endpoints to both Teams and to a third-party Private Branch Exchange (PBX) or Session Border Controller (SBC).</span></span>  <span data-ttu-id="c28b6-106">Dies ist beispielsweise hilfreich, wenn Sie einen Anruf an das Mobiltelefon und die Tischtelefone eines Benutzers gleichzeitig senden möchten.</span><span class="sxs-lookup"><span data-stu-id="c28b6-106">This is useful, for example, if you want to send a call to a user's mobile and desk phones at the same time.</span></span>   

<span data-ttu-id="c28b6-107">Im folgenden Diagramm hat der Benutzer Irena zwei Endpunkte:</span><span class="sxs-lookup"><span data-stu-id="c28b6-107">In the following diagram, user Irena has two endpoints:</span></span>

- <span data-ttu-id="c28b6-108">Ein Team Endpunkt</span><span class="sxs-lookup"><span data-stu-id="c28b6-108">A Teams endpoint</span></span>
- <span data-ttu-id="c28b6-109">Ein SIP-Telefon, das mit einem Drittanbieter-SBC verbunden ist</span><span class="sxs-lookup"><span data-stu-id="c28b6-109">A SIP phone connected to a third-party SBC</span></span>

<span data-ttu-id="c28b6-110">Wenn ein Anruf eingeht, verzweigt der SBC den Anruf zwischen dem direkten Routing des Telefonsystems und dem Drittanbieter-SBC.</span><span class="sxs-lookup"><span data-stu-id="c28b6-110">When a call arrives, the SBC forks the call between Phone System Direct Routing and the third-party SBC.</span></span>


![Diagramm mit gegabelten Teams-Endpunkten](media/direct-routing-call-notification-1.png)

<span data-ttu-id="c28b6-112">Wenn der Anruf auf Fork 2 (vom Drittanbieter-SBC) akzeptiert wird, generiert Teams eine Benachrichtigung über verpasste Anrufe.</span><span class="sxs-lookup"><span data-stu-id="c28b6-112">If the call is accepted on Fork 2 (by the third-party SBC), Teams will generate a “Missed Call” notification.</span></span>  

<span data-ttu-id="c28b6-113">Sie können die Benachrichtigung "verpasste Anrufe" verhindern, indem Sie den SBC so konfigurieren, dass ein Cancel auf Gabel 1 wie folgt gesendet wird:</span><span class="sxs-lookup"><span data-stu-id="c28b6-113">You can prevent the “Missed Call” notification by configuring the SBC to send a Cancel on Fork 1 as follows:</span></span>

<span data-ttu-id="c28b6-114">Grund: SIP; Ursache = 200; Text "Anruf an anderer Stelle abgeschlossen"</span><span class="sxs-lookup"><span data-stu-id="c28b6-114">REASON: SIP; cause=200;text”Call completed elsewhere”</span></span> 

<span data-ttu-id="c28b6-115">Beachten Sie, dass der Anruf nicht in den Anruf Detaildatensätzen von Microsoft Phone System als erfolgreicher Anruf registriert wird.</span><span class="sxs-lookup"><span data-stu-id="c28b6-115">Note that the call will not be registered in the call detail records of Microsoft Phone System as a successful call.</span></span> <span data-ttu-id="c28b6-116">Der Anruf wird als "Versuch" mit dem endgültigen SIP-Code "487", dem endgültigen Microsoft-Subcode "540200" und dem letzten SIP-Codesatz "Anruf an anderer Stelle abgeschlossen" registriert.</span><span class="sxs-lookup"><span data-stu-id="c28b6-116">The call will be registered as an “Attempt” with Final SIP Code “487”, Final Microsoft subcode “540200”, and Final SIP Code Phrase “Call completed elsewhere”.</span></span>   <span data-ttu-id="c28b6-117">(Wenn Sie die Anruf Detaildatensätze anzeigen möchten, wechseln Sie zum Teamadministrator-Portal, Analyse-und Berichtsfunktionen, Verwendungsberichte, und wählen Sie PSTN-Verwendung aus.)</span><span class="sxs-lookup"><span data-stu-id="c28b6-117">(To view the call detail records, go the Teams Admin portal, Analytics and Reports, Usage Reports, and select PSNT Usage.)</span></span>


<span data-ttu-id="c28b6-118">Das folgende Diagramm zeigt die SIP-Leiter für Fork 1, erläutert den Anruffluss und den erwarteten Grund in der Abbruch Nachricht.</span><span class="sxs-lookup"><span data-stu-id="c28b6-118">The diagram below illustrates the SIP ladder for Fork 1, explains the call flow, and the expected REASON in the Cancel message.</span></span> 

![Diagramm mit gegabelten Teams-Endpunkten](media/direct-routing-call-notification-2.png)