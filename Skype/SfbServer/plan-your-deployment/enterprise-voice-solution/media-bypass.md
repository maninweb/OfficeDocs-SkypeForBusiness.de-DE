---
title: Planen der medienumgehung in Skype for Business
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom: ''
ms.assetid: 9ea090b3-f607-46f7-97dd-2510052524e5
description: Entscheidungen, die für die Planung der medienumgehung in Skype for Business Server Enterprise-VoIP erforderlich sind. Hierzu gehört die Interoperationalität mit Anrufsteuerung (CAC, call admission control).
ms.openlocfilehash: aed78aa12f593f834bc2c694fec87d5d31e6e47b
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41802705"
---
# <a name="plan-for-media-bypass-in-skype-for-business"></a>Planen der medienumgehung in Skype for Business

Entscheidungen, die für die Planung der medienumgehung in Skype for Business Server Enterprise-VoIP erforderlich sind. Hierzu gehört die Interoperationalität mit Anrufsteuerung (CAC, call admission control).

Medienumgehung bezieht sich auf das Entfernen des Vermittlungsservers aus dem Medienpfad, wenn möglich, für Anrufe, deren Signalisierung den Vermittlungsserver durchquert.

Die Medienumgehung kann die Sprachqualität verbessern, indem die Latenz verringert, eine unnötige Übersetzung und Paketverluste verhindert sowie potenzielle Fehlerstellen minimiert werden. Die Skalierbarkeit kann verbessert werden, da durch die Eliminierung der Medienverarbeitung für Umgehungs Anrufe die Belastung des Vermittlungsservers verringert wird. Diese Verringerung der Auslastung ergänzt die Möglichkeit des Vermittlungsservers, mehrere Gateways zu steuern.

 Wenn eine Verzweigungs Website ohne einen Vermittlungs Server über eine oder mehrere WAN-Links mit eingeschränkter Bandbreite mit einem zentralen Standort verbunden ist, senkt die medienumgehung die Bandbreitenanforderung, indem Medien von einem Client an einer Zweigstelle direkt an sein lokales Gateway fließen können, ohne Zunächst müssen Sie über die WAN-Verbindung zu einem Vermittlungs Server am zentralen Standort und zurückfließen.

Durch die Entlastung des Vermittlungsservers von der Medienverarbeitung kann die medienumgehung auch die Anzahl der Vermittlungsserver verringern, die für eine Enterprise-VoIP-Infrastruktur erforderlich sind. Generell gilt, dass die Medienumgehung möglichst immer aktiviert werden sollte.

Die folgende Abbildung zeigt grundlegende Pfade für Medien- und Signaldatenverkehr in Topologien mit und ohne Umgehung.

**Pfade für Medien- und Signaldatenverkehr mit und ohne Medienumgehung**

![Voice CAC Media Bypass-Verbindungserzwingung](../../media/Plan_CS_VoiceCAC_enforcementofconnectionstoPSTN.jpg)

Die medienumgehung ist nützlich, wenn Sie die Anzahl der bereitgestellten Vermittlungsserver minimieren möchten. In der Regel wird ein Vermittlungs Server Pool an einem zentralen Standort bereitgestellt, und er steuert Gateways an Zweigstellen. Durch Aktivierung der Medienumgehung können Mediendaten für PSTN-Anrufe (Telefonfestnetz) von Clients an Zweigstellenstandorten direkt durch die Gateways an diesen Standorten geleitet werden. Skype for Business Server-ausgehende Anrufrouten und Enterprise-VoIP-Richtlinien müssen ordnungsgemäß konfiguriert sein, damit PSTN-Anrufe von Clients an einem Zweigstellenstandort an das entsprechende Gateway weitergeleitet werden.

In Wi-Fi-Netzwerken treten üblicherweise mehr Paketverluste auf als in verkabelten Netzwerken. Die Wiederherstellung der Daten aus diesen Paketen kann normalerweise nicht mithilfe von Gateways durchgeführt werden. Daher wird empfohlen, die Qualität eines Wi-Fi-Netzwerks auszuwerten, bevor Sie entscheiden, ob die Medienumgehung für ein Funksubnetz aktiviert werden soll. Darüber hinaus muss erwogen werden, ob eine geringere Latenz zu Lasten der Dateiwiederherstellung nach Paketverlusten akzeptabel ist. RTAudio - ein Codec für Anrufe, die den Vermittlungsserver nicht umgehen - eignet sich besser für die Verarbeitung von Paketverlusten.

