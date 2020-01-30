---
title: Verwenden Sie das Wiederherstellungstools für Microsoft Teams Rooms
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: sohailta
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection:
- M365-collaboration
localization_priority: Normal
description: In diesem Artikel wird erläutert, wie Sie das Wiederherstellungstool für Microsoft Teams-Räume verwenden, mit denen Sie ein veraltetes System in einen unterstützten Zustand bringen.
ms.openlocfilehash: 3a62256a5e39d93033588ca2be779e9c3b76a4f5
ms.sourcegitcommit: 9bead87a7f4c4e71f19f8980e9dce2b979735055
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "41268953"
---
# <a name="use-the-microsoft-teams-rooms-recovery-tool"></a><span data-ttu-id="57dc2-103">Verwenden Sie das Wiederherstellungstools für Microsoft Teams Rooms</span><span class="sxs-lookup"><span data-stu-id="57dc2-103">Use the Microsoft Teams Rooms recovery tool</span></span>

<span data-ttu-id="57dc2-104">In diesem Artikel wird erläutert, wie Sie das Wiederherstellungstool für Microsoft Teams-Räume verwenden, mit denen Sie ein veraltetes System in einen unterstützten Zustand bringen.</span><span class="sxs-lookup"><span data-stu-id="57dc2-104">This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state.</span></span> <span data-ttu-id="57dc2-105">Dieses Tool sollte angewendet werden, wenn die Microsoft Teams rooms-Konsole einen Fehler vom Typ "Systemkonfiguration veraltet" oder vor dem Durchführen einer [Wiederherstellung](https://docs.microsoft.com/microsoftteams/room-systems/rooms-operations#microsoft-teams-rooms-reset-factory-restore)des Zurücksetzens einer Drucktaste zeigt.</span><span class="sxs-lookup"><span data-stu-id="57dc2-105">This tool should be applied when either the Microsoft Teams Rooms console shows a "system config out of date" error, or prior to performing a push button reset [factory restore](https://docs.microsoft.com/microsoftteams/room-systems/rooms-operations#microsoft-teams-rooms-reset-factory-restore).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57dc2-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="57dc2-106">Prerequisites</span></span>

<span data-ttu-id="57dc2-107">Laden Sie das neueste [Microsoft Teams rooms-Installationspaket](https://go.microsoft.com/fwlink/?linkid=851168) herunter, und extrahieren Sie es auf einen USB-Speicherstick oder eine Netzwerkfreigabe, auf die das Microsoft Teams rooms-Gerät zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="57dc2-107">Download the latest [Microsoft Teams Rooms installation package](https://go.microsoft.com/fwlink/?linkid=851168) and extract it to a USB memory stick or network share accessible to the Microsoft Teams Rooms device.</span></span>

> [!NOTE]
> <span data-ttu-id="57dc2-108">Das Extrahieren der Dateien aus der MSI-Datei kann mit vielen Mitteln erfolgen.</span><span class="sxs-lookup"><span data-stu-id="57dc2-108">Extracting the files from the MSI can be accomplished by many means.</span></span> <span data-ttu-id="57dc2-109">Jeder Mechanismus, der alle Dateien extrahiert und die Verzeichnisstruktur erhält, ist akzeptabel.</span><span class="sxs-lookup"><span data-stu-id="57dc2-109">Any mechanism that extracts all the files and preserves their directory structure is acceptable.</span></span> <span data-ttu-id="57dc2-110">Eine Möglichkeit besteht darin, den Befehl `msiexec /qn PathToMsi /qb TARGETDIR=PathToTarget` zu verwenden `PathToMsi` , der den vollständigen Pfad zum Microsoft Teams Room-Installationspaket `PathToTarget` darstellt, und stellt den vollständigen Pfad zu dem Ordner dar, in den die Dateien extrahiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57dc2-110">One such way is to use the command `msiexec /qn PathToMsi /qb TARGETDIR=PathToTarget` where `PathToMsi` represents the full path to the Microsoft Teams Room installation package, and `PathToTarget` represents the full path to the folder you would like the files extracted to.</span></span>

## <a name="running-the-tool"></a><span data-ttu-id="57dc2-111">Ausführen des Tools</span><span class="sxs-lookup"><span data-stu-id="57dc2-111">Running the tool</span></span>

1) <span data-ttu-id="57dc2-112">Registrieren Sie sich auf Ihrem Microsoft Teams rooms-Gerät beim Administratorkonto, und starten Sie eine Eingabeaufforderung mit erhöhten Rechten.</span><span class="sxs-lookup"><span data-stu-id="57dc2-112">Sign in to the admin account on your Microsoft Teams Rooms device, and launch an elevated command prompt.</span></span>
2) <span data-ttu-id="57dc2-113">Überprüfen Sie im Microsoft Teams rooms-Gerät, auf das `RecoveryTool.ps1 file`Sie zugreifen können, das in den Dateien enthalten ist, die aus dem Installationspaket für Microsoft Teams rooms extrahiert wurden.</span><span class="sxs-lookup"><span data-stu-id="57dc2-113">Verify from the Microsoft Teams Rooms device that you are able to access the `RecoveryTool.ps1 file`, which is included in the files extracted from the Microsoft Teams Rooms installation package.</span></span> <span data-ttu-id="57dc2-114">Das Kit befindet sich auf der Netzwerkfreigabe oder dem USB-Laufwerk, das bei der Vorbereitung von Voraussetzungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="57dc2-114">The kit can be found on the network share or USB drive used when preparing prerequisites.</span></span>
3) <span data-ttu-id="57dc2-115">Ausführen `powershell.exe -ExecutionPolicy Unrestricted -File "<path to RecoveryTool.ps1>"`.</span><span class="sxs-lookup"><span data-stu-id="57dc2-115">Run `powershell.exe -ExecutionPolicy Unrestricted -File "<path to RecoveryTool.ps1>"`.</span></span>
4) <span data-ttu-id="57dc2-116">Wenn Sie eine Factory-Wiederherstellung durchführen:</span><span class="sxs-lookup"><span data-stu-id="57dc2-116">If you are performing a factory restore:</span></span>
   - <span data-ttu-id="57dc2-117">Wenn Sie vom Skript dazu aufgefordert werden, wählen Sie Option 2: **Zurücksetzen**aus.</span><span class="sxs-lookup"><span data-stu-id="57dc2-117">When prompted by the script select option 2: **Reset**.</span></span>
   - <span data-ttu-id="57dc2-118">Wenn BitLocker aktiviert ist, folgen Sie den Anweisungen am Ende der Skriptausgabe, um Sie zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="57dc2-118">If BitLocker is on, follow the instructions provided at the end of the script output to disable it.</span></span>
   - <span data-ttu-id="57dc2-119">Durchführen der Factory-Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="57dc2-119">Perform the factory restore.</span></span>
      - <span data-ttu-id="57dc2-120">Öffnen Sie die app " **Einstellungen** ", und wählen Sie **#a0 Sicherheit aktualisieren** aus.</span><span class="sxs-lookup"><span data-stu-id="57dc2-120">Open the **Settings** app, and select **Update & Security**</span></span>
      - <span data-ttu-id="57dc2-121">Navigieren Sie zur Registerkarte **Wiederherstellen** .</span><span class="sxs-lookup"><span data-stu-id="57dc2-121">Navigate to the **Recovery** tab.</span></span>
      - <span data-ttu-id="57dc2-122">Wählen Sie unter **diesen PC zurücksetzen die**Option **Erste Schritte** aus.</span><span class="sxs-lookup"><span data-stu-id="57dc2-122">Beneath **Reset this PC**, select **Get started**</span></span>
      - <span data-ttu-id="57dc2-123">Wählen Sie **alles entfernen**und dann **weiter** und **Zurücksetzen** aus.</span><span class="sxs-lookup"><span data-stu-id="57dc2-123">Select **Remove everything**, then **Next** and **Reset**</span></span>
      - <span data-ttu-id="57dc2-124">Das System wird mehrmals neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="57dc2-124">The system will reboot multiple times.</span></span> <span data-ttu-id="57dc2-125">Wenn der Reset abgeschlossen ist, befindet sich das System auf dem Windows-OOBE-Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="57dc2-125">When the reset is complete, the system will be at the Windows OOBE screen.</span></span>
