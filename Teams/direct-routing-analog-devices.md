---
title: Direktes Routing – Verbinden von analogen Geräten
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.reviewer: NMuravlyannikov
ms.topic: conceptual
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection:
- M365-voice
appliesto:
- Microsoft Teams
f1.keywords:
- NOCSH
description: Lesen Sie diesen Artikel, um zu erfahren, wie Sie analoge Geräte mit dem direkten Routing von Microsoft Phone System verwenden können.
ms.openlocfilehash: 0c6531a29e23e736a84db9bf8571abab2e13942a
ms.sourcegitcommit: f9daef3213a305676127cf5140af907e3b96d046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "48369190"
---
# <a name="how-to-use-analog-devices-with-phone-system-direct-routing"></a>Verwenden von analogen Geräten mit direktem Telefon System-Routing

In diesem Artikel wird beschrieben, wie Sie analoge Geräte mit direktem Telefon System-Routing verwenden. Wenn Sie analoge Geräte mit Direct Routing verbinden möchten, müssen Sie einen analogen Telefonie-Adapter (ATA) verwenden, und dieser Adapter muss vom Anbieter des Certified Session Border Controller (SBC) unterstützt werden. 

Wenn ein Benutzer einen Anruf von einem analogen Gerät tätigt, wird der Signal-und Medienfluss über den analogen Telefonie-Adapter (ATA) an den SBC übermittelt.  Der SBC sendet den Anruf an einen Microsoft Teams-Endpunkt oder an das öffentlich geschaltete Telefon Netzwerk (PSTN) basierend auf der internen Routingtabelle.  Wenn ein Gerät einen Anruf tätigt, hängt die Route, die es ausführt, von den für das Gerät erstellten Routing Richtlinien ab.

In der nachstehenden Abbildung ist das direkte Routing so konfiguriert, dass alle Teams, die zwischen + 1425 4xx XX XX und + 1425 5xx XX XX die rote Route (gepunktete Linie) anrufen müssen, und jeder PSTN-Anruf zwischen + 1425 4xx XX XX und jeder anderen Zahl mit Ausnahme des Nummernbereichs + 1425 5xx XX XX die blaue Route (durchgezogene Linie) übernehmen muss. 

> [!div class="mx-imgBorder"]
> ![Diagramm mit direkter Routing Konfiguration](media/direct-routing-analog-device.png)

## <a name="example--how-to-configure-the-use-of-analog-devices-with-direct-routing"></a>Beispiel: Konfigurieren der Verwendung von analogen Geräten mit direktem Routing

Wenn Sie die Verwendung von analogen Geräten mit direktem Routing konfigurieren möchten, müssen Sie den analogen Telefonie-Adapter mit dem SBC verbinden und den SBC so konfigurieren, dass er mit direktem Routing funktioniert. 

Dieses Beispiel führt Sie durch die folgenden Schritte:

1. Verbinden Sie den SBC mit Direct Routing.
2. Erstellen Sie die PSTN-Nutzung.
3. Erstellen Sie eine VoIP-Route, und ordnen Sie Sie der PSTN-Nutzung zu.
4. Weisen Sie die VoIP-Route der PSTN-Nutzung zu.
5. Aktivieren Sie den Online Benutzer.
6. Weisen Sie dem Benutzer die VoIP-Routen Richtlinie zu.
7. Erstellen Sie eine VoIP-Route für ein analoges Gerät.

Informationen zum Verbinden eines ATA mit einem SBC und zum Konfigurieren des SBC finden Sie im Konfigurationshandbuch des SBC-Herstellers:

