---
title: Überprüfen von Administratorberichten in Skype for Business Server 2015
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 4/5/2016
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 22d480ea-cd64-4d09-99fe-96e997570844
description: Die Administratorberichte stellen detaillierte Informationen zu Bereitstellung und Betrieb bereit. Die Berichte werden anhand der auf der Seite Websites entwerfen angegebenen Auswahl erstellt. Der für den Entwurf verantwortliche Nutzer kann die Administratorberichte durch Bearbeiten der Netzwerkdiagramme und Definieren der vollständigen IP-Adressen und vollqualifizierten Domänennamen (Fully Qualified Domain Names, FQDNs) für Server, Pools und Lastenausgleich ergänzen.
ms.openlocfilehash: ae6dba3f5967fcd10618a8ab53c754a4f38da748
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41816294"
---
# <a name="review-the-administrator-reports-in-skype-for-business-server-2015"></a>Überprüfen von Administratorberichten in Skype for Business Server 2015

Die Administratorberichte stellen detaillierte Informationen zu Bereitstellung und Betrieb bereit. Die Berichte werden anhand der auf der Seite **Websites entwerfen** angegebenen Auswahl erstellt. Der für den Entwurf verantwortliche Nutzer kann die Administratorberichte durch Bearbeiten der Netzwerkdiagramme und Definieren der vollständigen IP-Adressen und vollqualifizierten Domänennamen (Fully Qualified Domain Names, FQDNs) für Server, Pools und Lastenausgleich ergänzen.

Die Administratorberichte-Funktion ermöglicht Ihnen Folgendes:

