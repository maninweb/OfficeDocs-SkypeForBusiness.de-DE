---
title: Festlegen der in Einladungen enthaltenen Telefonnummern
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 32954439-d365-4125-872f-b37466ecb035
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- M365-voice
- M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Audio Conferencing
- seo-marvel-mar2020
description: Führen Sie die folgenden Schritte aus, um eine Standardtelefonnummer für Anrufer zu erstellen und an einer Microsoft Teams-Besprechung teilzunehmen.
ms.openlocfilehash: 7dd59950403543074d8428d35270ab963ca824e3
ms.sourcegitcommit: 3e5cac88911611c94c0330bf50af9c34db308cdf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45372184"
---
# <a name="set-the-phone-numbers-included-on-invites-in-microsoft-teams"></a>Festlegen der in Einladungen in Microsoft Teams enthaltenen Telefonnummern

Audiokonferenzen in Microsoft 365 und Office 365 ermöglichen es Benutzern in Ihrer Organisation, Microsoft Teams-Besprechungen zu erstellen und Benutzern dann das Einwählen in diese Besprechungen mithilfe eines Telefons zu ermöglichen.
  
Eine Konferenzbrücke bietet Ihnen eine Reihe von Einwahlnummern für Ihre Organisation. All diese Nummern können verwendet werden, um an den Besprechungen teilzunehmen, die ein Besprechungsorganisator erstellt hat. Sie können aber auch eine Auswahl treffen, die bei den Einladungen zur jeweiligen Besprechung berücksichtigt werden sollen.
  
> [!NOTE]
> Für einen Besprechungsorganisator kann maximal eine gebührenpflichtige und eine gebührenfreie Telefonnummer in der Besprechungseinladung angegeben werden. Im unteren Bereich jeder Besprechungseinladung befindet sich jedoch auch ein Link, über den eine vollständige Liste aller Einwahlnummern aufgerufen werden kann, über die Benutzer an einer Besprechung teilnehmen können.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## <a name="initial-assignment-of-phone-numbers-that-are-included-in-the-meeting-invites-for-new-users"></a>Die anfängliche Zuweisung von Telefonnummern, die in der Besprechung enthalten sind, lädt für neue Benutzer ein.

Die Telefonnummern, die in der Besprechungseinladung enthalten sind, werden von Benutzern, die für Audiokonferenzen aktiviert sind, durch die standardmäßige Konferenzgebühren pflichtige Telefonnummer und die Einstellungen des standardmäßigen Konferenzgebühren freien Telefonnummern-Benutzers festgelegt. Jede Einstellung gibt an, welche gebührenpflichtige und gebührenfreie Nummer in der Besprechungseinladung eines bestimmten Benutzers enthalten sein wird. Wie bereits erwähnt, enthält jede Besprechungseinladung eine gebührenpflichtige Nummer, eine optionale gebührenfreie Nummer und einen Link, der die vollständige Liste aller Einwahl Telefonnummern öffnet, die für die Teilnahme an einer bestimmten Besprechung verwendet werden können.

Für einen neuen Benutzer werden die standardmäßigen Konferenzgebühren Nummern basierend auf dem Verwendungs Speicherort zugewiesen, der in der Microsoft 365-Verwaltungskonsole des Benutzers festgelegt ist, wenn der Benutzer für den Audiokonferenzdienst aktiviert ist. Wenn sich in der Konferenzbrücke eine gebührenpflichtige Nummer befindet, die dem Land des Benutzers entspricht, wird diese Nummer automatisch als Standardgebühren Nummer des Benutzers zugewiesen. Wenn es keinen gibt, wird die Nummer, die als standardmäßige gebührenpflichtige Nummer der Konferenzbrücke definiert ist, als die standardmäßige gebührenpflichtige Nummer des Benutzers zugewiesen.  

Sobald der Benutzer für den Audiokonferenzdienst aktiviert ist, können die standardmäßigen gebührenpflichtigen und gebührenfreien Telefonnummern des Benutzers vom mandantenadministrator jederzeit von den anfänglichen Werten geändert werden.

## <a name="set-or-change-the-default-audio-conferencing-phone-number-for-a-meeting-organizer-or-user"></a>Festlegen oder Ändern der Standardtelefonnummer für Audiokonferenzen für Besprechungsorganisatoren oder-Benutzer

![Ein Symbol mit dem Microsoft Teams-Logo](media/teams-logo-30x30.png) **Verwenden des Microsoft Teams Admin Centers**

Sie müssen ein Team Dienstadministrator sein, um diese Änderungen vornehmen zu können. Informationen zum Abrufen von Administratorrollen und-Berechtigungen finden Sie unter [Verwenden von Teams-Administratorrollen zum Verwalten von Teams](https://docs.microsoft.com/microsoftteams/using-admin-roles) .

1. Melden Sie sich beim Microsoft Teams Admin Center an.

2. Klicken Sie in der linken Navigationsleiste auf **Benutzer**.

    ![Zeigt das Auswählen von Benutzern im Microsoft Teams Admin Center](media/Admin-users.png)

3. Klicken Sie in der Liste der verfügbaren Benutzer auf den Benutzernamen.

4. Klicken Sie neben **Audiokonferenzen**auf **Bearbeiten**.

    ![Klicken Sie neben Audiokonferenzen auf Bearbeiten.](media/teams-set-phone-numbers-on-invites-image3.png)

5. Verwenden Sie die Felder **gebührenpflichtige** Nummer oder **gebührenfreie Nummer** , um die Nummern für den Benutzer einzugeben.

> [!IMPORTANT]
> Wenn Sie die Einstellungen für die Audiokonferenz eines Benutzers ändern, müssen wiederkehrende und zukünftige Microsoft Teams-Besprechungen aktualisiert und an die Teilnehmer gesendet werden.

## <a name="want-to-use-windows-powershell"></a>Möchten Sie Windows PowerShell verwenden?

Bei Windows PowerShell dreht sich alles um das Verwalten von Benutzern und Funktionen, die Benutzer verwenden oder nicht verwenden können. Mit Windows PowerShell können Sie Microsoft 365 oder Office 365 mithilfe einer zentralen Verwaltungsstelle verwalten, die Ihre tägliche Arbeit vereinfachen kann, wenn mehrere Aufgaben ausgeführt werden müssen. Informieren Sie sich in den folgenden Themen über die Verwendung von Windows PowerShell:

- [Warum Sie Office 365 PowerShell verwenden müssen](https://go.microsoft.com/fwlink/?LinkId=525041)

- [Beste Möglichkeiten zum Verwalten von Microsoft 365 oder Office 365 mit Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)

Weitere Informationen zu Windows PowerShell finden Sie in der [PowerShell-Referenz für Microsoft Teams](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps).
  
## <a name="related-topics"></a>Verwandte Themen

[Testen oder kaufen von Audiokonferenzen in Microsoft 365 oder Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)

[Ändern der Telefonnummern in Ihrer Audiokonferenzbrücke](change-the-phone-numbers-on-your-audio-conferencing-bridge.md)