## <a name="planning-your-media-bypass-deployment"></a>Planen der Medien Umgehungs Bereitstellung

Nachdem Ihre Enterprise-VoIP-Struktur vorhanden ist, ist die Planung der medienumgehung einfach.

- Wenn Sie über eine zentralisierte Topologie ohne WAN-Verbindungen mit Zweigstellenstandorten verfügen, können Sie die globale Medienumgehung aktivieren, da eine genaue Steuerung nicht erforderlich ist.

- Wenn Sie dagegen eine verteilte Topologie mit mehreren Netzwerkregionen und zugehörigen Zweigstellenstandorten eingerichtet haben, müssen Sie sich die folgenden Fragen stellen:

  - Können die Vermittlungsserverpeers die für die Medienumgehung erforderlichen Funktionen unterstützen?

  - Welche Standorte in den jeweiligen Netzwerkregionen verfügen über eine gute Verbindung?

  - Welche Kombination aus Medienumgehung und Anrufsteuerung eignet sich für Ihr Netzwerk?

Wenn Sie die Medienumgehung aktivieren, wird automatisch eine eindeutige Umgehungs-ID für eine Netzwerkregion und für alle Netzwerkstandorte ohne Bandbreiteneinschränkungen innerhalb dieser Region generiert. Standorte mit Bandbreiteneinschränkungen innerhalb der Region und Standorte, die über WAN-Verbindungen mit Bandbreiteneinschränkungen mit der Region verbunden sind, erhalten jeweils eine eigene eindeutige Umgehungs-IDs.

Wenn ein Benutzer einen Anruf an das PSTN tätigt, vergleicht der Vermittlungs Server die Bypass-ID des Client-Subnets mit der Bypass-ID des Gateway-Subnetzes. Wenn die beiden Umgehungs-IDs übereinstimmen, wird für den Anruf die Medienumgehung verwendet. Wenn die Bypass-IDs nicht übereinstimmen, müssen Medien für den Anruf über den Vermittlungs Server fließen.

Wenn ein Benutzer einen Anruf vom PSTN erhält, vergleicht der Client seinen Bypass-ID mit dem des PSTN-Gateways. Wenn die beiden IDs übereinstimmen, fließt das Medium direkt vom Gateway zum Client, wobei der Vermittlungs Server umgangen wird.

Nur lync 2010 oder neuere Clients und Geräte unterstützen Medien Umgehungs Interaktionen mit einem Vermittlungs Server.

> [!IMPORTANT]
> Zusätzlich zur globalen Aktivierung der Medienumgehung müssen Sie die Medienumgehung auf jedem PSTN-Trunk einzeln aktivieren. Wenn die Umgehung zwar global, jedoch für einen bestimmten PSTN-Trunk nicht aktiviert wurde, wird sie für Anrufe über diesen PSTN-Trunk nicht ausgelöst. Darüber hinaus müssen Sie alle routingfähigen Subnetze den Standorten zuordnen, in denen sie sich befinden, wenn die Medienumgehung auf **Informationen zu Standort und Region verwenden** festgelegt ist. Routingfähige Subnetze in einem Standort, für den eine Medienumgehung nicht gewünscht wird, sollten vor Aktivierung der Umgehung in einem neuen Standort gruppiert werden. Auf diese Weise stellen Sie sicher, dass den nicht routingfähigen Subnetzen eine andere Umgehungs-ID zugewiesen wird.

## <a name="media-bypass-modes"></a>Modi für die Medienumgehung

Sie müssen die Medienumgehung sowohl global als auch für jeden einzelnen PSTN-Trunk konfigurieren. Wenn Sie die Medienumgehung global aktivieren, haben Sie die Auswahl zwischen zwei Optionen: **Immer umgehen** und **Informationen zu Standort und Region verwenden**.

