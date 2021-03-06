---
title: Anzeigen der Microsoft Teams-Auslastung in Power BI mithilfe von CQD-Daten
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: siunies
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection:
- M365-voice
- Teams_ITAdmin_RemoteWorkers
search.appverid: MET150
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
description: Verwenden Sie die Power BI-Berichte der Teams-Auslastung für den Zugriff auf Microsoft Teams Call Quality Dashboard-Daten (CQD), um die Verwendung von Microsoft Teams in Ihrer Organisation zu überwachen.
ms.openlocfilehash: bda89f3715997016e6c1bea242dcf6b8b182c6bf
ms.sourcegitcommit: 43d66693f6f08d4dcade0095bf613240031fec56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "46581546"
---
# <a name="view-microsoft-teams-utilization-in-power-bi-using-cqd-data"></a>Anzeigen der Microsoft Teams-Auslastung in Power BI mithilfe von CQD-Daten

Neu im März 2020 haben wir unseren herunterladbaren [Power BI-Abfragevorlagen für CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true)einen Bericht zur Nutzung von Teams hinzugefügt. 

In diesen Berichten zur neuen Teams-Auslastung können Sie sehen, wie (und wie viel) Ihre Benutzer Microsoft Teams verwenden, indem Sie auf die CQD-Daten (Teams Call Quality Dashboard) zugreifen. Bei diesen Berichten handelt es sich um einen zentralen Standort, an dem sowohl Administratoren als auch Unternehmensleiter schnell zu diesen Daten wechseln können.

Der Power BI-Bericht "Teams-Auslastung" besteht aus zwei Hauptberichten: Zusammenfassung der **[Anruf Anzahl](#call-count-summary-report)** und **[Zusammenfassung der audiominuten](#audio-minutes-summary-report)**. Die [tägliche Nutzung](#daily-usage), [regionale Audiodetails](#regional-audio-details), [Konferenzdetails](#conference-details) und [Benutzerlisten](#user-list) Berichte kommen in den Spielzustand, wenn ein Benutzer die Drilldown-Berichte nutzt, die in den folgenden Beschreibungen aufgeführt sind.

> [!NOTE]
> Gebäude-und subnetzdaten müssen ausgefüllt werden, um regionale und Netzwerkfilter Funktionen bereitzustellen.

## <a name="call-count-summary-report"></a>Zusammenfassungsbericht "Anruf Anzahl"

Auf der Hauptseite (Zusammenfassung der Anruf Anzahl) werden die Anzahl der Audio-, Video-und Bildschirmfreigabe Sitzungen über die letzten 30 und 90 Tage, wie im Abschnittstitel angegeben, sofort bereitgestellt. Die anfänglich angezeigten Daten sind für die gesamte Organisation und können mithilfe der Dropdownoptionen für datenschnitt auf der linken Seite der Seite gefiltert werden.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report1.png)

1. Rechts neben der Dropdownliste der datenschnitte wird die Anzahl der Anrufe nach Medientyp in den letzten dreißig Tagen in eine interne/externe Ansicht aufgeteilt. Der obige Screenshot zeigt, dass weitere Anrufe von außerhalb der Unternehmensstandorte ablaufen, was in der aktuellen globalen Umgebung Sinn macht.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report2.png)

1. Rechts neben dem Feld "Medientyp Anzahl" haben wir die monatlichen Anruf Anzahl nach Medientyp für die letzten 90 Tage. Jede Spalte und jeder Medientyp können mit der Maus eingeblendet werden, um die Anzahl für einen vorherigen Monat oder den aktuellen Monat bis dato anzuzeigen, wobei Trendinformationen zur Verwendung bereitgestellt werden.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report3.png)
 

1. Das mittlere Diagramm funktioniert wie das 90-Tage-Diagramm, bietet jedoch eine tägliche Nutzungs Ansicht für die letzten 30 Tage und ermöglicht einem Benutzer, mit der rechten Maustaste zu klicken und Details für einen bestimmten Tag zu durchlaufen.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report4.png)

In der unteren linken Ecke der Seite befindet sich eine Tabelle, in der die Gesamtwerte für die einzelnen Medientypen im letzten Jahr bereitgestellt werden. 
    ![Screenshot: Teams-Auslastungsberichte ](media/CQD-teams-utilization-report5.png) ![ – Screenshot: Berichte zur Auslastung von Teams](media/CQD-teams-utilization-report6.png)   

Rechts neben der Tabelle werden in einem Balkendiagramm die Clients angezeigt, die in den letzten 30 Tagen die meisten Verwendungszwecke (Anrufe/Streams) verwendet haben.
   ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report7.png)

