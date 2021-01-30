---
title: Een werkbaar concept van migratie naar Power BI testen
description: Richtlijnen voor het testen van een werkbaar concept bij het migreren naar Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: a51aaee15fc2a5e8d8facc1d34c0724dfa71d663
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086505"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Een werkbaar concept van migratie naar Power BI testen

In dit artikel wordt **Fase 3** beschreven, welke is gericht op het testen van een werkbaar concept (Proof of Concept, POC) om risico's te beperken en zo snel mogelijk in te spelen op onbekende factoren wanneer u naar Power BI migreert.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. Fase 3 wordt in dit artikel uitgelicht.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De nadruk in fase 3 ligt op de aanpak van onbekende factoren en het zo tijdig mogelijk elimineren van risico's. Een technische POC is handig voor het valideren van hypotheses. Dit kan iteratief worden uitgevoerd naast de implementatieplanning voor de oplossing (beschreven in [fase 2](powerbi-migration-planning.md)).

De uitvoer van deze fase is een Power BI-oplossing die een beperkt bereik heeft, de eerste open vragen afhandelt en klaar is voor extra werk in [fase 4](powerbi-migration-create-validate-content.md) om de oplossing gereed te maken voor productie.

> [!IMPORTANT]
> Het is niet de bedoeling dat er niks meer met de POC wordt gedaan. We verwachten dat dit een vroege iteratie is van de oplossing die later wordt gebruikt voor productie. U zou deze activiteit in uw organisatie een prototype, pilot, mockup, quickstart of minimaal levensvatbaar product (MVP) kunnen noemen. De uitvoering van een werkbaar concept is niet altijd nodig en kan een informeel karakter hebben.

> [!TIP]
> De meeste onderwerpen die in dit artikel worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject. Naarmate uw organisatie meer ervaring krijgt met Power BI, neemt de behoefte aan POC's af. Vanwege het snelle release-patroon van Power BI en de continue introductie van nieuwe functies, kunt u echter regelmatig technische POC's blijven maken voor leerdoeleinden.

## <a name="set-poc-goals-and-scope"></a>Doelstellingen en bereik voor POC bepalen

Voor een POC kunt u zich richten op de volgende doelen:

- Controleren van uw veronderstellingen over de werking van een functie.
- Meer leren over de verschillen tussen hoe Power BI en het verouderde BI-platform werken.
- Valideren van de eerste inzichten in bepaalde vereisten door experts.
- Een kleine gegevensset met echte gegevens maken om problemen met de gegevensstructuur, relaties, gegevenstypen of gegevenswaarden te begrijpen en te detecteren.
- Experimenteren en valideren met expressies in de [DAX-syntaxis](/dax/) die worden gebruikt door modelberekeningen.
- De verbinding van de gegevensbron testen met behulp van een gateway (als het een gatewaybron is).
- Het vernieuwen van de gegevens testen met behulp van een gateway (als het een gatewaybron is).
- De beveiligingsconfiguraties controleren, inclusief beveiliging op rijniveau, indien van toepassing.
- Experimenteren met indelings- en cosmetische beslissingen.
- Controleren of alle functionaliteit in de Power BI-service werkt zoals verwacht.

Het bereik van de POC is afhankelijk van wat de onbekende factoren zijn of van welke doelstellingen moeten worden gevalideerd met collega's. Als u de complexiteit wilt verminderen, moet u het bereik van de POC zo beperkt mogelijk houden.

Meestal zijn bij een migratie de vereisten bekend, omdat er basissituatie met een bestaande oplossing is. Afhankelijk van hoeveel verbeteringen er worden aangebracht of van de bestaande Power BI-vaardigheden, kan een POC toch een aanzienlijke waarde bieden. Bovendien kan het handig zijn om snel een prototype te maken met feedback van klanten, om zo de vereisten te verduidelijken, vooral als er verbeteringen moeten worden aangebracht.

> [!IMPORTANT]
> Zelfs als een POC slechts een subset van de gegevens bevat, of alleen een beperkt aantal visuals bevat, is het vaak belangrijk dat u deze van begin tot eind doorloopt. Dat wil zeggen: van de ontwikkeling van Power BI Desktop tot implementatie naar een ontwikkelingswerkruimte in de Power BI-service. Dit is de enige manier om de doelstellingen van de POC volledig te realiseren. Dit geldt met name wanneer de Power BI-service essentiële functionaliteit moet leveren die u nog niet eerder hebt gebruikt, zoals een DirectQuery-gegevensset met behulp van eenmalige aanmelding. Tijdens de POC kunt u zich richten op aspecten waarover u twijfels hebt of die u met anderen moet verifiëren.

