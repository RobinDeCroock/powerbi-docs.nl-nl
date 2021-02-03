---
title: Inhoud insluiten in uw toepassing voor ingesloten analyses in Power BI voor betere ingesloten BI-inzichten voor uw organisatie
description: Informatie over het integreren van Power BI in uw toepassing met behulp van software voor ingesloten analyse, hulpprogramma's voor ingesloten analyse of hulpprogramma's voor ingesloten business intelligence. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494952"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>Zelf studie: Power BI inhoud insluiten met behulp *van een voor beeld insluiten voor uw organisatie* toepassing

Met Power BI embedded Analytics kunt u Power BI inhoud zoals rapporten, Dash boards en tegels insluiten in uw toepassing.

In deze zelfstudie leert u het volgende:

>[!div class="checklist"]
>* Uw embedded omgeving instellen.
>* Een *voor beeld van een invoeg toepassing voor uw organisatie* configureren (ook wel bekend als *gebruiker is eigenaar van gegevens*).

Als u uw toepassing wilt gebruiken, moeten uw gebruikers zich aanmelden bij Power BI.

De oplossing Insluiten voor uw organisatie wordt doorgaans gebruikt door ondernemingen en grote organisaties en is bedoeld voor interne gebruikers.

## <a name="code-sample-specifications"></a>Specificaties voor codevoorbeeld

Deze zelf studie bevat instructies voor het configureren van een *insluiting voor uw voorbeeld toepassing voor uw organisatie* in een van de volgende frameworks:

* .NET Framework
* .NET Core
* Type script reageren

>[!NOTE]
>Met de *.net core* -en de *.NET Framework* -voor beelden kan de eind gebruiker een Power bi dash board, rapport of tegel bekijken waartoe ze toegang hebben in Power bi-service. Met het voor beeld van *reageren type script* kunt u slechts één rapport insluiten waarmee uw eind gebruiker al toegang heeft tot Power bi-service.

De codevoorbeelden ondersteunen de volgende browsers:

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>Vereisten

Voordat u met deze zelfstudie begint, controleert u of u over de Power BI- en codeafhankelijkheden beschikt die hieronder worden vermeld:

