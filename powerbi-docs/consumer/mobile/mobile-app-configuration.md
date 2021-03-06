---
title: Configuratie-instellingen voor de Power BI-app
description: Het gedrag van Power BI aanpassen met het hulpprogramma MDM
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 07/14/2020
ms.openlocfilehash: a867c0480e9c0762d1594016fb807cab8261c14c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414594"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>De Power BI-app extern configureren met behulp van het hulpprogramma Mobile Device Management (MDM)

De mobiele Power BI-app voor iOS en Android biedt ondersteuning voor app-instellingen waarmee beheerders van MDM-services (Mobile Device Management), zoals Intune, het gedrag van de app kunnen aanpassen.

De mobiele Power BI-app biedt ondersteuning de volgende configuratiescenario's:

* Configuratie van de rapportserver (iOS en Android)
* Instellingen voor gegevensbeveiliging (iOS en Android)
* Eenmalige aanmelding uitschakelen (iOS en Android)
* Instellingen voor interactie (iOS en Android)

## <a name="report-server-configuration-ios-and-android"></a>Configuratie van de rapportserver (iOS en Android)

Met de Power BI-app voor iOS en Android kunnen beheerders de configuratie van de rapportserver extern pushen naar ingeschreven apparaten.

| Sleutel | Type | Beschrijving |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Tekenreeks | Rapportserver-URL.<br><br>Moet beginnen met http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Tekenreeks | [optioneel]<br><br>De gebruikersnaam die u wilt gebruiken om verbinding te maken met de server.<br><br>Als deze niet bestaat, wordt de gebruiker gevraagd de gebruikersnaam voor de verbinding in te voeren.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Tekenreeks | [optioneel]<br><br>De standaardwaarde is Rapportserver<br><br>Een beschrijvende naam die in de app wordt gebruikt als naam voor de server. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | [optioneel]<br><br>De standaardwaarde is Waar. Als deze optie is ingesteld op Waar, worden hiermee alle eventuele definities van de rapportserver overschreven die al op het mobiele apparaat bestaan. Bestaande servers die al zijn geconfigureerd, worden verwijderd. Wanneer overschrijven is ingesteld op Waar, voorkomt u hiermee ook dat gebruikers die configuratie kunnen verwijderen.<br><br>Wanneer de optie is ingesteld op Onwaar, worden de gepushte waarden toegevoegd en blijven bestaande instellingen bestaan. Als dezelfde server-URL al is geconfigureerd in de mobiele app, blijft deze configuratie bestaan. De gebruiker wordt niet vanuit de app gevraagd zich opnieuw te verifiëren voor dezelfde server. |

## <a name="data-protection-settings-ios-and-android"></a>Instellingen voor gegevensbeveiliging (iOS en Android)

De mobiele Power BI-app voor iOS en Android biedt beheerders de mogelijkheid de standaardconfiguratie aan te passen voor beveiligings- en privacy-instellingen. Voor iOS kunt u afdwingen dat gebruikers hun Face ID, Touch ID of een wachtwoordcode opgeven bij het openen van de mobiele Power BI-app. Voor Android kunt u afdwingen dat gebruikers biometrische verificatie (vingerafdruk-id) gebruiken.

| Sleutel | Type | Beschrijving |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolean | De standaardwaarde is Onwaar. <br><br>Biometrie, zoals Touch ID of Face ID (iOS) of vingerafdruk-id (Android), kan vereist zijn voor gebruikers om toegang te krijgen tot de app op hun apparaat. Indien vereist, wordt er biometrie naast verificatie gebruikt.<br><br>Als u gebruikmaakt van beveiligingsbeleid voor apps, is het aan te raden deze instelling uit te schakelen om te voorkomen dat er dubbel om toegang wordt gevraagd. |

>[!NOTE]
>Instellingen voor gegevensbeveiliging worden alleen toegepast op Android-apparaten die biometrische verificatie ondersteunen.

## <a name="disable-single-sign-on-ios-and-android"></a>Eenmalige aanmelding uitschakelen (iOS en Android)

