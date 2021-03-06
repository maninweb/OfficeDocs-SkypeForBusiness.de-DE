---
title: Microsoft 365-und Office 365-URLs und IP-Adressbereiche
ms.reviewer: ''
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 08/21/2018
ms.topic: article
audience: admin
ms.service: msteams
description: Erfahren Sie, wie Sie Microsoft 365-oder Office 365-URLs und IP-Adressbereiche ordnungsgemäß konfigurieren und den Forward-Proxy nach Möglichkeit für Verbindungen mit Microsoft Teams-Dienst umgehen können.
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.meetingsettings.network.ports
- seo-marvel-mar2020
ms.collection:
- M365-collaboration
appliesto:
- Microsoft Teams
ms.openlocfilehash: 1ad3ffdfd47b67ce21fb7f47a911afa67159f3e7
ms.sourcegitcommit: 3a577c07b4f399c81d8650a2bba8cfc00b695b49
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2020
ms.locfileid: "48650818"
---
<a name="microsoft-365-and-office-365-urls-and-ip-address-ranges"></a>Microsoft 365-und Office 365-URLs und IP-Adressbereiche
=======================================================

Wechseln Sie zu [Microsoft 365-und Office 365-URLs und IP-Adressbereiche](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) , um eine detaillierte und aktuelle Liste der URLs, IP-Adressen, Ports und Protokolle zu finden, die für Teams ordnungsgemäß konfiguriert werden müssen. Microsoft verbessert die Microsoft 365- und Office 365-Dienste ständig und fügt neue Funktionen hinzu. Daher können sich die erforderlichen Ports, URLs und IP-Adressen im Lauf der Zeit ändern. Wir empfehlen, den Artikel [über RSS zu abonnieren](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams), damit Sie erfahren, wenn diese Informationen aktualisiert oder geändert werden.

Die Anruf- und Besprechungsfunktionen von Microsoft Teams beruhen auf der cloudbasierten Infrastruktur der nächsten Generation, die auch von Skype und Skype for Business genutzt wird. Zu diesen Technologieinvestitionen gehören Azure-basierte Clouddienste für Medienverarbeitung und Signalisierung, der Videocodec H.264, die Audiocodecs SILK und Opus, Netzwerkresilienz, Telemetrie und Qualitätsdiagnose. Daher sind URLs und IPs erforderlich, die sowohl Skype als auch Skype for Business zugeordnet sein können.

Für alle Microsoft 365-und Office 365-Arbeitsauslastungen wird die empfohlene Verbindungsmethode für Teams-Dienste nach Möglichkeit den Forward-Proxy umgehen. Wenn sich zwischen einem Client und den Office 365-Rechenzentren ein Proxyserver befindet, müssen die Medien möglicherweise über TCP anstatt über UDP übertragen werden. Dies wirkt sich auf die Medienqualität aus. Laden Sie Beispiel-Proxy-PAC-Dateien herunter, die zum Konfigurieren der Datenverkehrs Umgehung für die [Verwaltung von Microsoft 365 und Office 365-Endpunkten](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)verwendet werden können

Wenn für Ihre Netzwerk-und Sicherheitsrichtlinien Microsoft 365 oder Office 365-Datenverkehr über einen Proxy Server übermittelt werden muss, stellen Sie sicher, dass die oben genannten Anforderungen bereits erfüllt sind, bevor Sie Teams in der Produktion bereitstellen. Weitere Informationen finden Sie unter [Proxy Server für Teams oder Skype for Business Online](proxy-servers-for-skype-for-business-online.md).
