---
title: Allgemeine Einstellungen für externe Anwendungen – Erweiterung
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.ExternalApplicationGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aa7268ac-b9e3-4d25-bff4-e59d305120f2
ROBOTS: NOINDEX, NOFOLLOW
description: Führen Sie die folgenden Anweisungen aus, um die Eigenschaften für einen vertrauenswürdigen Anwendungsserver zu bearbeiten, der bereits definiert wurde.
ms.openlocfilehash: eacc0c854290fcf24196a8e4c58829231dc725c4
ms.sourcegitcommit: b1229ed5dc25a04e56aa02aab8ad3d4209559d8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41793743"
---
# <a name="external-application-general-settings-expander"></a>Allgemeine Einstellungen für externe Anwendungen – Erweiterung
 
Führen Sie die folgenden Anweisungen aus, um die Eigenschaften für einen vertrauenswürdigen Anwendungsserver zu bearbeiten, der bereits definiert wurde.
  
Es gibt zwei Abschnitte, die Sie ändern können:
  
> Allgemeine Einstellungen
> 
> Einstellungen für nächsten Hop
    
## <a name="general-settings"></a>Allgemeine Einstellungen

Sie können den aktuellen vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) für den vertrauenswürdigen Anwendungsserver Pool ändern. Bearbeiten Sie den Namen des FQDN des Pools. Für den neuen Eintrag müssen die DNS-Host (A)-Einträge (Domain Name System) vorhanden sein, bevor Clients oder Server eine Verbindung mit dem neuen Pool Namen herstellen können.
  
Wählen Sie **Replikation von Konfigurationsdaten in diesem Pool aktivieren** aus, wenn Sie die Replikation von Konfigurationsdaten in diesen Pool benötigen. Deaktivieren Sie das Häkchen, wenn Sie die Konfigurationsdaten nicht replizieren möchten.
  
## <a name="next-hop-settings"></a>Einstellungen für den nächsten Hop

Sie können den nächsten Hop-Server des Trusted Application Server-Pools angeben, indem Sie den definierten Enterprise Edition-Front-End-Pool oder den Standard Edition-Front-End-Server aus der Dropdownliste auswählen. Ein Director-oder Director-Pool ist keine gültige Auswahl für einen Trusted Application Server-nächsten Hop und wird nicht in der Liste angezeigt.
  

Klicken Sie auf **OK** , um die Änderungen zu übernehmen und zu speichern. Klicken Sie auf **Abbrechen**, um Ihre Änderungen zu verwerfen und die Eigenschaftenseite zu schließen.
  

