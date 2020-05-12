---
title: Gebruikers de mogelijkheid geven om visuals in een rapport aan te passen
description: Laat lezers van rapporten hun eigen weergave van een rapport maken zonder het te bewerken.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867111"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Gebruikers de mogelijkheid geven om visuals in een rapport aan te passen

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Wanneer u een rapport met een breed publiek deelt, willen sommige van uw gebruikers mogelijk enigszins verschillende weergaven van bepaalde visuals zien. Misschien willen ze elementen op de as omwisselen, het type visual wijzigen of iets toevoegen aan de knopinfo. Het is moeilijk om één visual te maken die voldoet aan de vereisten van iedereen. Met deze nieuwe functionaliteit kunt u uw gebruikers machtigen om visuals te verkennen en aan te passen, en dit allemaal in de leesweergave voor rapporten. Ze kunnen de visuals op elke gewenste manier aanpassen, en deze opslaan als bladwijzer om ernaar terug te gaan. Ze hoeven geen bewerkingsmachtiging voor het rapport te hebben of contact op te nemen met de auteur van het rapport om een wijziging aan te brengen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Een visual aanpassen":::
 
## <a name="what-report-consumers-can-change"></a>Welk rapport kunnen gebruikers wijzigen

Met deze functie kunnen gebruikers meer inzichten in een Power BI-rapport krijgen door middel van een ad-hoconderzoek van visuals. De functie is ideaal voor makers van rapporten die voor de lezers van hun rapporten basisscenario's voor onderzoek mogelijk willen maken. Dit zijn de wijzigingen die lezers van rapporten kunnen aanbrengen:

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

## <a name="personalize-visuals-in-the-power-bi-service"></a>Visuals aanpassen in de Power BI-service

Door een visual aan te passen, kunnen uw gebruikers uw gegevens op verschillende manieren verkennen zonder de leesweergave van het rapport te verlaten. In de volgende voorbeelden ziet u verschillende manieren waarop gebruikers een visualisatie kunnen aanpassen om deze aan hun wensen te laten voldoen. 

1. Open een rapport in de leesweergave in de Power BI-service.

2. Selecteer in de rechterbovenhoek van de visual het pictogram **Deze visual aanpassen** ![Het pictogram Deze visual aanpassen](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Het type visualisatie wijzigen

U kunt de visualisatie in een andere weergave bekijken door het **Visualisatietype** te wijzigen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Visualisatie wijzigen":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Een meting of afmeting uitwisselen
U kunt een meting of afmeting op de X-as vervangen door het veld te selecteren dat u wilt vervangen en vervolgens een andere meting of afmeting te selecteren.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="De as wijzigen":::
 
### <a name="add-or-remove-a-legend"></a>Een legenda toevoegen of verwijderen
Door een legenda toe te voegen, kunt u een visual van een kleurcode voorzien op basis van een categorie. U kunt de categorische kleurcodering verwijderen door het selectievakje **Legenda** uit te schakelen in het deelvenster **Aanpassen**. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="De legenda toevoegen of verwijderen":::

### <a name="compare-two-or-more-different-measures"></a>Twee of meer verschillende metingen vergelijken
U kunt waarden voor verschillende metingen vergelijken en contrasteren met behulp van het plus-pictogram om meerdere metingen in een visual toe te voegen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Metingen vergelijken":::

### <a name="change-aggregations"></a>Aggregaties wijzigen
U kunt wijzigen hoe een meting wordt berekend door de aggregatie te wijzigen in het deelvenster **Aanpassen**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Aggregaties wijzigen":::

### <a name="capture-changes"></a>Wijzigingen vastleggen 
Gebruik persoonlijke bladwijzers om uw wijzigingen vast te leggen, zodat u kunt terugkeren naar uw aangepaste weergave. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Een bladwijzer maken":::
 
U kunt de bladwijzer ook instellen als standaardweergave.

### <a name="share-changes"></a>Wijzigingen delen 
Als u machtigingen voor lezen en opnieuw delen hebt, kunt u ervoor kiezen om uw wijzigingen in het rapport op te nemen wanneer u dit deelt.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Wijzigingen delen":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Al uw wijzigingen in een rapport herstellen

Selecteer **Standaardinstelling herstellen** om alle wijzigingen in het rapport te verwijderen en de door de auteur laatst opgeslagen weergave van het rapport te herstellen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Alle wijzigingen herstellen":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Al uw wijzigingen in een visual herstellen

Selecteer **Deze visual herstellen** om alle wijzigingen in een bepaalde visual te verwijderen en de door de auteur laatst opgeslagen weergave van de visual te herstellen.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Alle visuele wijzigingen herstellen":::
 
### <a name="clear-recent-changes"></a>Recente wijzigingen wissen

Selecteer het gumpictogram om alle recente wijzigingen te wissen die u hebt aangebracht sinds u het deelvenster **Aanpassen** hebt geopend.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Recente wijzigingen ongedaan maken":::

## <a name="limitations-and-known-issues"></a>Beperkingen en bekende problemen

Op dit moment heeft de functie enkele beperkingen waarmee u rekening moet houden.

- Deze functie wordt niet ondersteund voor insluitingsscenario's, waaronder Publiceren op internet.
- Onderzoekingen van gebruikers blijven niet automatisch behouden. U moet uw weergave opslaan als een persoonlijke bladwijzer om uw wijzigingen vast te leggen.
- U kunt geen visuals wijzigen in de mobiele Power BI-apps. Wijzigingen in de visual die u in de Power BI-service in een persoonlijke bladwijzer opslaat, worden echter in de mobiele apps aangehouden.

Er zijn ook enkele bekende problemen die kunnen worden opgelost:

- Het toevoegen van een hiërarchie wordt niet ondersteund; u moet de afzonderlijke onderliggende items toevoegen.
- U kunt een datumhiërarchie niet wijzigen in een datum of vice versa. 
- Met persoonlijke bladwijzers krijgt u mogelijk resultaten die enigszins verschillen op basis van de reeks die u selecteert. Discrepanties zijn mogelijk omdat de volledige status van het rapport niet is vastgelegd, maar alleen de wijzigingen die zijn aangebracht. De tijdelijke oplossing is om **Standaardinstelling herstellen** te selecteren en vervolgens de bladwijzer te selecteren die u wilt weergeven. 

## <a name="next-steps"></a>Volgende stappen

Probeer de nieuwe ervaring met visuals aanpassen eens. Geef ons feedback over deze functie en vertel ons hoe we deze kunnen blijven verbeteren. Ga hiervoor naar de [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