## <a name="handle-differences-in-power-bi"></a>Omgaan met verschillen in Power BI

Power BI kan worden gebruikt als een _op modellen gebaseerd hulpprogramma_ of als een _op rapporten gebaseerd hulpprogramma_. Een oplossing op basis van modellen omvat het ontwikkelen van een gegevensmodel, terwijl een oplossing op basis van rapporten een koppeling maakt met een al geïmplementeerd gegevensmodel.

Vanwege de extreme flexibiliteit zijn er enkele aspecten van Power BI die fundamenteel kunnen afwijken van het oudere BI-platform waar u vandaan migreert.

### <a name="consider-redesigning-the-data-architecture"></a>Overwegen om de gegevensarchitectuur opnieuw te ontwerpen

Als u migreert van een verouderd BI-platform met een eigen semantische laag, is het waarschijnlijk een goede optie om een importgegevensset te maken. Power BI werkt het beste met een tabelontwerp met een [sterschema](star-schema.md). Als de verouderde semantische laag geen sterschema heeft, is het mogelijk dat een herontwerp vereist is om optimaal te profiteren van Power BI. Het definiëren van een semantische laag die voldoet aan de ontwerpprincipes van sterschema's (inclusief relaties, veelgebruikte metingen en beschrijvende organisatieterminologie) vormt een uitstekend uitgangspunt voor selfservice-rapportauteurs.

Als u migreert van een verouderd BI-platform waarbij rapporten verwijzen naar relationele gegevensbronnen met behulp van SQL-query's of opgeslagen procedures, en als u van plan bent Power BI te gebruiken in [DirectQuery-modus](../connect-data/desktop-use-directquery.md), kunt u mogelijk dat u uw gegevensmodel vrijwel ongewijzigd kunt migreren.

> [!CAUTION]
> Als u ziet dat er veel Power BI Desktop-bestanden met één geïmporteerde tabel ziet, is dat meestal een teken dat het ontwerp niet optimaal is. In dit geval moet u nagaan of het gebruik van [gedeelde gegevenssets](../connect-data/service-datasets-across-workspaces.md) op basis van een ontwerp met een [sterschema](star-schema.md) een beter resultaat kan opleveren.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Bepalen hoe dashboardconversies moeten worden verwerkt

In de BI-industrie is een dashboard een verzameling visuals die belangrijke metrische gegevens op één pagina weergeeft. In Power BI vertegenwoordigt een dashboard echter een specifieke visualisatiefunctie die alleen kan worden gemaakt in de Power BI-service. Wanneer u een dashboard migreert vanaf een verouderd BI-platform, hebt u twee opties:

1. Het verouderde dashboard kan opnieuw worden gemaakt als Power BI-_rapport_. De meeste rapporten worden gemaakt met Power BI Desktop. Gepagineerde rapporten en Excel-rapporten zijn ook mogelijk.
2. Het verouderde dashboard kan opnieuw worden gemaakt als Power BI-_dashboard_. [Dashboards](../fundamentals/service-basic-concepts.md#dashboards) zijn een visualisatiefunctie van de Power BI-service. Dashboard-visuals worden vaak gemaakt door visuals vast te maken uit een of meer rapporten, Q&A of Quick Insights.

> [!TIP]
> Omdat dashboards een Power BI-inhoudstype zijn, kunt beter niet het woord _dashboard_ gebruiken in de naam van het rapport of het dashboard.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Op het grotere geheel richten bij het opnieuw maken van visuals

Elk BI-hulpprogramma heeft zijn sterke punten en focusgebieden. Daarom is het mogelijk dat de exacte rapportvisuals waarvan u in een verouderd BI-platform afhankelijk was, geen exacte vervanging in Power BI hebben.

Bij het opnieuw maken van rapportvisuals kunt u zich beter richten op de hoofdvragen voor uw bedrijf die centraal staan in een bepaald rapport. Hiermee vermindert u de druk om het ontwerp van elke visual exact te repliceren. Hoewel inhoudsgebruikers blij zijn met consistentie bij het gebruik van gemigreerde rapporten, is het belangrijk dat u niet onnodig veel tijd besteed aan tijdrovende discussies over kleine details.

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel van deze reeks over Power BI-migratie](powerbi-migration-create-validate-content.md) komt u meer te weten over fase 4, die zich bezighoudt met het maken en valideren van inhoud tijdens de migratie naar Power BI.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).
