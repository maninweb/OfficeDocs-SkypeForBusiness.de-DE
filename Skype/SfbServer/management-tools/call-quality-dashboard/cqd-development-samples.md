---
title: CQD-Entwicklungsbeispiele
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
ms.collection: IT_Skype16
ms.assetid: 8ca9bf7a-2d6f-48d5-a821-531009726525
description: 'Zusammenfassung: Lesen Sie ein Lernprogramm und Entwicklungsbeispiele für das Dashboard für die Anrufqualität. Das Dashboard für die Anrufqualität ist ein Tool für Skype for Business Server.'
ms.openlocfilehash: 22b0e44ca3bf2e80d8d2674d0af1e6a8f157dc23
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41816874"
---
# <a name="cqd-development-samples"></a>CQD-Entwicklungsbeispiele

**Zusammenfassung:** Überprüfen Sie ein Lernprogramm und Entwicklungsbeispiele für das Dashboard für die Anrufqualität. Das Dashboard für die Anrufqualität ist ein Tool für Skype for Business Server.

Dieser Artikel enthält ein Lernprogramm und Beispiele für die Entwicklung des Anrufqualitäts-Dashboards (Call Quality Dashboard, CQD).

## <a name="call-quality-dashboard-cqd-development-samples"></a>Beispiele für die Entwicklung des Anrufqualitäts-Dashboards (CQD)

Lernprogramm: Erstellen benutzerdefinierter Berichte mit dem CQD-Datendienst und Repository Service-APIs.

### <a name="introduction-to-cqd"></a>Einführung in CQD

Das Anrufqualitäts-Dashboard (Call Quality Dashboard, CQD) bietet schnellen und einfachen Zugriff auf die zusammengefassten Daten zur Anrufqualität für lokale Skype for Business Server-Bereitstellungen. Das CQD besteht aus drei Komponenten: der QoE-Archivdatenbank, dem Cube und dem Portal. Das Portal ist die Hauptpräsentationsebene und ist ebenfalls in drei Komponenten unterteilt:

1. Datendienst, der für authentifizierte Benutzer über die [Daten-API für das Anruf Qualitäts Dashboard (CQD) in Skype for Business Server](data-api.md)zugänglich ist.

2. Repository-Dienst, der für authentifizierte Benutzer über die [Repository-API für das Anruf Qualitäts Dashboard (CQD) in Skype for Business Server](repository-api.md)zugänglich ist.

3. das Webportal der HTML5-basierte Schnittstelle, die CQD-Benutzer sehen und mit der sie interagieren können. Auch sie ist für authentifizierte Benutzer zugänglich.

Die auf dem Webportal angezeigten Berichte sind in "Berichts Sätze" gruppiert. Die Abbildung zeigt einen Berichtssatz mit zwei Berichten. Jeder Bericht in diesem Dashboard zeigt die Abfrageergebnisse für viele gute Anrufe, schlechte Anrufe und einen schlechten Anruf Prozentsatz für mehrere Monate, wobei verschiedene Filter angewendet werden. 

![CQD-Beispielbericht](../../media/9e0723f7-f850-4d11-9ecd-7e8e013a8bed.png)

Das Anrufqualitäts-Dashboard wird entsprechend der Call Quality Methodology (CQM) erstellt, sodass der standardmäßige Berichtesatz auf den Recherche-Workflow ausgelegt ist, der in CQM festgelegt wurde. Benutzer können aber die Berichte nach ihren eigenen Vorstellungen flexibel bearbeiten oder neu erstellen. Aufgrund der Vielzahl der Darstellungsmöglichkeiten erfüllen die im Dashboard bereitgestellten Visualisierungsvorgaben eventuell nicht die Bedürfnisse jedes Benutzers. In diesem Fall kann ein Benutzer die Daten- und Repository-APIs nutzen, um eigene Berichtseiten zu definieren. In diesem Lernprogramm stellen wir einige Beispiele dafür vor.

### <a name="how-the-dashboard-consumes-the-data-service"></a>Wie das Dashboard den Datendienst nutzt