Standaard biedt de mobiele Power BI-app handige eenmalige aanmelding voor een enkele gebruiker door het aantal keren dat de gebruiker een gebruikersnaam en wachtwoord moet opgeven tot een minimum te beperken. Eenmalige aanmelding is gebaseerd op de veronderstelling dat het apparaat het persoonlijke apparaat van de gebruiker is en dat er slechts één gebruiker is die het apparaat en de daarop geïnstalleerde apps gebruikt.

Beheerders kunnen de instelling **DisableSingleSignOn** in het app-configuratiebestand inschakelen om de app op afstand te configureren om eenmalige aanmelding uit te schakelen en expliciet te vragen om het wachtwoord van gebruikers wanneer ze zich aanmelden.

Dit is een instelling voor alleen beheerders die op afstand wordt geconfigureerd. De eindgebruiker kan deze instelling niet wijzigen.

| Sleutel | Type | Beschrijving |
|---|---|---|
| com.microsoft.powerbi.mobile.DisableSingleSignOn | Boolean | De standaardwaarde is Onwaar.<br><br>Wanneer een gebruiker zich afmeldt, worden de bestaande referenties niet opnieuw door de app gebruikt, maar wordt de volgende gebruiker gevraagd om een wachtwoord op te geven om de Power BI-service te verifiëren en er verbinding mee te maken.
 |

## <a name="interaction-settings-ios-and-android"></a>Instellingen voor interactie (iOS en Android)

De Power BI-app voor iOS en Android biedt beheerders de mogelijkheid om interactie-instellingen te configureren als wordt besloten dat de standaardinstellingen voor interactie moeten worden gewijzigd binnen groepen gebruikers in een organisatie.

>[!NOTE]
>Niet alle interacties worden momenteel op alle apparaten ondersteund. Zie [Interactie-instellingen ten aanzien van rapporten configureren](mobile-app-interaction-settings.md) voor een grafiek waarin de huidige beschikbaarheid op apparaten wordt weergegeven.

| Sleutel | Type | Waarden | Beschrijving |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Tekenreeks |  <nobr>tikken</nobr><br><nobr>dubbeltikken</nobr> | Configureren of bij het tikken op een visueel element ook een gegevenspunt wordt geselecteerd. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Boolean |  <nobr>True</nobr><br><nobr>False</nobr> | Configureren of bij het tikken op een gegevenspunt de huidige selectie wordt vervangen of wordt toegevoegd aan de huidige selectie. |
| com.microsoft.powerbi.mobile.RefreshAction | Tekenreeks |  <nobr>slepen om te vernieuwen</nobr><br>knop | Configureren of de gebruiker beschikt over een knop om het rapport te vernieuwen of pull moet gebruiken om te vernieuwen. |
| com.microsoft.powerbi.mobile.FooterAppearance | Tekenreeks |  gedokt<br>dynamisch | Configureren of de voettekst van het rapport wordt gedokt aan de onderkant van het rapport of automatisch wordt verborgen. |

## <a name="deploying-app-configuration-settings"></a>Configuratie-instellingen voor de app implementeren

Hier volgen de stappen die u nodig hebt om configuratiebeleid voor de app te maken. Nadat u het configuratiebeleid hebt gemaakt, kunt u de bijbehorende instellingen toewijzen aan groepen gebruikers.

1. Maak verbinding met uw MDM-hulpprogramma.
2. Maak en benoem een nieuw app-configuratiebeleid.
3. Kies naar welke gebruikers u dit app-configuratiebeleid wilt distribueren.
4. Maak sleutel-waardeparen voor de instelling die u wilt pushen naar uw gebruikers.

Vanuit de Intune-portal kunnen beheerders deze instellingen via app-configuratiebeleid eenvoudig implementeren in de Power BI-app. Elke MDM-provider wordt echter ondersteund. Als u Intune niet gebruikt, moet u uw MDM-documentatie raadplegen over het implementeren van deze instellingen.

## <a name="next-steps"></a>Volgende stappen

* Download de mobiele Power BI-app vanuit de [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) en [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Volg [@MSPowerBI op Twitter](https://twitter.com/MSPowerBI)
* Deelnemen aan conversaties in de [Power BI-community](https://community.powerbi.com/)