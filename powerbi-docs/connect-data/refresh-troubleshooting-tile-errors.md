---
title: Problemen met tegelfouten oplossen
description: Veelvoorkomende fouten bij het vernieuwen van een tegel in Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/06/2018
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f82c6c97b954745e264fe213b5070a9a498de939
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410707"
---
# <a name="troubleshooting-tile-errors"></a>Problemen met tegelfouten oplossen
Hieronder vindt u een overzicht en uitleg van enkele veelvoorkomende fouten voor tegels.

> [!NOTE]
> Als u een fout tegenkomt die hieronder niet wordt vermeld en die problemen veroorzaakt, kunt u om hulp vragen op de [site van de community](https://community.powerbi.com/) of een [ondersteuningsticket](https://powerbi.microsoft.com/support/) maken.
> 
> 

## <a name="errors"></a>Fouten
**Er is een onverwachte fout voor Power BI opgetreden tijdens het laden van het model. Probeer het later opnieuw.**
of **Het gegevensmodel kan niet worden opgehaald. Neem contact met de eigenaar van het dashboard op om te controleren of de gegevensbronnen en het model bestaan en toegankelijk zijn.**

We hebben geen toegang tot uw gegevens omdat de gegevensbron niet bereikbaar is. Het probleem kan zich voordoen als de naam van de gegevensbron is gewijzigd, als de gegevensbron is verwijderd, verplaatst of offline is of als de machtigingen zijn gewijzigd. Controleer of de bron zich nog op de locatie bevindt waarnaar wordt verwezen en u nog over de toegangsmachtiging beschikt. Als dit het probleem niet is, is de bron mogelijk langzaam. Probeer het later opnieuw, op een moment dat de bron minder zwaar wordt belast. Als het een on-premises bron betreft, kan de eigenaar van de bron mogelijk meer informatie verstrekken.

**U hebt geen toestemming om deze tegel weer te geven of de werkmap te openen.**

Neem contact op met de eigenaar van het dashboard om te controleren of de gegevensbronnen en het model bestaan en toegankelijk zijn voor uw account.

**Power BI-visuals zijn door uw beheerder uitgeschakeld.**

De Power BI-beheerder heeft het gebruik van Power BI-visuals voor uw organisatie of beveiligingsgroep uitgeschakeld.
U kunt geen Power BI- visuals van de [Microsoft marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) gebruiken of persoonlijke visuals importeren vanuit een bestand. U kunt alleen de vooraf verpakte set visuals gebruiken.


**Gegevensshapes moeten minstens één groep of één berekening bevatten die gegevens uitvoert. Neem contact op met de eigenaar van het dashboard.**

Er kunnen momenteel geen gegevens worden weergegeven, omdat de query leeg is. Voeg enkel velden uit de lijst met velden toe aan uw visual en maak deze opnieuw vast.

**Kan de gegevens niet weergeven omdat de relatie tussen twee of meer velden niet kan worden vastgesteld met Power BI.**

U probeert twee of meer velden uit niet-gerelateerde tabellen te gebruiken. U moet de niet-gerelateerde velden uit de visual verwijderen en vervolgens een relatie tussen de tabellen maken. Zodra u deze wijziging hebt doorgevoerd, kunt u de velden weer toevoegen aan de visual. Dit kan worden gedaan in Power BI Desktop of Power Pivot voor Excel. [Meer informatie](../transform-model/desktop-create-and-manage-relationships.md)

**De groepen op de primaire en secundaire as overlappen. Groepen op de primaire as kunnen niet dezelfde sleutels hebben als groepen op de secundaire as.**

Dit is doorgaans een tijdelijk probleem. Dit gebeurt meestal wanneer u groepen uit rijen naar kolommen verplaatst. In dit geval moet de fout verdwijnen wanneer alle groepen zijn verplaatst. Als het bericht nog steeds wordt weergegeven, kunt u de velden in de rijen en kolommen wisselen of de as-legenda of verwijdert u velden uit de visual.  

**De beschikbare resources zijn overschreden voor deze weergave. U kunt filteren om de hoeveelheid weergegeven gegevens te verminderen.**

Er zijn te veel gegevens met uw visual gezocht om alle resultaten met de beschikbare bronnen te kunnen verwerken. Filter de visual om de hoeveelheid gegevens in de resultaten te reduceren.

**Kan de volgende velden niet identificeren: {0}. Werk het visuele element bij met velden die onderdeel zijn van de gegevensset.**

Het veld is waarschijnlijk verwijderd of de naam van het veld is gewijzigd. U kunt het desbetreffende veld uit de visual verwijderen, een ander veld toevoegen en dit opnieuw vastmaken.

**Kan de gegevens voor dit visuele element niet ophalen. Probeer het later opnieuw.**

Dit is doorgaans een tijdelijk probleem. Als u het later opnieuw probeert en dit bericht nog steeds wordt weergegeven, neemt u contact op met de ondersteuning.

**Tegels blijven ongefilterde gegevens weergeven na het inschakelen van eenmalige aanmelding (SSO).**

Dat kan gebeuren als de onderliggende gegevensset is geconfigureerd voor het gebruik van de DirectQuery-modus of van een live-verbinding met Analysis Services via een on-premises gegevensgateway. In dit geval blijven de tegels de niet-gefilterde gegevens weergeven nadat SSO voor de gegevensbron is ingeschakeld, totdat de volgende tegel wordt vernieuwd. Bij de volgende tegelvernieuwing gebruikt Power BI SSO zoals geconfigureerd en tonen de tegels de gefilterde gegevens op basis van de identiteit van de gebruiker. 

Als u de gefilterde gegevens meteen wilt bekijken, kunt u het vernieuwen van tegels ook afdwingen door **Meer opties** (...) te selecteren in de rechterbovenhoek van een dashboard en vervolgens **Dashboardtegels vernieuwen** te selecteren.

Als eigenaar van een gegevensset kunt u ook de vernieuwingsfrequentie van tegels wijzigen en deze instellen op 15 minuten om het vernieuwen van tegels te versnellen. Selecteert het tandwiel in de rechterbovenhoek van de Power BI-service en selecteer **Instellingen**. Selecteer op de pagina **Instellingen** het tabblad **Gegevenssets**. Vouw **Geplande vernieuwing van cache** uit en wijzig **Vernieuwingsfrequentie**. Zorg ervoor dat u de configuratie opnieuw instelt op de oorspronkelijke vernieuwingsfrequentie nadat Power BI de volgende tegelvernieuwing heeft uitgevoerd.

> [!NOTE]
> De sectie **Geplande vernieuwing van cache** is alleen beschikbaar voor gegevenssets in de modus DirectQuery/LiveConnection. Voor gegevenssets in de importmodus is geen afzonderlijke tegelvernieuwing vereist omdat de tegels automatisch worden vernieuwd tijdens de volgende geplande gegevensvernieuwing.

## <a name="contact-support"></a>Contact opnemen met de ondersteuning
Als u nog steeds problemen ondervindt, [neemt u contact op met de ondersteuning](https://support.powerbi.com) om het probleem nader te onderzoeken.

## <a name="next-steps"></a>Volgende stappen
[Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  
[Problemen met Power BI Gateway - Personal oplossen](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
