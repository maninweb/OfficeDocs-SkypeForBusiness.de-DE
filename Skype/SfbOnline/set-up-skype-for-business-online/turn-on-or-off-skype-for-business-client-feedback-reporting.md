---
title: Aktivieren oder Deaktivieren von Feedbackberichten im Skype for Business-Client
ms.reviewer: ''
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 35562b48-1da1-4081-8a3a-033d0f1986b2
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1.keywords:
- NOCSH
ms.custom:
- Setup
description: Sie können Ihre Skype for Business-Benutzer in die Lage versetzen, das integrierte Skype for Business-App-Feedback Tool zu verwenden, um Benutzern die Möglichkeit zu geben, Probleme zu melden und Microsoft über ihre Erfahrungen direkt Feedback zu geben.
ms.openlocfilehash: 3b91bc88c20450b7c0d9c5705bceec53af5f9edb
ms.sourcegitcommit: 1a31ff16b8218d30059f15c787e157d06260666f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47814184"
---
# <a name="turn-on-or-off-skype-for-business-client-feedback-reporting"></a>Aktivieren oder Deaktivieren von Feedbackberichten im Skype for Business-Client

Sie können Ihre Skype for Business Online-Benutzer in die Lage versetzen, das integrierte Skype for Business-App-Feedback Tool zu verwenden, um Benutzern zu ermöglichen, Probleme zu melden und Microsoft über ihre Erfahrungen direkt Feedback zu geben. 
  
![Skype for Business client reporting.](../images/eac13837-04d9-4da1-8e80-54612cf6650d.png)
  
Mit diesem Tool können Benutzer die Protokolle aus der APP auf Ihrem Gerät kopieren, um Microsoft bei der Untersuchung und Behebung von Problemen zu helfen, die Sie möglicherweise haben. 
  
![Skype for Business client reporting.](../images/2dfb5603-1d69-41fc-a43e-91a3379acbe0.png)
  
Sie können auch die Einstellung  _EnableOnlineFeedbackScreenshot_ verwenden, damit Benutzer zusammen mit dem Feedback einen Screenshot von ihrem Gerät senden können.
  
![Skype for Business client reporting form.](../images/d859578d-8116-4d4b-a08f-c0cae28b8b76.png)
  
> [!IMPORTANT]
> Die vom Feedback Tool der APP gesammelten Protokolle werden für maximal 90 Tage in den Vereinigten Staaten gespeichert, während das Problem untersucht wird. Aktivieren Sie daher das Feedbacktool nicht, wenn dies einen Verstoß gegen die Datenschutzrichtlinien Ihrer Organisation darstellt. 
  
## <a name="verify-and-start-windows-powershell"></a>Überprüfen und Starten von Windows PowerShell

- **Überprüfen, ob Windows PowerShell 3.0 oder höher ausgeführt wird**
    
1. Zur Überprüfung ob Sie Version 3.0 oder höher verwenden: **Start Menu** > **Windows PowerShell**.
    
2. Überprüfen Sie die Version, indem Sie im Fenster _Windows PowerShell_ die Zeichenfolge **Get-Host** eingeben.
    
3. Wenn Sie nicht über Version 3.0 oder eine höhere Version verfügen, müssen Sie Updates für Windows PowerShell herunterladen und installieren. Informationen zum herunterladen und Aktualisieren von Windows PowerShell auf Version 4,0 finden Sie unter [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkId=716845) . Starten Sie Ihren Computer neu, wenn Sie dazu aufgefordert werden.
    
4. Außerdem müssen Sie das Windows PowerShell-Modul für Teams installieren, mit dem Sie eine Windows PowerShell-Remotesitzung erstellen können, die eine Verbindung mit Skype for Business Online herstellt. 
    
Wenn Sie weitere Informationen benötigen, lesen Sie [Herstellen einer Verbindung mit allen Microsoft 365-oder Office 365-Diensten in einem einzigen Windows PowerShell-Fenster](https://technet.microsoft.com/library/dn568015.aspx).
    
- **Starten einer Windows PowerShell-Sitzung**
    
1. Vom **Start Menu** > **Windows PowerShell**.
    
2. Stellen Sie im **Windows PowerShell** -Fenster eine Verbindung mit Ihrem Microsoft 365 oder Office 365 her, indem Sie Folgendes ausführen:
    
  > [!NOTE]
  > Skype for Business Online Connector ist derzeit Teil des neuesten Teams PowerShell-Moduls.
  >
  > Wenn Sie die neueste Version von [Teams PowerShell](https://www.powershellgallery.com/packages/MicrosoftTeams/)verwenden, müssen Sie den Skype for Business Online-Connector nicht installieren.
 
   ```PowerShell
   Import-Module -Name MicrosoftTeams
    $credential = Get-Credential
    $session = New-CsOnlineSession -Credential $credential
    Import-PSSession $session
   ```
   Wenn Sie weitere Informationen zum Starten von Windows PowerShell benötigen, lesen Sie [Herstellen einer Verbindung mit allen Microsoft 365-oder Office 365-Diensten in einem einzelnen Windows PowerShell-Fenster](https://technet.microsoft.com/library/dn568015.aspx) oder[Einrichten Ihres Computers für Windows PowerShell](../set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md).
    
## <a name="turn-on-client-app-feedback-reporting-for-all-the-users-in-your-organization"></a>Aktivieren von Feedbackberichten in der Client-App für alle Benutzer in Ihrer Organisation

Führen Sie die folgenden Anweisungen aus, um feedbackberichte für Benutzer in Ihrer Organisation zu aktivieren und zu ermöglichen, Geräte Screenshots zu senden:
 
  ```PowerShell
  Set-CsClientPolicy -Identity EnableOnlineFeedback -EnableOnlineFeedback $true -EnableOnlineFeedbackScreenshots $true
  ```
## <a name="want-to-know-more-about-windows-powershell"></a>Möchten Sie mehr über Windows PowerShell erfahren?
- Bei Windows PowerShell dreht sich alles um das Verwalten von Benutzern und Funktionen, die Benutzer verwenden oder nicht verwenden können. Mit Windows PowerShell können Sie Microsoft 365 oder Office 365 und Skype for Business Online mit einem zentralen Verwaltungspunkt verwalten, der Ihre tägliche Arbeit vereinfachen kann, wenn mehrere Aufgaben ausgeführt werden müssen. Informieren Sie sich in den folgenden Artikeln über die Verwendung von Windows PowerShell:
    
  - [Einführung in Windows PowerShell und Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Sechs Gründe für die Verwendung von Windows PowerShell zum Verwalten von Microsoft 365 oder Office 365](https://go.microsoft.com/fwlink/?LinkId=525041)
    
- Windows PowerShell bietet zahlreiche Vorteile in Geschwindigkeit, Einfachheit und Produktivität, wenn Sie nur das Microsoft 365 Admin Center verwenden, beispielsweise wenn Sie für viele Benutzer gleichzeitig Einstellungsänderungen vornehmen. Informationen zu diesen Vorteilen finden Sie unter den folgenden Themen:
    
  - [Beste Möglichkeiten zum Verwalten von Microsoft 365 oder Office 365 mit Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  - [Verwenden von Windows PowerShell zum Verwalten von Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Verwenden von Windows PowerShell für die Durchführung gängiger Verwaltungsaufgaben von Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525038)

## <a name="related-topics"></a>Verwandte Themen
[Einrichten von Skype for Business Online](set-up-skype-for-business-online.md)

[Zulassen, dass Skype for Business-Benutzer Skype-Kontakte hinzufügen](let-skype-for-business-users-add-skype-contacts.md)

  
 
