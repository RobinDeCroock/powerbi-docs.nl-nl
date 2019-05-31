---
title: Sjabloon-apps maken in Power BI (preview-versie)
description: Informatie over het maken van sjabloon-apps in Power BI die u naar elke Power BI-klant kunt distribueren.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: maggies
ms.openlocfilehash: 653050fbe5c860ef1902a4700c3a70a8af2f7092
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514957"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Een sjabloon-app maken in Power BI (preview-versie)

Met de nieuwe Power BI-*sjabloon-apps* kunnen Power BI-partners Power BI-apps maken met weinig of geen code en deze implementeren naar elke Power BI-klant.  Dit artikel bevat stapsgewijze instructies voor het maken van een Power BI-sjabloon-app.

Als u Power BI-rapporten en dashboards maken kunt, kunt u meer een *sjabloon app builder* en bouwt en verpakt analytische inhoud in een *app*. U kunt uw app implementeren in andere Power BI-tenants via elk beschikbaar platform, zoals AppSource, of met behulp van deze in uw eigen webservice. Als een opbouwfunctie hebt u de mogelijkheid om een beveiligde analytics-pakket voor distributie te maken.

Power BI-tenantbeheerders beheren en bepalen wie er binnen hun organisatie sjabloon-apps kan maken en wie deze kan installeren. Gebruikers die zijn gemachtigd kunnen uw sjabloon-app installeren en vervolgens wijzigen en deze distribueren naar de Power BI-gebruikers in hun organisatie.

## <a name="prerequisites"></a>Vereisten

Dit zijn de vereisten voor het bouwen van een sjabloon-app:  