5) <span data-ttu-id="57dc2-126">Wenn Sie ein veraltetes System reparieren:</span><span class="sxs-lookup"><span data-stu-id="57dc2-126">If you are repairing an "out of date" system:</span></span>
    - <span data-ttu-id="57dc2-127">Wenn Sie vom Skript dazu aufgefordert werden, wählen Sie Option 1: **Reparieren**aus.</span><span class="sxs-lookup"><span data-stu-id="57dc2-127">When prompted by the script select option 1: **Repair**.</span></span>
    - <span data-ttu-id="57dc2-128">Starten Sie nach Abschluss das Microsoft Teams rooms-Gerät neu.</span><span class="sxs-lookup"><span data-stu-id="57dc2-128">Upon completion, reboot the Microsoft Teams Rooms device.</span></span> <span data-ttu-id="57dc2-129">Sie wird automatisch neu gestartet und beim zweiten Mal wieder vollständig wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="57dc2-129">It will reboot again automatically and come up fully recovered the second time.</span></span>

> [!NOTE]
> <span data-ttu-id="57dc2-130">Es gibt ein bekanntes Problem, bei dem die Microsoft Teams-Räume unbrauchbar werden können, wenn die Option **meine Dateien beibehalten-apps und Einstellungen entfernt, aber Ihre persönlichen Dateien beibehalten** aktiviert ist, während des Windows-Reset-Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="57dc2-130">There is a known issue where the Microsoft Teams Rooms can become unusable if the  **Keep my files - Removes Apps and settings, but keeps your personal files** option is selected during the Windows Reset process.</span></span> <span data-ttu-id="57dc2-131">Verwenden Sie diese Option *nicht* .</span><span class="sxs-lookup"><span data-stu-id="57dc2-131">Do *not* use this option.</span></span>

## <a name="see-also"></a><span data-ttu-id="57dc2-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="57dc2-132">See also</span></span>

[<span data-ttu-id="57dc2-133">Microsoft Teams Rooms-Hilfe</span><span class="sxs-lookup"><span data-stu-id="57dc2-133">Microsoft Teams Rooms help</span></span>](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[<span data-ttu-id="57dc2-134">Microsoft Teams Rooms verwalten</span><span class="sxs-lookup"><span data-stu-id="57dc2-134">Manage Microsoft Teams Rooms</span></span>](rooms-manage.md)