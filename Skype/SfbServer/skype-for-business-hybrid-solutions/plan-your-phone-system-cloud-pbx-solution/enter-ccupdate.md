---
title: Enter-CcUpdate
ms.reviewer: ''
ms.author: crowe
author: CarolynRowe
ms.date: 3/31/2017
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: 330367f2-22b0-43e3-b8fb-3e0d2e3b330e
description: Das Cmdlet "Enter-CcUpdate" bereitet den Skype for Business Cloud Connector Edition-Hostserver für den Updateprozess vor, indem er in den Wartungsmodus versetzt wird. Die Appliance beendet sofort alle Dienste, beendet alle laufenden Anrufe und lehnt alle neuen Anrufe ab.
ms.openlocfilehash: 25d2fbc56bd4de6a08985de18c178d5a8f993492
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41802175"
---
# <a name="enter-ccupdate"></a>Enter-CcUpdate

Das Cmdlet "Enter-CcUpdate" bereitet den Skype for Business Cloud Connector Edition-Hostserver für den Updateprozess vor, indem er in den Wartungsmodus versetzt wird. Die Appliance beendet sofort alle Dienste, beendet alle laufenden Anrufe und lehnt alle neuen Anrufe ab.
  
```powershell
Enter-CcUpdate
```

## <a name="parameters"></a>Parameter

Keine
  
## <a name="examples"></a>Beispiele
<a name="Examples"> </a>

### <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel wird die Appliance auf den Updateprozess vorbereitet, indem sie in den Wartungsmodus versetzt wird:
  
```powershell
Enter-CcUpdate 
```

## <a name="detailed-description"></a>Detaillierte Beschreibung
<a name="DetailedDescription"> </a>

Das Cmdlet "Enter-CcUpdate" beendet sofort alle Dienste, die alle laufenden Anrufe beenden, und die Appliance lehnt alle neuen Anrufe ab, die an andere Produktions-Appliances übertragen werden. Sie müssen sicherstellen, dass die verbleibenden Produktions-Appliances über genügend Kapazität verfügen, um die Anrufe von der Appliance zu verarbeiten, die Sie aktualisieren möchten.
  
Der Wartungsmodus ist hilfreich, wenn zum Beispiel für Ihre Appliance automatische Updates aktiviert sind und Microsoft einen wichtigen Hotfix veröffentlicht. Außerdem ist der Wartungsmodus hilfreich, wenn Sie zwar beschließen, automatische Updates zu deaktivieren, aber regelmäßig manuelle Updates ausführen.
  
Nach der Installation der Updates kann die Appliance durch Ausführen des Cmdlets Exit-CcUpdate wieder in den Produktionsmodus versetzt werden.
  
> [!NOTE]
> Wenn Sie sich entscheiden, eine Cloud Connector-Appliance manuell zu aktualisieren, müssen Sie Sie innerhalb von 60 Tagen aktualisieren, nachdem Microsoft die nächste Version veröffentlicht hat. Microsoft unterstützt die zuvor veröffentlichte Version von Cloud Connector für 60 Tage nach der Veröffentlichung der neuen Version. 
  
## <a name="input-types"></a>Eingabetypen
<a name="InputTypes"> </a>

Keine. Das Cmdlet „Enter-CCUpdate“ akzeptiert keine Pipelineeingaben.
  
## <a name="return-types"></a>Rückgabetypen
<a name="ReturnTypes"> </a>

Keine  
  
## <a name="see-also"></a>Siehe auch
<a name="ReturnTypes"> </a>

[Exit-CcUpdate](exit-ccupdate.md)
  

