---
title: Get-CcVersion
ms.reviewer: ''
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 6/30/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: 7d370abd-0c01-4490-88a1-55b42e51b663
description: Gibt die Version der Cloud Connector-Appliance zurück. "Get-CCVersion" kann nur auf dem Hostcomputer von Cloud Connector verwendet werden.
ms.openlocfilehash: 706b480c2f8e277b7f41fe28e88cc062fea6603a
ms.sourcegitcommit: e64c50818cac37f3d6f0f96d0d4ff0f4bba24aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41799845"
---
# <a name="get-ccversion"></a>Get-CcVersion
 
Gibt die Version der Cloud Connector-Appliance zurück. "Get-CCVersion" kann nur auf dem Hostcomputer von Cloud Connector verwendet werden.
  
```powershell
Get-CcVersion [[-VersionType] <String>] [<CommonParameters>]
```

## <a name="detailed-description"></a>Detaillierte Beschreibung

Gibt die Version der Cloud Connector-Appliance basierend auf installierten PowerShell-Skripts, Dateien im Appliance-Verzeichnis und die auf dem Hostserver bereitgestellten virtuellen Computer zurück.
  
## <a name="parameters"></a>Parameter

|**Parameter**|**Erforderlich**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|:-----|
|Versiontype  <br/> |Optional  <br/> |System.String  <br/> |Der Typ der Version. Der Wert des Parameters kann RunningScripts, RunningBits, BackupBits oder alle sein. Der Standardwert ist RunningScripts.  <br/> |
   
## <a name="examples"></a>Beispiele
<a name="Examples"> </a>

### <a name="example-1"></a>Beispiel 1

Das folgende Beispiel zeigt die Cloud Connector-Version des aktuell ausgeführten Skripts in Ihrer geöffneten PowerShell-Konsole:
  
```powershell
Get-CcVersion
```

### <a name="example-2"></a>Beispiel 2

Das folgende Beispiel zeigt die Cloud Connector-Version der aktuell ausgeführten Binärdateien, die auf den virtuellen Computern bereitgestellt werden. Sie können die Version in den Namen der ausgeführten virtuellen Computer in Hyper-v-Manager anzeigen:
  
```powershell
Get-CCVersion -VersionType RunningBits
```

## <a name="input-types"></a>Eingabetypen
<a name="Examples"> </a>

Keine. Das Cmdlet "Get-CcVersion" akzeptiert keine Pipeline-Eingabe.
  
## <a name="return-types"></a>Rückgabetypen
<a name="Examples"> </a>

Keine.
  
## <a name="see-also"></a>Siehe auch
<a name="Examples"> </a>

Keine.
  

