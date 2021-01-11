---
title: Veelgestelde vragen over Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: Hier vindt u een lijst met veelgestelde vragen en antwoorden over Power BI-visuals. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: b2bfac5cbd3ce9b850e42ebf25c63b6e22fbeb68
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97884919"
---
# <a name="power-bi-visuals-faq"></a>Veelgestelde vragen over Power BI-visuals

## <a name="organizational-power-bi-visuals"></a>Power BI-visuals voor organisaties

Via de beheerportal kunt u Power BI-visuals voor uw organisatie beheren.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Hoe kan de beheerder de Power BI-visuals van uw organisatie beheren?

In de beheerportal, op het tabblad *Visuals van organisaties*, kan de beheerder [alle Power BI-visuals voor organisaties van het bedrijf](../../admin/organizational-visuals.md#organizational-visuals) zien en beheren. Dit omvat het toevoegen, uitschakelen, inschakelen en verwijderen van Power BI-visuals.

Gebruikers in de organisatie kunnen eenvoudig Power BI-visuals vinden en deze rechtstreeks importeren vanuit Power BI Desktop of de Power BI-service.

Nadat de beheerder een nieuwe versie van een Power BI-visual voor organisaties heeft geüpload, ontvangt iedereen in de organisatie dezelfde bijgewerkte versie. Alle rapporten waarin bijgewerkte Power BI-visuals worden gebruikt, worden automatisch bijgewerkt.

Gebruikers kunnen de Power BI-visuals voor organisaties vinden in de ingebouwde zakelijke opslag van Power BI Desktop en de Power BI-service op het tabblad *Mijn organisatie*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Als een beheerder een Power BI-visual uploadt vanuit de openbare marketplace naar een zakelijke opslag met behulp van *Visual toevoegen > vanuit AppSource*, wordt de visual dan automatisch bijgewerkt nadat een leverancier de visual in de openbare marketplace heeft bijgewerkt?

Ja, de visual wordt automatisch bijgewerkt vanuit de openbare marketplace. Als de visual is gecertificeerd, blijft de certificering behouden, met inbegrip van aanvullende functies zoals exporteren naar PDF of PowerPoint.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Is er een manier om de zakelijke opslag uit te schakelen?

Nee, gebruikers kunnen het tabblad *Mijn organisatie* altijd zien in Power BI Desktop en de Power BI-service. Als een beheerder alle Power BI-visuals voor organisaties in de beheerportal uitschakelt of verwijdert, is de zakelijke opslag leeg.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Als de beheerder Power BI-visuals vanuit de beheerportal (tenantinstellingen) uitschakelt, hebben gebruikers dan nog steeds toegang tot de Power BI-visuals voor organisaties?

Ja, als de beheerder de Power BI-visuals vanuit de beheerportal uitschakelt, heeft dat geen invloed op de zakelijke opslag.

Sommige organisaties schakelen Power BI-visuals uit en schakelen alleen geselecteerde visuals in die door de Power BI-beheerder zijn geïmporteerd en geüpload naar de zakelijke opslag.

Power BI-visuals uitschakelen vanuit de beheerportal is niet mogelijk in Power BI Desktop. Desktopgebruikers kunnen nog steeds Power BI-visuals in hun rapporten gebruiken en toevoegen vanuit de openbare marketplace. Die openbare Power BI-visuals worden echter niet meer weergegeven nadat ze zijn gepubliceerd naar de Power BI-service en geven vervolgens een bijbehorende foutmelding. 

Als de instelling van Power BI-visuals in de beheerportal wordt afgedwongen, kunnen gebruikers in de Power BI-service geen Power BI-visuals importeren uit de openbare marketplace. Alleen visuals uit de zakelijke opslag kunnen worden geïmporteerd.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Wat zijn de voordelen van Power BI-visuals in de zakelijke opslag?

* Iedereen krijgt dezelfde versie van de visual. De versie wordt beheerd door de Power BI-beheerder. Wanneer de beheerder de versie van de visual bijwerkt in de beheerportal, krijgen alle gebruikers in de organisatie automatisch de bijgewerkte versie.

* Het is niet nodig om bestanden van visuals via e-mail of gedeelde mappen te delen. Het aanbod in de zakelijke opslag is zichtbaar voor alle leden die zijn aangemeld.

* Beveiliging en ondersteuning, nieuwe versies van Power BI-visuals van organisaties worden automatisch in alle rapporten bijgewerkt.

* Beheerders kunnen bepalen welke Power BI-visuals er beschikbaar zijn binnen de organisatie.

* Beheerders kunnen visuals inschakelen/uitschakelen vanuit de beheerportal, zodat deze kunnen worden getest.

## <a name="certified-power-bi-visuals"></a>Gecertificeerde visuals in Power BI

### <a name="what-are-certified-power-bi-visuals"></a>Wat zijn gecertificeerde Power BI-visuals?

Gecertificeerde Power BI-visuals zijn Power BI-visuals die voldoen aan bepaalde [vereisten](power-bi-custom-visuals-certified.md) en zijn gecertificeerd door Microsoft.

In de [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) hebben gecertificeerde Power BI-visuals een gele badge die aangeeft dat ze zijn gecertificeerd.

Microsoft is niet de auteur van Power BI-visuals van derden. Klanten wordt aangeraden om rechtstreeks contact op te nemen met de auteur om de functionaliteit van visuals van derden te controleren.

### <a name="what-tests-are-done-during-the-certification-process"></a>Welke testen zijn uitgevoerd tijdens het certificeringsproces?

De testen van het certificeringsproces omvatten maar zijn niet beperkt tot: 
* Codebeoordelingen
* Analyse van statische code
* Gegevenslekken
* Datafuzzing
* Penetratietesten
* Toegang tot XSS-testen
* Injectie van schadelijke gegevens
* Invoervalidatie
* Functietesten
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Worden gecertificeerde Power BI-visuals opnieuw gecontroleerd bij elke nieuwe inzending (upgrade)?

Ja. Steeds wanneer een nieuwe versie van een gecertificeerde visuals wordt verzonden naar de Marketplace, ondergaat de versie-update van de visual dezelfde certificeringscontroles.

De versie-update wordt automatisch gecertificeerd. Als er een schending is die ervoor zorgt dat de update wordt afgewezen, wordt er een e-mailbericht naar de ontwikkelaar verzonden om uit te leggen wat er moet worden opgelost.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Kan een gecertificeerde Power BI-visual de certificering verliezen na een nieuwe update?

Nee, dit is niet mogelijk. Een gecertificeerde visual kan de certificering niet verliezen bij een nieuwe update. De update is geweigerd.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Moet ik mijn code delen in een openbare opslagplaats als ik mijn Power BI-visual laat certificeren?

Nee, u hoeft uw code niet openbaar te delen.

Geef leesmachtigingen op voor de controle van de code van de Power BI-visual. Gebruik bijvoorbeeld een privé-opslagplaats in GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Moet een gecertificeerde Power BI-visual in de marketplace staan?

Ja. Privé-visuals worden niet gecertificeerd.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Hoe lang duurt om mijn visual te laten certificeren?

Het laten certificeren van een nieuwe Power BI-visual (eerste certificering) kan tot wel vier weken duren. 

Het certificeren van een bijgewerkte versie van een Power BI-visual kan tot wel drie weken duren. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Zorgt het certificeringsproces ervoor dat er geen gegevens worden gelekt?

De testen die worden uitgevoerd, zijn ontworpen om te controleren of de visual geen toegang heeft tot externe services of resources. 

Microsoft is niet de auteur van Power BI-visuals van derden. Klanten wordt aangeraden om rechtstreeks contact op te nemen met de auteur om de functionaliteit van Power BI-visuals van derden te controleren.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Zijn niet-gecertificeerde Power BI-visuals veilig om te gebruiken?

Niet-gecertificeerde Power BI-visuals zijn niet automatisch onveilige visuals.

Sommige visuals zijn niet gecertificeerd omdat ze niet voldoen aan een of meer [certificeringsvereisten](power-bi-custom-visuals-certified.md#certification-requirements). Bijvoorbeeld als er verbinding wordt gemaakt met een externe service zoals kaartvisuals of visuals waarvoor commerciële bibliotheken worden gebruikt.
 
## <a name="visuals-with-additional-purchases"></a>Visuals met aanvullende aankopen

### <a name="what-is-a-visual-with-additional-purchases"></a>Wat is een visual met aanvullende aankopen?

Een visual met aanvullende aankopen is vergelijkbaar met een invoegtoepassing voor in-app aankopen (IAP). Dergelijke invoegtoepassingen zijn te herkennen aan een prijskaartje met **Mogelijk is een extra aankoop vereist**.

Power BI IAP-visuals zijn gratis te downloaden. Gebruikers betalen niets om deze Power BI-visuals te downloaden van de marketplace.

IAP-visuals bieden optionele aankopen in de app om te kunnen profiteren van geavanceerde functies.  

### <a name="what-is-changing-in-the-submission-process"></a>Hoe verandert het indieningsproces?

Het indieningsproces voor Power BI IAP-visuals uit de marketplace is hetzelfde als voor gratis Power BI-visuals. U kunt een Power BI-visual verzenden om deze te laten certificeren met behulp van [Partnercentrum](/partner-center/).


Ga voor het registreren van uw Power BI-visual naar het tabblad *Productinstallatie* en schakel het selectievakje *Mijn product vereist de aanschaf van een service* in.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Wat moet ik doen voordat ik mijn Power BI IAP-visual indien?

Als u aan een Power BI IAP-visual werkt of als u er al een hebt, zorgt u ervoor dat deze aan de [richtlijnen](guidelines-powerbi-visuals.md) voldoet.  

> [!NOTE]
> Gratis Power BI-visuals met een toegevoegde IAP-functie, moeten dezelfde functies bieden als daarvoor. Naast de oude, gratis functies kunt u optionele, geavanceerde betaalde functies toevoegen. U wordt aangeraden de Power BI IAP-visual met de geavanceerde functies als een nieuwe Power BI-visual in te dienen en de oude gratis visual niet bij te werken.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Moeten Power BI IAP-visuals worden gecertificeerd?

Het [certificeringsproces](power-bi-custom-visuals-certified.md) is optioneel. Het is aan de ontwikkelaar om te bepalen of deze zijn of haar Power BI IAP-visual wil laten certificeren.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Kan ik mijn Power BI IAP-visual laten certificeren?

Ja. Zodra uw Power BI IAP-visual is goedgekeurd door het AppSource-team kunt u uw Power BI-visual indienen voor [certificering](power-bi-custom-visuals-certified.md).

Het certificeringsproces is optioneel. Het is aan u om te beslissen of u uw IAP-visual wilt laten certificeren.

## <a name="additional-questions"></a>Aanvullende vragen

### <a name="how-to-get-support"></a>Ondersteuning verkrijgen

U kunt contact opnemen met het ondersteuningsteam voor Power BI-visuals via pbicvsupport@microsoft.com bij vragen, opmerkingen of problemen.  

## <a name="next-steps"></a>Volgende stappen

Ga naar [Problemen met Power BI-visuals oplossen](power-bi-custom-visuals-troubleshoot.md) voor meer informatie.