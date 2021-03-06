---
title: Konfigurieren von Einwahlkonferenzen in Skype for Business Server
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: 38d9f168-80b8-46f2-a1c0-becd84e58e73
description: 'Zusammenfassung: Lesen Sie dieses Thema, um zu erfahren, wie Sie Einwahlkonferenzen in Skype for Business Server konfigurieren.'
ms.openlocfilehash: 4e8523cbaadfc13b985cf33e06e68fcd5d209c89
ms.sourcegitcommit: dd3a3ab4ddbdcfe772f30fb01ba3b97c45c43dd4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "41768528"
---
# <a name="configure-dial-in-conferencing-in-skype-for-business-server"></a>Konfigurieren von Einwahlkonferenzen in Skype for Business Server
 
**Zusammenfassung:** In diesem Thema erfahren Sie, wie Sie Einwahlkonferenzen in Skype for Business Server konfigurieren.
  
Nachdem Sie eine Topologie erstellt haben, die die Konferenz Arbeitsauslastung und ausgewählte Einwahlkonferenzen umfasst, müssen Sie zusätzliche Schritte ausführen, um Einwahlkonferenzen zu konfigurieren. Bevor Sie dieses Thema lesen, stellen Sie sicher, dass Sie den [Plan für Einwahlkonferenzen in Skype for Business Server](../../plan-your-deployment/conferencing/dial-in-conferencing.md), [Hardware-und Softwareanforderungen für Konferenzen in Skype for Business Server](../../plan-your-deployment/conferencing/hardware-and-software-requirements.md)und das [Bereitstellungs Flussdiagramm und die Checkliste für Einwahlkonferenzen](deploy-conferencing.md#deployment-flowchart-and-checklist-for-dial-in-conferencing)gelesen haben. 
  
Zum Konfigurieren von Einwahlkonferenzen müssen Sie die folgenden Aufgaben ausführen:
  
- [Configure dial plans](dial-in-conferencing.md#BKMK_ConfigureDialPlans)
    
- [Configure dial-in conferencing regions](dial-in-conferencing.md#BKMK_ConfigureDialInRegions)
    
- [Configure dial-in access numbers](dial-in-conferencing.md#BKMK_ConfigureDialInAccessNumbers)
    
- [Configure conferencing policies](dial-in-conferencing.md#BKMK_ConfigureConferencingPolicies)
    
- [Assign a Line URI to a user account](dial-in-conferencing.md#BKMK_AssignaLineURI)
    
Zusätzlich können Sie die folgenden optionalen Aufgaben ausführen. Weitere Informationen zu diesen optionalen Aufgaben finden Sie unter [Verwalten von Einwahlkonferenzen in Skype for Business Server](../../manage/conferencing/dial-in-conferencing.md).
  
- Verwalten von PIN-Richtlinien für Einwahlkonferenzen
    
- Verwalten der Tastenzuordnung für DTMF-Befehle
    
- Erstellen von Konferenzverzeichnissen
    
- Verwalten der Ankündigungen beim Beitreten oder Verlassen einer Konferenz
    
- Testen der Einwahlkonferenzeinstellungen
    
- Senden einer Begrüßungs-E-Mail an die Einwahlbenutzer
    
## <a name="configure-dial-plans"></a>Konfigurieren von Wähleinstellungen
<a name="BKMK_ConfigureDialPlans"> </a>

Bei der Bereitstellung von Einwahlkonferenzen müssen Sie einen oder mehrere Sätze mit Wähleinstellungen zum Routen von Zugriffsnummern für die Einwahl erstellen oder ändern. Darüber hinaus müssen Sie sicherstellen, dass jeder Wählplan mindestens eine Normalisierungsregel enthält – eine Regel, die Telefonerweiterungen in vollständige Telefonnummern im E. 164-Format umwandelt. 
  
Benutzer von Einwahlkonferenzen nehmen an Konferenzen als authentifizierte Unternehmensbenutzer teil, indem sie ihre PIN und die Telefonnummer eingeben. Sie benötigen eine Normalisierungsregel zum Konvertieren von Durchwahlen in vollständige Rufnummern, damit Benutzer bei Eingabe einer Durchwahl authentifiziert werden können.
  
So richten Sie Wähleinstellungen für Einwahlkonferenzen ein:
  
- Unabhängig davon, ob Sie Enterprise-VoIP bereitstellen oder nicht, fügen Sie zu den Wähleinstellungen eine Region für Einwahlkonferenzen hinzu und stellen Sie sicher, dass Ihre Einwahlnummern einwandfrei von einer Normalisierungsregel umgewandelt werden. Ausführliche Anweisungen finden Sie unter [erstellen oder Ändern eines Wählplans in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
- Wenn Sie Enterprise-VoIP nicht bereitstellen, erstellen Sie Wählpläne für Ihre Einwahlnummern. Fügen Sie auf jeden Fall eine Region für Einwahlkonferenzen hinzu. Ausführliche Anweisungen finden Sie unter [erstellen oder Ändern eines Wählplans in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
- Wenn Sie Enterprise-VoIP bereitgestellt haben, ändern Sie Enterprise-sprach Wählpläne nach Bedarf, um Regionen einzubeziehen und geeignete Normalisierungsregeln für Einwahl Zugriffsnummern zu verwenden. Sie können auch dedizierte Wählpläne erstellen, die nur für Einwahl Zugriffsnummern verwendet werden. Ausführliche Anweisungen finden Sie unter [erstellen oder Ändern eines Wählplans in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
    
Details zum Erstellen von Normalisierungsregeln finden Sie unter [erstellen oder Ändern einer Normalisierungsregel in Skype for Business](../../deploy/deploy-enterprise-voice/normalization-rules.md).
  
## <a name="configure-dial-in-conferencing-regions"></a>Konfigurieren von Einwahlkonferenzregionen
<a name="BKMK_ConfigureDialInRegions"> </a>

Wenn Sie einen Satz mit Wähleinstellungen einrichten, geben Sie die Region für Einwahlkonferenzen an, die für diese Wähleinstellungen gilt. Die Einwahlkonferenzregion ordnet den Einwahlkonferenznummern die entsprechenden Wähleinstellungen zu. Wenn Sie anschließend die Zugriffsnummern für Einwahlkonferenzen erstellen, wählen Sie die Regionen aus, welche die Zugriffsnummern den geeigneten Wähleinstellungen zuordnen. 
  
Da es wichtig ist, eine Region für alle Wähleinstellungen anzugeben, wird empfohlen, das Vorhandensein von Konferenzregionen für alle Wähleinstellungen zu überprüfen. 
  
Verwenden Sie das Cmdlet **Get-CsDialPlan**, um zu überprüfen, ob die Region für alle Wählpläne für Einwahlkonferenzen festgelegt wurde. Wenn die Region in bestimmten Wählplänen nicht vorhanden ist, können Sie die Region über das Cmdlet **Set-CsDialPlan** festlegen. Sie können die Region auch in vorhandenen Wählplänen mit der Skype for Business Server-Systemsteuerung aktualisieren. Ausführliche Informationen zur Verwendung der Skype for Business Server-Systemsteuerung finden Sie unter [erstellen oder Ändern eines Wählplans in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
  
### <a name="to-verify-whether-dial-plans-have-the-region-property-set"></a>So überprüfen Sie, ob für Wähleinstellungen die Region festgelegt wurde

1. Melden Sie sich beim Computer als Mitglied der Gruppe „RTCUniversalServerAdmins“ oder als Benutzer mit der Rolle **Cs-VoiceAdministrator**, **Cs-ServerAdministrator** oder **CsAdministrator** an.
    
2. Starten Sie die Skype for Business Server-Verwaltungsshell: Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme** und dann auf **Skype for Business 2015** und klicken Sie anschließend auf **Skype for Business Server-Verwaltungsshell**.
    
3. Führen Sie den folgenden Befehl an der Eingabeaufforderung aus:
    
   ```powershell
   Get-CsDialPlan [-Identity <Identifier of the dial plans to be retrieved>]
   ```

   Beispiel:
    
   ```powershell
   Get-CsDialPlan
   ```

   In diesem Beispiel werden alle für Ihre Organisation konfigurierten Wähleinstellungen zurückgegeben.
    
4. Überprüfen Sie die zurückgegebenen Wähleinstellungen, um fehlende Regionen für Einwahlkonferenzen zu ermitteln. 
    
Weitere Informationen finden Sie unter [Get-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/get-csdialplan?view=skype-ps).
  
### <a name="to-set-the-region-property-for-a-dial-plan"></a>So legen Sie die Region für einen Satz mit Wähleinstellungen fest

1. Melden Sie sich beim Computer als Mitglied der Gruppe „RTCUniversalServerAdmins“ oder als Benutzer mit der Rolle **Cs-VoiceAdministrator**, **Cs-ServerAdministrator** oder **CsAdministrator** an.
    
2. Starten Sie die Skype for Business Server-Verwaltungsshell: Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme** und dann auf **Skype for Business 2015** und klicken Sie anschließend auf **Skype for Business Server-Verwaltungsshell**.
    
3. Führen Sie für alle Wähleinstellungen, in denen die Region für Einwahlkonferenzen fehlt, den folgenden Befehl aus:
    
   ```powershell
   Set-CsDialPlan [-Identity <Identity of the dial plan to be modified>] -DialinConferencingRegion "<new region>"
   ```

   Beispiel:
    
   ```powershell
   Set-CsDialPlan -Identity Redmond -DialinConferencingRegion "US West Coast"
   ```

   In diesem Beispiel wird die Eigenschaft "DialinConferencingRegion" in den Wähleinstellungen mit der Identität "Redmond" in den Wert "US West Coast" geändert. 
    
Weitere Informationen finden Sie unter [Satz-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/set-csdialplan?view=skype-ps).
  
## <a name="configure-dial-in-access-numbers"></a>Konfigurieren von Zugriffsnummern für die Einwahl
<a name="BKMK_ConfigureDialInAccessNumbers"> </a>

Beim Bereitstellen von Einwahlkonferenzen müssen Sie Telefonnummern einrichten, die Benutzer aus dem Telefonfestnetz (Public Switched Telephone Network, PSTN) wählen können, um am Audioteil einer Konferenz teilzunehmen. Diese Zugriffsnummern für die Einwahl werden in Besprechungseinladungen und auf der Webseite mit den Einstellungen für Einwahlkonferenzen angezeigt.
  
Vor dem Erstellen von Zugriffsnummern für die Einwahl müssen Sie zunächst die Regionen Ihrer Einwahlkonferenzen planen und anschließend Wählpläne für die Regionen konfigurieren. Details zu Regionen finden Sie unter [Planen von Einwahlkonferenzen in Skype for Business Server](../../plan-your-deployment/conferencing/dial-in-conferencing.md). Details zum Konfigurieren von Wählplänen für Einwahlkonferenzen finden Sie unter [erstellen oder Ändern eines Wählplans in Skype for Business Server](../../deploy/deploy-enterprise-voice/dial-plans.md).
  
> [!NOTE]
> Sie können eine neue Zugriffsnummer erst dann für Einwahlkonferenzen verwenden, wenn die Replikation der Active Directory-Domänendienste (AD DS) für diese Zugriffsnummer abgeschlossen ist. Die Replikation kann mehrere Stunden in Anspruch nehmen. 
  
> [!NOTE]
> Nach dem Erstellen von Zugriffsnummern für die Einwahl können Sie den Anzeigenamen für die Active Directory-Kontaktobjekte modifizieren, sodass Benutzer die richtige Zugriffsnummer einfacher identifizieren können. Wenn Sie den Anzeigenamen ändern möchten, verwenden Sie das Cmdlet " [Satz-CsDialInConferencingAccessNumber](https://docs.microsoft.com/powershell/module/skype/set-csdialinconferencingaccessnumber?view=skype-ps) ". Active Directory-Objekte sollten nicht manuell geändert werden.
  
### <a name="to-create-a-dial-in-access-number"></a>So erstellen Sie eine Einwahlnummer

1. Melden Sie sich mit einem Benutzerkonto, dem die Rolle "CsUserAdministrator" oder "CsAdministrator" zugewiesen ist, auf einem beliebigen Computer in Ihrer internen Bereitstellung an.
    
2. Öffnen Sie die Skype for Business Server-Systemsteuerung.
    
3. Klicken Sie in der linken Navigationsleiste auf **Konferenz** und dann auf **Einwahlnummer**.
    
4. Führen Sie auf der Seite **Einwahlnummer** einen der folgenden Schritte aus:
    
   - Klicken Sie auf **Neu**, um **Neue Einwahlnummer** zu öffnen.
    
   - Klicken Sie auf eine der Einwahlnummern in der Liste, klicken Sie auf **Bearbeiten** und anschließend auf **Details anzeigen**.
    
     > [!NOTE]
     > Die Suche nach den Inhalten einer Spalte in der Liste der Zugriffsnummern für die Einwahl über das Suchfeld führt möglicherweise nicht zu den erwarteten Ergebnissen. Sortieren Sie die Liste stattdessen nach der gewünschten Spalte, um nach der Zugriffsnummer für die Einwahl zu suchen, die Sie anzeigen oder ändern möchten. 
  
5. Geben Sie im Feld **Anzeigenummer** die Telefonnummer ein, die PSTN-Telefonbenutzer (Public Switched Telephone Network, Telefonfestnetz) wählen, um an einer Konferenz teilzunehmen. Diese Nummer wird in Besprechungseinladungen und auf der Webseite mit den Einstellungen für die Einwahlkonferenz angezeigt.
    
6. Geben Sie in **Anzeigename** eine Beschreibung für die Zugriffsnummer für die Einwahl ein. Dies ist der Name, der der Einwahl Zugriffsnummer in den Suchergebnissen von Skype for Business zugeordnet ist. Der Name wird im Client angezeigt, wenn ein Benutzer die Einwahlnummer wählt. 
    
7. Geben Sie im Feld **Anschluss-URI** die E.164-Nummer der Zugriffsnummer für die Einwahl im TEL-URI-Format ein, einschließlich des +-Symbols vor der Nummer und ohne Leerzeichen. Beispiel: tel:+14255550200.
    
    > [!NOTE]
    > Dieser Anschluss-URI kann nicht für eine andere Einwahlnummer für Einwahlkonferenzen verwendet werden. 
  
8. Führen Sie unter **SIP-URI** die folgenden Aktionen aus:
    
   - Geben Sie in das Textfeld einen eindeutigen SIP-URI für diese Zugriffsnummer für Einwahlkonferenzen ein. Dieser SIP-URI wird an verschiedenen Speicherorten angezeigt, einschließlich, aber nicht ausschließlich, von Benachrichtigungsnachrichten und früheren Versionen von lync-Clients.
    
     > [!NOTE]
     > Dieser SIP-URI kann nicht für eine andere Zugriffsnummer für Einwahlkonferenzen verwendet werden. Der SIP-URI kann nach der Erstellung der Zugriffsnummer nicht geändert werden. Die einzige Möglichkeit zum Ändern des SIP-URI besteht darin, die Zugriffsnummer zu löschen und neu zu erstellen. 
  
   - Klicken Sie im Dropdown-Listenfeld auf die Domäne der Conferencing Attendant-Anwendung, die diese Einwahl Zugriffsnummer unterstützt.
    
9. Klicken Sie unter **Pool** auf den Pool, der die Instanz der Konferenzzentrale ausführt, die diese Einwahlnummer unterstützt.
    
    > [!NOTE]
    > Wenn der Pool nach dem Erstellen der Zugriffsnummer geändert werden muss, müssen Sie das Cmdlet [Move-CsApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/move-csapplicationendpoint?view=skype-ps) verwenden oder die Zugriffsnummer löschen und neu erstellen.
  
10. Klicken Sie unter **Primäre Sprache** auf die Sprache, in der Ansagen für diese Einwahlnummer wiedergegeben werden. 
    
    Bei der primären Sprache handelt es sich um die Sprache, die die Konferenzzentrale zum Beantworten des Anrufs verwendet. Die unterstützten Sprachen werden auf der Webseite mit den Einstellungen für die Einwahlkonferenz neben den verschiedenen Zugriffsnummern angezeigt.
    
11. (Optional) Klicken Sie unter **Sekundäre Sprachen (maximal vier)** auf **Hinzufügen**, wählen Sie eine oder mehrere zusätzliche Sprachen aus, die für Anrufer dieser Zugriffsnummer für die Einwahl unterstützt werden sollen, und klicken Sie dann auf **OK**. 
    
    Sie können für jede Zugriffsnummer für die Einwahl bis zu vier sekundäre Sprachen auswählen. Benutzer können beim Einwählen in eine Konferenz eine sekundäre Sprache auswählen, bevor sie die Konferenz-ID eingeben.
    
12. Wenn Sie einen Bereich für die Einwahl Zugriffsnummer hinzufügen möchten, klicken Sie unter **zugeordnete Regionen**auf **Hinzufügen**, klicken Sie auf eine oder mehrere Regionen, die den Wählplänen für diese Einwahl Zugriffsnummer zugeordnet sind, und klicken Sie dann auf **OK**.
    
13. Zum Löschen einer Region aus der Einwahlnummer klicken Sie unter **Zugeordnete Regionen** auf die zu löschende Region und anschließend auf **Entfernen**.
    
14. Klicken Sie auf **Commit ausführen**.
    
## <a name="configure-conferencing-policies"></a>Konfigurieren von Konferenzrichtlinien
<a name="BKMK_ConfigureConferencingPolicies"> </a>

Die Konferenzrichtlinie ist eine Benutzerkontoeinstellung, die die Konferenzmöglichkeiten für Teilnehmer festlegt. Sie können Konferenzrichtlinien auf Standort- oder Benutzerebene erstellen. Konferenzrichtlinieneinstellungen umfassen viele Aspekte der Konferenzplanung und -teilnahme. Mehrere Konferenzrichtlinieneinstellungen unterstützen Einwahlkonferenzen für Teilnehmer. Bei der Konfiguration von Einwahlkonferenzen sollten Sie sicherstellen, dass diese Felder für Ihre Organisation angemessen festgelegt sind, und sie bei Bedarf bearbeiten. 
  
Weitere Informationen zum Konfigurieren von Konferenzrichtlinien finden Sie unter [Verwalten von Konferenzrichtlinien in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).
  
## <a name="assign-a-line-uri-to-a-user-account"></a>Weisen Sie einem Benutzerkonto einen Anschluss-URI zu
<a name="BKMK_AssignaLineURI"> </a>

Teilnehmer an Einwahlkonferenzen geben ihre Telefonnummer oder Durchwahl sowie eine PIN ein, um als authentifizierte Benutzer an Konferenzen teilzunehmen. Die in den Skype for Business Server-Benutzerkonten angegebene Telefon **Leitungs-URI** ist für die Authentifizierung erforderlich.
  
In diesem Thema wird beschrieben, wie Sie einem einzelnen Benutzerkonto einen **Anschluss-URI** zuweisen. Wenn Sie mehreren Benutzerkonten einen **Anschluss-URI** zuweisen möchten, können Sie ein Skript erstellen, das das Cmdlet **Set-CsUser** verwendet. Details zur Verwendung eines Beispielskripts zum Zuweisen von **Leitungs-URI** zu mehreren Benutzerkonten finden Sie unter [Zuweisen von Leitungs-URIs zu mehreren Benutzern](https://go.microsoft.com/fwlink/p/?linkId=196945).
  
1. Melden Sie sich beim Computer als Mitglied der Gruppe „RTCUniversalServerAdmins“ oder als Benutzer mit der Rolle **Cs-UserAdministrator** oder **CsAdministrator** an.
    
2.  Öffnen Sie die Skype for Business Server-Systemsteuerung.
    
3. Klicken Sie in der linken Navigationsleiste auf **Benutzer**.
    
4. Geben Sie in das Suchfeld den Namen des Benutzers ein, den Sie für Einwahlkonferenzen konfigurieren möchten, oder klicken Sie auf **Filter hinzufügen**, um Suchfelder anzugeben und klicken Sie dann auf **Suchen**.
    
5. Doppelklicken Sie auf den Benutzernamen, um das Dialogfeld **Skype for Business Server-Benutzer bearbeiten** zu öffnen.
    
6. Geben Sie unter **Telefonie** in das Feld **Anschluss-URI** eine eindeutige, normalisierte Telefonnummer ein (beispielsweise tel:+14255550200).
    
    > [!NOTE]
    > Sie können **Anschluss-URI** nur angeben, wenn **Telefonie** auf **Nur von PC zu PC**, **Enterprise-VoIP**, **Remoteanrufsteuerung** oder **Nur Remoteanrufsteuerung** festgelegt ist. 
  
7. Klicken Sie auf **Commit ausführen**.
    