In der letzten Gruppe von Diagrammen für diese Seite werden die einzelnen Medientypen einzeln angezeigt, wobei die Verwendung von Konferenz-und P2P-Daten eine Unterbrechung zeigt. Die folgenden Diagramme zeigen, dass im Vergleich zu P2P eine deutlich höhere Anzahl von Konferenz Nutzungen vorliegt.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report8.png)

## <a name="audio-minutes-summary-report"></a>Zusammenfassungsbericht für Audio-Minuten

Im Bericht "audiominuten-Nutzung" wird die Gesamt Minuten Nutzung in einigen verschiedenen Ansichten bereitgestellt. 

Wir haben die Zusammenfassung der dreißigtägigen Verwendung neben den datenschnitten als einfach zu verwendende Textfelder angezeigt. Die obere Zahl zeigt die 30-Tage-Summe, wobei die internen und externen Ausfälle darunter liegen.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report9.png)

Das obere rechte Balkendiagramm bietet eine ganzjährige Ansicht der Nutzung der Konferenz Audiofunktionen. Zeigen Sie mit der Maus auf den Monat, um die Gesprächsminuten für die Konferenz anzuzeigen.

Um die Unterschiede zwischen P2P-und Konferenz-Audio anzuzeigen, nimmt das untere linke Diagramm alle Audiodaten für das vergangene Jahr auf und unterbricht es zwischen den beiden Typen.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report10.png)

Das letzte Diagramm für die Seite "audiominuten" zeigt die Verwendung der audiominuten auf einem globalen Karten-Overlay an. Dieses Diagramm funktioniert nur, wenn Gebäude-und Subnetdaten in den Mandanten hochgeladen werden. Das Kreisdiagramm-Overlay auf der Karte kann gebohrt werden, um anschließend die regionale audionutzung bereitzustellen.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report11.png)


## <a name="drill-through-capabilities"></a>Drill-Through-Funktionen

Wie bereits erwähnt, können Benutzer einen Drilldown in die Berichte für tägliche und regionale Nutzung durchführen.

### <a name="daily-usage"></a>Tägliche Nutzung

Der Bericht "tägliche Nutzung" ermöglicht es einem Administrator, die höchst Verbrauchs Zeiten im Laufe eines Tages zu erkennen. Neben der Nutzung sind wir auch in der Lage, die gesamte Benutzer Stimmung und das Feedback für diesen Tag zu erfassen.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report12.png)

Der Bericht "tägliche Nutzung" zeigt die Anzahl der Audio-, Video-und Bildschirm Freigaben für den ausgewählten Tag mit der zusätzlichen Möglichkeit, zwischen interner und externer Konnektivität zu unterscheiden. Eine Konferenz und eine Peer-to-Peer-Aufteilung erfolgt unmittelbar rechts neben dem Feld Modalwert. Oben rechts im Bericht finden Sie eine Liste der Konferenzen mit den zugehörigen IDs und Teilnehmern für den Tag. Die Konferenzliste bietet einen zusätzlichen Drilldown zum Konferenz Detailbericht. Grafik ersetzen

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report13.png)

Das Balkendiagramm im mittleren Bereich ermöglicht es dem Benutzer, Spitzenverbrauchs Perioden im Laufe eines Tages zu erkennen. Benutzer können einen Drilldown in die im Diagramm dargestellte Stunde durchführen, in der der Benutzerlisten Bericht für die Stunde vorliegt.

Rechts neben dem Balkendiagramm wird das Feedback des Benutzers in einem visuellen Format angezeigt. Während die Benutzer Empfindung subjektiv sein kann, bietet Sie eine Einsicht, die verwendet werden kann, um potenzielle Probleme zu erkennen.

Die untere Tabelle enthält eine Reihe von Metriken für den Tag. Schlechte Prozentwerte sowie Ausfallraten können einem Administrator potenzielle Verbesserungsmöglichkeiten bieten. Jede Stunde kann auch einzeln ausgewählt werden, wie unten dargestellt.

Diese Daten können verwendet werden, um Regionen zu identifizieren, die Probleme bei Spitzenverbrauchszeiten aufweisen.