- Een [Power BI Pro-licentie](service-self-service-signup-for-power-bi.md)
- De [installatie van Power BI Desktop](desktop-get-the-desktop.md) (optioneel)
- Vertrouwd zijn met de [basisconcepten van Power BI](service-basic-concepts.md)
- Machtigingen voor het maken van een sjabloon-app. Zie de Power BI-[beheerderportal en Instellingen voor sjabloon-apps](service-admin-portal.md#template-apps-settings-preview) voor meer informatie.

## <a name="enable-app-developer-mode"></a>Modus voor app-ontwikkelaars inschakelen

Voor het maken van een sjabloon-app die u naar andere Power BI-tenants kunt distribueren, moet u zich in de modus voor app-ontwikkelaars bevinden. Anders maakt u alleen een app voor Power BI-gebruikers in uw eigen organisatie.

1. Open de Power BI-service in een browser.
2. Ga naar **Instellingen** > **Algemeen** > **Ontwikkelaar** > **Ontwikkelingsmodus voor sjabloon-apps inschakelen**.

    ![Sjabloon-apps inschakelen](media/service-template-apps-create/power-bi-dev-template-app.png)

    Als u deze optie niet ziet, neemt u contact op met uw Power BI-beheerder om u [machtigingen voor de ontwikkeling van sjabloon-apps](service-admin-portal.md#template-apps-settings-preview) te verlenen in de beheerportal.

3. Selecteer **Toepassen**.

## <a name="create-the-template-app-workspace"></a>De werkruimte voor sjabloon-apps maken

Voor het maken van een sjabloon-app die u naar andere Power BI-tenants kunt distribueren, moet u de app in een van de nieuwe app-werkruimten maken.

1. In de Power BI-service selecteert u **Werkruimten** > **App-werkruimte maken**.

    ![App-werkruimte maken](media/service-template-apps-create/power-bi-new-workspace.png)

2. Selecteer in **Een app-werkruimte maken** in **Voorbeeld weergeven van verbeterde werkruimten** de optie **Nu proberen**.

    ![Nieuwe werkruimten proberen](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

3. Voer een naam, beschrijving (optioneel) en logoafbeelding (optioneel) voor uw app-werkruimte in.

4. Selecteer **Een sjabloon-app ontwikkelen**.

    ![Een sjabloon-app ontwikkelen](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selecteer **Opslaan**.
>[!NOTE]
>U moet machtigingen van uw Power BI-beheerder om te promoten sjabloon apps.

## <a name="create-the-content-in-your-template-app"></a>De inhoud van uw sjabloon-app maken

Net als bij een normale Power BI-app-werkruimte is de volgende stap het maken van de inhoud in de werkruimte.  In deze preview-versie van sjabloon-apps, wordt slechts één van elk type ondersteund: één gegevensset, één rapport en één dashboard.

- [Maak uw Power BI-inhoud](power-bi-creator-landing.md) in uw app-werkruimte.

Als u parameters in Power Query gebruikt, moet u ervoor zorgen dat deze een goed gedefinieerd type (bijvoorbeeld Text) hebben. De typen Any en Binary worden niet ondersteund.

[Tips voor het ontwerpen van sjabloon-apps in Power BI (preview)](service-template-apps-tips.md) bevat suggesties die u kunt overwegen bij het maken van rapporten en dashboards voor uw app-sjabloon.

## <a name="create-the-test-template-app"></a>De testsjabloon-app maken

Nu u inhoud in uw werkruimte hebt, kunt u deze verpakken in een sjabloonapp. De eerste stap is het maken van een testsjabloon-app, die alleen toegankelijk is binnen uw organisatie op uw tenant.

1. Selecteer **App maken** in de werkruimte van de sjabloon-app.

    ![App maken](media/service-template-apps-create/power-bi-create-app.png)

    Hier kunt vul u in gebouw aanvullende opties voor uw sjabloon-app in vijf categorieën:

    **Huisstijl**

    ![Huisstijl](media/service-template-apps-create/power-bi-create-branding.png)
    - App-naam
    - Beschrijving
    - Voor ondersteuningssite (koppeling wordt weergegeven onder app-gegevens na het opnieuw distribueren sjabloon-app als org app)
    - App-logo (maximumbestandsgrootte 45 kB, hoogte-breedteverhouding 1:1, .png jpg, JPEG indelingen)
    - De kleur van de App-thema

    **Inhoud**

    **Landingspagina van App:** Een rapport of dashboard wilt worden van de startpagina van uw app, gebruikt u een landingspagina waarmee de juiste indruk definiëren:

    ![Inhoud](media/service-template-apps-create/power-bi-create-content.png)

    **Besturingselement**

    Limieten en beperkingen die de gebruikers van uw toepassingen met de inhoud van uw toepassing instellen. U kunt dit besturingselement gebruiken ter bescherming van intellectueel eigendom in uw app.

    ![Besturingselement](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >Exporteren naar de .pbix-indeling is altijd geblokkeerd voor gebruikers installeren de app.

    **Parameters**

    Deze categorie gebruiken voor het beheren van parameter gedrag bij het verbinden met gegevensbronnen. Meer informatie over [het maken van queryparameters](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parameters](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Waarde**: parameter standaardwaarde.
    - **Vereiste**: Gebruik dit om te vereisen dat het installatieprogramma voor het invoeren van een bepaalde gebruiker-parameter.
    - **Vergrendeling**: Vergrendeling voorkomt dat het installatieprogramma voor het bijwerken van een parameter.
    - **Statische**: Schakel in het geval de app bevat *alleen* sample van gegevens. Wanneer u selecteert **statische**, de installatiewizard wordt niet gevraagd gebruikers verbinding maken met een gegevensbron.

    **Toegang tot** In de testfase, bepalen welke anderen in uw organisatie kunnen installeren en testen van uw app. Geen probleem, kunt u altijd terugkeren en deze instellingen later wijzigen (instelling heeft geen invloed op de toegang van de gedistribueerde sjabloon-app).

2. Selecteer **App maken**.

    U ziet een bericht dat de test-app gereed is, met daarin een koppeling om de app te kopiëren en te delen met de testers van uw app.

    ![Test-app is gereed](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    U hebt ook de eerste stap van het publicatiebeheerproces uitgevoerd, dat hieronder wordt uiteengezet.

## <a name="manage-the-template-app-release"></a>De publicatie van de sjabloon-app beheren

Voordat u deze sjabloon-app openbaar maakt, moet u controleren of de app helemaal klaar is voor gebruik. Power BI heeft een deelvenster voor publicatiebeheer gemaakt, waarin u het volledige publicatiepad van de app kunt volgen en controleren. U kunt de overgang ook per fase activeren. Dit zijn de algemene fasen:

- Test-app genereren: de app alleen in uw organisatie testen.
- Het testpakket promoveren naar de preproductiefase: de app buiten uw organisatie testen.
- Het preproductiepakket promoveren naar productie: productieversie.
- Een pakket verwijderen of opnieuw beginnen vanaf de vorige fase.

De URL wijzigen niet omdat u tussen fasen van de release verplaatsen. Promotie heeft geen invloed op de URL zelf.

Hieronder volgen de fasen:

1. Selecteer **Publicatiebeheer** in de werkruimte van de sjabloon-app.

    ![Pictogram voor Publicatiebeheer](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Selecteer **App maken**.

    Als u de test-app hebt gemaakt in het gedeelte **De testsjabloon-app maken** hierboven, is de gele stip naast **Testen** al gevuld en hoeft u **App maken** hier niet te selecteren. Als u App maken wel selecteert, gaat u terug naar het proces voor het maken van de sjabloon-app.

3. Selecteer **Koppeling ophalen**.

    ![App maken, koppeling ophalen](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Als u de installatie van de app wilt testen, kopieert u de koppeling in het meldingenvenster en plakt u deze in een nieuw browservenster.

    Vanaf hier volgt u dezelfde procedure als uw klanten. Zie [Install and distribute template apps in your organization](service-template-apps-install-distribute.md) (Sjabloon-apps in uw organisatie installeren en distribueren) voor hun versie.

5. Selecteer **Installeren** in het dialoogvenster.

    Wanneer de installatie is geslaagd, ziet u een melding dat de nieuwe app gereed is.

6. Selecteer **Naar de app**.
7. In **Aan de slag met uw nieuwe app** ziet u uw app zoals uw klanten deze ook zullen zien.

    ![Aan de slag met uw app](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Selecteer **App verkennen** om de test-app te controleren met de voorbeeldgegevens.
9. Als u wijzigingen wilt aanbrengen, gaat u terug naar de app in de oorspronkelijke werkruimte. Werk de test-app bij totdat u helemaal tevreden bent.
10. Als u klaar om te promoten van uw app naar Pre-productie voor het testen van meer buiten uw tenant bent, gaat u terug naar de **Release Management** deelvenster en selecteer **opwaarderen app**. 

    ![De app promoveren naar de preproductiefase](media/service-template-apps-create/power-bi-template-app-promote.png)

    >[!NOTE]
    > Wanneer de app wordt gepromoveerd wordt deze openbaar beschikbaar gesteld buiten uw organisatie.

11. Selecteer **Niveau verhogen** om uw keuze te bevestigen.
12. Kopieer deze nieuwe URL om de app buiten uw tenant te testen. Deze koppeling wordt ook u indienen om te beginnen met het proces van het distribueren van uw Apps weer op AppSource door het maken van een [nieuwe aanbieding voor Cloud Partner-Portal](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Verzend alleen Pre-productie-koppelingen naar de Cloud Partner-Portal. Nadat de app is goedgekeurd en u een melding dat deze is gepubliceerd in AppSource, kunt u dit pakket naar productie in Power BI promoveren.
13. Wanneer uw app gereed is voor productie of kan worden gedeeld via AppSource, gaat u terug naar het deelvenster **Publicatiebeheer** en selecteert u **App promoten** naast **Vóór productie**.
14. Selecteer **Niveau verhogen** om uw keuze te bevestigen.

    Uw app is nu in productie en gereed voor distributie.

    ![App in productie](media/service-template-apps-create/power-bi-template-app-production.png)

Als u uw app algemeen beschikbaar wilt stellen voor duizenden Power BI-gebruikers wereldwijd, raden we u aan de app te verzenden naar AppSource. Zie de [aanbieding voor Power BI-toepassing](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) voor meer informatie.

## <a name="update-your-app"></a>Uw app bijwerken

Nu uw app in productie is, kunt u opnieuw beginnen in de testfase, zonder de app in productie te onderbreken.

1. Selecteer **App maken** in het deelvenster **Publicatiebeheer**.
2. Ga terug via het proces voor het maken van een app.
3. Nadat u **Huisstijl**, **Inhoud**, **Besturingselement** en **Toegang** hebt ingesteld, selecteert u **App maken** opnieuw.
4. Selecteer **Sluiten** en ga terug naar **Publicatiebeheer**.

   U hebt nu twee versies: De versie in productie en een nieuwe versie in de testfase.

    ![Twee versies van een sjabloon-app](media/service-template-apps-create/power-bi-template-app-2-versions.png)

5. Wanneer u klaar om te promoten van uw app naar Pre-productie voor het testen van meer buiten uw tenant bent, gaat u terug naar het deelvenster met Release Management en selecteer **opwaarderen app** naast **testen**.
6. De koppeling is nu live, het opnieuw verzenden naar de Cloud Partner-Portal met de volgende stappen op [update van Power BI-App-aanbieding](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).

>[!NOTE]
>Promoot uw app naar de productiefase nadat uw app is goedgekeurd door de Cloud Partner-Portal en u deze hebt gepubliceerd.

## <a name="next-steps"></a>Volgende stappen

Zie hoe uw klanten werken met uw sjabloon-app in [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Sjabloon-apps in uw organisatie installeren, aanpassen en distribueren).

Zie de [aanbieding voor Power BI-toepassing](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) voor meer informatie over het distribueren van uw app.
