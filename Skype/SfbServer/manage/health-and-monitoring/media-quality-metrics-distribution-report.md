---
title: Der Verteilungs Bericht zur Medien Qualitätsmetrik in Skype for Business Server
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: d07996e6-b0a5-4ff8-9512-ab707762b4e2
description: 'Zusammenfassung: Informationen zum Verteilungs Bericht zur Medien Qualitätsmetrik in Skype for Business Server.'
ms.openlocfilehash: f656a44ac1437a9c57cb5efe757757e7d695c2a5
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41817854"
---
# <a name="the-media-quality-metrics-distribution-report-in-skype-for-business-server"></a>Der Verteilungs Bericht zur Medien Qualitätsmetrik in Skype for Business Server 
 
**Zusammenfassung:** Erfahren Sie mehr über den Verteilungs Bericht zur Medien Qualitätsmetrik in Skype for Business Server.
  
Mit dem Bericht über die Metrikverteilung der Medienqualität wird ein Diagramm mit den Verteilungswerten für eine QoE-Metrik (Quality of Experience) wie z. B. Jitter oder Paketverlust angezeigt. Angenommen, Ihre Benutzer tätigen insgesamt 10 Telefonanrufe, für die die folgenden Roundtripzeiten gemeldet werden:
  
|**Anrufnummer**|**Roundtripzeit (Millisekunden)**|
|:-----|:-----|
|1  <br/> |50  <br/> |
|2  <br/> |50  <br/> |
|3  <br/> |50  <br/> |
|4  <br/> |50  <br/> |
|5  <br/> |50  <br/> |
|6  <br/> |50  <br/> |
|7  <br/> |50  <br/> |
|8  <br/> |4550  <br/> |
|9  <br/> |50  <br/> |
|10  <br/> |50  <br/> |
   
Der Durchschnittswert für diese Roundtripzeiten beträgt 500 Millisekunden (5000 geteilt durch 10). Fünfhundert Millisekunden ist eine extrem lange Roundtripzeit. Sie könnten deshalb daraus folgern, dass ein schwerwiegendes Netzwerküberlastungsproblem vorliegt. (Lange Roundtripzeiten sind in der Regel auf überlastete Netzwerke zurückzuführen.)
  
In Wirklichkeit hatten natürlich 90 % Ihrer Anrufe hervorragende Roundtripzeiten. Es gab nur einen Anruf mit einem sehr schlechten Wert, durch den das Gesamtergebnis verfälscht wurde. Wenn Sie nur die durchschnittliche Roundtripzeit betrachten, könnten Sie ganz falsche Schlussfolgerungen ziehen.
  
Der Bericht über die Metrikverteilung der Medienqualität hilft Ihnen, falsche Schlussfolgerungen zu vermeiden, indem die grafische Verteilung einer angegebenen Metrik (z. B. Roundtripzeit) angezeigt wird. Anhand dieser Diagramme lässt sich erkennen, dass es neun Anrufe mit sehr guten Werten und einen Anruf mit einem sehr schlechten Wert gibt. Zugegebenermaßen sollten Sie diesen einen Anruf weiter analysieren. Die Tatsache jedoch, dass 9 der 10 Anrufe sehr gute Werte aufweisen, ist ein Hinweis darauf, dass es keinen Grund gibt, drastische Änderungen an Ihrem Netzwerk vorzunehmen. Zumindest nicht zu diesem Zeitpunkt.
  
## <a name="filters"></a>Filter

Mithilfe von Filtern können Sie eine gezieltere Datenauswahl erreichen oder die zurückgegebenen Daten auf unterschiedliche Weise anzeigen. In der folgenden Tabelle werden die Filter aufgelistet, die Sie im Bericht über die Metrikverteilung der Medienqualität verwenden können.
  
**Filter im Bericht über die Metrikverteilung der Medienqualität**

|**Name**|**Beschreibung**|
|:-----|:-----|
|**Von** <br/> |Anfangsdatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Anfangsdatum und -uhrzeit wie folgt ein:  <br/> 07.07.2015 13:00  <br/> Wenn Sie keinen Anfangszeitpunkt eingeben, beginnt der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 07.07.2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 03.07.2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Bis** <br/> |Enddatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Enddatum und -uhrzeit wie folgt ein:  <br/> 07.07.2015 13:00  <br/> Wenn Sie keinen Endzeitpunkt eingeben, endet der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 07.07.2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 03.07.2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Minimum in X-Achse** <br/> |Der niedrigste Wert, der auf der X-Achse des Diagramms angezeigt werden soll.  <br/> |
|**Maximum in X-Achse** <br/> |Der höchste Wert, der auf der X-Achse des Diagramms angezeigt werden soll.  <br/> |
|**Zugriffstyp** <br/> | Gibt an, ob der Client am internen oder am externen Netzwerk angemeldet wurde, als der Anruf getätigt wurde. Wählen Sie eine der folgenden Optionen aus: <br/>  [Alle] <br/>  Intern <br/>  Extern <br/> |
|**VPN** <br/> | Gibt an, ob ein externer Client eine VPN-Verbindung (Virtual Private Network) verwendete, als der Anruf getätigt wurde. Wählen Sie eine der folgenden Optionen aus: <br/>  [Alle] <br/>  VPN <br/>  Nicht-VPN <br/> |
|**Netzwerktyp** <br/> | Gibt den Typ des Netzwerks an, mit dem der Client verbunden wurde, als der Anruf erfolgte. Wählen Sie eine der folgenden Optionen aus: <br/>  [Alle] <br/>  Verkabelt <br/>  Funk <br/> |
   

