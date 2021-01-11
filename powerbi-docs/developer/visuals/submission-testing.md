---
title: Tests voor het indienen van een Power BI-visual in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel worden de testcases beschreven waarvoor uw visual moet slagen voordat u de visual kunt publiceren in AppSource. Er zijn ook optionele testcases. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: b5054d821dc797f1606fea8ec5d0bb43569a57e5
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888461"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Tests voor het indienen van een Power BI-visual

Voordat u uw visual publiceert in [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), moet uw visual slagen voor de in dit artikel vermelde tests. Test uw visual voordat u deze indient. Als uw visual niet slaagt voor de verplichte testcases, wordt deze afgewezen.

Zie [Power BI-visuals publiceren in Partnercentrum](./office-store.md) voor meer informatie over het publicatieproces.

## <a name="testing-a-new-version-of-a-published-visual"></a>Een nieuwe versie van een gepubliceerde visual testen

Als u een nieuwe versie van een al gepubliceerde visual wilt testen of fouten erin wilt opsporen, kunt u de AppSource-versie overschrijven met een lokale bestandsversie door de ontwikkelaarsmodus in Power BI Desktop in te schakelen.

Voer de volgende stappen uit om de ontwikkelaarsmodus in te schakelen:

1. Open Power BI Desktop.

2.  Selecteer **Bestand** > **Opties en Instellingen**.

3.  Selecteer **Opties**.

4. Selecteer in het venster Opties in de lijst HUIDIG BESTAND **Rapportinstellingen**.

5. Selecteer in de ontwikkelaarsmodus de optie **Ontwikkelaarsmodus voor deze sessie inschakelen**.

>[!NOTE]
>In Power BI Desktop is de ontwikkelaarsmodus alleen geldig voor de duur van één sessie. Als u een nieuw Power BI Desktop-exemplaar voor het testen opent, moet u de ontwikkelaarsmodus weer inschakelen.

## <a name="general-test-cases"></a>Algemene testcases

Controleer of uw visual voor de algemene testcases slaagt.

| Testcase | Verwachte resultaten
| --------- | ----------------
| Maak een **gestapeld kolomdiagram** met **Categorie** en **Waarde**. Converteer deze naar uw visual en vervolgens terug naar het kolomdiagram. | Er treden geen fouten op bij deze conversies. |
| Maak een **meter** met drie metingen. Converteer deze naar uw visual en vervolgens terug naar de **meter**. | Er treden geen fouten op bij deze conversies. |
| Maak selecties in uw visual. | De selecties worden weergegeven in andere visuals. |
| Selecteer elementen in andere visuals. | In uw visual worden gefilterde gegevens weergegeven in overeenstemming met de selectie in andere visuals. |
| Controleer de minimale/maximale **dataViewMapping**-voorwaarden. | Veldbuckets kunnen een of meer velden accepteren of worden bepaald door andere buckets. De minimale/maximale **dataViewMapping**-voorwaarden moeten correct worden ingesteld in de mogelijkheden van uw visual. |
| Verwijder alle velden in verschillende volgordes. | De visual wordt op de juiste wijze opgeschoond als velden in willekeurige volgorde worden verwijderd. Er treden geen fouten op in de-console of in de browser. |
| Open het deelvenster **Notatie** met elke mogelijke bucketconfiguratie. | Er treden geen null-referentie-uitzonderingen op bij deze test. |
| Filter gegevens met behulp van het deelvenster **Filter** op visual-, pagina- en rapportniveau. | De juiste knopinfo wordt weergegeven na het toepassen van filters. De gefilterde waarde wordt weergegeven in de knopinfo. |
| Filter gegevens met behulp van een **slicer**. | De juiste knopinfo wordt weergegeven na het toepassen van filters. De gefilterde waarde wordt weergegeven in de knopinfo. |
| Filter gegevens met behulp van een gepubliceerde visual. Selecteer bijvoorbeeld een cirkelsegment of een kolom. | De juiste knopinfo wordt weergegeven na het toepassen van filters. De gefilterde waarde wordt weergegeven in de knopinfo. |
| Als kruislings filteren wordt ondersteund, controleert u of de filters goed werken. | Bij het toepassen van de selectie worden andere visuals op deze pagina van het rapport gefilterd. |
| Selecteer items met de toetsen Ctrl, Alt en Shift. | Er treedt geen onverwacht gedrag op. |
| Wijzig de **weergavemodus** in **Werkelijke grootte**, **Passend op pagina** en **Passend in breedte**. | De muiscoördinaten kloppen. |
| Wijzig de grootte van uw visual. | De visual reageert normaal op de wijziging van de grootte. |
| Stel de rapportgrootte in op het minimum. | Er treden geen weergavefouten op. |
| Controleer of de schuifbalken goed werken. | Waar nodig moeten er schuifbalken aanwezig zijn. Controleer de grootte van de schuifbalken. Schuifbalken mogen niet te breed of te dun zijn. De positie en grootte van schuifbalken moeten in overeenstemming zijn met andere elementen van uw visual. Controleer of er schuifbalken nodig zijn voor verschillende grootten van de visual. |
| Maak uw visual vast aan een **dashboard**. | De visual moet correct worden weergegeven. |
| Voeg meerdere versies van uw visual toe aan één rapportpagina. | Alle versies van de visual worden goed weergegeven en functioneren correct. |
| Voeg meerdere versies van uw visual toe aan meerdere rapportpagina's. | Alle versies van de visual worden goed weergegeven en functioneren correct. |
| Schakel tussen rapportpagina's. | De visual wordt correct weergegeven. |
| Test de leesweergave en de bewerkweergave voor uw visual. | Alle functies werken goed. |
| Als in uw visual animaties worden gebruikt, moet u elementen toevoegen, wijzigen en verwijderen. | De animatie van de elementen van uw visual werkt correct. |
| Open het deelvenster **Eigenschappen**. Schakel eigenschappen in en uit, voer aangepaste tekst in, belast de beschikbare opties zwaar en voer onjuiste gegevens in. | De visual reageert op de juiste manier. |
| Sla het rapport op en open het opnieuw. | Alle instellingen voor eigenschappen blijven behouden. |
| Schakel heen en weer tussen verschillende pagina's in het rapport. | Alle instellingen voor eigenschappen blijven behouden. |
| Test alle functionaliteit van uw visual, met inbegrip van de verschillende opties in de visual. | Alle weergaven en functies werken naar behoren. |
| Test alle numerieke, datum- en tekengegevenstypen, zoals in de volgende tests. | Alle gegevens worden correct opgemaakt. |
| Bekijk de opmaak van knopinfowaarden, aslabels, gegevenslabels en andere elementen met opmaak van de visual. | Alle elementen worden correct opgemaakt. |
| Controleer of gegevenslabels gebruikmaken van de notatiereeks. | Alle gegevenslabels worden correct opgemaakt. |
| Schakel automatische opmaak in en uit voor numerieke waarden in knopinfo. | Knopinfowaarden worden correct weergegeven. |
| Test gegevensinvoer met verschillende soorten gegevens, zoals numerieke gegevens, tekst, datum/tijd en andere notatiereeksen van het model. Test verschillende gegevensvolumes, zoals duizenden rijen, één rij en twee rijen. | Alle weergaven en functies werken naar behoren. |
| Geef verkeerde gegevens op in uw visual, zoals null-, oneindige en negatieve waarden en onjuiste waardetypen. | Alle weergaven en functies werken naar behoren. |