Beim Navigieren zur CQD-Startseite (z http://localhost/cqd). b. werden der Berichtssatz und die entsprechenden Berichte für einen authentifizierten und autorisierten Benutzer aus dem Repository-Dienst abgerufen. Eine vollständige URL wird aus der Berichtssatz-ID und dem Jahres Monat erstellt (die Berichtssatz-ID ist die ganzzahlige Zahl nach dem Abschnitt "/#/" in der URL, und standardmäßig wird der aktuelle Jahr-Monat am Ende der Berichtssatz-ID nach dem Schrägstrich angefügt). Die Berichtsdefinitionen werden im JSON-Format gespeichert und, wenn Sie aus dem Repository-Dienst abgerufen werden, als Eingabe für den Datendienst verwendet. Der Datendienst generiert MDX-Abfragen (Multidimensional Expressions) basierend auf der Eingabe und führt dann diese MDX-Abfragen für den Cube aus, um Daten für jeden Bericht abzurufen. 

### <a name="building-customized-reports"></a>Erstellen benutzerdefinierter Berichte

Das Anrufqualitäts-Dashboard bietet bereits ein hohes Maß an Flexibilität zum Anpassen von Berichten, aber es kann Situationen geben, in denen Benutzer Daten aus mehreren in CQD erstellten Berichten zusammenführen möchten. So könnte beispielsweise die Notwendigkeit bestehen, einen Bericht zu erstellen, in dem aus allen möglichen Kombinationen von kabelgebundenen Anrufen der Prozentsatz der Anrufe schlechter Qualität in einer Tabelle dargestellt werden (mit einem Ergebnis ähnlich wie in der Abbildung):

![CQD-Tabelle](../../media/ef19d535-5da6-44a9-91f6-1ed3f30b96f1.png)

Über das vom Anrufqualitäts-Dashboard bereitgestellte Portal müsste der Benutzer durch mehrere Berichte navigieren, um für jeden einzelnen den Prozentsatz von Anrufen schlechter Qualität zu ermitteln, was sehr umständlich sein kann, wenn man zahlreiche Datenpunkte sammeln möchte. Durch den Abruf der Daten mittels eines Datendiensts (z. B. per AJAX-Abruf) bieten die Daten-APIs dem Benutzer eine automatisierte Form der Abfrage. 

 **Beispiel 1: Beispiel für einen einfachen Bericht**

Lassen Sie uns zuerst ein einfaches Beispiel anschauen. Angenommen, wir möchten die Zahl an gut gestreamten und schlecht gestreamten Audio-Inhalten im Februar 2015 auf einer HTML-Seite ähnlich der folgenden anzeigen:

![CQD-Beispielbericht](../../media/f0e4e61f-1fa5-4d69-b192-f19e9612bf1c.png)

Dazu müssen wir eine Abfrage mit den entsprechenden Parametern an den Datendienst senden und die Ergebnisse in einer HTML-Tabelle darstellen. Im Folgenden sehen Sie ein Beispiel für den JavaScript-Code:

```javascript        
$($.fn.freeFormReport = function (queries, urlApi, presentation) {
            var query = {
                Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                Filters: [{
                    DataModelName: '[StartDate].[Month]',
                    Value: '[2015-02-01T00:00:00]',
                    Operand: 0
                }],
                Measurements:
                    [{ DataModelName: '[Measures].[Audio Good Streams JPDR Count]' },
                     { DataModelName: '[Measures].[Audio Poor Streams JPDR Count]' },]
            };            

            $.ajax({
                url: 'http://localhost/QoEDataService/RunQuery',
                data: JSON.stringify(query),
                type: 'POST',
                async: true,
                contentType: 'application/json;charset=utf-8',
                success: function (data) {
                    //This is the jQuery syntax for document.GetElementById()
                    $('#AudioGoodStreamsJPDRCount').html(data.DataResult[0][1]);
                    $('#AudioPoorStreamsJPDRCount').html(data.DataResult[0][2]);
                }
                error: function (error) {
                    alert('Error getting data, check that the data service is running and that the URL is correct.');
           }
            });
        });
```

Dieses Beispiel lässt sich weiter in drei Schritte unterteilen:

1. Erstellen Sie die Abfrage (im Beispiel wird dies in der Variablen "Query" definiert). Die Abfrage ist als JSON-Objekt definiert, das die folgenden Daten enthält:

   a. Null oder mehr Dimensionen. Jede Dimension wird durch einen DataModelName angezeigt.

   b. Null oder mehr Filter. Jeder Filter verfügt über folgende Elemente:

   - DataModelName (die Dimension, für die der Filter gesetzt wird).

   - Wert (der Wert, der vom Operanden verglichen wird).

   - Operand (Comparison Type, 0 bedeutet "gleich").

     c. Ein oder mehrere Messwerte.

2. Senden Sie die Anfrage per AJAX-Abruf an den Datendienst. Folgende Abfrageparameter müssen angegeben sein:

   a. URL (http://[ServerName]/QoEDataService/RunQuery).

   b. Data (Dies ist die Zeichenfolgendarstellung des JSON-Objekts, das in der Variablen "Query" definiert ist). Der Datendienst gibt die Abfrageergebnisse als Parameter der Rückruffunktion „Erfolg“ zurück.

   c. Type (für QoEDataService akzeptiert RunQuery nur "Post"-Anforderungen).

   d. Asynchron (ein Flag, das anzeigt, ob der AJAX-Abruf synchron oder asynchron ablaufen soll).

   e. ContentType (sollte "application/json" sein).

   f. Erfolg (Rückruffunktion, wenn der Ajax-Abruf erfolgreich abgeschlossen wurde).

   g. Fehler (Fehlerbehandlungsfunktion, wenn der AJAX-Abruf fehlschlägt).

3. Dateneingabe für die einzelnen Elemente in der HTML (im vorliegenden Beispiel für den Code geschieht dies über einen anonymen Funktionsabruf, nachdem die AJAX-Abfrage erfolgreich abgeschlossen wurde).

Nach Einfügen des Java Script-Codes in eine HTML-Seite erhält man eine ähnliche Berichtseite wie in der Abbildung. Die vollständige HTML sieht wie folgt aus:

```javascript
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
</head>
<body>
    <script src="OpenSourceSoftware/Scripts/jquery-2.1.1.js"></script>

    <script>
        $($.fn.freeFormReport = function (queries, urlApi, presentation) {

            var query = {
                Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                Filters: [{
                    DataModelName: '[StartDate].[Month]',
                    Value: '[2015-02-01T00:00:00]',
                    Operand: 0
                }],
                Measurements:
                    [{ DataModelName: '[Measures].[Audio Good Streams JPDR Count]' },
                     { DataModelName: '[Measures].[Audio Poor Streams JPDR Count]' },]
            };            

            $.ajax({
                url: 'http://localhost/QoEDataService/RunQuery',
                data: JSON.stringify(query),
                type: 'POST',
                async: true,
                contentType: 'application/json;charset=utf-8',
                success: function (data) {
                    //This is the jQuery syntax for document.GetElementById()
                    $('#AudioGoodStreamsJPDRCount').html(data.DataResult[0][1]);
                    $('#AudioPoorStreamsJPDRCount').html(data.DataResult[0][2]);
                }
                error: function (error) {
                    alert('Error getting data, check that the data service is running and that the URL is correct.');
           }

            });
        });
    </script>
    <table border="1">
        <tr>
            <td></td>
            <td><div>Audio Good Streams JPDR Count</div></td>
            <td><div>Audio Poor Streams JPDR Count</div></td>
        </tr>
        <tr>
            <td>February</td>
            <td><div id="AudioGoodStreamsJPDRCount"></div></td>
            <td><div id="AudioPoorStreamsJPDRCount"></div></td>
        </tr>
    </table>
</body>
</html>
```

Bis hierher war der Bericht noch sehr einfach. Der Benutzer kann aber weitere Messwerte, Dimensionen oder Filter hinzufügen, um den Bericht nach seinen Wünschen zu gestalten. Wenn Sie beispielsweise den Prozentsatz an Anrufen schlechter Qualität für AppSharing darstellen möchten, müssen Sie einen neuen Messwert für AppSharing hinzufügen. Wenn Sie sämtliche TCP-Anrufe vs. UDP-Anrufe anzeigen möchten, müssen Sie eine neue Dimension für den Transporttyp hinzufügen. Wenn Sie die Anzahl an Anrufen schlechter Qualität innerhalb eines bestimmten Gebäudes anzeigen möchten, müssen Sie einen neuen Filter hinzufügen, damit nur die ein- und ausgehenden Anrufe dieses Gebäudes berücksichtigt werden.

 **Beispiel 2: Beispiel für eine Berichtdefinition**

Beim Programmieren einer Abfrage kann es manchmal schwierig sein herauszufinden, wie man die vollständige Liste aus Messwerten/Dimensionen/Filtern mit den entsprechenden Werten erstellen soll. In diesem Fall können Sie zum Portal wechseln, einen Bericht mithilfe des Berichteditors definieren, sich dann die JSON-Zeichenfolge der Berichtdefinition anzeigen lassen und die Definition in einen neuen benutzerdefinierten Bericht kopieren. 

In diesem Beispiel erstellen wir eine Webseite wie in der Abbildung, in der ein Benutzer die Kennung eines vorhandenen Berichtsatzes (oder Berichts) eingeben und die Definition des Berichtsatzes oder Berichts auf der Webseite anzeigen kann. Anschließend kann er die JSON-Zeichenfolge der einzelnen Berichte in einen Code ähnlich wie Beispiel 1 einfügen und jeden beliebigen benutzerdefinierten Bericht erstellen. 

![CQD-Beispiel](../../media/01c45c23-c4d2-47b8-819f-0888cf71260f.png)

Zur Erstellung eines Anzeigetools für die Berichtdefinition muss eine Anfrage an den Repository-Service gesendet werden, um die JSON-Zeichenfolgedarstellungen für die Definitionen des gewünschten Berichtsatzes abzurufen. Die Repository-API gibt daraufhin eine Berichtsatzdefinition zurück, die auf einer vorhandenen Berichtsatzkennung basiert. 

Ein kurzes Beispiel sieht wie folgt aus: der Code enthält einen Block, der ein einfaches Beispiel zum Senden einer Abfrage an den Repository-Dienst ist, um den Inhalt eines Repository-Elements basierend auf dessen Bezeichner abzurufen. Und der nächste Teil des Codes (processReportSetData-Methode) sendet AJAX-Aufrufe, um die Definition der einzelnen Berichte innerhalb dieses Berichtssatzes abzurufen. Da die ID im CQD-Webportal die ID eines Berichtssatzes ist, gibt der Ajax-Aufruf ein Berichtssatz Element zurück. Weitere Informationen zur Repository-API und insbesondere zu GetItems finden Sie in den [Get-Elementen](get-items.md). 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta http-equiv='cache-control' content='no-cache'>
    <meta http-equiv='expires' content='0'>
    <meta http-equiv='pragma' content='no-cache'>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta http-equiv="x-content-type-options" content="nosniff">
    <title>CQD Report definition viewer</title>
</head>
<body>    
    <div style="font-size:32pt">CQD Report definition viewer</div>
        <p>ReportSet Id: <input id="reportSetId" /></p>
        <button onclick='loadReportSet()'>Load</button>
        <div id="Report"></div>
    <!-- Third party Libraries -->
    <script src="OpenSourceSoftware/Scripts/jquery-2.1.1.js"></script>

    <script>
        var urlRepositoryApi = 'http://localhost/QoERepositoryService/repository/item/';

        var loadReportSet = function ()
        {
            var reportSetId = document.getElementById('reportSetId').value;

            $.ajax({
                url: urlRepositoryApi + reportSetId,
                data: '',
                type: 'GET',
                async: false,
                contentType: 'application/json;charset=utf-8',
                success: function (data) {
                    var reportSetDiv = document.getElementById('Report');
                    reportSetDiv.innerHTML = '';
                    processReportSetData(reportSetDiv, data);
                },
                error: function (error) {
                    alert('Error getting Report, check that the qoe data service is running and url is correct.');
                }
            });
        };

        var processReportSetData = function (divReportSet, reportSetDef) {
             //show the report set definition like Title, Description, etc
            showReportSetDefinition(divReportSet, reportSetDef);

            //for each Report in the Reportset, get the Report definition from the Repository Service
            for (var i = 0; i < reportSetDef.subItemIds.length; i++)
            {
                //the reportId is in the subItemIds array.  This is not shown in the CQD UI at all
                var reportId = reportSetDef.subItemIds[i];

                var divReport = document.createElement('div');
                divReport.style.margin = '12px';                
                divReportSet.appendChild(divReport);

                //retrieve the report definition with the reportId
                $.ajax({
                    url: urlRepositoryApi + reportId,
                    data: '',
                    type: 'GET',
                    async: false,
                    contentType: 'application/json;charset=utf-8',
                    success: function (reportData) {
                        processReportData(divReport, reportData, reportId);
                    },
                    error: function (error) {
                        alert('Error getting Report ' + reportId.toString() + ', check that the qoe data service is running and url is correct.');
                    }
                });
            }
        };

        //helper function to render the ReportSet definition
        var showReportSetDefinition = function (divReportSet, reportSetDef) {
            var div = document.createElement('div');
            ReportSetDefinition = reportSetDef.content;
            txt = document.createTextNode(ReportSetDefinition);
            div.style.margin = '12px';
            div.appendChild(txt);
            divReportSet.appendChild(div);
        };

        //show the report definition
        var processReportData = function (divReport, reportData, itemId) {
            if (divReport != undefined &amp;&amp; reportData.content != undefined) {
                var Report = JSON.parse(reportData.content);

                var divReportId = document.createElement('div');
                var subItemId = reportData.subItemIds.length > 0 ? reportData.subItemIds[0].toString() : 'none';
                divReportId.innerHTML = 'ItemId: ' + itemId.toString() + ' (' + Report.Title + ') [subItemId:' + subItemId + ']';
                divReport.appendChild(divReportId);

                var divReportDef = document.createElement('div');
                txt = document.createTextNode(JSON.stringify(Report));
                divReportDef.style.margin = '12px';
                divReportDef.appendChild(txt);                            
                divReport.appendChild(divReportDef);
            }
        };
    </script>
</body>
</html>
```

Das obige Ergebnis führt zu einer Webseite wie der in der Abbildung (ohne die Berichtsdefinition bei einem ersten Besuch). Besorgen Sie sich die Berichtssatz-ID vom CQD-Portal (nach "/#/" melden Sie sich CQD Portal-URL an (z.b. in der ersten Abbildung ist die Berichtssatz-ID 3024), und fügen Sie diese Berichtssatz-ID in den Eingabebereich dieser Webseite ein. Drücken Sie die Schaltfläche "Laden", und sehen Sie sich die vollständige Definition (Maße, Maße, Filterlisten) des Berichtssatzes an.

Zusammenfassung, um schnell die vollständige Definition eines Berichts/Berichtssatzes zu erhalten. Führen Sie folgende Schritte aus:

1. Wechseln Sie zum Portal, und verwenden Sie den Abfrage-Editor, um einen Bericht anzupassen (Klicken Sie auf die Schaltfläche "Bearbeiten" oberhalb eines Berichts, um Sie zu bearbeiten, hinzuzufügen, Maße/Dimensionen/Filter zu entfernen und dann den Bericht zu speichern).

2. Rufen Sie die Berichtssatz-ID von URL ab (die Ganzzahl nach '/#/' Anmelde-URL).

3. Starten Sie die Berichtdefinitions-Webseite, die in Beispiel 2 erstellt wurde, geben Sie die Berichtsatzkennung ein und rufen Sie die vollständige Definition eines Berichtsatzes ab (um ihn bei API-Abrufen zu verwenden).

   **Beispiel 3: Beispiel mit einer Scorecard**

Jetzt ist es an der Zeit für eine kompliziertere Aufgabe. Wie gehen wir vor, um eine Webseite wie in der Abbildung zu erstellen? Hierzu müssen wir Beispiel 1 aktualisieren (mithilfe der Webseite aus Beispiel 2, um die vollständige Definition eines beliebigen Berichts abzurufen), damit wir größere Datenmengen bewältigen können.

In diesem Fall müssen wir die Liste der Messwerte und Dimensionen aktualisieren. Um einen Messwert und/oder eine Dimension hinzuzufügen oder zu bearbeiten, folgen Sie den Anweisungen aus Beispiel 2 und rufen Sie die vollständige Berichtdefinition (einschließlich der vollständigen Listen für Messwerte und Dimensionen) ab. Fügen Sie die vollständige Berichtdefinition in den Beispielcode ein. 

Im Folgenden erhalten Sie detaillierte Anweisungen zum Abruf der Scorecard-Seite in der Abbildung mit den Daten aus Beispiel 1:

1. Aktualisieren Sie die Maße in der Abfragevariablen von `[Measures].[Audio Good Streams JPDR Count]` und `[Measures].[Audio Poor Streams JPDR Count]` bis `[Measures].[AudioPoorJPDRPercentage]`. 

2. Aktualisieren Sie die Filter. Die JSON-Daten für Filter in Beispiel 1 verfügen über einen Filter, der für die Dimension `[StartDate].[Month]`gesetzt ist. Da Filter JSON-Arrays sind, können zur Liste der Filter weitere Dimensionen hinzugefügt werden. Wenn Sie beispielsweise den Server-Client in Wired-anrufen für das "currentMonth" abrufen möchten, sollten die folgenden Filter vorhanden sein:

   ```javascript
   Filters: [
     { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
    {
        "DataModelName": "[Scenarios].[ScenarioPair]",
         "Caption": " Server-Inside-wired,Client-Inside-wired",
         "Value": "[1]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]",
         "Operand": 0,
         "UnionGroup": ""
     },

     { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
   ],
   ```

   Hier wird die `[Scenarios].[ScenarioPair]` Dimension auf "gleich `[1]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]`" gesetzt. Das `[Scenario.][ScenarioPair]` ist eine spezielle Dimension, die zur Vereinfachung der Berichterstellung erstellt wurde. Sie hat sechs Werte, die `[FirstIsServer], [SecondIsServer], [FirstInside], [SecondIsServer], [FirstConnectionType], [SecondConnectionType]`dem entsprechen. Um ein Szenario definieren zu können, brauchen wir also anstelle einer Kombination von 6 Filtern nur 1 Filter. In unserem Beispiel wird der Wert `[1]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]` in das Szenario übersetzt, in dem: First ist Server, zweiter ist kein Server, zunächst innerhalb, zweite befindet sich innerhalb, erster Verbindungstyp ist verkabelt, und zweiter Verbindungstyp ist verkabelt, was die exakte Definition von "Server-Client-Inside Wired" ist.

3. Erstellen Sie einen einzelnen Filtersatz pro Szenario. In der Abbildung steht jede Zeile in der Scorecard für ein anderes Szenario, das wiederum für einen anderen Filter steht (während Dimensionen und Messwerte gleich bleiben). 

4. Analysieren Sie die Ergebnisse aus den AJAX-Abrufen und fügen Sie sie an der richtigen Stelle in der Tabelle ein. Da es sich hierbei in der Hauptsache um eine HTML- und JavaScript-Manipulation handelt, gehen wir nicht im Detail darauf ein. Den Code finden Sie in Anhang A.

    > [!NOTE]
    >  Wenn die übergreifende Ressourcenfreigabe (CORS) aktiviert ist, treten möglicherweise Fehler auf, wie die Kopfzeile "keine Zugriffssteuerung-Allow-Origin" für die angeforderte Ressource vorhanden ist. Der Ursprung "Null" ist daher nicht zulässig. " Um das Problem zu beheben, platzieren Sie die HTML-Datei unter dem Ordner, in dem das Portal installiert ist (Standard `%SystemDrive%\Program Files\Skype for Business 2015 CQD\CQD)`mäßig sollte dies der Fall sein. Greifen Sie dann über einen beliebigen Browser mit der URL `http://<servername>/cqd/<html_file_name>`auf den HTML-Code zu. (Die Standard-URL für lokales CQD- `http://<servername>/cqd.`Dashboard ist) 

### <a name="appendix-a"></a>Anhang A

HTML-Code für Beispiel 3 (Scorecard-Beispiel):

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <meta http-equiv='cache-control' content='no-cache'>
    <meta http-equiv='expires' content='0'>
    <meta http-equiv='pragma' content='no-cache'>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Scoreboard Sample</title>

    <style>
        .row {
            margin-right: -15px;
            margin-left: -15px;
            display: table-row;
        }
        .col-md-3 {
            width: 25%;
            display: table-cell;
        }
        .col-md-2 {
            width: 16.66666667%;
            display: table-cell;
        }
        .col-md-1 {
            width: 8.33333333%;
            display: table-cell;
        }

    </style>
</head>
<body>    

    <!-- Third party Libraries -->
    <script src="OpenSourceSoftware/Scripts/jquery-2.1.1.js"></script>

    <table id="ScoreCardTable" style="margin:100px">
        <tr>
            <td width="250px" style="text-align: center; font-size: 24px; font-family: 'Segoe UI'; font-weight: lighter; color: white; background-color: #505050">
                <div style="margin:10px">Scoreboard Sample</div>
            </td>
            <td width="1200px">
                <div style="margin:10px;background-color:#D9D9D9" >
                    <div class="row" id="Header" style="font-size:24px;font-family:'Segoe UI';font-weight:lighter;color:white;background-color:#505050">
                        <div class="col-md-3">Poor Call %</div>
                        <div class="col-md-1">Month1</div>
                        <div class="col-md-1">Month2</div>
                        <div class="col-md-1">Month3</div>
                        <div class="col-md-1">Month4</div>
                        <div class="col-md-1">Month5</div>
                        <div class="col-md-1">Month6</div>
                    </div>                    
                    <div class="row"><div class="col-md-3" style="font-weight:bold">Wired</div></div>
                    <div class="row" id="SS"><div class="col-md-3">Server-Server</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="SWI"><div class="col-md-3">Server-Client (inside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="SWO"><div class="col-md-3">Server-Client (outside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="WWI"><div class="col-md-3">Client-Client (inside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="WIWO"><div class="col-md-3">Client-Client (outside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row"><div class="col-md-3" style="font-weight:bold">Wireless</div></div>
                    <div class="row" id="SWFI"><div class="col-md-3">Server-Client (inside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="SWFO"><div class="col-md-3">Server-Client (outside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="WFIWFI"><div class="col-md-3">Client-Client (inside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="WFOWFO"><div class="col-md-3">Client-Client (outside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row"><div class="col-md-3" style="font-weight:bold">Mobile/Broadband</div></div>
                    <div class="row" id="SMP"><div class="col-md-3">Server-MobilePhone</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row" id="SMBB"><div class="col-md-3">Server-MobileBroadBand</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                    <div class="row"><div class="col-md-3" style="font-weight:bold">Lync Web App</div></div>
                    <div class="row" id="SLWA"><div class="col-md-3">Server-Client (inside &amp; outside)</div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div><div class="col-md-1"></div></div>
                </div>
            </td>
        </tr>
        <tr>
            <td><br /></td>
        </tr>
    </table>

    <script>

        $(function () {
            var month_names_short = ['NAM', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
            var currentMonth = '2015-3';

            //update the header with the month names
            var row = document.getElementById('Header');
            var numMonthsToShow = 6;
            for (var m = numMonthsToShow-1; m >= 0; m--) {
                var dateSplit = currentMonth.split('-');
                var monthInt = parseInt(dateSplit[1]);
                var yearInt = parseInt(dateSplit[0]);
                monthInt = monthInt - m;
                if (monthInt < 1)
                {
                    monthInt += 12;
                    yearInt--;
                }
                row.children[numMonthsToShow-m].innerHTML = month_names_short[monthInt];
            }

            var queries = [
            {
                Label: "Server-Server",
                ID: "SS",
                Query:
                {
                  Dimensions: [{ DataModelName: '[StartDate].[Month]'}],
                  Filters: [
                      {
                          "DataModelName": "[Scenarios].[ScenarioPair]",
                          "Caption": " Server-Inside-wired,Server-Inside-wired",
                          "Value": "[1]&amp;[1]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]",
                          "Operand": 0,
                          "UnionGroup": ""
                      },
                      { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                      { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: ""}
                  ],
                  Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]'}],
                  Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                 }
            },
            {
                Label: "Server-Client (inside)",
                ID: "SWI",
                Query:
                {
                  Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                  Filters: [
                      {
                          "DataModelName": "[Scenarios].[ScenarioPair]",
                          "Caption": " Server-Inside-wired,Client-Inside-wired",
                          "Value": "[1]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]",
                          "Operand": 0,
                          "UnionGroup": ""
                      },
                      { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                      { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                  ],
                  Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                  Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-Client (outside)",
                ID: "SWO",
                Query:
                {
                  Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                  Filters: [
                      {
                          "DataModelName": "[Scenarios].[ScenarioPair]",
                          "Caption": " Server-Inside-wired,Client-Outside-wired",
                          "Value": "[1]&amp;[0]&amp;[1]&amp;[0]&amp;[Wired]&amp;[Wired]",
                          "Operand": 0,
                          "UnionGroup": ""
                      },
                      { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                      { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                  ],
                  Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                  Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                 }
            },
            {
                Label: "Client-Client (inside)",
                ID: "WWI",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {
                            "DataModelName": "[Scenarios].[ScenarioPair]",
                            "Caption": " Client-Inside-wired,Client-Inside-wired",
                            "Value": "[0]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wired]",
                            "Operand": 0,
                            "UnionGroup": ""
                        },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            }
            ,
            {
                Label: "Client-Client (outside)",
                ID: "WIWO",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {
                          "DataModelName": "[Scenarios].[ScenarioPair]",
                          "Caption": "Client-Outside-Wired,Client-Outside-Wired",
                          "Value": "[0]&amp;[0]&amp;[0]&amp;[0]&amp;[Wired]&amp;[Wired]",
                          "Operand": 0,
                          "UnionGroup": ""
                        },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-Client (inside)",
                ID: "SWFI",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {
                            "DataModelName": "[Scenarios].[ScenarioPair]",
                            "Caption": " Server-Inside-wired,Client-Inside-wifi",
                            "Value": "[1]&amp;[0]&amp;[1]&amp;[1]&amp;[Wired]&amp;[Wifi]",
                            "Operand": 0,
                            "UnionGroup": ""
                        },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-Client (outside)",
                ID: "SWFO",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                         {
                             "DataModelName": "[Scenarios].[ScenarioPair]",
                             "Caption": " Server-Inside-wired,Client-Outside-wifi",
                             "Value": "[1]&amp;[0]&amp;[1]&amp;[0]&amp;[Wired]&amp;[Wifi]",
                             "Operand": 0,
                             "UnionGroup": ""
                         },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Client-Client (inside)",
                ID: "WFIWFI",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {
                            "DataModelName": "[Scenarios].[ScenarioPair]",
                            "Caption": " Client-Inside-Wifi,Client-Inside-Wifi",
                            "Value": "[0]&amp;[0]&amp;[1]&amp;[1]&amp;[Wifi]&amp;[Wifi]",
                            "Operand": 0,
                            "UnionGroup": ""
                        },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Client-Client (outside)",
                ID: "WFOWFO",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {
                          "DataModelName": "[Scenarios].[ScenarioPair]",
                          "Caption": "Client-Outside-Wifi,Client-Outside-Wifi",
                          "Value": "[0]&amp;[0]&amp;[0]&amp;[0]&amp;[Wifi]&amp;[Wifi]",
                          "Operand": 0,
                          "UnionGroup": ""
                        },
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                        { DataModelName: '[StreamType].[StreamType]', Caption: "Valid", Value: "[False]", Operand: 0, UnionGroup: "" }
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-MobilePhone",
                ID: "SMP",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {"DataModelName": "[First Is Server].[Agent]","Caption": "Server","Value": "[1]","Operand": 0,"UnionGroup": ""},
                        {"DataModelName": "[Second User Agent].[User Agent Type]","Caption": "AndroidLync | iPhoneLync | WPLync","Value": "[AndroidLync],[iPhoneLync],[WPLync]","Operand": 0,"UnionGroup": ""},
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 },
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-MobileBroadBand",
                ID: "SMBB",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {"DataModelName": "[Second Network Connection Type].[Network Connection Detail]","Caption": "MobileBB","Value": "[MobileBB]","Operand": 0,"UnionGroup": ""},
                        {"DataModelName": "[First Is Server].[Agent]","Caption": "Server","Value": "[1]","Operand": 0,"UnionGroup": ""},
                        {"DataModelName": "[Second Is Server].[Agent]","Caption": "Client ","Value": "[0]","Operand": 0,"UnionGroup": ""},
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 }                       
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            },
            {
                Label: "Server-LWA",
                ID: "SLWA",
                Query:
                {
                    Dimensions: [{ DataModelName: '[StartDate].[Month]' }],
                    Filters: [
                        {"DataModelName": "[First Is Server].[Agent]","Caption": "Server","Value": "[1]","Operand": 0,"UnionGroup": ""},
                        {"DataModelName": "[Second User Agent].[User Agent Type]","Caption": "LWA","Value": "[LWA]","Operand": 0,"UnionGroup": ""},
                        { DataModelName: '[StartDate].[Month]', Value: currentMonth, Operand: 0 }                       
                    ],
                    Measurements: [{ DataModelName: '[Measures].[AudioPoorJPDRPercentage]' }],
                    Trend: { EnableTrend: true, SpanCount: numMonthsToShow, TrendDate: currentMonth, Type: 0 }
                }
            }

            ];

            //get the overall corpnet data
            for (var i = 0; i < queries.length; i++) {
                $.ajax({

                    url: 'http://localhost/QoEDataService/RunQuery',
                    data: JSON.stringify(queries[i].Query),
                    type: 'POST',
                    async: false,
                    withCredentials: true,
                    contentType: 'application/json;charset=utf-8',
                    success: function (data) {

                        //find the table row corresponding to the name of this query
                        var row = document.getElementById(queries[i].ID);

                        //update the values for each month
                        for (var m = 0; m < data.DataResult.length; m++)
                        {
                            row.children[m + 1].innerHTML = data.DataResult[m][1].toFixed(2).toString();
                        }

                    },
                    error: function (error) {
                        var row = document.getElementById(queries[i].ID);
                        row.children[1].innerHTML = 'error';
                    }
                });
            }
        });
    </script>
</body>
</html>
```