Wie der Name vermuten lässt, wird die Medienumgehung bei Auswahl von **Immer umgehen** auf alle PSTN-Anrufe angewendet. **Immer umgehen** wird in Bereitstellungen verwendet, in denen weder eine Anrufsteuerung noch die Bereitstellung detaillierter Konfigurationsinformationen für die Medienumgehung erforderlich ist. Darüber hinaus wird die Option **Immer umgehen** verwendet, wenn vollständige Konnektivität zwischen Clients und PSTN-Gateways gegeben ist. In dieser Konfiguration sind alle Subnetze einer einzigen ID für die Umgehung zugeordnet, die durch das System berechnet wird.

Bei Auswahl der Option **Informationen zu Standort und Region verwenden** werden Entscheidungen zur Medienumgehung anhand der ID für die Umgehung und der zugeordneten Standort- und Regionenkonfiguration getroffen. Diese Konfiguration bietet die Flexibilität, die Medienumgehung für die gängigsten Topologien zu konfigurieren, da einerseits genau gesteuert werden kann, wann eine Umgehung stattfindet, und andererseits eine Interaktion mit der Anrufsteuerung unterstützt wird. Das System versucht, diese Aufgabe zu vereinfachen, indem automatisch IDs für die Umgehung zugewiesen werden:

- Das System weist jeder Region eine einzelne, eindeutige ID für die Umgehung zu.

- Jeder Standort, der über eine WAN-Verbindung ohne Bandbreiteneinschränkungen mit einer Region verbunden ist, erbt dieselbe Umgehungs-ID wie die Region.

- Einem Standort, der über eine WAN-Verbindung mit Bandbreiteneinschränkungen mit der Region verbunden ist, wird eine andere ID für die Umgehung zugewiesen als der Region.

- Die jedem Standort zugeordneten Subnetze erben die Umgehungs-ID für diesen Standort.

## <a name="media-bypass-and-call-admission-control"></a>Medienumgehung und Anrufsteuerung

Medienumgehung und Anrufsteuerung (Call Admission Control, CAC) arbeiten zusammen, um eine Bandbreitensteuerung für den Mediendatenverkehr bei Anrufen zu erzielen.  Die Medienumgehung fördert den Mediendatenfluss über Leitungen mit guter Konnektivität; die Anrufsteuerung verwaltet den Datenverkehr für Verbindungen mit Bandbreiteneinschränkungen. Da Medienumgehung und Anrufsteuerung sich gegenseitig ausschließen, müssen Sie bei der Planung die jeweils andere Funktion berücksichtigen. Die folgenden Kombinationen werden unterstützt:

- Sowohl Anrufsteuerung als auch Medienumgehung sind aktiviert. Die Medienumgehung muss auf **Informationen zu Standort und Region verwenden** festgelegt sein. Die Informationen zu Standort und Region sind dieselben wie für die Anrufsteuerung.

    Wenn Sie die Anrufsteuerung aktivieren, können Sie die Option **Immer umgehen** nicht auswählen (und umgekehrt), da die zwei Konfigurationen sich gegenseitig ausschließen. Dies bedeutet, dass jeweils nur eine der zwei Optionen auf einen PSTN-Anruf angewendet wird. Zunächst wird überprüft, ob für den Anruf die Medienumgehung gilt. Ist dies der Fall, wird die Anrufsteuerung nicht verwendet. Dies ist plausibel, da ein für die Medienumgehung aktivierter Anruf per Definition eine Verbindung verwendet, für die eine Anrufsteuerung nicht notwendig ist. Wenn Bypass nicht auf den Anruf angewendet werden kann (das heißt, wenn die Bypass-IDs des Clients und des Gateways nicht übereinstimmen), wird CAC auf den Anruf angewendet.

- Die Anrufsteuerung ist nicht aktiviert, und die Medienumgehung ist auf **Immer umgehen** festgelegt.

    In dieser Konfiguration sind sowohl Client- als auch Trunksubnetze einer einzigen ID für die Umgehung zugeordnet, die durch das System berechnet wird.

