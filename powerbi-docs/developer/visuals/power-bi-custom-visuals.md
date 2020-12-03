---
title: Visuals in Power BI
description: In dit artikel worden aangepaste Power BI-visuals beschreven
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: overview
ms.date: 07/14/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 91c9115f7d9ca0eb15606fcd77f99070e949842e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416756"
---
# <a name="visuals-in-power-bi"></a>Visuals in Power BI

Power BI wordt geleverd met veel kant-en-klare Power BI-visuals. Deze visuals zijn beschikbaar in het visualisatiedeelvenster van zowel [Power BI Desktop](https://powerbi.microsoft.com/desktop/) als de [Power BI-service](https://app.powerbi.com) en kunnen worden gebruikt voor het maken en bewerken van Power BI-inhoud.

:::image type="content" source="media/power-bi-custom-visuals/power-bi-visualizations.png" alt-text="Schermopname van het Power BI-deelvenster Visualisaties zoals dit wordt weergegeven in Power BI Desktop en de Power BI-service.":::

Er zijn veel meer Power BI-visuals beschikbaar via de Microsoft [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) of via Power BI. Deze visuals worden gemaakt door Microsoft en Microsoft-partners, en ze worden getest en gevalideerd door het AppSource-validatieteam.

U kunt ook uw eigen Power BI-visual ontwikkelen die vervolgens kan worden gebruikt door uzelf, uw organisatie of de hele Power BI-community.

## <a name="default-power-bi-visuals"></a>Standaard Power BI-visuals

Dit zijn de kant-en-klare Power BI-visuals die beschikbaar zijn in het visualisatiedeelvenster in *Power BI Desktop* en de *Power BI-service*.

Als u een Power BI-visual van het visualisatiedeelvenster wilt losmaken, klikt u er met de rechtermuisknop op en selecteert u **Losmaken**.

Als u de standaard Power BI-visuals in het visualisatiedeelvenster wilt herstellen, klikt u op **Een aangepaste visual importeren** en selecteert u **Standaardvisuals herstellen**. 

## <a name="appsource-power-bi-visuals"></a>AppSource-visuals in Power BI

Microsoft en Communityleden hebben ten behoeve van het algemene belang Power BI-visuals bijgedragen en deze naar de [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) gepubliceerd. U kun deze visuals downloaden en toevoegen aan uw Power BI-rapporten. Deze Power BI-visuals zijn door Microsoft getest op functionaliteit en kwaliteit en goedgekeurd.

>[!NOTE]
>* Door Power BI-visuals te gebruiken die met onze SDK zijn gemaakt, kunt u gegevens importeren uit of verzenden naar externe of andere services buiten het geografische gebied, de jurisdictie of het nationale cloudexemplaar van uw Power BI-tenant.
>* Gecertificeerde Power BI-visuals zijn visuals in AppSource die als aanvulling zijn getest om te controleren of de visual geen toegang heeft tot externe services of resources.
>* Zodra Power BI-visuals vanuit AppSource zijn geïmporteerd, kunnen visuals zonder extra kennisgeving automatisch worden bijgewerkt.

### <a name="what-is-appsource"></a>Wat is AppSource?

In [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) vindt u apps, invoegtoepassingen en uitbreidingen voor uw Microsoft-software. AppSource is de plek waar miljoenen gebruikers van producten zoals Microsoft 365, Azure, Dynamics 365, Cortana en Power BI oplossingen vinden die hen helpen efficiënter en slimmer te werken.

### <a name="certified-power-bi-visuals"></a>Gecertificeerde visuals in Power BI

Gecertificeerde Power BI-visuals zijn visuals in de [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) die voldoen aan bepaalde vereisten voor opgegeven code die zijn getest en goedgekeurd door het Microsoft Power BI-team. De testen zijn ontworpen om te controleren of de visual geen toegang heeft tot externe services of resources.

Zie [Gecertificeerde Power BI-visuals](power-bi-custom-visuals-certified.md) voor de lijst met gecertificeerde Power BI-visuals of om uw eigen visuals in te dienen.

### <a name="samples-for-power-bi-visuals"></a>Voorbeelden voor Power BI-visuals

Elke Power BI-visual in AppSource bevat een gegevensvoorbeeld waarmee wordt aangetoond hoe de visual werkt. Als u het voorbeeld wilt downloaden, selecteert u in de [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) een Power BI-visual en klikt u in de sectie *Voorbeeld proberen* op de koppeling **voorbeeldrapport**.

## <a name="organizational-store"></a>Organisatiearchief

Power BI-beheerders moeten Power BI-visuals in hun organisatie goedkeuren en implementeren. Zo kunnen auteurs van rapporten deze Power BI-visuals gemakkelijk detecteren, bijwerken en gebruiken. Beheerders kunnen deze visuals eenvoudig beheren met acties zoals het bijwerken van versies, en het uitschakelen en het inschakelen van Power BI-visuals.

Als u toegang wilt krijgen tot het archief van de organisatie, klikt u in het deelvenster *Visualisatie* op **Een aangepaste visual importeren**, selecteert u **Importeren uit Marketplace** en selecteert u boven in het venster *Power BI-visuals* het tabblad **Mijn organisatie**.

[Meer informatie over organisatievisuals](power-bi-custom-visuals-organization.md).

## <a name="visual-files"></a>Bestanden met visuals

Power BI-visuals zijn pakketten die code bevatten voor het weergeven van de gegevens die aan deze visuals worden geleverd. Iedereen kan een aangepaste visual maken en die inpakken als één `.pbiviz`-bestand dat in een Power BI-rapport kan worden geïmporteerd.

Als u een Power BI-visual wilt importeren, klikt u in het deelvenster *Visualisatie* op **Een aangepaste visual importeren** en selecteert u **Importeren uit bestand**.

Als u een webontwikkelaar bent en geïnteresseerd bent in het maken van uw eigen visual en deze wilt toevoegen aan AppSource, kunt u leren hoe u [een Power BI-visual van een cirkelkaart ontwikkelt](develop-circle-card.md) en [een Power BI-visual naar AppSource publiceert](office-store.md).

> [!WARNING]
> Een Power BI-visual kan code bevatten met beveiligings- of privacyrisico's. Controleer of u de auteur en bron van de Power BI-visuals vertrouwt voordat u ze in uw rapport importeert.

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Een visual van een cirkelkaart ontwikkelen in Power BI](develop-circle-card.md)

>[!div class="nextstepaction"]
>[Projectstructuur van Power BI-visuals](visual-project-structure.md)

>[!div class="nextstepaction"]
>[Richtlijnen voor Power BI-visuals](guidelines-powerbi-visuals.md)

>[!div class="nextstepaction"]
>[Veelgestelde vragen](power-bi-custom-visuals-faq.md)

>[!div class="nextstepaction"]
>[Power BI-community](https://community.powerbi.com/)