---
title: Gebruikers de mogelijkheid geven om visuals in een rapport aan te passen
description: Laat lezers van rapporten hun eigen weergave van een rapport maken zonder het te bewerken.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 27f71da8a8396de30254c1a02307aa48281db5a8
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83793601"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Gebruikers de mogelijkheid geven om visuals in een rapport aan te passen

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Wanneer u een rapport met een breed publiek deelt, willen sommige van uw gebruikers mogelijk enigszins verschillende weergaven van bepaalde visuals zien. Misschien willen ze elementen op de as omwisselen, het type visual wijzigen of iets toevoegen aan de knopinfo. Het is moeilijk om één visual te maken die voldoet aan de vereisten van iedereen. Met deze nieuwe functionaliteit kunt u uw gebruikers machtigen om visuals te verkennen en aan te passen, en dit allemaal in de leesweergave voor rapporten. Ze kunnen de visuals op elke gewenste manier aanpassen, en deze opslaan als bladwijzer om ernaar terug te gaan. Ze hoeven geen bewerkingsmachtiging voor het rapport te hebben of contact op te nemen met de auteur van het rapport om een wijziging aan te brengen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Een visual aanpassen":::
 
## <a name="what-report-consumers-can-change"></a>Welk rapport kunnen gebruikers wijzigen

Met deze functie kunnen gebruikers meer inzichten in een Power BI-rapport krijgen door middel van een ad-hoconderzoek van visuals. Zie [Visuals aanpassen in uw rapporten](../consumer/end-user-personalize-visuals.md) voor meer informatie over het gebruik van deze functie als gebruiker. De functie is ideaal voor makers van rapporten die voor de lezers van hun rapporten basisscenario's voor onderzoek mogelijk willen maken. Dit zijn de wijzigingen die lezers van rapporten kunnen aanbrengen:

- Het type visualisatie wijzigen
- Een meting of afmeting uitwisselen
- Een legenda toevoegen of verwijderen
- Twee of meer metingen vergelijken
- Aggregaties enzovoort wijzigen

Deze functie biedt niet alleen de mogelijkheid om nieuwe functies te verkennen. Deze omvat ook manieren waarop gebruikers hun wijzigingen kunnen vastleggen en delen:

- Hun wijzigingen vastleggen
- Hun wijzigingen delen
- Al hun wijzigingen voor een rapport herstellen
- Al hun wijzigingen voor een visual herstellen
- Recente wijzigingen wissen

## <a name="turn-on-the-preview-feature"></a>De preview-functie inschakelen

Omdat deze functie in preview is, moet u eerst de functieswitch inschakelen. Ga naar **Bestand** > **Opties en instellingen** > **Opties**. Controleer of onder **Globale** instellingen > **Preview-functies** **Visuals aanpassen** is geselecteerd.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Visuals aanpassen inschakelen":::

Mogelijk moet u Power BI Desktop opnieuw opstarten om deze configuratie weer te geven in de instellingen voor het huidige bestand.

## <a name="enable-personalization-in-a-report"></a>Aanpassing inschakelen in een rapport

Nadat u de previewswitch hebt ingeschakeld, moet u deze specifiek inschakelen voor de rapporten waarvoor u wilt dat gebruikers visuals kunnen aanpassen.

U kunt deze functie inschakelen in Power BI Desktop en in de Power BI-service.

### <a name="in-power-bi-desktop"></a>In Power BI Desktop

Als u de functie in Power BI Desktop wilt inschakelen, gaat u naar **Bestand** > **Opties en instellingen** > **Opties**  > **Huidige bestand**  > **Rapportinstellingen**. Zorg ervoor **Visuals aanpassen (preview)** is ingeschakeld.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Aanpassing inschakelen in een rapport":::

### <a name="in-the-power-bi-service"></a>In de Power BI-service

Als u in plaats daarvan de functie wilt inschakelen in de Power BI-service, gaat u naar **Instellingen** voor uw rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Rapportinstellingen in de Power BI-service":::

Schakel **Visuals aanpassen (preview)**  > **Opslaan** in.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Visuals aanpassen inschakelen in de service":::

## <a name="select-visuals-that-can-be-personalized"></a>Visuals selecteren die kunnen worden aangepast

Wanneer u deze instelling inschakelt voor een bepaald rapport, kunnen standaard alle visuals in dat rapport worden aangepast. Als u niet wilt dat alle visuals worden aangepast, kunt u de instelling per visual in- of uitschakelen.

Selecteer de visual > selecteer **Indeling** in het deelvenster **Visualisaties** > vouw **Visuele koptekst** uit.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Visuele koptekst selecteren":::
 
Zet de schuifregelaar **Visual aanpassen** >  **Aan** of **Uit**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="De schuifregelaar van Visual aanpassen aan- of uitzetten":::


## <a name="limitations-and-known-issues"></a>Beperkingen en bekende problemen

Op dit moment heeft de functie enkele beperkingen waarmee u rekening moet houden.

- Deze functie wordt niet ondersteund voor insluitingsscenario's, waaronder Publiceren op internet.
- Onderzoekingen van gebruikers blijven niet automatisch behouden. U moet uw weergave opslaan als een persoonlijke bladwijzer om uw wijzigingen vast te leggen.
- Deze functie wordt ondersteund in de mobiele apps van Power BI Mobile voor iOS en Android-tablets en in de Power BI Windows-app. Het wordt niet ondersteund in de Power BI Mobile Apps voor telefoons. Wijzigingen in de visual die u in de Power BI-service in een persoonlijke bladwijzer opslaat, worden echter in alle mobiele Power BI-apps aangehouden.

Er zijn ook enkele bekende problemen die kunnen worden opgelost:

- Het toevoegen van een hiërarchie wordt niet ondersteund; u moet de afzonderlijke onderliggende items toevoegen.
- U kunt een datumhiërarchie niet wijzigen in een datum of vice versa. 
- Met persoonlijke bladwijzers krijgt u mogelijk resultaten die enigszins verschillen op basis van de reeks die u selecteert. Discrepanties zijn mogelijk omdat de volledige status van het rapport niet is vastgelegd, maar alleen de wijzigingen die zijn aangebracht. De tijdelijke oplossing is om **Standaardinstelling herstellen** te selecteren en vervolgens de bladwijzer te selecteren die u wilt weergeven. 

## <a name="next-steps"></a>Volgende stappen

[Visuals aanpassen in uw rapporten](../consumer/end-user-personalize-visuals.md).     

Probeer de nieuwe ervaring met visuals aanpassen eens. Geef ons feedback over deze functie en vertel ons hoe we deze kunnen blijven verbeteren. Ga hiervoor naar de [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
