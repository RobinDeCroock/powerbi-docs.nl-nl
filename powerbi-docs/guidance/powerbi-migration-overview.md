---
title: Overzicht van Power BI-migratie
description: Lees hoe u een migratie en uitvoert van een ander BI-hulpprogramma van derden naar Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: aa17e6293a4bd946b1d6b7acad45623fa2393c57
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803314"
---
# <a name="power-bi-migration-overview"></a>Overzicht van Power BI-migratie

Klanten maken steeds meer gebruik van Power BI ter ondersteuning van een gegevenscultuur. Hiervoor moet beheerde SSBI (selfservice business intelligence) worden ingeschakeld, de levering van ondernemings-BI worden gerationaliseerd en moet een oplossing worden gevonden voor economische druk. Het doel van deze reeks artikelen over Power BI-migratie is het geven van een richtlijn over de planning en uitvoering van een migratie van een BI-hulpprogramma van derden naar Power BI.

De reeks over Power BI-migratie bevat onder andere de volgende artikelen:

1. Overzicht van Power BI-migratie (dit artikel)
1. [Migratie naar Power BI voorbereiden](powerbi-migration-pre-migration-steps.md)
1. [Vereisten voor migratie naar Power BI verzamelen (fase 1)](powerbi-migration-requirements.md)
1. [Implementatie voor migratie naar Power BI plannen (fase 2)](powerbi-migration-planning.md)
1. [Een werkbaar concept van migratie naar Power BI testen (fase 3)](powerbi-migration-proof-of-concept.md)
1. [Inhoud maken om te migreren naar Power BI (fase 4)](powerbi-migration-create-validate-content.md)
1. [Implementatie naar Power BI (fase 5)](powerbi-migration-deploy-support-monitor.md)
1. [Leren van Power BI-migraties van klanten](powerbi-migration-learn-from-customers.md)

Er zijn twee veronderstellingen: Uw organisatie heeft momenteel een verouderd BI-platform en er is besloten om inhoud en gebruikers formeel te migreren naar Power BI. Migreren naar de Power BI-service is de primaire focus van deze reeks. Het is mogelijk dat er voor nationale cloudklanten aanvullende overwegingen zijn buiten deze die in deze reeks artikelen worden besproken.

Het volgende schema toont de vier hoofdfasen voor de implementatie van Power BI in uw organisatie.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Afbeelding van de vier fasen op hoog niveau, welke in de volgende tabel worden beschreven.":::

|Fase|Beschrijving|
|--------|-----------|
|![Fase 1.](media/common/icon-01-red-30x30.png)|**Power BI instellen en evalueren.** In de eerste fase moet de eerste Power BI-architectuur worden ingesteld. In deze fase vindt de voorbereidende planning van de implementatie en governance plaats, evenals Power BI-evaluaties, waaronder het investeringsrendement en/of de kosten-/batenanalyse.|
|![Fase 2.](media/common/icon-02-red-30x30.png)|**Snel nieuwe oplossingen maken in Power BI.** In de tweede fase kunnen selfservice BI-auteurs Power BI gaan gebruiken en evalueren voor hun doelstellingen en kan al snel voordeel worden gehaald uit Power BI. De activiteiten in fase 2 zijn gericht op flexibiliteit en snelle bedrijfswaarde, wat cruciaal is voor de acceptatie van de selectie van een nieuw BI-hulpprogramma, zoals Power BI. In het schema worden de activiteiten in fase 2 daarom parallel met de migratieactiviteiten in fase 3 weergegeven.|
|![Fase 3.](media/common/icon-03-red-30x30.png)|**BI-assets migreren van een verouderd platform naar Power BI.** De derde fase heeft betrekking op de migratie naar Power BI. Het is de focus van deze reeks artikelen over Power BI-migratie. In de volgende sectie worden vijf specifieke migratiefasen besproken.|
|![Fase 4.](media/common/icon-04-red-30x30.png)|**Power BI aannemen, beheren en bewaken.** De laatste fase omvat doorlopende activiteiten zoals het bevorderen van een gegevenscultuur, communicatie en training. Deze activiteiten hebben een grote invloed op een efficiënte Power BI-implementatie. Het is belangrijk dat u beschikt over governance- en beveiligingsbeleid en -processen die geschikt zijn voor uw organisatie, evenals auditing en bewaking, zodat u kunt schalen, groeien en voortdurend kunt verbeteren.|

