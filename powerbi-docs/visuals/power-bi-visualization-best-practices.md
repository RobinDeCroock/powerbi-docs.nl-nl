---
title: Aanbevolen procedures voor het ontwerpen van rapporten en visuele elementen
description: In dit artikel worden de aanbevolen procedures voor het ontwerpen van rapporten in Power BI beschreven.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 53a8847f96d6aa3143e91cab07029a8e0f6afc85
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523748"
---
# <a name="best-design-practices-for-reports-and-visuals"></a>Aanbevolen procedures voor het ontwerpen van rapporten en visuele elementen

In dit artikel worden de aanbevolen procedures voor het ontwerpen van rapporten in Power BI beschreven. Er wordt aandacht besteed aan de beginselen van het ontwerpen die u kunt toepassen op uw rapporten, en op de pagina's en afzonderlijke visuele elementen die deel uitmaken van een rapport. Veel van deze aanbevolen procedures zijn ook van toepassing op het ontwerpen van het dashboard.

> [!NOTE]
> De aanbevelingen in dit artikel kunt u als richtlijn gebruiken wanneer ze van toepassing zijn. Houd er wel rekening mee dat er voor elk principe dat hieronder wordt beschreven uitzonderingen bestaan.

We hopen dat u dit document als uitgangspunt kunt gebruiken en het geleerde toepast op uw eigen rapporten en visuele elementen. Bovendien hopen we dat u verder met ons van gedachten wisselt op [Microsoft Power BI Community](http://community.powerbi.com/). Het ontwerp van BI-rapporten en het gebruik van visuele elementen is een populair onderwerp op dit moment. Er zijn veel thought leaders, bloggers en websites die uitgebreid aandacht hebben voor het ontwerpen van BI-rapporten. Aan het einde van het artikel vindt u een aantal koppelingen naar interessante informatie.

> *We worden overspoeld door informatie, niet omdat er te veel van is, maar omdat we niet weten hoe we het in goede banen moeten leiden.*
-- Stephen Few

## <a name="a-look-at-the-landscape-and-terminology"></a>Algemene aspecten en terminologie

In Power BI kan een rapport een of meer rapportpagina's hebben. Alle pagina's samen worden het rapport genoemd. De basiselementen van het rapport zijn visuele elementen (ook wel visualisaties of visuals genoemd in dit artikel), zelfstandige afbeeldingen en tekstvakken. Er zijn talloze opmaakopties voor de afzonderlijke gegevenspunten, de rapportelementen en de rapportpagina zelf.

We beginnen met de planningsfase van het rapport, gaan verder met de basisbeginselen voor het ontwerpen van rapporten, bespreken daarna de beginselen voor visuele ontwerpen en sluiten af met een beschrijving van de aanbevolen procedures voor afzonderlijke typen visuele elementen.

Gedetailleerde richtlijnen en instructies voor het maken en gebruiken van Power BI-rapporten vindt u in [Met Power BI leren werken](https://powerbi.microsoft.com/learning/).

## <a name="before-you-build-your-first-visualization-focus-on-requirements"></a>Vereisten controleren voordat u uw eerste visuele element maakt

Het maken van een rapport begint al voordat u het eerste visuele element maakt. Een goed rapport vereist namelijk planning. Ga na met welke gegevens u gaat werken en noteer de vereisten voor het rapport. Stel uzelf deze vragen:

* Wat heeft het bedrijf nodig?

* Hoe gaan de lezers deze gegevens gebruiken?

* Wie gaat deze gegevens gebruiken?

* Welke beslissingen wil de gebruiker kunnen nemen op basis van dit rapport?

Het antwoord op deze vragen vormt de basis van uw ontwerp. Elk rapport vertelt een verhaal. Zorg ervoor dat het verhaal aansluit bij de bedrijfsbehoefte. Het kan verleidelijk zijn om visuele elementen toe te voegen die indrukwekkende inzichten opleveren, maar als deze inzichten niet aansluiten bij de bedrijfsbehoefte, heeft het rapport geen enkel nut. De gebruikers worden mogelijk alleen maar afgeleid door deze visuele elementen. Misschien merkt u ook dat de gegevens niet geschikt zijn om de informatie af te leiden die nodig is om dit besluit te nemen. Kunt u dit rapport gebruiken om te meten wat u wilt meten?

U kunt rapporten onder andere gebruiken voor controleren, achterhalen, bijhouden, voorspellen, meten, beheren en testen. Zo kan de bedrijfsbehoefte een verkooprapport zijn waarin de prestaties worden gemeten. U kunt dan een rapport maken waarin de huidige verkoopcijfers worden vermeld en worden vergeleken met voorgaande verkoopcijfers en met die van concurrenten. Daarnaast kunt u een aantal KPI's opnemen waarmee waarschuwingen worden geactiveerd. Misschien kunnen gebruikers inzoomen op de verkoopcijfers om filiaalsluitingen of problemen met de toeleveringsketen te bekijken die mogelijk van invloed zijn op de verkoop. Misschien kan er ook worden ingezoomd op de omzet per filiaal, regio, product, seizoen enzovoort.

Het is belangrijk om te weten wie de klanten voor het rapport zijn. Ontwerp een rapport waarin vertrouwde terminologie wordt gebruikt en dat gegevens bevat met een detail- en complexiteitsniveau dat aansluit bij het kennisniveau van de klant. Hebt u verschillende soorten klanten? Er is niet altijd één pasklare oplossing. Ontwerp afzonderlijke rapportpagina's die zijn gebaseerd op kennis. Zorg ervoor dat elke pagina duidelijk is gelabeld zodat klanten snel hun weg kunnen vinden. U kunt ook slicers gebruiken, zodat gebruikers de pagina aan hun eigen wensen kunnen aanpassen. Betrek de gebruiker bij de planning en ga er bij het maken van een rapport niet vanuit dat u wel weet wat de gebruiker wil. Als u deze fout maakt, zult u helemaal opnieuw moeten beginnen.

Wanneer u de bedrijfsbehoefte, de klanten en de gewenste metrische gegevens hebt bepaald, kiest u in de volgende stap de juiste visuele elementen om uw verhaal te vertellen. Bepaal hoe u deze visuele elementen zo effectief mogelijk kunt presenteren. Laten we beginnen met enkele basisbeginselen van het ontwerpen van rapporten.

## <a name="principles-of-report-design"></a>Beginselen voor het ontwerpen van rapporten

Een rapportpagina heeft maar beperkte ruimte en het is een hele opgave om alle gewenste elementen in die ruimte te passen en de informatie toch begrijpelijk te houden. Ook is het belangrijk om de waarde van een visueel aantrekkelijke rapport niet te onderschatten. Het is dan ook cruciaal om de balans te vinden tussen een rapport dat er mooi uitziet en dat zinvol is.

Laten we de opmaak, duidelijkheid en vormgeving van het rapport eens bekijken.

### <a name="layout-of-the-report-canvas"></a>Indeling van het rapportcanvas

Het canvas van een rapport heeft een beperkte hoeveelheid ruimte. Als niet alle elementen op één rapportpagina passen, verdeelt u het rapport over meerdere pagina's. U kunt een rapportpagina afstemmen op een specifieke doelgroep (bijvoorbeeld HR, IT, Verkoop, SLT). Als u wilt, kunt u een pagina ook toespitsen op een specifieke zakelijke vraag:

* "Hoe hebben fouten invloed hebben op onze downtime?"

* "Wat is de impact van onze marketingcampagne op het sentiment?"

Het is misschien beter om te kiezen voor een verhaal dat zich steeds verder ontwikkelt. Misschien op de eerste pagina een overzicht of een statement om de aandacht te trekken, op de tweede pagina kunt u het verhaal dan verder uitwerken, waarna u op de derde pagina de diepte ingaat, enzovoort. Als het hele rapport op één pagina past, is dat ook prima. Als dat niet het geval is, maakt u afzonderlijke rapportpagina's waarop de inhoud logisch wordt verdeeld. Geef de pagina's een betekenisvolle en nuttige naam.

U kunt het maken van een rapport vergelijken met het inrichten van een kunstgalerie. U zou ook geen 50 kunstwerken in een kleine zaal plaatsen, deze met stoelen vullen en elke muur in een andere kleur verven. Als de curator kiest u alleen de werken die een gemeenschappelijk thema hebben. U zou ze verspreiden over de galerie, met voldoende ruimte voor de bezoekers om rond te lopen en te reflecteren. U zou zelfs informatiekaartjes kunnen gebruiken die beschrijven waar mensen naar kijken. Het is geen toeval dat de meeste galeries met moderne kunst witte muren hebben!

We beginnen dit document met een voorbeeld van een rapport dat veel werk vereist. Naarmate we de aanbevolen procedures en beginselen voor het ontwerpen van rapporten toepassen, wordt ons rapport beter.

![Er moet heel wat verbeterd worden aan deze rommelige rapportpagina](media/power-bi-visualization-best-practices/power-bi-example1newa.png)

**Afbeelding 1: er moet heel wat verbeterd worden aan deze rommelige rapportpagina**

Het bovenstaande voorbeeld bevat veel ontwerpproblemen die betrekking hebben op de ruimte (opmaak) die we hieronder zullen bespreken:

* Uitlijning, volgorde en nabijheid

* Slecht gebruik van ruimte en sortering

* Onoverzichtelijk

### <a name="alignment-order-and-proximity"></a>Uitlijning, volgorde en nabijheid

De opmaak van de rapportelementen helpt de lezer om het rapport goed te begrijpen en door de rapportpagina te navigeren. Met het plaatsen en positioneren van de elementen brengt u een boodschap over. Deze boodschap kan zijn: ‘Begin hier en kijk vervolgens hier’ of ‘Deze drie elementen zijn aan elkaar gerelateerd’.

* In veel culturen nemen mensen een tekst van links naar rechts en van boven naar beneden door. Plaats het belangrijkste element daarom in de linkerbovenhoek van uw rapport. Orden de rest van de visuele elementen zo dat de gebruiker op een logisch manier door het rapport navigeert en de informatie goed begrijpt.

* Positioneer elementen waarbij de gebruiker een keuze moet maken, slicers bijvoorbeeld aan de linkerkant van de visualisaties waarop de keuze betrekking heeft.

* Plaats gerelateerde elementen dicht bij elkaar. Nabijheid is een visuele implicatie dat de elementen gerelateerd zijn.

* Een andere manier om aan te geven dat elementen zijn gerelateerd, is door rondom deze elementen een rand of gekleurde achtergrond te plaatsen. U kunt daarentegen een scheidingslijn aanbrengen om onderscheid te maken tussen de verschillende secties van een rapport.

* Gebruik open ruimte om secties als afzonderlijke onderdelen op de rapportpagina weer te geven.

* Vul de rapportpagina. Als er te veel witruimte is, maakt u de visuele elementen groter of het canvas kleiner.

* Bepaal het formaat van de rapportelementen op basis van het doel dat u wilt bereiken. Laat het formaat van een visualisatie niet afhangen van de beschikbare ruimte.

* Maak belangrijke elementen groter dan de andere elementen of voeg een visueel element, zoals een pijl, toe om hierop de aandacht te vestigen.

* Lijn de elementen op de rapportpagina symmetrisch of opzettelijk asymmetrisch uit.

Laten we de uitlijning eens nader bekijken.

#### <a name="alignment"></a>Uitlijning

Uitlijning betekent niet dat de verschillende onderdelen dezelfde grootte moeten hebben. Het betekent ook niet dat u op elke rij van het rapport hetzelfde aantal onderdelen moet hebben. Wat het wel betekent, is dat de pagina een structuur moet hebben die helpt bij het navigeren en die de leesbaarheid vergroot.

In het bijgewerkte rapport kunnen we zien dat we de rapportonderdelen hebben uitgelijnd op de linker- en rechterranden. Daarnaast hebben we de rijen van het rapport horizontaal en verticaal uitgelijnd. De slicers worden weergegeven aan de linkerkant van de visuele elementen waarop ze betrekking hebben.

![Ons rommelige rapportvoorbeeld is duidelijk verbeterd met deze aanpassingen van de opmaak.](media/power-bi-visualization-best-practices/power-bi-example2new.png)

**Afbeelding 2: ons rommelige voorbeeld is duidelijk verbeterd met de opmaakbewerkingen**

Power BI bevat hulpprogramma's waarmee u de visuele elementen kunt uitlijnen. Wanneer u in Power BI Desktop meerdere visuele elementen selecteert, kunt u met de opties **Uitlijnen** en **Verdelen** op het tabblad **Visual Tools** van het lint de positie van de visuele elementen met elkaar in overeenstemming brengen.

![Lijn visuele elementen uit in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization.png)

**Afbeelding 3a: hulpmiddelen voor uitlijnen van visuele elementen in Power BI Desktop**

![Lijn visuele elementen uit in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization-pbi-service.png)

**Afbeelding 3b: hulpmiddelen voor uitlijnen van visuele elementen in de Power BI-service**

In de Power BI-service en in Power BI Desktop hebt u ook nauwkeurige controle over de grootte en positie van visuele elementen. U vindt dit besturingselement op het tabblad **Algemeen** in het deelvenster **Indeling** voor alle visuele elementen:

![Stel de exacte positie voor het visuele element in.](media/power-bi-visualization-best-practices/power-bi-align-vizs.png)

**Afbeelding 4: de exacte positie voor het visuele element instellen**

In ons voorbeeld van de rapportpagina (afbeelding 2) zijn de twee kaarten en de lange rand uitgelijnd op de waarde 200 voor **X-positie**.

#### <a name="fit-to-the-space"></a>Aanpassen aan de ruimte

Gebruik de ruimte zo optimaal mogelijk. Als u weet hoe mensen het rapport weergeven en bekijken, kunt u het ontwerp daarop aanpassen. Verminder de lege ruimte zodat het canvas wordt opgevuld. Probeer het gebruik van schuifbalken voor afzonderlijke visuele elementen zo veel mogelijk te voorkomen. Vul de ruimte, maar laat de visuele elementen voldoende vrij.

##### <a name="adjust-the-page-size"></a>Het formaat van de pagina aanpassen

Door het formaat van de pagina te verkleinen, worden de afzonderlijke elementen groter ten opzichte van de gehele pagina. U kunt dit doen door de selectie van visuele elementen op de pagina uit te schakelen en het tabblad **Paginaformaat** in het deelvenster **Indeling** te gebruiken.

Hieronder wordt een rapportpagina weergegeven met het paginaformaat **4:3** en vervolgens met het paginaformaat **16:9**. U ziet dat de opmaak veel beter tot zijn recht komt bij het paginaformaat 16:9. Er is zelfs zo veel ruimte dat de schuifbalk van het tweede het visuele element kan worden verwijderd.

![Het rapport met het paginaformaat 4:3](media/power-bi-visualization-best-practices/power-bi-page-view-before.png)

**Afbeelding 5a: het rapport met het paginaformaat 4:3**

![Het rapport met het paginaformaat 16:9](media/power-bi-visualization-best-practices/power-bi-page-view-after.png)

**Afbeelding 5b: het rapport met het paginaformaat 16:9**

Gaan gebruikers uw rapport weergeven in het formaat 4:3, 16:9 of een andere hoogte-breedteverhouding? Op kleine of grote schermen? Of in alle mogelijke beeldverhoudingen en -formaten? Houd hier rekening mee bij het ontwerpen.

Ons voorbeeld van een rapportpagina ziet er nogal overvol uit. Ga als volgt te werk zonder dat er een visueel element is geselecteerd:

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Vouw **Paginaformaat** uit.

1. Selecteer **Aangepast** in de vervolgkeuzelijst **Type**.

1. Wijzig de waarde voor **Hoogte** in **900**.

    ![Maak de pagina hoger.](media/power-bi-visualization-best-practices/power-bi-page-size.png)

**Afbeelding 6: de paginahoogte vergroten**

#### <a name="reduce-clutter"></a>Een pagina overzichtelijker maken

Het is moeilijk om in een oogopslag inzicht te krijgen in een rommelige rapportpagina en dit kan de gebruikers afschrikken. Verwijder alle overbodige rapportelementen. Voeg geen functies toe als de duidelijkheid of navigatie daar niet bij gebaat is. De informatie op de rapportpagina moet duidelijk, snel en samenhangend overkomen.

Edward Tufte noemt het 'data to ink ratio' (verhouding van de kerninformatie tot het afgedrukte geheel) in zijn boek *The Visual Display of Quantitative Information*. Het komt er in feite op neer dat u alle onbelangrijke informatie verwijdert.

Hierdoor ontstaat er meer witruimte op de rapportpagina en dus meer ruimte om de aanbevolen procedures toe te passen die we hebben behandeld in de sectie [Uitlijning, volgorde en nabijheid](#alignment-order-and-proximity).

Ons voorbeeld ziet er hier al weer een stuk beter uit. We hebben overbodige elementen verwijderd en vormen toegevoegd om elementen te groeperen. De achtergrondafbeelding is verdwenen, evenals de overbodige pijl en het tekstvak, er is één visueel element verplaatst naar een andere pagina in het rapport, enzovoort. We hebben de pagina ook langer gemaakt om de witruimte te vergroten.

![Ons rommelig voorbeeldrapport overzichtelijk gemaakt.](media/power-bi-visualization-best-practices/power-bi-example3newer.png)

**Afbeelding 7: ons voorbeeld van een rommelig rapport is overzichtelijk gemaakt**

### <a name="tell-a-story-at-a-glance"></a>Een boodschap in een oogwenk overbrengen

Een rapport is goed ontworpen als een gebruiker zonder voorkennis en zonder uitleg van een ander snel begrijpt welke boodschap met het rapport wordt overgebracht. Gebruikers kunnen in een oogopslag zien waar de pagina over gaat en wat er met de grafieken/tabellen wordt bedoeld.

Als lezers het rapport bekijken, moet hun aandacht worden getrokken naar het element dat volgens u de hoogste prioriteit heeft. Vervolgens kunnen ze de pagina van links en rechts en van boven naar beneden scannen. U kunt deze standaardnavigatie door een rapport aanpassen door visuele aanwijzingen, zoals tekstvaklabels, vormen, randen en kleur toe te voegen of de grootte te wijzigen.

#### <a name="text-boxes"></a>Tekstvakken

Soms zijn titels bij visualisaties alleen niet voldoende om de boodschap over te brengen. Voeg tekstvakken toe om informatie te verstrekken aan de gebruikers die uw rapporten bekijken. Gebruik tekstvakken om een beschrijving te geven van de rapportpagina, een groep visuele elementen of een afzonderlijk visueel element. Met tekstvakken kunnen resultaten worden uitgelegd of een visueel element, onderdelen in het visuele element of relaties tussen visuele elementen nader worden gedefinieerd. U kunt tekstvakken gebruiken om de aandacht trekken op basis van verschillende criteria die in het tekstvak worden gebruikt.

Selecteer in de Power BI-service in de bovenste menubalk de optie **Tekstvak**. (Selecteer in Power BI Desktop de optie **Tekstvak** in het gebied **Invoegen** van het lint.)

![Voeg een tekstvak toe in de Power BI-service.](media/power-bi-visualization-best-practices/power-bi-text-boxes.png)

**Afbeelding 8: een tekstvak toevoegen in de Power BI-service**

Typ tekst in het lege vak. Gebruik vervolgens de besturingselementen om bijvoorbeeld het lettertype, de grootte en uitlijning in te stellen. Gebruik de grepen om het formaat van het vak aan te passen.

![Maak het tekstvak op.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Afbeelding 9: het tekstvak opmaken**

Overdrijf het echter niet! Te veel tekst in een rapport doet afbreuk aan de visuele elementen. Als u ontdekt dat er heel veel tekst nodig is om de rapportpagina begrijpbaar te maken, moet u opnieuw beginnen met het ontwerp. Kunt u een ander visueel element gebruiken dat meer voor zichzelf spreekt? Kunt u de systeemeigen titels van het visuele element aanpassen zodat het begrijpelijker is?

#### <a name="text"></a>Tekst

Maak een stijlgids voor de tekst en pas deze toe op alle pagina's van uw rapport. Gebruik maar een paar lettertypen, tekstgrootten en kleuren. Pas deze stijlgids toe op tekstuele elementen. Gebruik de gids ook bij het kiezen van de lettertypen die u in uw visuele elementen gebruikt. Zie het gedeelte [Titels en labels die deel uitmaken van de visuele elementen](#titles-and-labels-that-are-part-of-the-visualizations). Stel regels in voor het gebruik van onder andere een vet, cursief of groter lettertype of bepaalde kleuren. Vermijd het gebruik van woorden met uitsluitend hoofdletters of onderstreepte woorden.

#### <a name="shapes"></a>Vormen

Vormen kunnen ook bijdragen aan een duidelijker ontwerp en een betere navigatie. Gebruik vormen om gerelateerde gegevens te groeperen en belangrijke gegevens te markeren. Gebruik pijlen om de gebruiker in een bepaalde richting te leiden. Dankzij vormen weten gebruikers waar ze in het rapport moeten beginnen en hoe ze het moeten interpreteren. Dit wordt in het ontwerpen vaak aangeduid als *contrast*.

![Vormen in de Power BI-service.](media/power-bi-visualization-best-practices/shapes.png)

**Afbeelding 10a: vormen in de Power BI-service**

![Vormen in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-desktop-shapes2new.png)

**Afbeelding 10b: vormen in Power BI Desktop**

Hoe ziet onze voorbeeldpagina er nu uit? In afbeelding 11 ziet u een overzichtelijker, minder rommelige pagina met een consistent gebruik van lettertypen, tekengrootten en kleuren. De paginatitel in de linkerbovenhoek duidt het onderwerp van de pagina aan.

![Ons rapportvoorbeeld waarop de tekstrichtlijnen zijn toegepast en waaraan een titel is toegevoegd.](media/power-bi-visualization-best-practices/power-bi-example4new.png)

**Afbeelding 11: het rapportvoorbeeld waarop de tekstrichtlijnen zijn toegepast en waaraan een titel is toegevoegd**

In ons voorbeeld hebben we een titel voor de rapportpagina toegevoegd in de linkerbovenhoek. Dat is de eerste plek waar gebruikers naar kijken. De tekengrootte is 28 punten en het lettertype is Segoe Bold, zodat de titel opvalt en zich onderscheidt van de rest van de pagina. Onze tekststijlgids adviseert geen achtergronden, en zwarte titels, legenda's en labels. We hebben dit waar mogelijk toegepast op alle visuele elementen op de pagina (de assen en labels van de combinatiegrafiek kunnen niet worden bewerkt). Daarnaast zijn deze elementen geconfigureerd volgens de specificaties van de stijlgids:

* Kaarten: **Categorielabel** ingesteld op **Uit**, **Titel** op **Aan**, 12 punten, zwart en gecentreerd.

* Titels voor visuele elementen: Indien ingesteld op **Aan**, de grootte instellen op 12 punten en links uitlijnen.

* Slicers: **Koptekst** ingesteld op **Uit**, **Titel** op **Aan**. Laat **Items** > **Tekst** op grijs en 10 punten staan.

* Spreidings- en kolomdiagrammen: zwart lettertype voor X- en y-as en de titels voor beide assen, indien gebruikt.

#### <a name="color"></a>Kleur

Gebruik kleur voor de consistentie. De algemene aspecten van kleur bespreken we verderop in het gedeelte [Beginselen voor het ontwerpen van visuele elementen](#principles-of-visual-design). Hier gaan we in op het belang van het weloverwogen kiezen van kleuren. Het kleurgebruik moet zodanig zijn dat de kleur lezers niet belemmert in hun wens om snel een beeld van het rapport te krijgen. Wanneer u te veel heldere kleuren gebruikt, trekt dit te veel de aandacht. In dit gedeelte wordt meer beschreven wat u niet moet doen met een kleur.

#### <a name="backgrounds"></a>Achtergrond

Gebruik bij het instellen van een achtergrond voor de rapportpagina's kleuren die het rapport niet overschaduwen, niet vloeken met andere kleuren op de pagina of in het algemeen geen pijn doen aan de ogen. Houd er rekening mee dat sommige kleuren een inherente betekenis hebben. In de Verenigde Staten wordt rood in een rapport bijvoorbeeld meestal als negatief geïnterpreteerd.

![Stel de achtergrond van het rapport in.](media/power-bi-visualization-best-practices/power-bi-page-background.png)

**Afbeelding 12: de achtergrond van een rapport instellen**

U maakt geen kunstwerk, maar een functioneel rapport. Kies een kleur waardoor het rapport beter leesbaar wordt en die de rapportelementen goed uit de verf laat komen. Een onderzoek naar het gebruik van kleur en visuele elementen op webpagina's heeft aangetoond dat een groter contrast tussen kleuren zorgt voor een sneller begrip. In de volgende twee whitepapers wordt dit onderwerp nader besproken:

* [The effect of text and background color on visual search of Web pages](https://www.sciencedirect.com/science/article/pii/S0141938202000410)

* [Determining Users’ Perception of Web Page Visual Complexity and Aesthetic Characteristics](https://www.researchgate.net/publication/301362579_Determining_Users'_Perception_of_Web_Page_Visual_Complexity_and_Aesthetic_Characteristics)

We hebben een aantal aanbevolen procedures voor het gebruik van kleur toegepast op ons voorbeeldrapport (afbeeldingen 20 en 21). De opvallendste wijziging is dat we de achtergrondkleur hebben gewijzigd in zwart. Het geel was te fel en zorgde voor overbelaste ogen. In het diagram **Count of Athlete Name by Year and Medal Class** viel het gele gedeelte van de balken weg in de gele achtergrond. Door een zwarte (of witte) achtergrond te gebruiken, wordt het contrast optimaal en komt de focus op de visuele elementen te liggen.

Hier volgen de andere stappen die we hebben uitgevoerd om het voorbeeldrapport te verbeteren:

#### <a name="page-title"></a>Paginatitel

Toen we de achtergrond zwart hebben gemaakt, verdween de titel omdat in het tekstvak alleen een zwart lettertype kan worden gebruikt. U kunt dit probleem oplossen door een tekstvaktitel toe te voegen:

1. Selecteer het tekstvak en verwijder de tekst.

1. Zet op het tabblad **Visualisaties** de optie **Titel** op **Aan**.

1. Selecteer de pijl om de opties voor **Titel** weer te geven.

1. Typ **Summer Olympic Games** in het veld **Titeltekst**.

1. Selecteer wit bij **Tekenkleur**.

    ![Voeg een paginatitel toe.](media/power-bi-visualization-best-practices/power-bi-text-box-title.png)

    **Afbeelding 13: een paginatitel toevoegen**

#### <a name="cards"></a>Kaarten

Voor de visuele kaartelementen:

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Zet **Achtergrond** op **Aan**.

1. Selecteer de kleur wit en stel **Doorzichtigheid** in op **0%** .

    ![Achtergrondkleuren van kaart.](media/power-bi-visualization-best-practices/power-bi-card-background.png)

1. Zet **Titel** vervolgens op **Aan**.

1. Selecteer wit bij **Tekenkleur** en zwart bij **Achtergrondkleur**.

    ![Kleuren van kaarttitel.](media/power-bi-visualization-best-practices/power-bi-card-title.png)

#### <a name="slicers"></a>Slicers

Tot nu toe hadden de twee slicers een verschillende opmaak, iets wat normaal gesproken niet hoort in een goed ontwerp. Voor beide slicers: 

1. Wijzig de achtergrondkleur in aquamarijn.

    ![Wijzig de achtergrondkleur voor de slicers.](media/power-bi-visualization-best-practices/power-bi-slicer-background.png)

    **Afbeelding 14: de achtergrondkleur voor de slicers wijzigen**

    Aquamarijn is een goede keuze omdat het deel uitmaakt van het kleurenpalet van de pagina: de kleur wordt gebruikt in de choropletenkaart, de structuurkaart en het kolomdiagram.

1. Voeg een dunne witte rand toe.

    ![Voeg een rand toe aan de slicer.](media/power-bi-visualization-best-practices/power-bi-slicer-outline.png)

    **Afbeelding 15: een rand toevoegen aan de slicer**

1. Het grijze lettertype is moeilijk te zien tegen een zeeblauwe achtergrond. Wijzig de kleur voor **Items** in wit.

    ![Wijzig de tekstkleur voor de slicers.](media/power-bi-visualization-best-practices/power-bi-slicer-items.png)

    **Afbeelding 16: de tekstkleur voor de slicers wijzigen**

1. Wijzig ten slotte onder **Titel** de optie **Tekenkleur** in wit en stel **Achtergrondkleur** in op zwart.

    ![Maak de titel van de slicer op.](media/power-bi-visualization-best-practices/power-bi-card-formatting.png)

    **Afbeelding 17: de slicertitel opmaken**

#### <a name="rectangle-shape"></a>Rechthoek

De rechthoek is ook opgegaan in de zwarte achtergrond. U kunt dit probleem als volgt oplossen:

1. Selecteer de vorm.

1. Zet in het deelvenster **Vorm opmaken** de optie **Achtergrond** op **Aan**.

    ![De vorm opmaken](media/power-bi-visualization-best-practices/power-bi-shape-format.png)

    **Afbeelding 18: de vorm opmaken**

#### <a name="column-charts-bubble-chart-filled-map-and-treemap"></a>Kolomdiagrammen, bellendiagram, choropletenkaart en structuurkaart

Voeg een witte achtergrond toe aan de resterende visuele elementen op de rapportpagina. In het deelvenster **Indeling**:

1. Vouw de optie **Achtergrond** uit.

1. Selecteer wit bij **Kleur**.

1. Wijzig de waarde voor **Doorzichtigheid** in 0.

    ![Voeg een witte achtergrond toe aan de resterende visuele elementen.](media/power-bi-visualization-best-practices/power-bi-background.png)

    **Afbeelding 19: een witte achtergrond toevoegen aan de resterende visualisaties**

Het rapport ziet er zo uit nadat u de opmaak hebt aangepast:

![Rapportvoorbeeld waarop de aanbevolen procedures voor het gebruik van kleur zijn toegepast (zwarte achtergrond).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Afbeelding 20: rapportvoorbeeld waarop de aanbevolen procedures voor het gebruik van kleur zijn toegepast (zwarte achtergrond)**

![Rapportvoorbeeld waarop de aanbevolen procedures voor het gebruik van kleur zijn toegepast (witte achtergrond)](media/power-bi-visualization-best-practices/power-bi-example5b.png)

**Afbeelding 21: rapportvoorbeeld waarop de aanbevolen procedures voor het gebruik van kleur zijn toegepast (witte achtergrond)**

### <a name="aesthetics"></a>Vormgeving

We hebben hierboven een groot aantal aspecten van vormgeving beschreven: uitlijning, kleur, lettertypen en overzichtelijkheid. Er zijn nog een paar aanbevolen procedures voor het ontwerpen van rapporten die we niet mogen vergeten. Deze hebben betrekking op het algehele uiterlijk van het rapport.

Het doel van een rapport is uiteindelijk om in een bedrijfsbehoefte te voorzien, niet om een mooi plaatje te presenteren. Een bepaalde mate van aantrekkelijkheid is echter vereist omdat dit van belang is bij een eerste indruk. De consultant Tony Bodoh uit Nashville legt uit: "De emoties zijn de eerste halve seconde bepalend en daarna neemt de logica het over". Lezers reageren in eerste instantie op een emotioneel niveau op de rapportpagina voordat ze die goed gaan bestuderen. Als uw pagina er ongeordend, verwarrend en onprofessioneel uitziet, is het mogelijk dat de lezer de boodschap van uw rapport niet meekrijgt.

Blogger en branche-analist voor TechTarget Wayne Eckerson maakt een goede vergelijking. Het ontwerpen van een rapport is vergelijkbaar met het inrichten van een kamer. In de loop van de tijd koopt u een vaas, bank, bijzettafel en een schilderij. Afzonderlijk bevallen al deze elementen u. Maar hoewel elke afzonderlijke keuze begrijpelijk is, passen de spullen niet bij elkaar of concurreren ze om aandacht.

Let daarom op de volgende dingen:

* Bedenk een algemeen thema of gemeenschappelijke opmaak voor het rapport en pas deze toe op alle pagina's van het rapport.

* Gebruik op zichzelf staande afbeeldingen en andere illustraties die de boodschap ondersteunen en hier niet de aandacht van afleiden.

* Pas alle aanbevolen procedures toe die we tot nu toe hebben besproken.

## <a name="principles-of-visual-design"></a>Beginselen voor het ontwerpen van visuele elementen

We hebben de beginselen voor het ontwerpen van rapporten besproken en gezien hoe rapportelementen zo kunnen worden geordend dat de gebruiker gemakkelijk en snel inzicht krijgt in het rapport. Nu zullen we de beginselen voor het ontwerpen van de visuele elementen zelf bespreken. In het volgende gedeelte gaan we nader in op de afzonderlijke visuele elementen en bespreken we de aanbevolen procedures voor een aantal van de meest gebruikte typen.

We laten ons voorbeeldrapport even met rust en gebruiken een paar andere voorbeelden. Nadat we de beginselen voor het ontwerpen van visuele elementen hebben doorgenomen, keren we weer terug naar ons voorbeeld van de rapportpagina en passen we het geleerde toe (met stapsgewijze instructies).

### <a name="planning--choose-the-right-visual"></a>Planning: kies het juiste visuele element

Net zoals het belangrijk is dat u uw rapport plant voordat u het maakt, moet u dit ook doen voor elk visueel element. Stel uzelf de vraag 'Wat wil ik zeggen met dit visuele element?' en bepaal vervolgens welk visueel element de boodschap het beste ondersteunt. U kunt de voortgang in een verkoopcyclus weergeven in een staafdiagram, maar misschien wordt deze beter overgebracht via een watervalgrafiek of trechterdiagram. Lees voor hulp bij dit proces de laatste sectie van dit artikel, [Typen visuele elementen en aanbevolen procedures](#visual-types-and-best-practices). Hierin worden aanbevolen procedures beschreven voor enkele van de meest gebruikte typen visuele elementen. Het is goed mogelijk dat het eerste visuele element dat u kiest uiteindelijk niet de beste optie is. Probeer meerdere visuele elementen uit om te zien welke het beste werkt.

U moet het verschil begrijpen tussen kwantitatieve en categorische gegevens, en weten welke typen visuele elementen het meest geschikt zijn voor de verschillende typen gegevens. Kwantitatieve gegevens worden vaak aangeduid als metingen en zijn meestal numeriek. Categorische gegevens worden vaak aangeduid als dimensies en kunnen worden geclassificeerd. Dit wordt hieronder nader besproken in [Kies de juiste meetgegevens](#choose-the-right-measure).

Laat u niet verleiden om mooie of ingewikkelde typen visuele elementen te gebruiken met als enig doel het maken van een indrukwekkend rapport. Zoek gewoon de eenvoudigste optie om uw boodschap over te brengen. Met horizontale staafdiagrammen en eenvoudige lijndiagrammen kan informatie snel worden overgebracht. Gebruikers zijn ermee bekend en de informatie kan gemakkelijk worden afgelezen en geïnterpreteerd. Een bijkomend voordeel is dat de meeste mensen van links naar rechts en van boven naar beneden lezen. Deze twee diagramtypen kunnen daarom snel worden gescand en begrepen.

Moet er bij het visuele element worden gescrold om de boodschap te begrijpen? Zorg er, indien mogelijk, voor dat er niet hoeft te worden gescrold. Probeer te filteren en maak gebruik van hiërarchieën/drilldowns. Als dan nog steeds een schuifbalk nodig is, is het misschien beter om een ander type visueel element te kiezen. Als scrollen niet kan worden voorkomen, is het handig om te weten dat lezers liever horizontaal scrollen dan verticaal.

Zelfs wanneer u het ideale visuele element voor de boodschap kiest, moet dit mogelijk op andere manieren worden ondersteund om de boodschap goed over te brengen. Daarvoor kunt u labels, titels, menu's, kleur en grootte gebruiken. Deze ontwerpelementen komen verderop in het gedeelte [Ontwerpelementen](#design-elements) ter sprake.

### <a name="choose-the-right-measure"></a>Kies de juiste meetgegevens

Is de boodschap die door het visuele element wordt overgebracht boeiend? Is dat belangrijk? Maak visuele elementen niet alleen om visuele elementen te maken. Misschien had u gehoopt dat u met de gegevens een interessante boodschap kon overbrengen, maar is dat niet het geval. Begin gewoon overnieuw en zoek naar een interessantere boodschap. Het is ook mogelijk dat er niets mankeert aan de boodschap, maar dat deze op een andere manier moet worden gemeten.

Stel dat u het succes van uw verkoopmanagers wilt meten. Welke meetgegevens zou u hiervoor gebruiken? Kunt u dit het beste meten door te kijken naar de totale verkoop of de totale winst, de groei gedurende het voorgaande jaar of de prestaties ten opzichte van een gestelde target? Verkoopster Sandra boekt misschien de meeste winst, en als u de totale winst per verkoper in een staafdiagram zou weergeven, zouden ze met kop en schouders uitsteken boven de andere verkopers. Maar als Sandra hoge verkoopkosten (reiskosten, verzendkosten, productiekosten, enzovoort) heeft, wordt niet de volledige boodschap overgebracht als we alleen naar de verkoopcijfers kijken.

#### <a name="reflect-reality-dont-distort-reality"></a>De realiteit weerspiegelen en niet de realiteit verdraaien

Het is mogelijk om een visueel element te maken dat geen juist beeld geeft van de werkelijkheid. Er is een website waarop liefhebbers van gegevensanalyses 'slechte' visuele elementen delen. Uit de reacties komt naar voren dat men teleurgesteld is in het bedrijf dat het visuele element heeft gemaakt en gedistribueerd. Dit wekt de indruk bij het publiek dat het bedrijf niet kan worden vertrouwd.

Maak dus visuele elementen die de realiteit niet opzettelijk verdraaien en niet zodanig zijn bewerkt dat ze de boodschap overbrengen die u graag wilt vertellen. Hier volgt een voorbeeld:

![Een diagram met een verdraaide realiteit.](media/power-bi-visualization-best-practices/corp-success-distorted.png)

**Afbeelding 22: een diagram met een verdraaide realiteit**

In dit voorbeeld lijkt het of er een groot verschil is tussen de vier bedrijven en dat CorpB veel succesvoller is dan de andere drie bedrijven. Als u echter goed kijkt, ziet u dat de x-as niet bij nul begint en dat de verschillen tussen de bedrijven waarschijnlijk binnen de foutmarge vallen. Hieronder worden dezelfde gegevens weergegeven met een x-as die wel bij nul begint.

![Realistisch diagram.](media/power-bi-visualization-best-practices/corp-success.png)

**Afbeelding 23: realistisch diagram**

Lezers verwachten vaak dat de x-as bij nul begint en gaan hier dan ook vanuit. Als u besluit om niet bij nul te beginnen, doe dit dan op een manier die de resultaten niet verdraait. U kunt een visuele hint of het tekstvak toevoegen om de afwijking van de norm te vermelden.

### <a name="design-elements"></a>Ontwerpelementen

Wanneer u een type en meting hebt geselecteerd en het visuele element hebt gemaakt, kunt u de weergave afstemmen om een zo optimaal mogelijk resultaat te bereiken. In deze sectie wordt het volgende besproken:

* Opmaak, ruimte en grootte

* Tekstelementen: labels, aantekeningen, menu's en titels

* Sorteren

* Visuele interactie

* Kleur

#### <a name="tweaking-visuals-for-best-use-of-space"></a>Visuele elementen aanpassen zodat optimaal gebruik wordt gemaakt van de ruimte

Als u meerdere diagrammen in een rapport wilt opnemen, komt de boodschap van het rapport het beste tot zijn recht als u voor een optimale data-ink ratio zorgt. Zoals eerder vermeld, is Edward Tufte de bedenker van de zogenaamde 'data to ink ratio'. Het doel is om zoveel mogelijk markeringen uit een diagram te verwijderen zonder dat de gebruiker hierdoor wordt belemmerd om de gegevens te interpreteren.

In de eerste reeks grafieken hieronder staan overbodige aslabels: **Jan 2014**, **Apr 2014**, enzovoort. In de titels wordt **by Date** herhaald. Voor de titels van elke grafiek is ook aparte horizontale ruimte in elke grafiek nodig. Door de grafiektitels te verwijderen en afzonderlijke aslabels in te schakelen, verwijderen we een aantal gegevens en wordt er beter gebruikgemaakt van de totale ruimte. We kunnen de aslabels voor de eerste twee grafieken verwijderen om de hoeveelheid niet-essentiële informatie nog verder te beperken en meer ruimte te gebruiken voor de kerninformatie.

Als u de aandacht wilt vestigen op bepaalde perioden, kunt u lijnen of rechthoeken achter alle grafieken trekken zodat de gebruiker wordt aangespoord om deze perioden met elkaar te vergelijken.

![Vóór.](media/power-bi-visualization-best-practices/power-bi-multiples-before.png)

**Afbeelding 24: vóór**

![Na.](media/power-bi-visualization-best-practices/power-bi-multiples-after.png)

**Afbeelding 25: na**

**Astitels in- en uitschakelen**

1. Selecteer het visuele element om het te activeren.

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Vouw de opties voor **X-as** of **Y-as** uit.

1. Zet de schuifregelaar voor **Titel** op Aan of Uit.

    ![Schakel astitels in en uit.](media/power-bi-visualization-best-practices/power-bi-axis-titles.png)

    **Afbeelding 26: astitels in- en uitschakelen**

##### <a name="to-turn-axis-labels-on-and-off"></a>Aslabels in- en uitschakelen

1. Selecteer het visuele element om het te activeren.

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Naast de **x-as** en **y-as** worden schuifregelaars weergegeven.

1. Sleep met de schuifregelaar om de aslabels in- of uit te schakelen.

    ![Schakel aslabels in en uit.](media/power-bi-visualization-best-practices/power-bi-axis-labels.png)

    **Afbeelding 27: Aslabels in- en uitschakelen**

    > [!TIP]
    > U kunt de labels voor de y-as bijvoorbeeld uitschakelen als u **Gegevenslabels** hebt ingeschakeld.

##### <a name="to-remove-visual-titles"></a>Titels voor visuele elementen verwijderen

1. Selecteer het visuele element om het te activeren.

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Zet de schuifregelaar voor **Titel** op **Uit**.

    ![Verwijder titels uit visuele elementen.](media/power-bi-visualization-best-practices/power-bi-title-off.png)

    **Afbeelding 28: titels uit visuele elementen verwijderen**

Houd rekening met hoe uw lezers het rapport weergeven. Zorg ervoor dat uw visuele elementen en de tekst groot genoeg en donker genoeg zijn om te kunnen worden gelezen. Als de pagina een in verhouding groter visueel element bevat, gaan de lezers er mogelijk van uit dat dit het belangrijkste element is. Zorg ervoor dat er voldoende ruimte is tussen de visuele elementen zodat het rapport er niet rommelig uitziet en geen vragen oproept bij de gebruiker. Lijn de visuele elementen uit zodat de gebruiker gemakkelijker door de pagina navigeert.

##### <a name="to-resize-a-visual"></a>Het formaat van een visueel element aanpassen

1. Selecteer het visuele element om het te activeren.

1. Pak een van de grepen en sleep hiermee om de grootte aan te passen.

    ![Pas het formaat van een visueel element aan.](media/power-bi-visualization-best-practices/power-bi-drag-handles.png)

    **Afbeelding 29: visual vergroten of verkleinen**

##### <a name="to-move-a-visual"></a>Een visueel element verplaatsen

1. Selecteer het visuele element om het te activeren.

1. Houd de balkgreep midden boven in het visuele element ingedrukt en

1. sleep het visuele element naar de nieuwe locatie.

    ![Verplaats een visueel element.](media/power-bi-visualization-best-practices/power-bi-move.png)

    **Afbeelding 30: een visual verplaatsen**

#### <a name="titles-and-labels-that-are-part-of-the-visualizations"></a>Titels en labels die deel uitmaken van de visualisaties

Zorg ervoor dat titels en labels goed leesbaar zijn en voor zichzelf spreken. Tekst in titels en labels moet een optimale grootte hebben en in een kleur zijn die opvalt. Herinnert u zich nog onze stijlgids? Zie het gedeelte [Tekst](#text) eerder in dit artikel. Beperk het aantal kleuren en formaten. Te veel verschillende tekengrootten en kleuren zorgen voor een drukke en verwarrende pagina. Het kan een goed idee zijn om voor alle visuele elementen op een rapportpagina dezelfde tekstkleur en tekengrootte te gebruiken voor de titels. Kies ook dezelfde uitlijning voor alle titels op een rapportpagina.

Het deelvenster **Indeling**

Als u een van de onderstaande opmaakbewerkingen wilt uitvoeren, selecteert u het pictogram met de verfroller ![Verfrollerpictogram voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

![Open het deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paintbrush.png)

**Afbeelding 31: het deelvenster Indeling openen**

Selecteer vervolgens het visuele element dat u wilt aanpassen en zorg ervoor dat het is ingesteld op **Aan**. Voorbeelden van visuele elementen zijn: **X-as**, **Y-as**, **titel**, **gegevenslabels** en **legenda**. In het voorbeeld hieronder wordt het element **Titel** weergegeven.

![Maak de titel van een visueel element op.](media/power-bi-visualization-best-practices/power-bi-title-formatting.png)

**Afbeelding 32: een titel van een visueel element opmaken**

##### <a name="set-the-text-size"></a>De tekengrootte instellen

U kunt de tekengrootte aanpassen voor titels en gegevenslabels, maar niet voor de X- en y-as of legenda's. In het geval van gegevenslabels is het handig om te experimenteren met de waarden voor **Weergave-eenheden** en **Decimaalposities**. Uiteindelijk vindt u zo het optimale detailniveau voor het weergeven van informatie in uw rapport.

##### <a name="set-the-text-alignment"></a>De tekstuitlijning instellen

U kunt titels links of rechts uitlijnen of centreren. Kies een van de opties en pas dezelfde instelling toe op alle visuele elementen op de pagina.

##### <a name="set-the-text-position"></a>De tekstpositie instellen

U kunt de tekstpositie aanpassen voor sommige y-assen en de legenda. Pas uw keuze ook toe op de andere y-assen en eventuele andere legenda's op de pagina.

##### <a name="set-the-title-and-label-length"></a>De lengte van titels en labels instellen

Pas de lengte van de titels, astitels, gegevenslabels en legenda's aan. Als u een van de volgende elementen wilt weergeven, zorgt u er met het aanpassen van de lengte (samen met de tekengrootte) voor dat de tekst niet wordt afgekapt:

* Voor **Titel** en **Legenda** is de instelling **Titeltekst**. Voer de titel in die moet worden weergegeven in het visuele element.

* Voor **X-as** en **Y-as** is de instelling **Stijl** en u selecteert een optie uit een vervolgkeuzelijst.

* Voor **Gegevenslabels** zijn de instellingen **Weergave** en **Decimaal**. Selecteer in de vervolgkeuzelijst **Weergave-eenheden** de eenheid: **Miljoenen**, **Duizenden**, **Geen**, **Automatisch**, enzovoort. Geef in het veld **Decimaal** aan hoeveel decimalen moeten worden weergegeven.

##### <a name="set-the-text-color"></a>De tekstkleur instellen

U kunt de tekstkleur aanpassen voor titels, assen en gegevenslabels.

#### <a name="titles-and-labels-that-arent-part-of-the-visualizations"></a>Titels en labels die geen deel uitmaken van de visuele elementen

Eerder in dit artikel hebben we besproken hoe tekstvakken worden toegevoegd aan rapportpagina's. Soms zijn titels bij visualisaties alleen niet voldoende om de boodschap over te brengen. Voeg tekstvakken toe om aanvullende informatie door te geven aan de lezers van uw rapporten.

Door consistent te zijn in het gebruik van de lettertypen voor tekstvakken, grootten, kleuren en uitlijning, voorkomt u dat de rapportpagina vragen oproept bij de lezer of te druk overkomt. Als u de tekst in een tekstvak wilt wijzigen, selecteert u het tekstvak om het opmaakmenu weer te geven.

![Maak het lettertype op dat wordt gebruikt in een tekstvak.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Afbeelding 33: het lettertype dat wordt gebruikt in een tekstvak opmaken**

#### <a name="sorting"></a>Sorteren

U kunt er eenvoudig voor zorgen dat een gebruiker beter inzicht krijgt in een rapport door de sortering van visuele elementen in te stellen. Wanneer u bijvoorbeeld staafdiagrammen in oplopende of aflopende volgorde sorteert op basis van de waarde in de staven, kunt u snel belangrijke aanvullende informatie overbrengen zonder meer ruimte te gebruiken.

Een grafiek sorteren:

1. Selecteer het beletselteken in de rechterbovenhoek van de grafiek.

1. Selecteer **Sorteren**.

1. Kies het veld waarop u wilt sorteren en de richting.

Zie [De sortering van een visueel element wijzigen](../consumer/end-user-change-sort.md) voor meer informatie.

#### <a name="chart-interaction-and-interplay"></a>Interactie en wisselwerking tussen diagrammen

Power BI beschikt over een zeer interessante functie waarmee u de wijze waarop interactie plaatsvindt tussen diagrammen kunt bewerken. Gerelateerde gegevens in verschillende diagrammen worden standaard belicht: wanneer u een gegevenspunt selecteert, worden de gerelateerde gegevens in andere diagrammen belicht en worden niet-gerelateerde gegevens onbelicht. U kunt dit gedrag vervangen door een diagram als filter te gebruiken zodat er ruimte op de pagina wordt bespaard. Selecteer in de Power BI-service **Visuele interacties** in de menubalk om de wijziging te maken.

![Visuele interacties.](media/power-bi-visualization-best-practices/power-bi-visual-interactions.png)

**Afbeelding 34: visuele interacties**

Geef vervolgens voor elk visueel element op de pagina aan of dit worden gefilterd, of er gerelateerde gegevens moeten worden belicht of dat er niets moet worden gedaan. U kunt niet alle visuele elementen belichten. Voor visuele elementen die u niet kunt belichten, is het betreffende besturingselement niet beschikbaar. Zie [Visuele interacties in Power BI](../consumer/end-user-interactions.md) voor meer informatie.

> [!TIP]
> Voor gebruikers die nog geen ervaring hebben met Power BI is deze functie voor selecteren en interactie met rapporten misschien niet meteen duidelijk. Voeg tekstvakken toe om aan te geven wat ze kunnen selecteren om meer inzichten te verkrijgen.

#### <a name="the-use-of-color-in-visuals"></a>Het gebruik van kleuren in visuele elementen

Eerder in dit artikel hebben we besproken dat het belangrijk is om kleur met een doelbewust plan in een rapport te gebruiken. In dit gedeelte worden ook eerder beschreven thema's besproken, maar het gaat voornamelijk over het gebruik van kleuren in afzonderlijke visuele elementen. Dezelfde beginselen zijn van toepassing: gebruik kleur om de verschillende onderdelen van het rapport met elkaar te verbinden, belangrijke informatie te benadrukken en de gebruiker een beter inzicht te geven in het visuele element. Het gebruik van te veel verschillende kleuren kan storend zijn. U maakt het hierdoor lastig voor de lezer om te bepalen waar ze moeten kijken. De duidelijkheid van het rapport moet niet ten koste gaan van een mooie vormgeving. Voeg alleen kleur toe als dit zorgt voor meer duidelijkheid.

> [!TIP]
> Houd rekening met de gebruikers van het rapport en hoe zij kleuren interpreteren. In de Verenigde Staten heeft de kleur groen bijvoorbeeld meestal een positieve betekenis en de kleur rood een negatieve betekenis.

In de volgende secties besteden we aandacht aan deze onderwerpen:

* Kleur van de gegevens

* Kleur van de gegevenslabels

* Kleur voor de categorische waarden

* Kleur voor de numerieke waarden

##### <a name="use-colors-to-highlight-interesting-data"></a>Kleuren gebruiken om interessante gegevens te belichten

De eenvoudigste manier om kleur te gebruiken, is door de kleur of kleuren van een of meer gegevenspunten te wijzigen om hierop de aandacht te vestigen. In dit voorbeeld verandert de kleur op het moment dat de Olympische Spelen zijn overgegaan van een vierjarige cyclus in een tweejarige cyclus waarbij de Olympische Zomerspelen en Winterspelen elkaar afwisselen.

![Gebruik kleur om een boodschap over te brengen.](media/power-bi-visualization-best-practices/power-bi-data-color.png)

**Afbeelding 35: kleur gebruiken om een boodschap over te brengen**

U kunt de kleuren van gegevenspunten wijzigen op het tabblad **Gegevenskleuren** van het deelvenster **Indeling**. Als u elk gegevenspunt afzonderlijk wilt aanpassen, moet **Alles weergeven** zijn ingesteld op **Aan**.

![Stel de kleuren van gegevenspunten in.](media/power-bi-visualization-best-practices/power-bi-colors.png)

**Afbeelding 36: de kleuren van gegevenspunten instellen**

> [!NOTE]
> Er wordt door Power BI een standaardthema toegepast op de visuele elementen van uw rapport. De themakleuren zijn geselecteerd om variatie en contrast te bieden. Als u andere kleuren wilt gebruiken dan de kleuren van het standaardthema, selecteert u **Aangepaste kleur**.
>
> ![Kies een aangepaste kleur.](media/power-bi-visualization-best-practices/power-bi-custom-color.png)
>
> **Afbeelding 37: een aangepaste kleur kiezen**

In Power BI Desktop kunt u zelfs **uitbijters** of een gedeelte van een lijn belichten met behulp van een tweede reeks:

![Gebruik Desktop om uitbijters uit te zetten.](media/power-bi-visualization-best-practices/power-bi-outliers.png)

**Afbeelding 38: Power BI Desktop gebruiken om uitbijters uit te zetten**

Waarden in de reeks **Uitbijters** komen hier alleen voor waar de gemiddelde temperatuur van augustus lager is dan 60 (Fahrenheit). We hebben dit gedaan door een met DAX berekende kolom te maken aan de hand van de volgende formule:

```
Outliers = if(Editions[Temp]<60, Editions[Temp], BLANK())
```

In ons voorbeeld zijn er drie uitbijters: **1952**, **1956** en **2000**.

##### <a name="colors-for-labels-and-titles"></a>Kleuren voor labels en titels

Als u alle beschikbare opmaakopties bekijkt, komt u tot de ontdekking dat u op veel verschillende plaatsen kleur kunt toevoegen aan titels en legenda's. U kunt bijvoorbeeld de kleur van gegevenslabels en astitels wijzigen. Wees echter voorzichtig. Over het algemeen is het verstandig om één kleur te gebruiken voor alle titels van visuele elementen. Net als bij de andere richtlijnen in dit artikel, zijn er altijd situaties en redenen om hierop een uitzondering te maken. Als u besluit om een uitzondering op de regels te maken, moet u wel een goede reden hebben.

##### <a name="colors-for-categorical-values"></a>Kleuren voor categorische waarden

Diagrammen met een gegevensreeks hebben doorgaans een categorische waarde in de legenda. Met elke kleur in de onderstaande legenda wordt bijvoorbeeld een andere categorie voor Land/Regio aangegeven.

![De standaardkleuren zijn toegepast.](media/power-bi-visualization-best-practices/power-bi-bubble-color.png)

**Afbeelding 39: de standaardkleuren zijn toegepast**

De kleuren die standaard in Power BI worden gebruikt, zijn gekozen omdat ze duidelijk van elkaar verschillen en de categorische waarden zo goed van elkaar te onderscheiden zijn. Soms vervangen gebruikers deze kleuren bijvoorbeeld door de bedrijfskleuren, maar dit kan tot problemen leiden.

![De kleuren zijn toegepast als kleurschakeringen van één kleur.](media/power-bi-visualization-best-practices/power-bi-bubble-color2.png)

**Afbeelding 40: de kleuren zijn toegepast als kleurschakeringen van één kleur**

Door slechts één kleurschakering te gebruiken en de intensiteit van de kleur te variëren, geeft dit visuele element een foutief beeld van de ordening tussen de categorieën. Het geeft de indruk dat de donkere bellen hoger of lager op een bepaalde schaal zijn geplaatst dan de lichtere kleurschakeringen. Afgezien van de alfabetische volgorde is er normaal gesproken geen inherente volgorde bij dit soort categorische waarden.

Als u de standaardkleuren wilt wijzigen, selecteert u ![Pictogram van verfroller voor het deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen en selecteert u **Gegevenskleuren**.

##### <a name="colors-for-numerical-values"></a>Kleuren voor numerieke waarden

Voor velden die een bepaalde inherente volgorde en een numerieke waarde hebben, kunt u gegevenspunten ook een kleur geven naargelang de waarde. Dit kan handig zijn om de verspreiding van waarden over de gegevens weer te geven en biedt Power BI ook de mogelijkheid om twee variabelen in één diagram weer te geven. Uit het volgende diagram blijkt bijvoorbeeld dat hoewel China de meeste medailles heeft behaald, Japan en Thailand aan meer Olympische Spelen hebben deelgenomen.

![Geef gegevenspunten een kleur op basis van de waarde.](media/power-bi-visualization-best-practices/power-bi-saturation.png)

**Afbeelding 41: gegevenspunten een kleur geven op basis van de waarde**

Ga als volgt te werk om deze grafiek te maken:

1. Selecteer het visuele element om het te activeren.

1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

1. Selecteer **Gegevenskleuren** > optie > **Voorwaardelijke opmaak**:

    ![Selecteer Voorwaardelijke opmaak.](media/power-bi-visualization-best-practices/power-bi-conditional-formatting.png)

    **Afbeelding 42: Voorwaardelijke opmaak selecteren**

1. Pas die kleuren aan in het dialoogvenster **Standaardkleur - *Gegevenskleuren*** .

    ![Pas de kleuren aan die worden gebruikt voor de kleurintensiteit.](media/power-bi-visualization-best-practices/power-bi-color-controls.png)

    **Afbeelding 43: de kleuren die worden gebruikt voor de kleurintensiteit aanpassen**

U kunt kleur ook gebruiken om verschillen ten opzichte van een centrale waarde te benadrukken. Positieve waarden worden dan bijvoorbeeld in het groen en negatieve waarden in het rood weergegeven. Houd rekening met culturele verschillen wanneer u kleuren toewijst aan positieve of negatieve waarden. Het is namelijk niet in alle culturen zo dat rood wordt gebruikt om negatief aan te geven en groen voor positief.

![Met kleur verschillen ten opzichte van een centrale waarde benadrukken.](media/power-bi-visualization-best-practices/power-bi-color.png)

**Afbeelding 44: met kleur verschillen ten opzichte van een centrale waarde benadrukken**

### <a name="principles-of-visual-design--applied-to-example-report-page"></a>Beginselen voor het ontwerpen van visuele elementen, toegepast op een voorbeeld van een rapportpagina

Laten we nu eens de hierboven besproken beginselen voor het ontwerpen van visuele elementen toepassen op ons voorbeeldrapport.

![Ons voorbeeldrapport (vóór).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Afbeelding 45: ons voorbeeldrapport (vóór)**

![Ons voorbeeldrapport (na).](media/power-bi-visualization-best-practices/power-bi-example6anew.png)

**Afbeelding 46: ons voorbeeldrapport (na)**

#### <a name="what-did-we-do"></a>Wat hebben we gedaan?

| Item | Beschrijving |
| ---- | ----------- |
| Slicer | De lege waarden zijn uit de slicers verwijderd door een filter op paginaniveau toe te voegen en alleen **Gold**, **Silver** en **Bronze** te selecteren. <br> De instelling voor **Selectiebesturingselementen** is gewijzigd in **Uit** voor **Eén selecteren** en **Alles selecteren**. |
| Bellen | Er zijn zo veel items in de legenda dat ze buiten het scherm vallen. De legenda is verwijderd en **Categorielabels** is in plaats daarvan ingeschakeld. Gebruikers kunnen met de muisaanwijzer over de bellen bewegen om de details te bekijken.<br> De titel is ingekort en 'by country region' is verwijderd omdat dat voor de hand ligt. <br> De aslabels zijn voor beide assen op **Aan** gezet, zodat het diagram gemakkelijker te begrijpen is. |
| Choropletenkaart | De instelling voor **Gegevenskleuren** is gewijzigd zodat de kaart meer opvalt. <br> **Afwijken** is ingeschakeld en **Minimum** is ingesteld op roze en **Maximum** op rood.
| Treemap | Filter verwijderd dat alleen voor de Verenigde Staten was ingesteld. <br> **Gegevenslabels** ingesteld op één decimaal. <br> Het visuele element gebruikte het veld **Class**, dat niet erg nuttig is omdat de waarde hiervoor bijna altijd 33% zal zijn voor de drie medailles: Gold, Silver en Bronze. <br> We hebben een ander interessanter veld geselecteerd, namelijk **Gender**. We hebben Watersport gewijzigd in blauw en Atletiek in grijs uit ontwerpoverwegingen.
| Bovenste staafdiagram | De titel is ingekort, de gegevenslabels zijn verwijderd en de legendatitel is uitgeschakeld. <br> De woordvolgorde van de titel is gewijzigd zodat deze overeenkomt met het onderstaande diagram.
| Onderste staafdiagram | Gesorteerd op jaar en oplopend zoals het bovenstaande diagram. <br> De kleuren zijn gewijzigd zodat deze overeenkomen met de klasse. <br> De titel is gewijzigd. <br> De legenda is uitgeschakeld zodat er meer ruimte is voor de gegevens. <br> Gegevenslabels ingeschakeld. Deze worden niet weergegeven in het rapport omdat het visuele element te klein is om de labels goed te kunnen lezen. De labels worden weergegeven wanneer de lezer het visuele element opent in de **focusmodus**. Lees hier meer over de [focusmodus](../consumer/end-user-focus.md). <br> **Count of Event (Distinct)** toegevoegd aan **Knopinfo**. Als u nu de muisaanwijzer over een gestapelde kolom beweegt, ziet u in de knopinfo ook aan hoeveel evenementen de personen in dat jaar hebben deelgenomen. |
| Visuele interacties | Interacties uitgeschakeld voor beide kaarten omdat we hier altijd alle wedstrijden en sporten willen weergeven. |

## <a name="visual-types-and-best-practices"></a>Typen visuele elementen en aanbevolen procedures

Power BI beschikt over een groot aantal ingebouwde visuele elementen. Als we de aangepaste visuele elementen van Microsoft en de Power BI-community hieraan toevoegen, zijn er in totaal te veel mogelijke visuele elementen om hier te beschrijven. Laten we in ieder geval de meest gebruikte ingebouwde typen visuele elementen bekijken.

### <a name="line-charts"></a>Lijndiagrammen

![Lijndiagram.](media/power-bi-visualization-best-practices/power-bi-line-chartb.png)

Met lijndiagrammen kunnen gegevens gedurende een bepaalde periode goed worden weergegeven. In lijndiagrammen kunnen gebruikers sneller pieken, dalen, cycli en patronen in gegevens waarnemen dan in bijvoorbeeld tabellen. In het volgende voorbeeld worden de trends weergegeven in het aantal uitgereikte medailles en het aantal atleten die deze medailles hebben gewonnen.

![Lijndiagrammen.](media/power-bi-visualization-best-practices/power-bi-line-chart.png)

**Afbeelding 47: lijndiagrammen**

#### <a name="best-practices"></a>Aanbevolen procedures

* Wanneer gebruikers naar lijndiagrammen kijken, valt hen als eerste de vorm van de curve op. Daarom is het belangrijk dat uw diagram een x-as heeft die betekenis geeft aan de curve, zoals een x-as met een tijdsbestek of de verdeling over verschillende categorieën. Als u categorische velden met betrekking tot bijvoorbeeld een product of geografie gebruikt voor de x-as, is het lijndiagram niet interessant omdat de curve geen betekenisvolle informatie uitdrukt.

* Als u meerdere diagrammen boven en onder elkaar plaatst, stelt u de x-assen op elkaar af zodat de gebruiker de gegevensreeksen gemakkelijker met elkaar kan vergelijken. Gebruik filters zodat hetzelfde waardebereik wordt weergegeven in Power BI. Als u datumbereiken gebruikt, moet u dezelfde datumbereiken gebruiken. Bijvoorbeeld 1896 tot 2012 in beide diagrammen.

* Maak optimaal gebruik van de ruimte. Als de gegevens er zich voor lenen, stelt u het begin- en eindpunt in (met **Begin** en **Eind**) voor de y-as zodat er aan de bovenkant en onderkant van het diagram geen lege ruimte ontstaat. Dit helpt ook om het visuele element te laten focussen op de feitelijke gegevenspunten. Waarden opgeven voor **Begin** en **Eind**:

  1. Selecteer het visuele element om het te activeren.

  1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.
  
  1. Vouw het gebied voor **Y-as** uit en stel het **Begin**- en **Eind**-punt in.
  
      ![Stel het begin- en eindpunt in.](media/power-bi-visualization-best-practices/power-bi-start-end.png)
  
      **Afbeelding 48: het begin- en eindpunt instellen**

* Het is ook handig om de waarden voor **Begin** en **Eind** expliciet in te stellen als u twee of meer diagrammen wilt vergelijken die op dezelfde pagina worden weergegeven en die hetzelfde veld voor de y-as gebruiken. Als we bijvoorbeeld het samengevoegde aantal voor evenementen bekijken, varieert het aantal voor het Verenigd Koninkrijk van 1 tot 70 en voor Australië van 1 tot 12 en worden voor de twee lijndiagrammen verschillende y-assen weergegeven (afbeelding 49). Dit maakt het moeilijk om de twee diagrammen in één oogopslag te vergelijken. Stel daarom hetzelfde bereik in voor de y-assen van beide diagrammen (afbeelding 50).
  
  ![Lijndiagrammen met verschillende y-assen.](media/power-bi-visualization-best-practices/power-bi-line-chart2.png)
  
  **Afbeelding 49: lijndiagrammen met verschillende y-assen**
  
  ![Lijndiagrammen met dezelfde y-as.](media/power-bi-visualization-best-practices/power-bi-line-chart3.png)
  
  **Afbeelding 50: lijndiagrammen met dezelfde y-as**

Zie voor meer informatie:

* [Eigenschappen van x-as en y-as aanpassen](power-bi-visualization-customize-x-axis-and-y-axis.md)

* [Line Graphs and Irregular Intervals: An Incompatible Partnership](http://www.perceptualedge.com/articles/visual_business_intelligence/line_graphs_and_irregular_intervals.pdf)

* [Data Visualization 101: Line Charts](http://www.columnfivemedia.com/data-visualization-101-line-charts)

### <a name="bar-and-column-charts"></a>Staaf- en kolomdiagrammen

![Staaf- en kolomdiagrammen.](media/power-bi-visualization-best-practices/power-bi-bar-chart.png)

Waar lijndiagrammen standaard worden gebruikt om gegevens gedurende een bepaalde periode weer te geven, worden staafdiagrammen standaard gebruikt om een specifieke waarde in verschillende categorieën weer te geven. Als u de balken op basis van de waarde sorteert, zijn de hoogste waarden en de verdeling over de verschillende categorieën snel en duidelijk zichtbaar. Horizontale staafdiagrammen zijn geschikt voor gebruik met lange labels.

![Horizontaal staafdiagram.](media/power-bi-visualization-best-practices/power-bi-horizontal-scroll.png)

**Afbeelding 51: horizontaal staafdiagram**

#### <a name="best-practices"></a>Aanbevolen procedures

* Gegevenslabels weergeven voor waarden. Hiermee kunnen specifieke waarden gemakkelijker worden waargenomen. Gegevenslabels weergeven: 

  1. Selecteer het visuele element om het te activeren.

  1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.
  
  1. Zet **Gegevenslabels** op **Aan**.

      ![Schakel gegevenslabels in.](media/power-bi-visualization-best-practices/power-bi-data-labels.png)

      **Afbeelding 52: gegevenslabels inschakelen**

* Het bovenstaande staafdiagram is handig om één meting met verschillende andere metingen te vergelijken op een bepaald tijdstip. In een lijndiagram wordt de trend gedurende een bepaalde periode weergegeven en in een staafdiagram de trend voor één categorie op een bepaald tijdstip. In een oogopslag zien we in het staafdiagram dat Spanje met 24,70% een van de hoogste werkloosheidspercentages ter wereld heeft.

* Wanneer het staaf- of kolomdiagram niet in zijn geheel in de betreffende ruimte past, worden er schuifbalken toegevoegd door Power BI. Indien mogelijk en wanneer van toepassing moet u het visuele element en het rapport zo ontwerpen dat het hele diagram wordt weergegeven en de gebruiker een overzicht krijgt van de verdeling over alle categorieën. Dit is in ons voorbeeld helaas niet mogelijk, gezien het grote aantal landen in de wereld.

  Een manier om de waarden in het diagram te beperken, is door een filter toe te passen. Voeg bijvoorbeeld een filter op het niveau van het **visuele element** toe, waarmee alleen de landen met een werkloosheidspercentage van meer dan 20% worden getoond.

* U kunt inzoomen (en weer uitzoomen) op staaf- en kolomdiagrammen. Dit is een goede manier om meer informatie in een visueel element te verpakken zonder dat dit meer ruimte in beslag neemt. In het volgende voorbeeld ziet u een hiërarchie voor Regio's > Landen. Als u dubbelklikt op een balk voor een regio, wordt er ingezoomd op de landen die deel uitmaken van deze regio. Zie [Drill mode in a visualization in Power BI](../consumer/end-user-drill.md) (Zoommodus in een visualisatie in Power BI) voor meer informatie over de zoommodus.
  
  ![Zoom in.](media/power-bi-visualization-best-practices/power-bi-drill.png)
  
  **Afbeelding 53: inzoomen**

Raadpleeg voor meer informatie over staaf- en kolomdiagrammen:

* [Data Visualization 101: Bar Charts](http://blog.newscred.com/article/data-visualization-101-bar-charts)

* [Data Visualization Catalog: staafdiagram](http://www.datavizcatalogue.com/methods/bar_chart.html#.VYV-hY3bLJw)

* [Data Visualization Catalog: staafdiagram met meerdere sets](http://www.datavizcatalogue.com/methods/multiset_barchart.html#.VYV_gI3bLJw)

### <a name="stacked-bar-and-column-charts"></a>Gestapelde staaf- en kolomdiagrammen

![Gestapelde diagrammen.](media/power-bi-visualization-best-practices/power-bi-stacked.png)

Voeg een andere dimensie toe aan uw staaf- en kolomdiagrammen door verschillende categorieën in de balk of kolom te stapelen. Het diagram bevat nu informatie over een algemene trend (gebaseerd op de hoogte en lengte), maar het geeft nu ook de invloed van de categorieën op deze trend weer. In het volgende diagram is te zien dat de totale omzet van de belangrijkste voetbalteams in 2014 is gegroeid tot boven de zes miljard.

![Gestapeld kolomdiagram](media/power-bi-visualization-best-practices/power-bi-deloite.png)

**Afbeelding 54: gestapelde kolomdiagram**

In dit gestapelde kolomdiagram is te zien dat de totale omzet (**Total Revenue**) in de loop van de tijd groeit en dat de categorieën **Commercial** en **Broadcasting** in dezelfde periode ook gestaag groeien, waardoor dus de totale omzet toeneemt. Bij dit diagram is het echter niet eenvoudig om het effect te vergelijken dat elk van de drie categorieën op elkaar heeft. Hoe verhoudt bijvoorbeeld de groei van de categorie Commercial zich tot de groei van Broadcasting of Match Day? Voor deze gegevens kan beter een lijndiagram of een lijndiagram als aanvullend visueel element worden gebruikt.

![Omzetting in een lijndiagram.](media/power-bi-visualization-best-practices/power-bi-deloite2.png)

**Afbeelding 55: omzetting in een lijndiagram**

In dit lijndiagram is beter te zien hoe de commerciële omzet het meest is gegroeid, gevolgd door de televisiegelden en de wedstrijddagen.

#### <a name="best-practices"></a>Aanbevolen procedures

* Net als bij kolom- en staafdiagrammen kunt u kiezen uit een horizontale of verticale weergave. U kunt het beste een horizontale weergave kiezen als u lange labels gebruikt en een verticale weergave als u met tijdsbereiken werkt.

* Gebruik geen gestapelde staaf- of kolomdiagrammen als u trends en andere veranderingspatronen gedurende een bepaalde periode wilt weergeven. U kunt hiervoor beter andere diagrammen, zoals lijndiagrammen, gebruiken.

* U kunt de verdeling ook baseren op het totale volume of weergeven als een percentage van een totaal.

* Zoals Few opmerkte:

    > *... is het moeilijk om de segmenten van een gestapeld staafdiagram te vergelijken. Als de segmenten naast elkaar zouden zijn gerangschikt en allemaal vanaf dezelfde basislijn omhoog zouden groeien, zouden hun respectievelijke hoogten gemakkelijk kunnen worden vergeleken. Wanneer ze echter op elkaar zijn gestapeld, wordt dit een moeilijke opgave. En hoewel het redelijk eenvoudig is om te zien hoe de (opbrengst) van maand tot maand is gewijzigd, is het erg moeilijk te zien hoe de (opbrengst) in de andere (categorieën) is gewijzigd*.

* Gestapelde diagrammen met 100%-balken zijn een goede keuze wanneer u percentages gebruikt die samen 100% zijn. In het onderstaande voorbeeld ziet u de categorieverdeling per team. De percentages zijn relatief zodat we de patronen in een oogopslag kunnen zien. De omzet van Everton is voornamelijk afkomstig uit televisiegelden (meer dan 70%), terwijl PSG slechts 20% van de omzet uit televisiegelden haalt. Bij een horizontale weergave is het gemakkelijker om de teamlabels in te passen en is het effect van het type omzet beter af te lezen.

  ![Horizontaal gestapeld diagram.](media/power-bi-visualization-best-practices/power-bi-deloite3.png)

  **Afbeelding 56: horizontaal gestapeld diagram**

Meer informatie over gestapelde diagrammen:

* [Data Visualization Catalog: Stacked Bar Graphs](http://www.datavizcatalogue.com/methods/stacked_bar_graph.html#top)

* [Wanneer moet u gestapelde staafdiagrammen met 100%-balken gebruiken?](http://www.perceptualedge.com/blog/?p=2239)

### <a name="combo-bar-and-column-charts"></a>Gecombineerde staaf- en kolomdiagrammen

![Combinatiegrafieken.](media/power-bi-visualization-best-practices/power-bi-combo.png)

In Power BI kunt u kolom- en lijndiagrammen combineren tot een combinatiegrafiek. De opties zijn: 

* Lijndiagram en gestapeld kolomdiagram 

* Lijndiagram en gegroepeerd kolomdiagram

Bespaar kostbare ruimte voor uw rapport door twee afzonderlijke visuele elementen te combineren tot één.

De volgende twee schermopnames geven de situatie vóór en na de combinatie weer.

![Als twee afzonderlijke diagrammen](media/power-bi-visualization-best-practices/power-bi-spain-line.png)

 **Afbeelding 57: als twee afzonderlijke diagrammen**

Het eerste diagram heeft twee afzonderlijke visuele elementen: een kolomdiagram dat de bevolking gedurende een bepaalde periode weergeeft en een lijndiagram waarin het BBP gedurende dezelfde periode wordt weergegeven. Deze diagrammen zijn geschikt voor een combinatiegrafiek omdat ze dezelfde x-as (jaar) en waarden (2002 tot 2012) hebben. Waarom zou u deze diagrammen niet combineren om deze twee trends in één visueel element te vergelijken? Als u deze twee diagrammen combineert, kunt u de gegevens beter vergelijken.

![Als één combinatiegrafiek](media/power-bi-visualization-best-practices/power-bi-spain-combo.png)

 **Afbeelding 58: als één combinatiegrafiek**

Op de nieuwe rapportpagina staat één visueel element: een lijndiagram en een gestapeld kolomdiagram. We hadden net zo goed een lijndiagram en een gegroepeerd kolomdiagram kunnen maken. Het is nu gemakkelijker om een verband tussen de twee trends te herkennen. U ziet dat tot en met 2008 de bevolking en het BBP een vergelijkbare trend volgen. Maar vanaf 2009 toen de bevolkingsgroei afvlakte, was het BBP veranderlijk.

#### <a name="best-practices"></a>Aanbevolen procedures

* U kunt het beste een combinatiegrafiek gebruiken wanneer beide visuele elementen ten minste één as gemeen hebben.

* Let op de assen! Is uw combinatiegrafiek gemakkelijk te lezen en te interpreteren? Bevat het diagram ongelijke bereiken en waarden? Als de schaal van de y-as voor het kolomdiagram veel kleiner is dan de schaal van de y-as van het lijndiagram, levert de combinatiegrafiek geen zinvolle informatie op. Kijk bijvoorbeeld eens naar de derde lijn (aquamarijn) onderaan de grafiek.

   ![Een mislukt lijndiagram.](media/power-bi-visualization-best-practices/power-bi-dual-line.png)

   **Afbeelding 59: een mislukt lijndiagram**

  Zo levert de combinatiegrafiek ook geen zinvolle informatie op als het kolomdiagram en het lijndiagram twee verschillende maten gebruiken en u geen twee assen maakt. Bijvoorbeeld dollars tegenover een percentage. Zorg dat beide assen in de grafiek worden weergegeven zodat de gebruiker deze gemakkelijker begrijpt en voeg eventueel ook aslabels toe.

  Twee assen maken:

    1. Selecteer het visuele element om het te activeren.

    1. Selecteer ![Pictogram van verfroller voor deelvenster Indeling.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) om het deelvenster **Indeling** te openen.

    1. Vouw **Y-as** uit en zet **Secundaire weergeven** op **Aan**.

          ![De secundaire as weergeven.](media/power-bi-visualization-best-practices/power-bi-show-secondary-new.png)

          **Afbeelding 60: secundaire as weergeven**

    1. Stel **Y-as (kolom)**  > **Titel** in op **Aan**.

    1. Stel **Y-as (lijn)**  > **Titel** in op **Aan**.

  Zo ziet de grafiek er dan uit:

  ![Maak in plaats daarvan een combinatiegrafiek.](media/power-bi-visualization-best-practices/power-bi-combo-chart.png)

  **Afbeelding 61: in plaats daarvan een combinatiegrafiek maken**

* Maak gebruik van de voordelen die twee assen bieden. Het is een goede manier om meerdere maten met verschillende waardebereiken te vergelijken. U kunt zo ook het verband tussen twee metingen in één visueel element illustreren.

Zie voor meer informatie:

* [Combinatiegrafieken in Power BI](power-bi-visualization-combo-chart.md)

* [Dual-Scaled Axes in Graphs: Are They Ever the Best Solution? ](http://www.perceptualedge.com/articles/visual_business_intelligence/dual-scaled_axes.pdf)

### <a name="scatter-chart"></a>Spreidingsdiagram

![Spreidingsdiagram](media/power-bi-visualization-best-practices/power-bi-scatter.png)

Soms werken we met veel variabelen die we graag in één beeld willen vangen en een spreidingsdiagram geeft zo'n volledig beeld. Met spreidingsdiagrammen worden verbanden tussen twee (spreiding) of drie (bellen) kwantitatieve maten weergegeven. Een spreidingsdiagram heeft altijd twee waardeassen, waarbij een reeks numerieke gegevens op een horizontale as en een andere reeks numerieke waarden op de verticale as wordt weergegeven. In het diagram worden punten weergegeven op het snijpunt van een numerieke X- en Y-waarde, waarbij deze waarden in één gegevenspunt worden gecombineerd. Power BI kan deze gegevenspunten gelijkmatig of ongelijkmatig over de horizontale as verdelen. Dat hangt af van de gegevens.

Bij een bellendiagram worden de gegevenspunten vervangen door bellen. De grootte van de bellen geven de gegevens een extra dimensie.

In het onderstaande bellendiagram dat betrekking heeft op Zuid-Amerika worden het BBP per inwoner (y-as), de som van het BBP (x-as) en de bevolking per Zuid-Amerikaans land vergeleken.

![Het BBP en de bevolking in Zuid-Amerika als een bellendiagram](media/power-bi-visualization-best-practices/power-bi-bubble.png)

**Afbeelding 62: het BBP en de bevolking in Zuid-Amerika als een bellendiagram**

De grootte van de bellen geeft de totale bevolking van dat land aan. Brazilië heeft de grootste bevolking (belgrootte) en het grootste aandeel aan het BBP van Zuid-Amerika (het staat het verst op de x-as). Het BBP per inwoner is voor Uruguay, Chili en Argentinië echter hoger dan voor Brazilië (en ze staan dus hoger boven op de y-as).

Als u een afspeelas toevoegt, kunt u Hans Rosling imiteren en vertellen hoe de ontwikkeling door de jaren heen is: [From Data to Insight & Impact: Showing Africa's Progress with Power View and PPI by Microsoft](https://www.youtube.com/watch?v=PbaDBJWCeD4). Als u een afspeelas wilt toevoegen, sleept u een Datum/tijd-veld naar de **afspeelas**.

#### <a name="best-practices"></a>Aanbevolen procedures

* Met spreidings- en beldiagrammen kunt u goed een bepaald verhaal vertellen. Ze zijn minder geschikt als het gaat om het verkennen van gegevens. Stephen Few verwoordt het zo:

    > *Het voordeel van deze benadering is dat je hiermee goed een verhaal kunt vertellen. Wanneer Rosling vertelt wat er gebeurt in het diagram als de bellen rondbewegen en van waarde veranderen en hij wijst op de dingen die hij ons wil laten zien, komen de gegevens tot leven. Animaties van bellendiagrammen zijn echter veel minder effectief als het gaat om het verkennen en begrijpen van gegevens die op zichzelf staan. Ik denk niet dat Rosling deze methode gebruikt om verhalen te ontdekken, maar eerder om deze te vertellen wanneer ze eenmaal bekend zijn. We kunnen niet op meer dan één bel tegelijk letten terwijl ze rondbewegen, zodat we de animatie keer op keer moeten afspelen om een idee te krijgen van wat er precies gebeurt. We kunnen sporen toevoegen aan geselecteerde bellen, zodat kan worden nagegaan welk pad ze hebben afgelegd. Als er echter sporen worden gebruikt voor meer dan een paar bellen, wordt het diagram snel onoverzichtelijk. Waar ik eigenlijk op wil wijzen, is dat deze methode niet de beste manier is om deze gegevens weer te geven als u ze wilt verkennen en analyseren.*

* Voeg labels toe voor de x- en y-as om het verhaal te vertellen. Vooral bij bellendiagrammen spelen er veel aspecten mee en vormen labels een goede toelichting op het visuele element.

* Voeg gegevenslabels toe zodat het visuele element gemakkelijker kan worden geïnterpreteerd. Met name voor bellendiagrammen geldt dat wanneer de legenda veel items bevat, het moeilijk kan zijn om onderscheid te maken tussen vergelijkbare kleuren. In het bovenstaande visuele element lijken de kleuren voor Suriname, Colombia en Ecuador op elkaar.

* Hebt u een spreidingsdiagram gemaakt en wordt daarin slechts één gegevenspunt weergegeven waarin alle waarden op de x- en y-as worden samengevoegd? Of worden in het diagram alle waarden langs een horizontale of verticale lijn weergegeven? Als u dit wilt oplossen, voegt u een veld toe aan het gebied **Details** om aan te geven hoe de waarden moeten worden gegroepeerd. Het veld moet uniek zijn voor elk punt dat moet worden weergegeven. Raadpleeg de [zelfstudie voor Power BI- spreidingsdiagrammen en -beldiagrammen](power-bi-visualization-scatter.md) voor meer informatie.

### <a name="treemap-charts"></a>Treemap grafieken

![Treemap grafieken.](media/power-bi-visualization-best-practices/power-bi-treemap.png)

Treemaps zijn met name handig om een goed overzicht te geven van de relatieve grootte van de verschillende onderdelen die deel uitmaken van een groter geheel. Dit geldt vooral wanneer u ze in categorieën kunt indelen. Telkens wanneer u inzicht wilt krijgen in een nieuw onderwerp, biedt een treemap met de belangrijkste onderdelen nuttige informatie over de algehele verdeling.

In het eerste diagram hieronder ziet u direct dat Brazilië goed is voor ongeveer de helft van het BBP van Zuid-Amerika en dat Columbia en Chili ongeveer hetzelfde BBP hebben.

Stel dat u een bredere context wilt hebben, maar nog steeds een idee wilt hebben van de impact van de belangrijkste landen. U kunt dan visuele hiërarchieën maken met categorieleden (landen) die zijn genest in regio's. De tweede treemap geeft hoofdzakelijk een beeld van de relatieve grootte van de regio's. Binnen elke regio kunnen we zien welke afzonderlijke landen de grootste bijdrage leveren. We zien dat er drie enorme regio's zijn: Europa, Azië en Noord-Amerika. Binnen deze regio's kunnen we eenvoudig de belangrijkste landen/regio's zien.

De belangrijkste beperking van een treemap is dat het lastig is om de kleinere rechthoeken te vergelijken. Het is een goede keuze voor een overzicht, maar kolom- en staafdiagrammen geven waarschijnlijk een nauwkeuriger beeld van de relatieve grootte van de verschillende onderdelen.

De eerste treemap geeft een brede indicatie van de volgorde van de BBP-grootte. Het is echter moeilijk om specifieke verschillen tussen de landen te bepalen, met name bij de kleinere bladeren zonder label. U kunt voor dit soort gegevens, waarbij de onderdelen van één groep worden vergeleken, dan ook beter een staaf- of kolomdiagram gebruiken.

![Vergelijking van het BBP in Zuid-Amerika weergegeven als een treemap.](media/power-bi-visualization-best-practices/power-bi-treemap3.png)

**Afbeelding 63: Vergelijking van het BBP in Zuid-Amerika weergegeven als een treemap**

Vervolgens hebben we Region toegevoegd als een ander niveau van de gegevens. We kunnen zo de totale bijdrage aan het BBP per regio zien. Ook zien we de relatieve impact binnen de regio's. Houd er rekening mee dat wanneer u dit met metingen doet die niet kunnen worden opgeteld (zoals gemiddelden), de som van de gegevens mogelijk niet de werkelijke waarde op het samenvoegingsniveau weergeeft.

![BBP per regio en land als een treemap.](media/power-bi-visualization-best-practices/power-bi-treemap2.png)

**Afbeelding 64: BBP per regio en land als een treemap**

Meer informatie over treemaps:

* [Discovering Business Intelligence Using Treemap Visualizations](http://www.perceptualedge.com/articles/b-eye/treemaps.pdf)

* [Data Visualization Catalog: Treemap](http://www.datavizcatalogue.com/methods/treemap.html#.VYhylI3bL7Y)

### <a name="other-charts"></a>Andere diagrammen

#### <a name="pie-or-donut-charts"></a>Ring- of cirkeldiagrammen

![Ring- of cirkeldiagrammen](media/power-bi-visualization-best-practices/power-bi-donut.png)

Over het algemeen zijn staaf-, kolom- en lijndiagrammen geschikt voor de meeste scenario's. Het is bekend dat gebruikers van rapporten moeite hebben met het interpreteren van ring- en cirkeldiagrammen en dat deze diagrammen vaak de gegevens kunnen verdraaien. Gebruik deze diagrammen zo min mogelijk. Stephen Few heeft een interessant verslag geschreven over de geschiedenis en gevaren in [Save the Pies for Dessert](https://www.perceptualedge.com/articles/08-21-07.pdf).

Stephen legt uit dat cirkeldiagrammen wel nuttig zijn om de verhouding van een onderdeel tot het geheel weer te geven. Een cirkeldiagram is echter zelden beter dan een 100% gestapeld staafdiagram.

Een ander grappig artikel (met animatie) over cirkeldiagrammen vindt u op de [site Darkhorse Analytics](http://www.darkhorseanalytics.com/blog/salvaging-the-pie).

#### <a name="radial-gauges--kpis"></a>Radiale meters en KPI's

![Radiale meters en KPI's.](media/power-bi-visualization-best-practices/power-bi-gauge.png)

Radiale meters kunnen goed worden gebruikt als visueel element waarin prestaties worden weergegeven ten opzichte van een gesteld doel en worden vaak gebruikt in dashboards voor leidinggevenden. Deze meters schieten echter op twee punten tekort. Net als bij cirkeldiagrammen is het moeilijk om de hoek van het gekleurde gedeelte ten opzichte van de volledige 180 graden boog of de doellijn te interpreteren. De radiale meter neemt ook veel ruimte in beslag om slechts één waarde weer te geven.

Een goed alternatief is een eenvoudig visueel element dat een KPI weergeeft:

![Een eenvoudige KPI-visualisatie.](media/power-bi-visualization-best-practices/power-bi-kpi.png)

Met KPI's worden de waarde, de status, het doel, de afwijking van het doel en de trend weergegeven in dezelfde hoeveelheid ruimte. De groene kleur verandert in rood als het doel niet wordt behaald en geel als een tussenliggend doel wordt behaald. Het is veel eenvoudiger af te lezen en te interpreteren dan de meter.

Zie voor meer informatie:

* [Radiale-meterdiagrammen in Power BI](power-bi-visualization-radial-gauge-charts.md)

* [Visuele KPI-elementen](power-bi-visualization-kpi.md)

## <a name="conclusion"></a>Conclusie

Het moment is nu aangebroken om zelf deze aanbevolen procedures toe te passen. Houd contact en deel uw eigen aanbevelingen met ons. Bent u het niet eens met onze aanbevelingen of hebt u een goede reden gevonden om een uitzondering te maken? We horen het graag van u.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

### <a name="book-recommendations"></a>Aanbevolen boeken

Er zijn tegenwoordig veel goede boeken beschikbaar waarmee teams hun kennis over de verschillende technieken voor visueel ontwerpen kunnen opfrissen. *Information Dashboard Design* van Stephen Few is verplichte kost. Ze gaan in twee andere boeken verder de diepte in: *Show Me the Numbers* en *Now You See It*. Few en anderen hebben zich laten inspireren door Edward R. Tufte. Zijn boek *The Visual Display of Quantitative Information* wordt beschouwd als een klassieker op dit gebied. Tufte heeft ook *Visual Explanations*, *Envisioning Information* en *Beautiful Evidence* geschreven. Het nieuwe boek van Andy Kirk, *Data Visualization: A Handbook for Data Driven Design* is ook een goede optie. Enkele andere aanbevolen auteurs: Lachlan James, William McKnight, Boris Evelson (Forrester) en Darkhorse Analytics.
