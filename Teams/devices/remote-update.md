---
title: Remote-Update von Microsoft Teams-Geräten
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection:
- M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Normal
description: Aktualisieren von Microsoft Teams-Smartphones und-Zusammenarbeits leisten über das Team Admin Center
ms.openlocfilehash: e57ca3f357deeb005f845d37a17c4b20db5d2035
ms.sourcegitcommit: b255db7ef816d1884c9c71af86a901bd83a1d9ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47962886"
---
# <a name="update-microsoft-teams-devices-remotely"></a>Remote-Update von Microsoft Teams-Geräten

Mit dem Microsoft Teams Admin Center können Sie Ihre Teams-Geräte wie Telefone und Kollaborations leisten Remote aktualisieren, und Sie können das automatische Updateverhalten der Gerätefirmware auswählen. Mit dem Team Admin Center können Sie Folgendes auf Ihren Geräten aktualisieren:

- Teams-APP und Team-Administrator-Agent
- Unternehmensportal-App
- OEM-Agent-App
- Geräte-Firmware

Geräte-Firmware-Updates können entweder automatisch oder für ein zukünftiges Datum und eine Uhrzeit geplant werden. Andere verfügbare Geräte Updates werden nicht automatisch angewendet, können aber manuell angewendet oder für ein zukünftiges Datum und eine Uhrzeit geplant werden.

> [!NOTE]
> Wenn die Gerätefirmware-Updates geplant werden können, wenn das geplante Datum und die Uhrzeit nach der konfigurierten maximalen Verzögerung von 30 oder 90 Tage fallen, wird die Firmware-Aktualisierung angewendet, wenn die maximale Verzögerung erreicht ist. Geplantes Datum und Uhrzeit werden ignoriert. Darüber hinaus ist die Aktualisierung von Microsoft Teams-Geräten in der Ferne ein Feature, das noch nicht für Cloud-Mandanten der US-Regierung (gcc-groß) verfügbar ist.

Zum Verwalten von Geräten müssen Sie ein globaler Administrator, Teams-Dienstadministrator oder Teams-Geräteadministrator sein. Weitere Informationen zu Administratorrollen finden Sie unter [Verwenden von Microsoft Teams-Administratorrollen zum Verwalten von Teams](../using-admin-roles.md).

## <a name="choose-automatic-device-firmware-update-behavior"></a>Auswählen des automatischen Gerätefirmware-Update Verhaltens

Geräte-Firmware-Updates werden automatisch angewendet. Sie können entscheiden, ob Updates angewendet werden sollen, sobald eine freigegeben wird (wenn Sie diese Option auswählen, werden Updates am ersten Wochenende nach Veröffentlichung eines Updates angewendet) oder 30 oder 90 Tage nach Veröffentlichung eines Updates. Standardmäßig werden Geräte-Firmware-Updates 30 Tage lang veröffentlicht.

> [!IMPORTANT]
> Die aktuelle Version der Firmware-Aktualisierung wird auf Ihrem Team-Gerät nicht angewendet. Stattdessen wird das Update, das auf Ihrem Gerät automatisch angewendet wird, um eine Version verzögert. Nehmen Sie beispielsweise an, dass auf Ihrem Gerät die Version "10" angewendet wurde und Version "11" freigegeben wird. Die Version "11" wird noch nicht angewendet. Ihr Gerät wird stattdessen nur auf Version "11" aktualisiert, nachdem die Version "12" veröffentlicht wurde.

> [!NOTE]
> Einige Geräte unterstützen die automatische Firmware-Aktualisierung noch nicht. Die Anwendung von Einstellungen für die automatische Firmware-Aktualisierung auf Geräten, die keine automatischen Updates unterstützen, hat keine Auswirkungen auf diese Geräte. Wenden Sie sich an Ihren Gerätehersteller, wenn Sie Fragen dazu haben, ob Ihr Gerät automatische Firmware-Aktualisierungen unterstützt.

Gehen Sie wie folgt vor, um das automatische Updateverhalten für Ihre Geräte zu wählen:

