---
title: Interactie-instellingen ten aanzien van rapporten configureren
description: Meer informatie over het overschrijven van standaardinstellingen voor interactie ten aanzien van-rapporten.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542284"
---
# <a name="configure-report-interaction-settings"></a>Interactie-instellingen ten aanzien van rapporten configureren

## <a name="overview"></a>Overzicht

De mobiele Power BI-app heeft een aantal configureerbare interactie-instellingen waarmee u kunt bepalen hoe u met uw gegevens omgaat en hoe sommige elementen in de mobiele app van Power BI zich gedragen. Er zijn momenteel instellingen voor
* [Interactie van tikken versus dubbeltikken op rapportvisuals](#single-tap)
* [Gedokte versus dynamische voettekst voor rapporten](#docked-report-footer-android-phones) (Android)
* [Rapporten vernieuwen via een knop versus de actie Slepen om te vernieuwen](#report-refresh-android-phones) (Android)

Als u de interactie-instellingen wilt weergeven, tikt u op uw profielafbeelding om het [zijpaneel](./mobile-apps-home-page.md#header) te openen, kiest u **Instellingen** en gaat u naar de sectie **Interactie**.

![Interactie-instellingen](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>Interactie-instellingen voor de knop Vernieuwen en voor het dokken van de rapportvoettekst hebben momenteel geen effect op rapportserver-rapporten. Dit verandert met de release van Report Server in januari 2020.

## <a name="interaction-settings"></a>Interactie-instellingen

### <a name="single-tap"></a>Tikken
Als u de Power BI Mobile-app downloadt, is deze ingesteld voor interactie met één tik. Dit betekent dat als u in een visual tikt om een actie uit te voeren, zoals het selecteren van een slicer-item, kruislings markeren, klikken op een koppeling of knop, enzovoort, zowel de visual wordt geselecteerd als de gewenste actie wordt uitgevoerd.

Als u wilt, kunt u interactie via tikken uitschakelen. U krijgt dan interactie via dubbeltikken. Bij interactie met dubbeltikken tikt u eerst op een visual om het te selecteren. Daarna tikt u nogmaals op de visual om uw gewenste actie uit te voeren.

### <a name="docked-report-footer-android-phones"></a>Gedokte voettekst van rapporten (Android-telefoons)

Met de instelling voor gedokte voettekst van rapporten bepaalt u of de voettekst van rapporten onderaan het rapport gedokt blijft (dat wil zeggen: vast en altijd zichtbaar), of wordt verborgen en opnieuw wordt weergegeven op basis van uw acties in het rapport, zoals schuiven.

Op Android-telefoons is de instelling voor gedokte voettekst van rapporten standaard **ingeschakeld**, wat inhoudt dat de voettekst van rapporten gedokt is en altijd zichtbaar is onderaan het rapport. Schakel de instelling **uit** als u de voorkeur geeft aan een dynamische rapportvoettekst die wordt weergegeven en verdwijnt afhankelijk van uw acties in het rapport.

### <a name="report-refresh-android-phones"></a>Rapporten vernieuwen (Android-telefoons)

De instelling voor het vernieuwen van rapporten bepaalt hoe u het vernieuwen van rapporten start. U kunt ervoor kiezen om het rapport te vernieuwen via een knop voor vernieuwen op alle rapportkopteksten of via de actie Slepen om te vernieuwen (licht slepen van boven naar beneden) op de rapportpagina. In de afbeelding hieronder kunt u de twee alternatieven zien. 

![De knop Vernieuwen versus de actie Slepen om te vernieuwen](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Op Android-telefoons wordt de knop Vernieuwen standaard toegevoegd.

Als u de instelling voor het vernieuwen van het rapport wilt wijzigen, gaat u naar het item Rapport vernieuwen in de interactie-instellingen. De huidige instelling wordt weergegeven. Tik op de waarde om een pop-up te openen waarin u een nieuwe waarde kunt kiezen.

![Vernieuwen instellen](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Externe configuratie

Interacties kunnen ook extern worden geconfigureerd door een beheerder met behulp van een MDM-hulpprogramma met een app-configuratiebestand. Op deze manier is het mogelijk om de interactie-ervaring met rapporten in de hele organisatie of voor specifieke groepen gebruikers in de organisatie te standaardiseren. Zie [Interactie configureren met behulp van Mobiele apparaten beheren](./mobile-app-configuration.md) voor meer informatie.


## <a name="next-steps"></a>Volgende stappen
* [Interactie met rapporten](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Interactie configureren met behulp van Mobiele apparaten beheren](./mobile-app-configuration.md)
