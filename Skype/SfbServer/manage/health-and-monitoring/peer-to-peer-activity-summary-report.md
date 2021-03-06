---
title: Bericht "Peer-to-Peer-Aktivitätszusammenfassung" in Skype for Business Server
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
ms.assetid: e829a21e-9dfa-46ba-9b5b-077c175d6586
description: 'Zusammenfassung: erfahren Sie mehr über den Bericht Peer-to-Peer-Aktivitätszusammenfassung in Skype for Business Server.'
ms.openlocfilehash: 001298b948f3a3b8b9b404387fe4d93843297c8a
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41817784"
---
# <a name="peer-to-peer-activity-summary-report-in-skype-for-business-server"></a>Bericht "Peer-to-Peer-Aktivitätszusammenfassung" in Skype for Business Server
 
**Zusammenfassung:** Informieren Sie sich über den Bericht Peer-to-Peer-Aktivitätszusammenfassung in Skype for Business Server.
  
Der zusammenfassende Bericht über Peer-to-Peer-Aktivität bietet eine Übersicht über Peer-to-Peer-Kommunikationssitzungen. Eine Peer-to-Peer-Sitzung umfasst in der Regel nur zwei Benutzer und erfordert keine Verwendung der Skype for Business Server-Konferenzdienste. Im Vergleich dazu umfasst eine Konferenz in der Regel mehr als zwei Benutzer und erfordert die Verwendung von Skype for Business Server-Konferenzdiensten. Konferenzaktivität wird im zusammenfassenden Konferenzbericht gemeldet.
  
Der zusammenfassende Bericht über Peer-to-Peer-Aktivität hilft Ihnen bei der Beantwortung der folgenden Fragen:
  
- Wie viele Peer-to-Peer-Chatnachrichten senden meine Benutzer an einem normalen Tag?
    
- Nutzt der Benutzer tatsächlich die Vorteile der Skype for Business Server-Anwendungsfreigabe und der Dateiübertragungsfunktionen?
    
- Die Benutzer haben sich darüber beklagt, dass das Netzwerk zu bestimmten Tageszeiten langsam ist. Wie viele Minuten werden in diesen Zeiten für Peer-to-Peer-Audio-/Videositzungen aufgewendet?
    
## <a name="accessing-the-peer-to-peer-activity-summary-report"></a>Zugriff auf den zusammenfassenden Bericht über Peer-to-Peer-Aktivität

Auf den zusammenfassenden Bericht über Peer-to-Peer-Aktivität greifen Sie über die Startseite für Überwachungsberichte zu. Sie öffnen den [Peer-zu-Peer-Chat Bericht in Skype for Business Server](im-report.md) , indem Sie auf eine der folgenden Metriken klicken:
  
- Peer-to-Peer-Chatsitzungen insgesamt
    
- Peer-to-Peer-Chatnachrichten insgesamt
    
Entsprechend können Sie den Bericht über Peer-to-Peer-Sprach- und -Videoaktivität öffnen, indem Sie auf eine der folgenden Metriken klicken:
  
- Peer-to-Peer-Audiositzungen insgesamt
    
- Gesamtdauer der Peer-to-Peer-Audiositzung in Minuten
    
- Peer-to-Peer-Audiositzungen insgesamt
    
- Gesamtdauer der Peer-to-Peer-Audiositzung in Minuten
    
## <a name="making-the-best-use-of-the-peer-to-peer-activity-summary-report"></a>Optimale Nutzung des zusammenfassenden Berichts über Peer-to-Peer-Aktivität

Im unteren Bereich des zusammenfassenden Berichts über Peer-to-Peer-Aktivität finden Sie Gesamtwerte für Metriken wie z. B. „Peer-to-Peer-Chatsitzungen insgesamt“ und „Peer-to-Peer-Chatnachrichten insgesamt“. Dies ermöglicht einen schnellen Überblick über die detaillierten Informationen im eigentlichen Bericht.
  
## <a name="filters"></a>Filter

Mithilfe von Filtern können Sie eine gezieltere Datenauswahl erreichen oder die zurückgegebenen Daten auf unterschiedliche Weise anzeigen. Mit dem zusammenfassenden Bericht über Peer-to-Peer-Aktivität können Sie beispielsweise wählen, wie Daten gruppiert werden sollen. In diesem Fall werden die Aktivitäten nach Stunde, Tag, Woche oder Monat zusammengefasst.
  
In der folgenden Tabelle werden die Filter aufgelistet, die Sie im zusammenfassenden Bericht über Peer-to-Peer-Aktivität verwenden können.
  
**Filter im zusammenfassenden Bericht über Peer-to-Peer-Aktivität**

