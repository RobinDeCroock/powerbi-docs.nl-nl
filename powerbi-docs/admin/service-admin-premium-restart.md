---
title: Een Power BI Premium-capaciteit opnieuw opstarten
description: Lees hoe u een Power BI Premium-capaciteit opnieuw opstart om problemen met de prestaties op te lossen.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: da6108927e9d6182c08db68972a5452514eedca7
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532953"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Een Power BI Premium-capaciteit opnieuw opstarten

Als Power BI-beheerder moet u mogelijk een Premium-capaciteit opnieuw opstarten. In dit artikel wordt uitgelegd hoe u een capaciteit opnieuw opstart en wordt een aantal vragen over opnieuw opstarten en prestaties beantwoord.

## <a name="why-does-power-bi-provide-this-option"></a>Waarom biedt Power BI deze optie?

Power BI biedt gebruikers de mogelijkheid om ingewikkelde analyses uit te voeren met enorme gegevenshoeveelheden. Helaas kunnen gebruikers prestatieproblemen veroorzaken door de Power BI-service met taken te overbelasten, te complexe query's te schrijven, cirkelverwijzingen te maken, enzovoort.

Power BI gedeelde capaciteit biedt enigszins bescherming tegen dergelijke situaties door limieten in te stellen voor de bestandsgrootte, vernieuwingsschema’s en andere aspecten van de service. In een Power BI Premium-capaciteit gelden de meeste van deze limieten echter niet meer. Als gevolg daarvan kan één rapport met een ongeldige DAX-expressie of een uiterst complex model significante prestatieproblemen veroorzaken. Wanneer een rapport wordt verwerkt, kunnen alle beschikbare resources van de capaciteit worden verbruikt. 

In Power BI worden voortdurend verbeteringen aangebracht door om gebruikers van Premium-capaciteit tegen dit soort situaties te beschermen. Ook geven we beheerders de middelen in handen om te analyseren wanneer en waarom capaciteiten worden overbelast. Bekijk onze [korte trainingssessie](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) en [langere trainingssessie](https://powerbi.tips/2018/07/) voor meer informatie. Tegelijkertijd hebt u de mogelijkheid nodig om grote problemen te beperken wanneer deze zich voordoen. De snelste manier om deze problemen te beperken is het opnieuw opstarten van de capaciteit.

> [!NOTE]
> Power BI Premium heeft onlangs een nieuwe versie van Premium uitgebracht, genaamd **Premium Gen2**, die momenteel beschikbaar is als preview. Voor Preview Gen2-capaciteiten is opnieuw opstarten niet vereist, dus deze functie is niet beschikbaar in Premium Gen2.
>
> Voor **Inge sloten Gen2** -capaciteit hoeft u ook niet opnieuw te worden opgestart. Raadpleeg [Power bi embedded Generation 2](../developer/embedded/power-bi-embedded-generation-2.md)om de Power bi embedded verbeteringen van Gen2 te bekijken.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Is het proces voor opnieuw opstarten veilig? Gaan er gegevens verloren?

Alle opgeslagen gegevens, definities, rapporten en dashboards in uw capaciteit blijven tijdens het opnieuw opstarten volledig intact. Wanneer u een capaciteit opnieuw opstart, worden in de meeste gevallen doorlopende geplande en ad-hoc vernieuwingen tijdelijk gestopt door de vernieuwingsengine en vervolgens opnieuw opgestart dankzij de ingebouwde herstartlogica van Power BI. De service probeert alle beïnvloede vernieuwingen opnieuw uit te voeren zodra de capaciteit weer beschikbaar is. De status van vernieuwingen kan in de gebruikersinterface tijdens het opnieuw opstarten niet worden gewijzigd. 

Gebruikers die met de capaciteit werken, raken niet-opgeslagen werk kwijt tijdens een herstartproces. Gebruikers moeten hun browsers vernieuwen zodra het opnieuw opstarten is voltooid.

## <a name="how-do-i-restart-a-capacity"></a>Hoe kan ik een capaciteit opnieuw opstarten?

Volg deze stappen om een capaciteit opnieuw op te starten.

1. Navigeer in de Power BI-beheerportal, op het tabblad **Capaciteitsinstellingen**, naar uw capaciteit. 

1. Voeg de *functievlag* **CapacityRestart** toe aan de URL van uw capaciteit: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Onder **Geavanceerde instellingen** > **CAPACITEIT OPNIEUW OPSTARTEN**, selecteert u de optie **Capaciteit opnieuw opstarten**.

    ![Capaciteit opnieuw opstarten](media/service-admin-premium-restart/restart-capacity.png)

1. In het dialoogvenster **Capaciteit opnieuw opstarten** selecteert u de optie **Ja, capaciteit opnieuw opstarten**.

    ![Opnieuw opstarten bevestigen](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Hoe kan ik voorkomen dat zich in de toekomst problemen voordoen?

De beste manier om problemen te voorkomen, is gebruikers te instrueren over het efficiënt modelleren van gegevens. Zie onze [trainingssessie](https://powerbi.tips/2018/07/) voor meer informatie.

Het is tevens aan te raden regelmatig [uw capaciteiten te controleren](service-admin-premium-monitor-capacity.md), om trends te vinden die mogelijk duiden op onderliggende problemen. We zijn van plan regelmatige updates van de bewakings-app en andere hulpprogramma’s te publiceren, zodat u uw capaciteiten effectiever kunt bewaken en beheren.

## <a name="next-steps"></a>Volgende stappen

[Wat is Power BI Premium?](service-premium-what-is.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