- [Review the Summary Report](review-the-administrator-reports.md#Summary_report)

- [Review the Certificates Report](review-the-administrator-reports.md#Certificates_Report)

- [Review the Firewall Report](review-the-administrator-reports.md#Firewall_report)

- [Review the DNS Report](review-the-administrator-reports.md#DNS_Report)

## <a name="review-the-summary-report"></a>Überprüfen des Zusammenfassungsberichts
<a name="Summary_report"> </a>

Der Skype for Business-Administrator Bericht ist der erste von vier wertvollen Berichten, die Ihr Design detailliert dokumentieren. Die Informationen in diesem und den drei weiteren Berichten sind überaus nützlich für Ihre IT-Teams:

![Allgemeine Zusammenfassung – Verwaltungsbericht](../../media/General_Summary_Report_Admin_Report.png)

Der Zusammenfassungsbericht enthält allgemeine Konfigurationsinformationen zu Ihrem Edgenetzwerk. In ihm werden Standort, vollqualifizierter Domänenname (Fully Qualified Domain Name, FQDN) und IP-Adresse sowie die Art des Netzwerks dokumentiert und Kommentare zu spezifischen Rollen bereitgestellt.

Der für den Entwurf verantwortliche Benutzer und alle Teams, die für Bereitstellung, Verwaltung und Wartung der Infrastruktur sorgen, sollten den Zusammenfassungsbericht prüfen, um die Richtigkeit der Informationen sicherzustellen und Fehler zu minimieren.

Sie können Berichte mit noch mehr Einzelheiten einsehen:

- Zertifikatbericht

- Firewallbericht

- DNS-Bericht

## <a name="review-the-certificates-report"></a>Überprüfen des Zertifikatberichts
<a name="Certificates_Report"> </a>

Der Bericht Zertifikate enthält alle Zertifikate, die in der empfohlenen Skype for Business Server 2015-Bereitstellung erforderlich sind. Das Planungs Tool berücksichtigt die eingegebenen Antragstellernamen und alternativen Subjektnamen. Nicht bearbeiteter Standardtext kann eine Herausforderung für das Team darstellen, das für das Anfordern und Ausstellen der Zertifikate verantwortlich ist. In den Zertifikatinformationen ist zudem angegeben, durch welche Stelle das Zertifikat typischerweise ausgestellt werden kann. Wenn die Infrastruktur nicht über eine interne Public Key-Infrastruktur (PKI) verfügt, können sämtliche Zertifikate über einen öffentlichen Zertifikatanbieter angefordert werden. Die Felder „Erweiterte Schlüsselverwendungen“ und „Zuweisen zu“ des Berichts sind äußerst nützlich und liefern Informationen zu Zweck und Speicherort der einzelnen Zertifikate.

![Zertifikatverwaltungsbericht](../../media/Certificates_Report_Admin_Report.png)

Überprüfen Sie die Verwendung und den Zweck der einzelnen Zertifikate innerhalb der Bereitstellung sorgfältig und stellen Sie sicher, dass Sie diese Informationen verstanden haben. Wenn Sie Fragen zum Zweck eines Zertifikats haben, ermitteln Sie, welcher Server oder Dienst mit welcher Komponente kommuniziert. Zertifikate in Skype for Business Server 2015 werden für zwei primäre Zwecke verwendet:

- Mutual Transport Layer Security (MTLS) – die Computer, die an der Kommunikation beteiligt sind, präsentieren ein Zertifikat, das Ihre Identität auf einem anderen Computer beweist. Dieser Vorgang wird als Serverauthentifizierung bezeichnet. Die Kommunikation kann erst beginnen, wenn jeder Computer der Identität des anderen Computers vertraut.

- Verschlüsselungs Verschlüsselung (Secure Sockets Layer oder SSL sowie Transport Layer Security oder TLS) ist ein wichtiges Mittel, um die Kommunikation zu sichern, den Datenschutz zu gewährleisten und ein vertrauenswürdiges Kommunikations-und Zusammenarbeitssystem zu erstellen.

## <a name="review-the-firewall-report"></a>Überprüfen des Firewallberichts
<a name="Firewall_report"> </a>

Für Skype for Business Server 2015 gibt es eine potenziell komplexe Gruppe von Firewall-Regeln. Das Planungs Tool reduziert diese Komplexität durch die Generierung eines Berichts, der alle Firewall-Anforderungen basierend auf den Eingabekriterien des Designers detailliert definiert. Der IT-Firewalladministrator kann die erforderlichen Regeln anhand dieses Berichts konfigurieren und definieren.

Für eine ordnungsgemäße Firewallverwaltung sollte der Bericht sorgfältig geprüft werden, um sicherzustellen, dass keine Konflikte mit vorhandenen Firewallregeln auftreten und keine Richtlinien oder Verfahren verletzt werden.

![Firewallverwaltungsbericht](../../media/Firewall_Report_Admin_Report.png)

## <a name="review-the-dns-report"></a>Überprüfen des DNS-Berichts
<a name="DNS_Report"> </a>

Der DNS-Bericht ist Bestandteil des Administratorberichts. In ihm werden alle empfohlenen und bekannten DNS-Einträge (Domain Name System) im internen Netzwerk, im Umkreisnetzwerk und in externen Netzwerken aufgeführt. Wenn der für den Entwurf verantwortliche Benutzer die Bearbeitung des Netzwerkdiagramms abgeschlossen und alle IP-Adressen und vollqualifizierten Domänennamen (Fully Qualified Domain Names, FQDNs) mit den Werten für die Produktion definiert hat, stellt der DNS-Bericht eine ausgezeichnete Konfigurationsressource dar. Gleichzeitig eignet sich dieser Bericht als Referenz bei der Problembehandlung.

![DNS-Verwaltungsbericht](../../media/DNS_Report_Admin_Report.png)

Sie sollten den DNS-Bericht von Ihrem DNS-Verwaltungsteam sorgfältig überprüfen lassen. Auf diese Weise stellen Sie sicher, dass die Konfiguration keine Fehler enthält, die u. U. zu Problemen bei der Bereitstellung oder einer unnötig erschwerten Problembehandlung führen.

## <a name="see-also"></a>Siehe auch
<a name="DNS_Report"> </a>

[Reviewing the Administrator Reports](https://technet.microsoft.com/library/1dee56a9-a033-4201-9765-e3469bd7d3e3.aspx)