> [!IMPORTANT]
> Een formele migratie naar Power BI vindt bijna altijd parallel met de ontwikkeling van een nieuwe Power BI-oplossing plaats. _Power BI-oplossing_ is een algemene term die het gebruik van zowel gegevens als rapporten omvat. Één Power BI Desktop-bestand (pbix) kan een gegevensmodel of rapport bevatten, of beide. [Het scheiden van het gegevensmodel van rapporten](../guidance/report-separate-from-model.md) wordt aangemoedigd voor het hergebruik van gegevens, maar is niet vereist.
>
> Het gebruik van Power BI om nieuwe vereisten te schrijven tijdens de planning en uitvoering van de formele migratie, zal u helpen inzet te krijgen. Gelijktijdige fasen geven auteurs van inhoud praktische en realistische ervaring met Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>Vijf fasen van een Power BI-migratie

Fase 3 van het schema heeft betrekking op migratie naar Power BI. Deze fase heeft vijf veelvoorkomende stadia.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Afbeelding van de stadia van een Power BI-migratie, die hieronder worden beschreven.":::

In het vorige diagram zag u de volgende stadia:

- [Stappen voorafgaand aan de migratie](#pre-migration-steps)
- [Fase 1: Vereisten verzamelen en prioriteiten toekennen](#stage-1-gather-requirements-and-prioritize)
- [Fase 2: Implementatie plannen](#stage-2-plan-for-deployment)
- [Fase 3: Een werkbaar concept testen](#stage-3-conduct-proof-of-concept)
- [Fase 4: Inhoud maken en valideren](#stage-4-create-and-validate-content)
- [Fase 5: Implementeren, ondersteunen en bewaken](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Stappen voorafgaand aan de migratie

De stappen voorafgaand aan de migratie omvatten acties die u kunt overwegen voordat u een project start om inhoud van een verouderd BI-platform naar Power BI te migreren. Het bevat gewoonlijk de eerste planning voor implementatie op tenantniveau. Zie [Migratie naar Power BI voorbereiden](powerbi-migration-pre-migration-steps.md) voor meer informatie over deze activiteiten.

### <a name="stage-1-gather-requirements-and-prioritize"></a>Fase 1: Vereisten verzamelen en prioriteiten toekennen

De nadruk in fase 1 ligt op het verzamelen van informatie en het plannen van de migratie van één oplossing. Dit is een iteratief proces dat moet worden afgestemd op een inspanning van redelijke omvang. De uitvoer van fase 1 bevat een prioriteitenoverzicht van rapporten en gegevens die moeten worden gemigreerd. In fase 2 en 3 zijn aanvullende activiteiten nodig om het inspanningsniveau volledig te kunnen inschatten. Zie [Vereisten voor migratie naar Power BI verzamelen](powerbi-migration-requirements.md) voor meer informatie over de activiteiten in fase 1.

### <a name="stage-2-plan-for-deployment"></a>Fase 2: Implementatie plannen

De focus in fase 2 ligt op de manier waarop de vereisten die in fase 1 zijn gedefinieerd, voor elke specifieke oplossing kunnen worden vervuld. De uitvoer van fase 2 omvat zo veel mogelijk specifieke details om het proces te sturen, ondanks dat het een iteratief, niet-lineair proces is. Parallel met deze fase kan een werkbaar concept (in fase 3) worden gemaakt. Zelfs tijdens het maken van de oplossing (in fase 4), is het mogelijk dat er aanvullende informatie aan het licht komt die invloed heeft op beslissingen ten aanzien van de implementatieplanning. Dit type implementatieplanning in fase 2 is gericht op het oplossingsniveau, rekening houdend met beslissingen die al op organisatieniveau zijn genomen. Zie [Implementatie voor migratie naar Power BI plannen](powerbi-migration-planning.md) voor meer informatie over de activiteiten in fase 2.

### <a name="stage-3-conduct-proof-of-concept"></a>Fase 3: Een werkbaar concept testen

De nadruk in fase 3 ligt op de aanpak van onbekende factoren en het zo tijdig mogelijk elimineren van risico's. Een technisch werkbaar concept (Proof of Concept of POC) is handig voor het valideren van veronderstellingen en kan iteratief worden uitgevoerd naast de implementatieplanning (fase 2). De uitvoer van deze fase is een Power BI-oplossing met een beperkt bereik. De POC is echter geen inspanning waar verder niks meer mee wordt gedaan. Het is wel zo dat er in fase 4 waarschijnlijk extra werk moet worden verricht om het geschikt te maken voor productie. U zou deze activiteit in uw organisatie een prototype, pilot, mockup, snelstartgids of minimaal levensvatbaar product (MVP) kunnen noemen. De uitvoering van een werkbaar concept is niet altijd nodig en kan een informeel karakter hebben. Zie [Een werkbaar concept van migratie naar Power BI testen](powerbi-migration-proof-of-concept.md) voor meer informatie over de activiteiten in fase 3.

### <a name="stage-4-create-and-validate-content"></a>Fase 4: Inhoud maken en valideren

Fase 4 is de fase waarin het werkbaar concept daadwerkelijk wordt omgezet in een oplossing die gereed is voor productie. De uitvoer van deze fase is een voltooide Power BI-oplossing die is gevalideerd in een ontwikkelomgeving. Deze moet gereed zijn voor implementatie in fase 5. Zie [Inhoud maken om te migreren naar Power BI](powerbi-migration-create-validate-content.md) voor meer informatie over de activiteiten in fase 4.

### <a name="stage-5-deploy-support-and-monitor"></a>Fase 5: Implementeren, ondersteunen en bewaken

De primaire focus in fase 5 ligt op de implementatie van de nieuwe Power BI-oplossing in productie. De uitvoer van deze fase is een productieoplossing die actief wordt gebruikt door zakelijke gebruikers. Wanneer u een agile methode gebruikt, is het acceptabel om enkele geplande verbeteringen te hebben die in een toekomstige iteratie worden geleverd. Afhankelijk van hoe vertrouwd u zich voelt met Power BI, bijvoorbeeld met het minimaliseren van risico's en onderbreking van de gebruiker, kunt u kiezen voor een gefaseerde implementatie. Of u kunt Power BI eerst implementeren voor een kleinere groep testgebruikers. Ondersteuning en bewaking zijn in deze fase en op doorlopende basis belangrijk. Zie [Migreren naar Power BI](powerbi-migration-deploy-support-monitor.md) voor meer informatie over de activiteiten in fase 5.

> [!TIP]
> De meeste concepten die in deze reeks artikelen over Power BI-migratie worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject.

## <a name="consider-migration-reasons"></a>Migratieredenen overwegen

Een productieve en goed functionerende gegevenscultuur is een hoofddoel van veel organisaties. Power BI is een uitstekend hulpprogramma om dit doel te helpen bereiken. Drie veelvoorkomende redenen waarom u zou willen migreren naar Power BI zijn:

- **Maak gebruik van beheerde selfservice BI** door nieuwe mogelijkheden te introduceren waarvan de selfservice BI-gebruikerscommunity kan profiteren. Power BI maakt toegang tot informatie en besluitvorming op breder vlak beschikbaar, terwijl men minder afhankelijk is van gespecialiseerde vaardigheden die soms moeilijk vindbaar zijn.
- **Rationaliseer de levering van ondernemings-BI** om te voldoen aan de vereisten die niet worden aangepakt via bestaande BI-hulpprogramma's, terwijl de complexiteit afneemt, de eigendomskosten worden verlaagd en/of standaarden worden ontwikkeld op basis van meerdere BI-hulpprogramma's die op dat moment in gebruik zijn.
- **Verlaag de economische druk** voor verhoogde productiviteit met minder resources, tijd en personeel.

## <a name="achieve-power-bi-migration-success"></a>Zorgen voor een geslaagde Power BI-migratie

Elke migratie is weer anders. Deze kan afhankelijk zijn van de organisatiestructuur, de gegevensstrategieën, de vervaldatum voor gegevensbeheer en de organisatiedoelstellingen. Er zijn echter enkele praktijken die we consistent terugzien bij onze klanten die een geslaagde Power BI-migratie hebben uitgevoerd.

- **Executive sponsoring:** Identificeer vroegtijdig in het proces een executive sponsor. Deze persoon moet iemand zijn die actief ondersteuning biedt voor BI in de organisatie en persoonlijk is gediend met het bereiken van een positief resultaat voor de migratie. In het ideale geval heeft de executive sponsor de ultieme autoriteit en verantwoordelijkheid voor de resultaten met betrekking tot Power BI.
- **Training, ondersteuning en communicatie:** Het is meer dan alleen een technologisch initiatief. Elk BI- of analyseproject is ook een initiatief van personen, dus overweeg om in een vroegtijdig stadium te investeren in gebruikerstraining en -ondersteuning. U kunt ook een communicatieplan maken om duidelijk aan alle belanghebbenden uit te leggen wat er waarom gebeurt en realistische verwachtingen te stellen. Zorg ervoor dat u een feedback-lus in uw communicatieplan opneemt om invoer van belanghebbenden vast te leggen.
- **Snelle winst:** Geef in eerste instantie prioriteit aan items met hoge waarde die een concrete zakelijke waarde hebben en dringend zijn. In plaats van te proberen om rapporten altijd nauwkeurig te migreren zoals ze in het oudere BI-platform werden weergegeven, kunt u zich bij het herontwerpen van het rapport beter richten op de zakelijke vraag die het rapport probeert te beantwoorden, inclusief de actie die moet worden ondernomen.
- **Modernisering en verbeteringen:** Wees bereid om de gebruikte methode opnieuw onder de loep te nemen. Een migratie kan een gelegenheid zijn om verbeteringen te introduceren. Bijvoorbeeld om handmatige gegevensvoorbereiding te elimineren of bedrijfsregels die beperkt waren tot één rapport, te verplaatsen. Overweeg om bestaande oplossingen te herstructureren, te moderniseren en samen te voegen wanneer de inspanning kan worden gerechtvaardigd. Het kan zijn dat hiervoor meerdere rapporten moeten worden samengevoegd tot één of dat verouderde artefacten die langere tijd niet zijn gebruikt, moeten worden verwijderd.
- **Continu leerproces:** Bereid u voor op een gefaseerde benadering tijdens welke u voortdurend blijft leren en zich zult moeten aanpassen. Werk in korte, iteratieve cycli om snel waarde te genereren. Maak er een gewoonte van om telkens kleine POC's te voltooien om zo het risico van onbekende factoren te minimaliseren, veronderstellingen te valideren en meer te weten te komen over nieuwe functies. Omdat Power BI een cloudservice is die maandelijks wordt bijgewerkt, is het belangrijk om op de hoogte te blijven van ontwikkelingen en van richting te veranderen wanneer dat nodig is.
- **Weerstand tegen verandering:** Er kunnen verschillende niveaus van weerstand zijn tegen verandering. Er zijn altijd wel gebruikers die zich verzetten tegen het leren van een nieuw hulpprogramma. Daarnaast kan het zijn dat professionals die veel tijd en moeite hebben besteed aan het verkrijgen van expertise met een ander BI-hulpprogramma, bang zijn dat ze overbodig worden. Dit kan leiden tot een interne politieke strijd, met name in zeer gedecentraliseerde organisaties.
- **Beperkingen:** Wees realistisch met migratieplannen, waaronder financiering, geschatte tijdsduur evenals rollen en verantwoordelijkheden voor alle betrokkenen.

## <a name="acknowledgments"></a>Dankwoord

Deze reeks artikelen is geschreven door Melissa Coates, Data Platform MVP en eigenaresse van [Coates Data Strategies](https://www.coatesdatastrategies.com/). Inzenders en revisoren zijn Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger en Peter Myers.

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel in deze serie over Power BI-migratie](powerbi-migration-pre-migration-steps.md) vindt u informatie over de stappen voorafgaand aan de migratie bij migratie naar Power BI.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- [SSRS-rapporten migreren naar Power BI](migrate-ssrs-reports-to-power-bi.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).
