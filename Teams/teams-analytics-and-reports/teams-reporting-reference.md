---
title: Microsoft Teams – Analyse und Berichterstellung
author: LanaChin
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: svemu
f1.keywords:
- NOCSH
- ms.teamsadmincenter.analyticsandreports.overview
localization_priority: Normal
search.appverid: MET150
ms.collection:
- M365-collaboration
description: In diesem Artikel erhalten Sie Informationen zu den Teams-berichten, die im Microsoft Teams Admin Center zur Verfügung stehen.
appliesto:
- Microsoft Teams
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 460037da3be0c2aaf1e546b97e0e5e911f6102a2
ms.sourcegitcommit: 4d6bf5c58b2c553dc1df8375ede4a9cb9eaadff2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "48515912"
---
# <a name="microsoft-teams-analytics-and-reporting"></a>Microsoft Teams – Analyse und Berichterstellung

Eine neue Analyse-und Berichterstellungsumgebung für Microsoft Teams steht im Microsoft Teams Admin Center zur Verfügung. Sie können unterschiedliche Berichte ausführen, um Einblicke in die Verwendung von Teams durch Benutzer in Ihrer Organisation zu erhalten. So können Sie beispielsweise sehen, wie viele Benutzer über Kanal-und Chatnachrichten kommunizieren und welche Arten von Geräten für die Verbindung zu Teams verwendet werden. Ihre Organisation kann die Informationen aus den Berichten verwenden, um Nutzungsmuster besser zu verstehen, geschäftliche Entscheidungen zu treffen und Schulungs-und Kommunikationsaktivitäten zu informieren.

## <a name="how-to-access-the-reports"></a>So greifen Sie auf die Berichte zu

Wenn Sie auf die Berichte zugreifen möchten, müssen Sie ein globaler Administrator in Microsoft 365 oder Office 365, Team Dienstadministrator oder Skype for Business-Administrator sein. Weitere Informationen zu den Rollen des Team Administrators sowie zu den Berichten, auf die jede Administratorrolle zugreifen kann, finden Sie unter [Verwenden von Teams-Administratorrollen zum Verwalten von Teams](../using-admin-roles.md).

Wechseln Sie zum Microsoft Teams Admin Center, wählen Sie im linken Navigationsbereich **Analyse & Berichte**aus, und wählen Sie dann unter **Bericht**den Bericht aus, den Sie ausführen möchten.

> [!NOTE]
> Die Berichte im Microsoft Teams Admin Center sind unabhängig von den Aktivitätsberichten für Teams, die Teil der Microsoft 365-Berichte im Microsoft 365 Admin Center sind. Weitere Informationen zu den Aktivitätsberichten im Microsoft 365 Admin Center finden Sie unter [Teams-Aktivitätsberichte im Microsoft 365 Admin Center](../teams-activity-reports.md) .

## <a name="teams-reporting-reference"></a>Referenz für Teams-Berichterstattung

Nachfolgend finden Sie eine Liste der Teamberichte, die im Microsoft Teams Admin Center zur Verfügung stehen, sowie eine Übersicht über einige der Informationen, die in den einzelnen Berichten zur Verfügung stehen.

Wir verbessern kontinuierlich die Berichts Erfahrung von Teams und fügen Features und Funktionen hinzu. Im Laufe der Zeit werden wir zusätzliche Funktionen in den Berichten erstellen und neue Berichte im Microsoft Teams Admin Center hinzufügen.

|Bericht  |Was wird gemessen? |
|---------|---------|
|[Teams-Nutzungsbericht](teams-usage-report.md)  |  Aktive Benutzer<br/>Aktive Benutzer in Teams und Kanälen<br/>Aktive Kanäle<br/>Meldungen<br/>Datenschutzeinstellungen für Teams<br/>Gäste in einem Team   |
|[Teams-Benutzeraktivitätsbericht](user-activity-report.md)  |  1:1-Anrufe, an denen ein Benutzer teilgenommen hat<br/>Nachrichten, die ein Benutzer in einem Teamchat gepostet hat<br/>Nachrichten, die ein Benutzer in einem privaten Chat gepostet hat<br/>Datum der letzten Aktivität eines Benutzers     |
|[Teams-Gerätenutzungsbericht](device-usage-report.md)   |  Windows-Benutzer<br/>Mac-Benutzer<br/>IOS-Benutzer<br/>Android-Telefon Nutzer     |
|[Teams-Liveereignis-Nutzungsbericht](teams-live-event-usage-report.md)   |  Gesamtansichten<br>Startzeitpunkt<br>Ereignisstatus<br>Organisator<br>Presenter<br>Produzent<br>Aufzeichnungseinstellung<br>Produktionsart    |
|[Berichte über PSTN-blockierte Benutzer von Teams](pstn-blocked-users-report.md)   |  Anzeigename<br>Telefonnummer<br>Grund<br>Aktionstyp<br>Datum und Uhrzeit der Aktion   |
|[Berichte für PSTN-Minuten Pools für Teams](pstn-minute-pools-report.md) |  Land oder Region<br>Funktion (Lizenz) <br>Gesamtzahl der Minuten<br>Verwendete Minuten<br>Minuten verfügbar|
|[PSTN-Nutzungsbericht für Teams – Anrufpläne](pstn-usage-report.md#calling-plans)|  Zeitstempel<br>Benutzername<br>Telefonnummer<br>Anruftyp <br>Aufgerufen an<br>Zu Land oder Region <br>Aufgerufen von <br>Aus Land oder Region<br>Kostenlos<br>Währung<br>Dauer<br>Domestic/International<br>Anruf-ID<br>Zahlentyp<br>Land oder Region<br>Konferenz-ID<br>Funktion (Lizenz)|
|[PSTN-Nutzungsbericht für Teams – Direktes Routing](pstn-usage-report.md#direct-routing)  |  Zeitstempel<br>Anzeigename<br>SIP-Adresse<br>Telefonnummer <br>Anruftyp<br>Aufgerufen an<br>Startzeitpunkt<br>Einladungszeitpunkt<br>Fehlerzeit<br>Endzeitpunkt<br>Dauer<br>Zahlentyp<br>Medienumgehung<br>SBC-FQDN<br>Azure-Bereich<br>Ereignistyp<br>Endgültiger SIP-Code<br>Letzter Microsoft-Subcode<br>Endgültige SIP-Phrase<br>Korrelations-ID  |

[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]
