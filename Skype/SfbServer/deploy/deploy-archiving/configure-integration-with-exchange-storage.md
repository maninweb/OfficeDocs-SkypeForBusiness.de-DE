---
title: Konfigurieren der Integration in Exchange Storage für Skype for Business Server
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
ms.assetid: 8f48b87f-a57f-4ed8-8c79-5c75b316b696
description: 'Zusammenfassung: Lesen Sie dieses Thema, um zu erfahren, wie Sie die Integration in den Exchange-Speicher in Skype for Business Server konfigurieren.'
ms.openlocfilehash: cee41a52593a90490ec8da90637ee4ec5de33d03
ms.sourcegitcommit: dd3a3ab4ddbdcfe772f30fb01ba3b97c45c43dd4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "41768888"
---
# <a name="configure-integration-with-exchange-storage-for-skype-for-business-server"></a>Konfigurieren der Integration in Exchange Storage für Skype for Business Server
 
**Zusammenfassung:** In diesem Thema erfahren Sie, wie Sie die Integration in den Exchange-Speicher in Skype for Business Server konfigurieren.
  
Wenn Sie die Microsoft Exchange-Integration für alle Benutzer in Ihrer Bereitstellung verwenden, müssen Sie die Skype for Business Server-Archivierungsrichtlinien für Ihre Benutzer nicht konfigurieren. Stattdessen konfigurieren Sie Exchange-in-situ-Speicherrichtlinien, um die Archivierung für Benutzer zu unterstützen, die sich in Exchange befinden, wobei ihre Postfächer in-situ gespeichert werden. Bevor Sie die Integration in Exchange-Speicher konfigurieren, lesen Sie [Planen der Archivierung in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md). Ausführliche Informationen zu den Exchange-in-situ-Speicherrichtlinien finden Sie in der Exchange-Produktdokumentation. 
  
## <a name="configure-integration-with-microsoft-exchange-storage"></a>Konfigurieren der Integration in den Microsoft Exchange-Speicher

1. Melden Sie sich mit einem Benutzerkonto, dem die Rolle "CsArchivingAdministrator" oder "CsAdministrator" zugewiesen ist, auf einem beliebigen Computer in Ihrer internen Bereitstellung an.
    
2. Öffnen Sie ein Browserfenster, und geben Sie dann die Administrator-URL ein, um das Skype for Business Server Control Panel zu öffnen. 
    
3. Klicken Sie auf der linken Navigationsleiste auf **Überwachung und Archivierung** und anschließend auf **Archivierungskonfiguration**.
    
4. Klicken Sie in der Liste der Archivierungskonfigurationen auf den Namen der betreffenden Konfiguration auf globaler, Standort- oder Poolebene. Klicken Sie auf **Bearbeiten** und auf **Details anzeigen** und führen Sie dann eine der folgenden Aktionen aus:
    
   - Wenn Sie die Integration in Exchange-Speicher aktivieren möchten, aktivieren Sie das Kontrollkästchen **Microsoft Exchange-Integration** .
    
   - Deaktivieren Sie das Kontrollkästchen **Microsoft Exchange-Integration** , um die Integration in Exchange-Speicher zu deaktivieren.
    
5. Klicken Sie auf **Commit ausführen**.
    
## <a name="when-skype-for-business-server-and-microsoft-exchange-are-deployed-in-different-forests"></a>Wenn Skype for Business Server und Microsoft Exchange in verschiedenen Gesamtstrukturen bereitgestellt werden

Wenn Sie die Microsoft Exchange-Integration verwenden und Microsoft Exchange Server nicht in derselben Gesamtstruktur wie Skype for Business Server bereitgestellt wird, müssen Sie sicherstellen, dass die folgenden Exchange Active Directory-Attribute mit der Gesamtstruktur synchronisiert werden, in der Skype für Business Server wird bereitgestellt:
  
- msExchUserHoldPolicies
    
- proxyAddresses
    
Dies ist ein mehrwertiges Attribut. Bei der Synchronisierung dieses Attributs müssen Sie die Werte zusammenführen und nicht ersetzen, um sicherzustellen, dass die vorhandenen Werte nicht verloren gehen.
  

