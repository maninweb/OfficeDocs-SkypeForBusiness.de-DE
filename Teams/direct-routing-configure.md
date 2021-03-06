---
title: Konfigurieren von direktem Routing
ms.reviewer: ''
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection:
- M365-voice
- m365initiative-voice
- m365solution-voice
- m365solution-scenario
appliesto:
- Microsoft Teams
f1.keywords:
- NOCSH
description: Hier erfahren Sie, wie Sie das direkte Routing von Microsoft Phone System so konfigurieren, dass die lokale Telefonie-Infrastruktur mit Microsoft Teams verbunden wird.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5388c93e741323d3dc9eda0fc51968b8b344d2cb
ms.sourcegitcommit: 380a96f1ed2cefb429286854f06546bdb28d7d74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "49701293"
---
# <a name="configure-direct-routing"></a>Konfigurieren von direktem Routing

Mit dem direkt Routing von Microsoft Phone System können Sie Ihre lokale Telefonie-Infrastruktur mit Microsoft Teams verbinden. Der Artikel listet die allgemeinen Schritte auf, die zum Verbinden eines unterstützten lokalen Session Border Controller (SBC) mit Direct Routing erforderlich sind, und wie Sie die Benutzer von Teams für die Verwendung des direkten Routings zum Herstellen einer Verbindung mit dem öffentlichen Telefonnetz (PSTN) konfigurieren. Dieser Artikel enthält Links zu den zugehörigen Artikeln für Details.  

Informationen dazu, ob Direct Routing die richtige Lösung für Ihre Organisation ist, finden Sie unter [Direktes Routing für Telefonsysteme](direct-routing-landing-page.md). Informationen zu den Voraussetzungen und zur Planung der Bereitstellung finden Sie unter [Planen des direkten Routings](direct-routing-plan.md).

> [!Tip]
> Sie können auch die folgende Sitzung sehen, um zu erfahren, welche Vorteile ein direktes Routing hat, wie Sie es planen und wie es bereitgestellt wird: [Direktes Routing in Microsoft Teams](https://aka.ms/teams-direct-routing).

Um die in diesem Artikel erläuterten Schritte ausführen zu können, benötigen Administratoren einige Vertrautheit mit PowerShell-Cmdlets. Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Einrichten Ihres Computers für Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell). 

Bevor Sie die Schritte in diesen Artikeln ausführen, empfiehlt Microsoft, dass Sie sicherstellen, dass Ihr SBC bereits vom SBC-Anbieter als empfohlen konfiguriert wurde: 

- [AudioCodes-Bereitstellungsdokumentation](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)
- [Oracle-Bereitstellungsdokumentation](https://www.oracle.com/industries/communications/enterprise-session-border-controller/microsoft.html)
- [Bereitstellungsdokumentation zur Multifunktionsleisten-Kommunikation](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions/direct-routing-microsoft-teams-calling)
- [TE-Systems (anynode)-Bereitstellungsdokumentation](https://www.anynode.de/anynode-and-microsoft-teams/)
- [Metaswitch-Bereitstellungsdokumentation](https://www.metaswitch.com/products/core-network/perimeta-sbc)

Eine vollständige Liste der unterstützten SBCS finden Sie unter [Liste der für die direkte Weiterleitung zertifizierten Session Border Controller](direct-routing-border-controllers.md).

Führen Sie die folgenden Schritte aus, um das Microsoft Phone-System zu konfigurieren und Benutzern die Verwendung des direkten Routings zu ermöglichen: 

- **Schritt 1:** [Verbinden des SBC mit dem Microsoft Phone-System und Überprüfen der Verbindung](direct-routing-connect-the-sbc.md)
- **Schritt 2:** [Aktivieren von Benutzern für Direct Routing, Voicemail und Voicemail](direct-routing-enable-users.md)
- **Schritt 3:** [Konfigurieren des VoIP-Routings](direct-routing-voice-routing.md)
- **Schritt 4:** [Übersetzen von Zahlen in ein anderes Format](direct-routing-translate-numbers.md) 

Wenn Sie einen SBC für mehrere Mandanten konfigurieren, sollten Sie auch die [Konfiguration eines SBC für mehrere Mandanten](direct-routing-sbc-multiple-tenants.md)lesen.


## <a name="related-topics"></a>Verwandte Themen

[Direktes Routing für Telefonsysteme](direct-routing-landing-page.md)

[Planen von direktem Routing](direct-routing-plan.md)