- [AudioCodes-Konfigurationsdokumentation](https://www.audiocodes.com/media/14278/connecting-audiocodes-sbc-with-analog-device-to-microsoft-teams-direct-routing-enterprise-model-configuration-note.pdf)

- [Menüband-Konfigurationsdokumentation](https://support.sonus.net/display/UXDOC81/Connect+SBC+Edge+to+Microsoft+Teams+Direct+Routing+to+Support+Analog+Devices)

## <a name="step-1--connect-the-sbc-to-direct-routing"></a>Schritt 1:  Verbinden des SBC mit Direct Routing

Mit dem folgenden Befehl wird die SBC-Verbindung wie folgt konfiguriert:

- FQDN SBC.contoso.com
- Signalisierungs-Port 5068
- Medien Umgehungsmodus
- Anrufverlaufs Informationen, die an den SBC weitergeleitet werden –
- P-Asserted-Identity (Pai)-Kopfzeile wird zusammen mit dem Anruf weitergeleitet 

```powershell
PS C:\> New-CsOnlinePSTNGateway -FQDN sbc.contoso.com -SIPSignalingPort 5068 -ForwardCallHistory $true -ForwardPAI $true -MediaBypass $true -Enabled $true 
```

## <a name="step-2--create-the-pstn-usage"></a>Schritt 2: Erstellen der PSTN-Nutzung 

Der nächste Befehl erstellt eine leere PSTN-Nutzung. Online PSTN-Nutzungen sind Zeichenfolgenwerte, die für die Anruf Autorisierung verwendet werden. Eine Online-PSTN-Nutzung verknüpft eine Online-VoIP-Richtlinie mit einer Route. In diesem Beispiel wird die Zeichenfolge "Interop" zur aktuellen Liste der verfügbaren PSTN-Nutzungen hinzugefügt. 

```powershell
PS C:\> Set-CsOnlinePstnUsage -Identity global -Usage @{add="Interop"} 
```

## <a name="step-3--create-a-voice-route-and-associate-it-with-the-pstn-usage"></a>Schritt 3: Erstellen Sie eine VoIP-Route, und ordnen Sie Sie der PSTN-Verwendung zu:

Dieser Befehl erstellt eine neue Online-VoIP-Route mit der Identität "Analog-Interop" für den Nummernbereich + 1425 XXX XX XX.  Die VoIP-Route gilt für eine Liste von Online-Gateways SBC.contoso.com und ordnet die Route der Online-PSTN-Nutzung "Interop" zu. Eine VoIP-Route enthält einen regulären Ausdruck, der angibt, welche Telefonnummern über eine bestimmte VoIP-Route weitergeleitet werden:

```powershell
PS C:\> New-CsOnlineVoiceRoute -Identity analog-interop -NumberPattern "^\+1(425)(\d{7}])$" -OnlinePstnGatewayList sbc.contoso.com -Priority 1 -OnlinePstnUsages "Interop"
```

## <a name="step-4-assign-the-voice-route-to-the-pstn-usage"></a>Schritt 4: Zuweisen der VoIP-Route zur PSTN-Nutzung:

Mit diesem Befehl wird eine neue Online-VoIP-Richtlinie für einzelne Benutzer mit der Identität "AnalogInteropPolicy" erstellt. Dieser Richtlinie wird eine einzelne Online PSTN-Nutzung zugewiesen: "Interop".

```powershell
PS C:\> New-CsOnlineVoiceRoutingPolicy -Identity "AnalogInteropPolicy" -Name "AnalogInteropPolicy" -OnlinePstnUsages "Interop"
```

## <a name="step-5-enable-the-online-user"></a>Schritt 5: Aktivieren des Online Benutzers

Dieser Befehl ändert das Benutzerkonto mit der Identität exampleuser@contoso.com. In diesem Fall wird das Konto geändert, um Enterprise-VoIP, die Microsoft-Implementierung von VoIP, mit aktivierter Voicemail zu aktivieren und diesem Benutzer die Nummer + 14255000000 zuzuweisen.  Dieser Befehl sollte für jeden Team Benutzer (mit Ausnahme von ATA-Geräte Benutzern) im Mandanten Mandanten ausgeführt werden.

```powershell
PS C:\> Set-CsUser -Identity "exampleuser@contoso.com" -EnterpriseVoiceEnabled $True -HostedVoiceMail $True -OnPremLineUri "tel:+14255000000"
```

## <a name="step-6-assign-the-voice-route-policy-to-a-user"></a>Schritt 6: Zuweisen der VoIP-Routen Richtlinie zu einem Benutzer

Mit diesem Befehl wird dem Benutzer die Richtlinie für die Online-VoIP-AnalogInteropPolicy des Benutzers mit dem Identitäts exampleuser@contoso.com zugewiesen.  Dieser Befehl sollte für jeden Team Benutzer (mit Ausnahme von ATA-Geräte Benutzern) im Mandanten Mandanten ausgeführt werden.

```powershell
PS C:\> Grant-CsOnlineVoiceRoutingPolicy -Identity "exampleuser@contoso.com" -PolicyName "AnalogInteropPolicy" 
```

## <a name="step-7--create-a-voice-route-for-an-analog-device"></a>Schritt 7: Erstellen einer VoIP-Route für ein analoges Gerät

Dieser Befehl erstellt eine Online-VoIP-Route mit der Identität "Analog-Interop" für den Nummernbereich + 1425 4xx XX XX, die für eine Liste von Online-Gateways SBC.contoso.com und mit der Online-PSTN-Nutzung "Interop" verknüpft ist.  Dieser Befehl sollte für jedes analoge Gerät mit dem entsprechenden Telefonnummernmuster ausgeführt werden. Alternativ können Sie beim Konfigurieren der Online-VoIP-Route in einem der vorherigen Schritte ein geeignetes Zahlenmuster für analoge Geräte verwenden.

```powershell
PS C:\> New-CsOnlineVoiceRoute -Identity analog-interop -NumberPattern "^\+1(4254)(\d{6}])$"  -OnlinePstnGatewayList sbc.contoso.com -Priority 1 -OnlinePstnUsages "Interop"
```

## <a name="considerations"></a>Überlegungen

- Sofern nicht anders angegeben, handelt es sich bei einem analogen Gerät um ein Gerät, das DTMF-Ziffern senden kann, um einen Anruf zu tätigen. Beispielsweise analoge Telefone, Faxgeräte und Overhead-Auslagerungsgeräte.

- Analoge Telefone, die mit einem ATA verbunden sind, können von Teams nicht durchsucht werden. Teams Benutzer müssen die Telefonnummer, die dem Gerät zugeordnet ist, manuell eingeben, um das Gerät anzurufen.  
 

## <a name="see-also"></a>Weitere Informationen

[Planen von direktem Routing](direct-routing-plan.md)

[Konfigurieren von direktem Routing](direct-routing-configure.md)
