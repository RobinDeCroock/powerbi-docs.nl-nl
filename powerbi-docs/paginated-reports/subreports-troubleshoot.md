---
title: Problemen met subrapporten in gepagineerde Power BI-rapporten oplossen
description: Meer informatie over oplossingen voor veelvoorkomende problemen bij het gebruik van subrapporten, die rapportitems zijn binnen een gepagineerd rapport.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 6a0e90036b759c409a9f5b3e994571c2a0eb510c
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747500"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Problemen met subrapporten in gepagineerde Power BI-rapporten oplossen

Soms krijgt u mogelijk een onverwacht resultaat of werkt de functie niet zoals verwacht wanneer u subrapporten in gepagineerde rapporten gebruikt. Dit artikel bevat oplossingen voor algemene problemen bij het gebruik van subrapporten. Een *subrapport* is een rapportitem waarin een ander rapport wordt weergegeven in de hoofdtekst van een gepagineerd hoofdrapport. Zie [Subrapporten in gepagineerde Power BI-rapporten](subreports.md) voor achtergrondinformatie.

## <a name="subreport-couldnt-be-found"></a>Kan het subrapport niet vinden

**Beschrijving:** Het subrapport wordt niet weergegeven. In plaats daarvan wordt een foutmelding weergegeven.

### <a name="message"></a>Bericht

Kan het subrapport Subreport1 niet vinden op de opgegeven locatie CustomerDetails. Controleer of het subrapport is gepubliceerd en of de naam juist is.

### <a name="possible-reasons"></a>Mogelijke redenen

- Een subrapport met de opgegeven naam bestaat niet in dezelfde werkruimte of app als het hoofdrapport.
- De gebruiker heeft geen toegang tot het subrapport.
- Het aantal subrapporten in het hoofdrapport heeft de limiet voor subrapporten bereikt (50 subrapporten).

### <a name="troubleshooting-steps"></a>Stappen voor probleemoplossing

**In een werkruimte**

- Controleer of het rapport met de naam in het foutbericht in de werkruimte voorkomt. De naam is niet hoofdlettergevoelig.

**In een app**

- Controleer of het rapport met de naam in het foutbericht in de app voorkomt. Neem contact op met de auteur van de app voor verdere ondersteuning.

**Als het rapport is gedeeld**

1. Controleer of het rapport met de naam in het foutbericht met u is gedeeld.
2. Als het rapport bestaat, controleert u of de naam van de eigenaar hetzelfde is voor het hoofdrapport en het subrapport. Neem vervolgens contact op met de eigenaar van het hoofdrapport met deze gegevens.

## <a name="subreport-renders-with-unexpected-content"></a>Het subrapport wordt weergegeven met onverwachte inhoud

### <a name="possible-reason"></a>Mogelijke reden

Met Power BI kunnen gebruikers meerdere rapporten met dezelfde naam in dezelfde werkruimte hebben

### <a name="troubleshooting-steps-for-report-authors"></a>Stappen voor probleemoplossing (voor auteurs van rapporten)

1. Open het hoofdrapport in Power BI Report Builder en bepaal de naam van het subrapport.
2. Zoek naar rapporten met dezelfde naam in de werkruimte.
3. Zoek het verwachte rapport op en wijzig de naam van de rest.

**Voor niet-auteurs:** Neem contact op met de auteur.

## <a name="data-retrieval-fails"></a>Kan geen gegevens ophalen

**Beschrijving:** Kan geen gegevens ophalen tijdens het weergeven van het subrapport. Het subrapport wordt niet weergegeven. In plaats daarvan wordt een foutmelding weergegeven.

### <a name="message"></a>Bericht

Kan geen gegevens ophalen voor het subrapport Subreport1, dat zich bevindt in: InvoiceDetails. Raadpleeg de logboekbestanden voor meer informatie.

### <a name="troubleshooting-steps"></a>Stappen voor probleemoplossing

Hetzelfde als de algemene stappen voor probleemoplossing voor rapporten met problemen ten aanzien van de gegevenstoegang.

## <a name="rendering-fails-unspecified-parameters"></a>Kan niet weergeven: Niet-opgegeven parameters

**Beschrijving:** Kan subrapport niet weergeven vanwege niet-opgegeven parameters. Het subrapport bevat verplichte parameters, maar het hoofdrapport heeft deze niet allemaal ingesteld.

### <a name="message"></a>Bericht 
Een of meer parameters zijn niet opgegeven voor het subrapport, Subreport1, dat zich bevindt in: SubreportAWithDS.

### <a name="troubleshooting-steps-for-the-report-author"></a>Stappen voor probleemoplossing (voor de auteur van het rapport)

1. Open het hoofdrapport in Power BI Report Builder.
2. Open het subrapport in Power BI Report Builder.
3. Controleer of de set parameters die zijn doorgegeven in het rapportitem van het subrapport in het hoofdrapport overeenkomt met de set parameters in het subrapport.

**Voor niet-auteurs:** Neem contact op met de auteur.

## <a name="rendering-fails-recursion-limit"></a>Kan niet weergeven: Limiet voor recursie

**Beschrijving:** Kan subrapport niet weergeven vanwege de limiet voor recursie. Subrapporten kunnen niet over meer dan 20 niveaus worden genest.

### <a name="message"></a>Bericht

Het rapport of subrapport heeft een recursief subrapport, Subreport1, dat het toegestane maximum voor recursie heeft overschreden.

### <a name="troubleshooting-steps-for-report-authors"></a>Stappen voor probleemoplossing (voor auteurs van rapporten)

- Minder nesten.
- Ontwerp de rapportstructuur opnieuw.

## <a name="other-errors"></a>Overige fouten

**Beschrijving:** Fouten die niet in de vorige categorieën vallen.

### <a name="message"></a>Bericht

‘Fout: Subrapport kan niet worden weergegeven.

### <a name="possible-reasons"></a>Mogelijke redenen

- Meerdere fouten tijdens het weergeven van subrapporten, zoals parameters die niet overeenkomen als er problemen zijn bij het ophalen van gegevens.
- Onverwachte fouten.

### <a name="troubleshooting-steps-for-report-authors"></a>Stappen voor probleemoplossing (voor auteurs van rapporten)

1. Controleer of het subrapport rechtstreeks kan worden weergegeven.
2. Als het subrapport kan worden weergegeven, controleert u de parameters in zowel het subrapport als het hoofdrapport.
3. Zorg ervoor dat het hoofdrapport niet meer dan 50 unieke subrapporten bevat en dat het subrapport niet over meer dan 20 niveaus is genest.
4. Als u het probleem niet kunt oplossen, neemt u contact op met Power BI-ondersteuning.

**Voor niet-auteurs:** Neem contact op met de auteur.

## <a name="next-steps"></a>Volgende stappen

[Subrapporten in gepagineerde Power BI-rapporten](subreports.md)

[Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