* **Power BI-afhankelijkheden**

    * Uw eigen [Azure Active Directory-tenant](create-an-azure-active-directory-tenant.md).

    * Een van de volgende licenties:

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [Premium per gebruiker (PPU)](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >Als u [wilt overstappen op productie](move-to-production.md) , hebt u een van de volgende configuraties nodig:
    >* Alle gebruikers met Pro-licenties.
    >* Alle gebruikers met PPU-licenties.
    >* Een [capaciteit](embedded-capacity.md). Met deze configuratie kunnen alle gebruikers gratis licenties hebben.

* **Codeafhankelijkheden**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (of hoger)
    
    * Een geïntegreerde ontwikkelomgeving (IDE of Integrated Development Environment). Het is raadzaam een van de volgende opties te gebruiken:

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[Type script reageren](#tab/react)

    * Een tekst editor

    * Opdracht regel Terminal (of Power shell)

---

## <a name="method"></a>Methode

Voer de volgende stappen uit om een *voor beeld-app voor het insluiten van uw organisatie* te maken:

1. [Registreer een Microsoft Azure Active Directory-app](#step-1---register-an-azure-ad-application).

2. [Maak een Power BI-werkruimte](#step-2---create-a-power-bi-workspace).

3. [Maak en publiceer een Power BI-rapport](#step-3---create-and-publish-a-power-bi-report).

4. [Haal de parameterwaarden voor de insluiting op](#step-4---get-the-embedding-parameter-values).

5. [Sluit uw inhoud in](#step-5---embed-your-content).

## <a name="step-1---register-an-azure-ad-application"></a>Stap 1: een Azure AD-toepassing registreren

Als u uw toepassing registreert met Azure AD, kunt u een identiteit voor uw app instellen.

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>Stap 2: een Power BI-werk ruimte maken

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>Stap 3: een Power BI rapport maken en publiceren

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>Stap 4: de waarden voor het insluiten van para meters ophalen

Als u uw inhoud wilt insluiten, moet u enkele parameter waarden ophalen. De parameter waarden die u nodig hebt, zijn afhankelijk van de taal van de voorbeeld toepassing die u wilt gebruiken. In de volgende tabel ziet u welke parameter waarden voor elk voor beeld zijn vereist.

|Parameter  |.NET Core  |.NET Framework  |Type script reageren |
|---------|---------|---------|---------|
|[Client ID](#client-id) |![Is van toepassing op.](../../media/yes.png) |![Is van toepassing op.](../../media/yes.png)         |![Is van toepassing op.](../../media/yes.png) |
|[Clientgeheim](#workspace-id) |![Is van toepassing op.](../../media/yes.png) |![Is van toepassing op.](../../media/yes.png) |![Is niet van toepassing op.](../../media/no.png) |
|[Werkruimte-id]() |![Is niet van toepassing op.](../../media/no.png) |![Is niet van toepassing op.](../../media/no.png) |![Is van toepassing op.](../../media/yes.png) |
|[Rapport-id]() |![Is niet van toepassing op.](../../media/no.png) |![Is niet van toepassing op.](../../media/no.png) |![Is van toepassing op.](../../media/yes.png) |

### <a name="client-id"></a>Client-id

>[!TIP]
>**Van toepassing op:** ![ Van toepassing op. ](../../media/yes.png) . NET core ![ is van toepassing op. ](../../media/yes.png) . NET Framework ![ is van toepassing op. ](../../media/yes.png) Type script reageren

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>Clientgeheim

>[!TIP]
>**Van toepassing op:** ![ Van toepassing op. ](../../media/yes.png) . NET core ![ is van toepassing op. ](../../media/yes.png) . NET Framework ![ is niet van toepassing op. ](../../media/no.png) Type script reageren

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>Werkruimte-id

>[!TIP]
>**Van toepassing op:** ![ Is niet van toepassing op. ](../../media/no.png) . NET core ![ is niet van toepassing op. ](../../media/no.png) . NET Framework ![ is van toepassing op. ](../../media/yes.png) Type script reageren

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>Rapport-id

>[!TIP]
>**Van toepassing op:** ![ Is niet van toepassing op. ](../../media/no.png) . NET core ![ is niet van toepassing op. ](../../media/no.png) . NET Framework ![ is van toepassing op. ](../../media/yes.png) ReactTypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>Stap 5: uw inhoud insluiten

Met de Power BI Inge sloten voorbeeld toepassing kunt u een *insluiten voor uw organisatie* Power bi app maken.

Volg deze stappen om de voorbeeld toepassing *embed voor uw organisatie* te wijzigen om uw Power bi-rapport in te sluiten.

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. Afhankelijk van de taal die u voor de app wilt gebruiken, opent u een van de volgende mappen:

    * .NET Core
    * .NET Framework
    * Reageren-TS

    >[!NOTE]
    >De *voor beeld-toepassingen voor het insluiten van uw organisatie* ondersteunen alleen de hierboven genoemde frameworks. De voorbeeld toepassingen *Java*, *node js* en *python* , bieden alleen ondersteuning *[voor de oplossing insluiten voor uw klanten](embed-sample-for-customers.md)* .

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>Uw Azure AD-App configureren

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Open in *platform configuraties* uw *webplatform en* Voeg in het gedeelte **omleidings-uri's** toevoegen toe `https://localhost:5000/signin-oidc` .

    > [!NOTE]
    >Als **u geen webplatform hebt** , selecteert u **een platform toevoegen** en in het venster *platforms configureren* selecteert u **Web**.

6. Sla uw wijzigingen op.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text="Scherm opname van de configuraties voor Azure AD-verificatie met de omleiding U R I voor het .net core-app-voor beeld.":::

### <a name="configure-the-sample-embedding-app"></a>De voor beeld-app voor insluiten configureren

1. Open de map **insluiten voor uw organisatie** .

2. Open de *voor beeld-app insluiten voor uw organisatie* met een van de volgende methoden:

    * Als u [Visual Studio](https://visualstudio.microsoft.com/)gebruikt, opent u het bestand **UserOwnsData. SLN** .

    * Als u [Visual Studio code](https://code.visualstudio.com/)gebruikt, opent u de map **UserOwnsData** .

3. Open **appsettings.jsop** en vul de volgende parameter waarden in:

    * `ClientId` -De [client-id](#client-id) -GUID gebruiken

    * `ClientSecret`-Het [client geheim](#client-secret) gebruiken

### <a name="run-the-sample-app"></a>De voorbeeld-app uitvoeren

1. Voer het project uit door de juiste optie te selecteren:

    * Als u **Visual Studio** gebruikt, selecteert u **IIS Express** (afspelen).

    * Als u **Visual Studio Code** gebruikt, selecteert u **Uitvoeren > Foutopsporing starten**.

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>Uw Azure AD-App configureren

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Configureer het volgende in *platform configuraties*:

    1. In uw webplatform, *in de sectie* **omleidings-uri's** , toevoegen `https://localhost:44300/` .

        > [!NOTE]
        >Als **u geen webplatform hebt** , selecteert u **een platform toevoegen** en in het venster *platforms configureren* selecteert u **Web**.
    
    2. Schakel in *impliciete toekenning en hybride stromen* de optie **id-tokens** in.
    
6. Sla uw wijzigingen op.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text="Scherm opname van de configuraties van Azure AD-verificatie, waaronder de omleiding U R I en de geselecteerde toegangs token optie voor het .NET Framework-app-voor beeld.":::

### <a name="configure-the-sample-embedding-app"></a>De voor beeld-app voor insluiten configureren

1. Open de map **insluiten voor uw organisatie** .

2. Open in [Visual Studio](https://visualstudio.microsoft.com/)het bestand **UserOwnsData. SLN** .

3. Open **Web.config** en vul de volgende parameter waarden in:

    * `clientId` -De [client-id](#client-id) -GUID gebruiken

    * `clientSecret`-Het [client geheim](#client-secret) gebruiken

### <a name="run-the-sample-app"></a>De voorbeeld-app uitvoeren

1. Voer het project uit door **IIS Express** (afspelen) te selecteren.

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[Type script reageren](#tab/react)

### <a name="configure-your-azure-ad-app"></a>Uw Azure AD-App configureren

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Configureer in *platform configuraties* **uw** webplatform als volgt:

    1. In **omleidings-uri's** kunt `https://localhost:3000` **u configureren** toevoegen en selecteren.

        > [!NOTE]
        >Als **u geen webplatform hebt** , selecteert u **een platform toevoegen** en in het venster *platforms configureren* selecteert u **Web**.

    2. Schakel in *impliciete toekenning en hybride stromen* beide opties in:
        * **Toegangstokens**
        * **Id-tokens**
    
6. Sla uw wijzigingen op.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="Scherm opname van de configuraties voor Azure AD-verificatie met de omleiding U R I die U hebt ingesteld voor localhost 3000.":::

### <a name="configure-the-sample-embedding-app"></a>De voor beeld-app voor insluiten configureren

1. Open de map **insluiting voor uw organisatie**  >  **UserOwnsData**  >   .

2. Open met een tekst editor het bestand **config. TS** en vul de volgende parameter waarden in:

    * `clientId` -De [client-id](#client-id) -GUID gebruiken

    * `workspaceId`-De [werk ruimte-id](#client-secret) gebruiken

    * `reportId`-De [rapport-id](#report-id) gebruiken

3. Sla het bestand op.

### <a name="run-the-sample-app"></a>De voorbeeld-app uitvoeren

1. Open een terminal in en navigeer naar **embed voor uw organisatie**  >  **UserOwnsData**.

2. Installeer de vereiste afhankelijkheden door de volgende opdracht uit te voeren:

   `npm install`

3. Voer de toepassing uit door de volgende opdracht uit te voeren:

   `npm run start`

    >[!NOTE]
    >Wanneer u zich voor het eerst aanmeldt, wordt u gevraagd Azure AD-machtigingen voor de app toe te staan.

---

## <a name="developing-your-application"></a>Uw toepassing ontwikkelen

Na het configureren en uitvoeren van de voorbeeld-app voor het *insluiten voor uw klanten*, kunt u beginnen met het ontwikkelen van uw eigen app.

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
>[Verplaatsen naar productie](move-to-production.md)

>[!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Gepagineerde rapporten insluiten voor uw klanten](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Gepagineerde rapporten voor uw organisatie insluiten](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Stel een vraag aan de Power BI-community](https://community.powerbi.com/)