1. Wenn Sie sich beim Microsoft Teams Admin Center anmelden, besuchen Sie https://admin.teams.microsoft.com
2. Navigieren in **Geräten**für  >  **Telefone** oder **Kollaborations leisten**
3. Wählen Sie ein oder mehrere Geräte aus, und wählen Sie dann **Aktualisieren** aus.
4. Wählen Sie unter **automatische Firmware-Aktualisierung**eine der folgenden Optionen aus:
    - Sobald **verfügbar** Das neueste Update für die Gerätefirmware wird am ersten Wochenende nach der Veröffentlichung des neuesten Updates angewendet.
    - **30 Tage verschieben** Das neueste Update der Geräte-Firmware wird 30 Tage nach der Veröffentlichung des neuesten Updates angewendet.
    - **Verschieben von 90 Tagen** Das neueste Update der Gerätefirmware wird 90 Tage nach der Veröffentlichung des neuesten Updates angewendet.
5. **Update** auswählen

Wenn Sie aus irgendeinem Grund eine Gerätefirmware-Aktualisierung wiederherstellen müssen, müssen Sie Ihr Gerät auf die Werkseinstellungen zurücksetzen. Setzen Sie Ihr Gerät mit den Anweisungen seines Herstellers zurück.  

## <a name="manually-update-remote-devices"></a>Manuelles Aktualisieren von Remotegeräten

Wenn Sie ein oder mehrere Geräte mithilfe des Admin Centers aktualisieren, können Sie entscheiden, ob Sie die Geräte sofort aktualisieren oder ein Update für ein zukünftiges Datum und eine Uhrzeit planen.

Gehen Sie wie folgt vor, um Remotegeräte manuell zu aktualisieren:

1. Wenn Sie sich beim Microsoft Teams Admin Center anmelden, besuchen Sie https://admin.teams.microsoft.com
2. Navigieren in **Geräten**für  >  **Telefone** oder **Kollaborations leisten**
3. Wählen Sie ein oder mehrere Geräte aus, und wählen Sie dann **Aktualisieren** aus.
4. Wählen Sie unter **Manuelle Updates**die Option **Zeitplan** aus, wenn Sie das Update für ein zukünftiges Datum und eine Uhrzeit planen möchten. Die Updates werden zu dem Datum und der Uhrzeit in der Zeitzone angewendet, die in **TimeZone**ausgewählt wurde.

Was Sie sehen, hängt davon ab, ob Sie ein oder mehrere Geräte ausgewählt haben. In der linken Abbildung unten sind mehrere Geräte ausgewählt, während das Bild auf der rechten Seite ein einzelnes Gerät ausgewählt zeigt.

:::image type="content" source="../media/device-update-status.png" alt-text="Einzel-und mehrere Geräte Ansichten im Bereich "Geräte Aktualisierungsstatus"":::

Wenn Sie mehrere Geräte auswählen, können Sie auswählen, welche Updatetypen für jedes ausgewählte Gerät gelten sollen. Wählen Sie die Updatetypen aus, die Sie anwenden möchten, und wählen Sie **Aktualisieren**aus.

Wenn Sie ein einzelnes Gerät auswählen, werden Updates angezeigt, die für das Gerät verfügbar sind. Wenn mehrere Updatetypen für das Gerät verfügbar sind, wählen Sie die einzelnen Updatetypen aus, die Sie anwenden möchten. Sie können die **aktuelle Version** anzeigen, die auf dem Gerät angewendet wurde, und die **neue Version** , die angewendet werden soll. Wählen Sie die Updates aus, die Sie anwenden möchten, und wählen Sie **Aktualisieren**aus.

Nachdem Sie **Update**ausgewählt haben, werden Updates auf Ihre Geräte zu dem Datum und der Uhrzeit angewendet, die Sie bei der Planung eines Updates ausgewählt haben. Wenn Sie kein zukünftiges Datum und keine Uhrzeit ausgewählt haben, werden Updates auf Ihre Geräte innerhalb weniger Minuten angewendet.