Klicken Sie auf die Spalte für diesen Tag, um Metriken für diese Stunde anzuzeigen.
![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report14.png)
  
  1.  In der Tabelle unter dem Diagramm werden die Metriken für diese Stunde angezeigt. Dies kann nach jeder Spaltenüberschrift sortiert werden. Wir wären jedoch daran interessiert, problematische Bereiche zu finden.  
    ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report15.png)
    
  2.  Wir sehen, dass die IND-Region während dieses Zeitraums eine schlechte Videoleistung in Konferenzen erlebt. Anschließend können die CQD-QER Microsoft-Berichte verwendet werden, um die problematische Position zu verkleinern, während der Bereich und der Zeitrahmen identifiziert wurden.

### <a name="conference-details"></a>Konferenz Details

Der Bericht "Konferenz Details" bietet zusätzliche Einblicke für Besprechungen, von einer Teilnehmerliste bis zu den Medientypen, die während der Sitzung verwendet werden.

Klicken Sie mit der rechten Maustaste auf eine Konferenz die Teilnehmer Leiste im Diagramm Konferenz-ID auf der Seite tägliche Nutzung, um einen Drilldown in die Konferenzdetails durchführen zu können.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report24.png)

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report25.png)
  

Wir können die Teilnehmer der Konferenz sowie alle relevanten Informationen bis hin zu Paketverlust und Jitter sehen, um mögliche Problembehandlungsschritte in der unteren Tabelle zu unterstützen.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report26.png)


### <a name="regional-audio-details"></a>Regionale Audiodaten

Im Bereich "regionale Audiodetails" wird die audiominuten-Verwendung für die ausgewählte Region speziell angezeigt. Benutzer mit Zugriff auf CQD können die Nutzungstrends sowohl für P2P-als auch für Konferenz-Audio in der ausgewählten Region sehen.

1.  Klicken Sie auf der Zusammenfassungsseite Anruf Anzahl auf eine bestimmte Region durch die Tabelle.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report16.png)

2.  Wählen Sie die Zeile mit dem Bereich aus, für den zusätzliche Informationen benötigt werden.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report17.png)

3.  Die Datentrends zeigen eine beträchtliche Anzahl von Minuten an, die im internen Netzwerk verwendet werden, wobei Conferencing die P2P-Nutzung weit übertrifft.
  ![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report18.png)

Der regionale audiotrend kann verwendet werden, um zu zeigen, wie Benutzer von externen Einflüssen in der Welt beeinflusst werden. Im Moment würden wir davon ausgehen, dass die externe Verwendung für die Regionen EMEA und APAC mit Personen, die zur Remote Arbeit aufgefordert werden, zunehmen wird.


### <a name="user-list"></a>Benutzerliste

Der Drilldown für Benutzerlisten bietet, wie man erwarten kann, benutzerspezifische Informationen für eine bestimmte Stunde, die von der Person, die den Bericht anzeigt, ausgewählt wurde. Der Benutzerlisten Bericht kann über einen Drilldown im Diagramm "stündliche Trends" im Bericht "tägliche Verwendung" aufgerufen werden. Klicken Sie mit der rechten Maustaste auf die Stunde, um weitere Informationen zu erhalten, und wählen Sie Drillthrough und Benutzerliste aus, wie unten dargestellt.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report19.png)

Der Bericht "Benutzerliste" zeigt die interne/externe Konnektivität über das Ringdiagramm oben in der Mitte der Seite an. Wir können festzustellen, dass es in der folgenden Abbildung eine große Beteiligung von außerhalb des Unternehmensnetzwerks gibt.

Oben rechts im Diagramm wird die Anzahl der Anrufe angezeigt, die von jedem Benutzer innerhalb dieser Stunde getätigt wurden.

![Screenshot: Teams-Auslastungsberichte](media/CQD-teams-utilization-report20.png)

Die untere Tabelle enthält detaillierte Informationen zu den Sitzungen, an denen jeder Benutzer während dieser Stunde teilgenommen hat. Die Spalte Fehlertyp ist nützlich, um zu ermitteln, was zu einem Anruf geführt hat. Die Spalten für das erfassen und Rendern von Geräten sind hilfreich, um zu ermitteln, warum ein Anruf mit schlechter Qualität gemeldet wurde.


## <a name="related-topics"></a>Verwandte Themen

[Im Anrufqualitäts-Dashboard verfügbare Dimensionen und Kennzahlen](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Datenstromklassifizierung im Dashboard für Anrufqualität](stream-classification-in-call-quality-dashboard.md)

[Einrichten der Anrufanalyse von Skype for Business](set-up-call-analytics.md)

[Verwenden von Anrufanalyse, um Probleme mit schlechter Anrufqualität zu behandeln](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Anrufanalyse- und Anrufqualitäts-Dashboard](difference-between-call-analytics-and-call-quality-dashboard.md)

[Teams-Problembehandlung](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)
 