---
title: Auswählen von Übersetzungsregeln
ms.reviewer: ''
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/24/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.lscp.VoiceTrunkSelRule
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 55776a94-4888-4436-a3b6-0e6f8252e392
description: Enterprise-VoIP setzt voraus, dass alle Wählzeichenfolgen im E. 164-Format normalisiert werden, um RNL (Reverse Number Lookup) durchzuführen. Der Trunkpeer (also das zugeordnete Gateway, Nebenstellensystem oder der zugeordnete SIP-Trunk) erfordert möglicherweise, dass die Nummern in einem lokalen Wählformat vorliegen. Um Nummern aus dem E.164-Format in ein lokales Wählformat zu übersetzen, können Sie optional eine oder mehrere Übersetzungsregeln definieren, mit denen der Anforderungs-URI vor dem Routen an den Trunkpeer geändert wird. Sie können beispielsweise eine Übersetzungsregel erstellen, mit der die Vorwahl +44 aus einer Wählzeichenfolge entfernt und durch 0144 ersetzt wird.
ms.openlocfilehash: 1825b2c234a6d2c0f1ab46ae0e62245ef54c9421
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41822108"
---
# <a name="select-translation-rules"></a>Auswählen von Übersetzungsregeln
 
 Enterprise-VoIP setzt voraus, dass alle Wählzeichenfolgen im E. 164-Format normalisiert werden, um RNL (Reverse Number Lookup) durchzuführen. Der Trunkpeer (also das zugeordnete Gateway, Nebenstellensystem oder der zugeordnete SIP-Trunk) erfordert möglicherweise, dass die Nummern in einem lokalen Wählformat vorliegen. Um Nummern aus dem E.164-Format in ein lokales Wählformat zu übersetzen, können Sie optional eine oder mehrere Übersetzungsregeln definieren, mit denen der Anforderungs-URI vor dem Routen an den Trunkpeer geändert wird. Sie können beispielsweise eine Übersetzungsregel erstellen, mit der die Vorwahl +44 aus einer Wählzeichenfolge entfernt und durch 0144 ersetzt wird.
  
> [!IMPORTANT]
> Die Möglichkeit, eine oder mehrere Übersetzungsregeln einer Enterprise Voice trunk-Konfiguration zuzuordnen, dient als Alternative zum Konfigurieren von Übersetzungsregeln für den trunk-Peer. Ordnen Sie Übersetzungsregeln keiner Enterprise-VoIP-trunk-Konfiguration zu, wenn Sie Übersetzungsregeln für den trunk-Peer konfiguriert haben, da die beiden Regeln möglicherweise in Konflikt stehen. 
  
Klicken Sie auf eine Regel in der Liste und anschließend auf **OK**, um eine vorhandene Übersetzungsregel zu verwenden.
  
Details zu den verschiedenen Verfahren, die Sie mit der Skype for Business Server-Systemsteuerung ausführen können, finden Sie unter [Verwalten von Skype for Business Server 2015](../../manage/manage.md).
  