## <a name="optional-browser-testing"></a>Optionele browsertests

Het AppSource-team controleert visuals in de meest recente Windows-versies van de browsers Google Chrome, Microsoft Edge en Mozilla Firefox.
Test uw visual in de volgende browsers (optioneel).

| Testcase | Verwachte resultaten
| --------- | ----------------
| **Windows** |
| Google Chrome (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| Mozilla Firefox (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| Microsoft Edge (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| Microsoft Internet Explorer 11 (optioneel) | Alle weergaven en functies werken naar behoren. |
| **MacOS** |
| Chrome (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| Firefox (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| Safari (eerdere versie) | Alle weergaven en functies werken naar behoren. |
| **Linux** |
| Firefox (nieuwste en eerdere versies) | Alle weergaven en functies werken naar behoren. |
| **Mobile iOS** |
| Apple Safari iPad (eerdere versie van Safari) | Alle weergaven en functies werken naar behoren. |
| Chrome iPad (nieuwste versie van Safari) | Alle weergaven en functies werken naar behoren. |
| **Mobile Android** |
| Chrome (nieuwste en eerdere versies) | Alle weergaven en functies werken naar behoren. |

## <a name="desktop-testing"></a>Desktoptests

Test uw visual in de huidige versie van [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Testcase | Verwachte resultaten
| --------- | ----------------
| Test alle functies van uw visual. | Alle weergaven en functies werken naar behoren. |
| Importeer een bestand, sla het op, open het bestand en publiceer het in de Power BI-webservice met behulp van de knop **Publiceren** in Power BI Desktop. | Alle weergaven en functies werken naar behoren. |
| Wijzig de numerieke notatiereeks in een waarde van nul of drie decimalen door de precisie te vergroten of verkleinen. | De visual wordt correct weergegeven. |

## <a name="performance-testing"></a>Prestaties testen

Het prestatieniveau bij uitvoering van uw visual moet acceptabel zijn. Gebruik hulpprogramma's voor ontwikkelaars om de prestaties te valideren. Vertrouw niet op visuele aanwijzingen en de tijdlogboeken van de console.

| Testcase | Verwachte resultaten
| --------- | ----------------
| Maak een visual met veel visuele elementen. | De visual moet goed functioneren en de toepassing mag niet vastlopen. Er mogen geen prestatieproblemen zijn met elementen, zoals animatiesnelheid, vergroten of verkleinen, filteren en selecteren.

## <a name="next-steps"></a>Volgende stappen

Zie [Power BI-visuals publiceren in Partnercentrum](./office-store.md) voor meer informatie over het publicatieproces.

Hebt u nog vragen? [Stel een vraag aan de Power BI-community](https://community.powerbi.com/).