- Die Anrufsteuerung ist nicht aktiviert, und die Medienumgehung ist auf **Informationen zu Standort und Region verwenden** festgelegt.

    Wenn die Option **Informationen zu Standort und Region verwenden** aktiviert ist, funktioniert die Umgehungsermittlung im Prinzip in gleicher Weise - unabhängig davon, ob die Anrufsteuerung aktiviert ist oder nicht. Das heißt, dass für einen bestimmten PSTN-Anruf das Subnetz des Clients einer bestimmten Website zugeordnet ist und die Bypass-ID für dieses Subnetz extrahiert wird. Ebenso wird das Subnetz des Gateways einer bestimmten Website zugeordnet, und die Umgehungs-ID für dieses Subnetz wird extrahiert. Nur wenn die zwei Umgehungs-IDs identisch sind, findet eine Medienumgehung für den Anruf statt. Unterscheiden sich die IDs, findet keine Medienumgehung statt.

    Selbst wenn die Anrufsteuerung global deaktiviert wurde, müssen Bandbreitenrichtlinien für jeden Standort und jede Verbindung definiert werden, wenn die Konfiguration von Standorten und Regionen für Entscheidungen zur Medienumgehung herangezogen werden soll. Der tatsächliche Wert der Bandbreiteneinschränkung oder deren Modalität spielt keine Rolle. Das Ziel besteht darin, dass das System automatisch unterschiedliche Umgehungs-IDs berechnet, die verschiedenen Standorten ohne gute Verbindung zugeordnet sind. Das Definieren einer Bandbreiteneinschränkung bedeutet per Definition, dass eine Verbindung keine gute Konnektivität aufweist.

- Weder die Anrufsteuerung noch die Medienumgehung sind aktiviert. Dieser Fall tritt nur ein, wenn alle Gateways und IP-Nebenstellenanlagen über Leitungen mit geringer Konnektivität verbunden sind oder andere Anforderungen für die Medienumgehung nicht erfüllen. Ausführliche Informationen zu den Anforderungen für die Medienumgehung finden Sie unter [Requirements for Media Bypass](https://technet.microsoft.com/library/6162a204-0e7c-460a-8eb2-e592c6590a8a.aspx).

## <a name="technical-requirements"></a>Technische Anforderungen

Für jeden Anruf an das PSTN ermittelt der Vermittlungsserver, ob Medien aus dem Skype for Business-Endpunkt des Ursprungs direkt an einen Vermittlungsserver-Peer gesendet werden können, ohne den Vermittlungsserver zu durchlaufen. Der Peer kann ein PSTN-Gateway, eine IP-Nebenstellenanlage oder ein SBC (Session Border Controller) bei einem Anbieter von Internettelefoniediensten sein, der zu der Leitung zwischen dem Vermittlungsserver gehört, bei dem der Anruf weitergeleitet wird.

Die Medienumgehung kann implementiert werden, wenn die folgenden Voraussetzungen erfüllt sind:

- Ein Vermittlungs Server-Peer muss die erforderlichen Funktionen für die medienumgehung unterstützen, wobei das wichtigste die Möglichkeit ist, mehrere gegabelte Antworten (so genannte "frühe Dialogfelder") zu verarbeiten. Wenden Sie sich an den Hersteller Ihres Gateways oder Ihrer Telefonanlage oder Ihres ITSP, um den Wert für die maximale Anzahl der frühen Dialogfelder abzurufen, die das Gateway, die Telefonanlage oder SBC akzeptieren können.

- Der Vermittlungs Server-Peer muss Mediendatenverkehr direkt von Skype for Business-Endpunkten akzeptieren. Mit vielen ITSPs können Ihre SBC nur Datenverkehr vom Vermittlungs Server empfangen. Wenden Sie sich an Ihren ITSP, um festzustellen, ob der SBC Media Traffic direkt von Skype for Business-Endpunkten akzeptiert.

- Skype for Business-Clients und ein Vermittlungs Server-Peer müssen gut verbunden sein, d. h., Sie befinden sich entweder im gleichen Netzwerkbereich oder auf Netzwerkstandorten, die eine Verbindung mit der Region über WAN-Links herstellen, die keine Bandbreiteneinschränkungen aufweisen.


