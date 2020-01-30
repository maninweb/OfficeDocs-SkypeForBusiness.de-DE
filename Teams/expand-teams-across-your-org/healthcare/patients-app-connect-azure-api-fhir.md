---
title: Verbinden der Patienten-App mit Azure-API für FHIR
author: lanachin
ms.author: v-lanac
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
search.appverid: MET150
localization_priority: Normal
MS.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
appliesto:
- Microsoft Teams
ms.reviewer: anach
description: Hier erfahren Sie, wie Sie die Patienten-app in Microsoft Teams mit Azure-API für FHIR (fast Healthcare-Interoperabilitäts Ressourcen) verbinden.
ms.openlocfilehash: e532aa9f9fbecb472db63a1ddad4cd71518a8041
ms.sourcegitcommit: d7fab927e96954f294f28dfb33c0889f736b3ab5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2020
ms.locfileid: "41259106"
---
# <a name="connect-the-patients-app-to-azure-api-for-fhir"></a><span data-ttu-id="660a7-103">Verbinden der Patienten-App mit Azure-API für FHIR</span><span class="sxs-lookup"><span data-stu-id="660a7-103">Connect the Patients app to Azure API for FHIR</span></span>

<span data-ttu-id="660a7-104">Führen Sie die folgenden Schritte aus, um der Patienten-app in Microsoft Teams den Zugriff auf eine Azure-API für die FHIR-Instanz zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="660a7-104">Follow these steps to allow the Patients app in Microsoft Teams access to an Azure API for FHIR instance.</span></span> <span data-ttu-id="660a7-105">In diesem Artikel wird davon ausgegangen, dass Sie eine [Azure-API für die FHIR-Instanz](https://azure.microsoft.com/services/azure-api-for-fhir/) eingerichtet und in Ihrem Mandanten konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="660a7-105">This article assumes that you have an [Azure API for FHIR instance](https://azure.microsoft.com/services/azure-api-for-fhir/) set up and configured in your tenant.</span></span>  <span data-ttu-id="660a7-106">Wenn Sie noch keine Azure-API für die FHIR-Instanz in Ihrem Mandanten erstellt haben, lesen Sie [Schnellstart: Bereitstellen der Azure-API für FHIR mithilfe von Azure Portal](https://docs.microsoft.com/azure/healthcare-apis/fhir-paas-portal-quickstart).</span><span class="sxs-lookup"><span data-stu-id="660a7-106">If you haven’t yet created an Azure API for FHIR instance in your tenant, see [Quickstart: Deploy Azure API for FHIR using Azure portal](https://docs.microsoft.com/azure/healthcare-apis/fhir-paas-portal-quickstart).</span></span>


1. <span data-ttu-id="660a7-107">Klicken Sie [hier](https://login.microsoftonline.com/common/adminConsent?client_id=4aee3506-b263-43e0-ba31-1468fa7b2806) , um die Zustimmung des Administrators für die Patienten-APP zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="660a7-107">Click [here](https://login.microsoftonline.com/common/adminConsent?client_id=4aee3506-b263-43e0-ba31-1468fa7b2806) to grant admin consent for the Patients app.</span></span> <span data-ttu-id="660a7-108">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem mandantenadministrator oder den globalen Administratoranmeldeinformationen an, und klicken Sie dann auf **annehmen** , um die erforderlichen Berechtigungen zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="660a7-108">When prompted, sign in using your tenant admin or global admin credentials, and then click **Accept** to grant the required permissions.</span></span>

    ![Screenshot der App "Berechtigungsanforderung für Patienten"](../../media/patients-app-permissions-request.png)

    <span data-ttu-id="660a7-110">Nachdem Sie die Ansicht akzeptiert haben, schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="660a7-110">After you accept, close the window.</span></span> <span data-ttu-id="660a7-111">Es wird eine Seite angezeigt, die wie folgt aussehen kann.</span><span class="sxs-lookup"><span data-stu-id="660a7-111">You'll see a page that may look like this.</span></span> <span data-ttu-id="660a7-112">Sie können die Fehlermeldung auf der Seite ignorieren.</span><span class="sxs-lookup"><span data-stu-id="660a7-112">You can ignore the error message on the page.</span></span> <span data-ttu-id="660a7-113">Sie ist harmlos und gibt an, dass die Zustimmung gewährt wird.</span><span class="sxs-lookup"><span data-stu-id="660a7-113">It's harmless and indicates that consent is granted.</span></span> <span data-ttu-id="660a7-114">(Wir arbeiten an einer benutzerfreundlicheren Seite für diese URL.</span><span class="sxs-lookup"><span data-stu-id="660a7-114">(We're working on a more user-friendly page for this URL.</span></span> <span data-ttu-id="660a7-115">Bleiben Sie dran!)</span><span class="sxs-lookup"><span data-stu-id="660a7-115">Stay tuned!)</span></span>

    ![Screenshot der App "Berechtigungsanforderung für Patienten"](../../media/patients-app-permissions-request-granted.png)
2. <span data-ttu-id="660a7-117">Melden Sie sich mit Ihren Administratoranmeldeinformationen beim [Azure-Portal](https://portal.azure.com) an.</span><span class="sxs-lookup"><span data-stu-id="660a7-117">Sign in to the [Azure portal](https://portal.azure.com) with your admin credentials.</span></span>
3. <span data-ttu-id="660a7-118">Wählen Sie in der linken Navigationsleiste **Azure Active Directory**aus, und wählen Sie dann **Enterprise-Anwendungen**aus.</span><span class="sxs-lookup"><span data-stu-id="660a7-118">In the left navigation, select **Azure Active Directory**, and then select **Enterprise Applications**.</span></span>
    <span data-ttu-id="660a7-119">Suchen Sie nach einer Zeile mit dem Namen **patients (dev)**, und kopieren Sie dann den Wert in der Spalte **Objekt-ID** in Ihre Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="660a7-119">Look for a row named **Patients (dev)**, and then copy the value in the **Object ID** column to your clipboard.</span></span>
    <span data-ttu-id="660a7-120">![Screenshot der Zeile "Patienten (dev)" im Azure-Portal](../../media/patients-app-azure-portal-object-id.png)</span><span class="sxs-lookup"><span data-stu-id="660a7-120">![Screenshot of Patients (dev) row in Azure portal](../../media/patients-app-azure-portal-object-id.png)</span></span>
4. <span data-ttu-id="660a7-121">Wechseln Sie zur Azure-API für FHIR-Ressourceninstanz, mit der Sie die Patienten-App verbinden möchten (entweder durchsuchen oder durch Durchsuchen Ihrer Ressourcen), und öffnen Sie dann die Einstellungen für diese Instanz.</span><span class="sxs-lookup"><span data-stu-id="660a7-121">Go to the Azure API for FHIR resource instance to which you want to connect the Patients app (either by searching for it or by browsing through your resources), and then open the settings for that instance.</span></span>

    ![Screenshot der Azure-API für FHIR-Instanzen Einstellungen in Azure Portal](../../media/patients-app-azure-portal-instance-settings.png)

5. <span data-ttu-id="660a7-123">Klicken Sie auf **Authentifizierung**, und fügen Sie dann die Objekt-ID, die Sie in Schritt 3 kopiert haben, in das Feld **zugelassene Objekt-IDs** ein.</span><span class="sxs-lookup"><span data-stu-id="660a7-123">Click **Authentication**, and then paste the object ID that you copied in step 3 to the **Allowed object IDs** box.</span></span> <span data-ttu-id="660a7-124">Dadurch kann die Patienten-App auf den FHIR-Server zugreifen.</span><span class="sxs-lookup"><span data-stu-id="660a7-124">This allows the Patients app to access the FHIR server.</span></span> <span data-ttu-id="660a7-125">Nachdem Sie die Objekt-ID eingefügt haben, wird Sie von Azure Active Directory überprüft, und daneben wird ein grünes Häkchen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="660a7-125">After you paste the object ID, Azure Active Directory validates it, and a green check mark appears next to it.</span></span>

    ![Screenshot der Authentifizierungseinstellungen in Azure Portal](../../media/patients-app-azure-portal-authentication.png)

6. <span data-ttu-id="660a7-127">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="660a7-127">Click **Save**.</span></span> <span data-ttu-id="660a7-128">Dadurch wird die Instanz erneut bereitgestellt, was einige Minuten dauern kann.</span><span class="sxs-lookup"><span data-stu-id="660a7-128">This redeploys the instance, which can take a few minutes.</span></span>
7. <span data-ttu-id="660a7-129">Klicken Sie auf **Übersicht**, und kopieren Sie dann die URL aus **FHIR-metadatenpunkt**.</span><span class="sxs-lookup"><span data-stu-id="660a7-129">Click **Overview**, and then copy the URL from **FHIR metadata endpoint**.</span></span> <span data-ttu-id="660a7-130">Entfernen Sie das Metadata-Tag, um die FHIR-Server-URL abzurufen.</span><span class="sxs-lookup"><span data-stu-id="660a7-130">Remove the metadata tag to get the FHIR server URL.</span></span> <span data-ttu-id="660a7-131">Beispiel: https://test02-teamshealth.azurehealthcareapis.com/.</span><span class="sxs-lookup"><span data-stu-id="660a7-131">For example, https://test02-teamshealth.azurehealthcareapis.com/.</span></span> 

    ![Screenshot des Metadaten-Endpunkts in Azure Portal](../../media/patients-app-azure-portal-metadata-endpoint.png)

8. <span data-ttu-id="660a7-133">Wechseln Sie in Teams zur Instanz der Patienten-APP, die in Ihrem Team geladen ist, klicken Sie auf **Einstellungen**, und geben Sie dann im Feld **Link** die URL des FHIR-Servers ein.</span><span class="sxs-lookup"><span data-stu-id="660a7-133">In Teams, go to the Patients app instance that's loaded in your team, click **Settings**, and then in the **Link** box, enter the FHIR server endpoint URL.</span></span> <span data-ttu-id="660a7-134">Klicken Sie dann auf **verbinden** , um eine Verbindung herzustellen, und suchen und Hinzufügen von Patienten zu Ihrer Liste.</span><span class="sxs-lookup"><span data-stu-id="660a7-134">Then, click **Connect** to establish a connection and search and add patients to your list.</span></span>  

    ![Screenshot der App-Einstellungen für Patienten in Microsoft Teams](../../media/patients-app-teams.png)
    
    <span data-ttu-id="660a7-136">Wenn beim Herstellen einer Verbindung mit Teams während dieses Schritts eine Fehlermeldung angezeigt wird, senden Sie einen detaillierten Screenshot des Fehlers, Protokolle von [Fiddler](https://www.telerik.com/download/fiddler) und alle anderen Repro Schritte in einer e-Mail mit einer Betreffzeile der Problembehandlung "Patienten-App – EMR-Modus" zu [teamsforhealthcare@Service.Microsoft.com](mailto:teamsforhealthcare@service.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="660a7-136">If you get an error when connecting to Teams during this step, send a detailed screenshot of the error, logs from [Fiddler](https://www.telerik.com/download/fiddler) and any other repro steps in an email with a subject line of “Patients App – EMR mode troubleshooting” to [teamsforhealthcare@service.microsoft.com](mailto:teamsforhealthcare@service.microsoft.com).</span></span>

## <a name="related-topics"></a><span data-ttu-id="660a7-137">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="660a7-137">Related topics</span></span>

- [<span data-ttu-id="660a7-138">Übersicht der Patienten-App</span><span class="sxs-lookup"><span data-stu-id="660a7-138">Patients app overview</span></span>](patients-app-overview.md)
- [<span data-ttu-id="660a7-139">Integration von elektronischen Datensätzen aus dem Gesundheitswesen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="660a7-139">Integrating Electronic Healthcare Records into Microsoft Teams</span></span>](patients-app.md)