|**Name**|**Beschreibung**|
|:-----|:-----|
|**Von** <br/> |Anfangsdatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Anfangsdatum und -uhrzeit wie folgt ein:  <br/> 17.07.2015 13:00 Uhr  <br/> Wenn Sie keinen Anfangszeitpunkt eingeben, beginnt der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 17.07.2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 13.07.2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Bis** <br/> |Enddatum und -uhrzeit für den Zeitraum. Wenn die Daten nach Stunden angezeigt werden sollen, geben Sie Enddatum und -uhrzeit wie folgt ein:  <br/> 17.07.2015 13:00 Uhr  <br/> Wenn Sie keinen Endzeitpunkt eingeben, endet der Bericht automatisch am angegebenen Tag um 12:00 Uhr. Zum Anzeigen der Daten nach Tag geben Sie nur das Datum ein:  <br/> 17.07.2015  <br/> Sollen die Daten nach Woche oder Monat angezeigt werden, geben Sie irgendein Datum ein, das in die anzuzeigende Woche oder den anzuzeigenden Monat fällt (Sie müssen nicht den ersten Tag der Woche oder des Monats eingeben):  <br/> 13.07.2015  <br/> Eine Woche läuft immer von Sonntag bis einschließlich Samstag.  <br/> |
|**Intervall** <br/> | Zeitintervall. Wählen Sie eine der folgenden Optionen aus: <br/>  Stündlich (maximal 25 Stunden können angezeigt werden) <br/>  Täglich (maximal 31 Tage können angezeigt werden) <br/>  Wöchentlich (maximal 12 Wochen können angezeigt werden) <br/>  Monatlich (maximal 12 Monate können angezeigt werden) <br/>  Wenn mit dem angegebenen Start- und Endzeitpunkt die maximale Anzahl der zulässigen Werte für das ausgewählte Intervall überschritten wird, wird nur die maximale Anzahl an Werten (beginnend mit dem Startzeitpunkt) angezeigt. Beispiel: Wenn Sie das Intervall „Täglich“ mit dem Startdatum 17.07.2015 und dem Enddatum 28.02.2015 ausgewählt haben, werden Daten für die Tage 07.08.2015 12:00 Uhr bis 07.09.2015 12:00 Uhr angezeigt (d. h. Daten für insgesamt 31 Tage). <br/> |
   
## <a name="metrics"></a>Metriken

In der folgenden Tabelle werden Metriken aufgelistet, die im zusammenfassenden Bericht über Peer-to-Peer-Aktivität angegeben werden.
  
**Metriken im zusammenfassenden Bericht über Peer-to-Peer-Aktivität**

|**Name**|**Kann nach dieser Metrik sortiert werden?**|**Beschreibung**|
|:-----|:-----|:-----|
|**Stündlich** <br/> **Täglich** <br/> **Wöchentlich** <br/> **Monatlich** <br/> |Nein  <br/> |Gibt das auf der Filtersymbolleiste gewählte Zeitintervall an. Sie können gegebenenfalls auf ein bestimmtes Zeitintervall klicken, um ausführliche Informationen zu diesem Intervall anzuzeigen. Wenn Sie beispielsweise das tägliche Intervall verwenden und auf 17.07.2015 klicken, wird eine stündliche Übersicht der Benutzerregistrierungsaktivität für dieses Datum angezeigt.  <br/> |
|**Peer-to-Peer-Sitzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der abgehaltenen Peer-to-Peer-Sitzungen, unabhängig vom Sitzungstyp.  <br/> |
|**Peer-to-Peer-Chatsitzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der Peer-to-Peer-Chatnachrichtensitzungen. Wenn Sie auf dieses Element klicken, wird der Bericht über Peer-to-Peer-Chatnachrichten für den gewählten Zeitraum angezeigt.  <br/> |
|**Peer-to-Peer-Chatnachrichten insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der in Peer-to-Peer-Sitzungen gesendeten Chatnachrichten. Wenn Sie auf dieses Element klicken, wird der Bericht über Peer-to-Peer-Chatnachrichten für den gewählten Zeitraum angezeigt.  <br/> |
|**Peer-to-Peer-Audiositzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der Peer-to-Peer-Audioanrufe. Wenn Sie auf dieses Feld klicken, wird der Bericht über Peer-to-Peer-Sprach- und -Videoaktivität für den gewählten Zeitraum angezeigt.  <br/> |
|**Gesamtdauer der Peer-to-Peer-Audiositzung in Minuten** <br/> |Nein  <br/> |Gesamtdauer der Peer-to-Peer-Audiositzungen. Wenn Sie auf dieses Element klicken, wird der Bericht über Peer-to-Peer-Sprach- und -Videoaktivität für den gewählten Zeitraum angezeigt.  <br/> |
|**Durchschnittliche Dauer der Peer-to-Peer-Audiositzung in Minuten** <br/> |Nein  <br/> |Durchschnittliche Dauer einer Peer-to-Peer-Audiositzung. Wird errechnet, indem die Gesamtdauer der Audiositzungen durch die Gesamtanzahl der Audiositzungen geteilt wird.  <br/> |
|**Peer-to-Peer-Videositzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der Peer-to-Peer-Videoanrufe. Beachten Sie, dass Videositzungen auch als Audiositzungen zählen; jede Videositzung zählt als eine Videositzung und eine Audiositzung. Wenn Sie auf dieses Element klicken, wird der Bericht über Peer-to-Peer-Sprach- und -Videoaktivität für den gewählten Zeitraum angezeigt.  <br/> |
|**Gesamtdauer der Peer-to-Peer-Videositzung in Minuten** <br/> |Nein  <br/> |Gesamtdauer der Peer-to-Peer-Videositzungen. Wenn Sie auf dieses Element klicken, wird der Bericht über Peer-to-Peer-Sprach- und -Videoaktivität für den gewählten Zeitraum angezeigt.  <br/> |
|**Durchschnittliche Dauer der Peer-to-Peer-Videositzung in Minuten** <br/> |Nein  <br/> |Durchschnittliche Dauer einer Peer-to-Peer-Videositzung. Wird errechnet, indem die Gesamtdauer der Videositzungen durch die Gesamtanzahl der Videositzungen geteilt wird.  <br/> |
|**Peer-to-Peer-Dateiübertragungssitzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der Peer-to-Peer-Sitzungen mit Dateiübertragungen.  <br/> |
|**Peer-to-Peer-Anwendungsfreigabesitzungen insgesamt** <br/> |Nein  <br/> |Gesamtanzahl der Peer-to-Peer-Sitzungen mit Anwendungsfreigabe.  <br/> |
   

