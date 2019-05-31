---
title: Toegang via mobiele iOS-apps tot rapportservers op afstand configureren
description: Leer hoe u de mobiele iOS-apps op afstand kunt configureren voor uw rapportserver.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/15/2018
ms.author: maggies
ms.openlocfilehash: 27b3aad6f1a96c069f56ed68823b71b38115a98a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770648"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Toegang via Power BI mobiele iOS-apps tot rapportservers op afstand configureren

In dit artikel leert u hoe u het MDM-hulpprogramma van uw organisatie gebruikt om toegang op afstand via de Power BI mobiele iOS-app tot een rapportserver te configureren. Voor de configuratie maken IT-beheerders een app-configuratiebeleid waarbij de vereiste informatie naar de app wordt gepusht. 

 Wanneer de verbinding met de rapportserver als is geconfigureerd, kunnen gebruikers van Power BI mobiele iOS-apps eenvoudiger op afstand verbinding maken met de rapportserver van hun organisatie. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Het app-configuratiebeleid maken in het MDM-hulpprogramma 

Als beheerder volgt u deze stappen in Microsoft Intune om het app-configuratiebeleid te maken. De stappen en ervaring bij het opzetten van het app-configuratiebeleid is mogelijk anders bij andere MDM-hulpprogramma’s. 

1. Maak verbinding met uw MDM-hulpprogramma. 
2. Maak en benoem een nieuw app-configuratiebeleid. 
3. Kies naar welke gebruikers u dit app-configuratiebeleid wilt distribueren. 
4. Maak sleutel-waardeparen. 

In de volgende tabel staan de paren.

|Sleutel  |Type  |Beschrijving  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Tekenreeks | Rapportserver-URL <br> Moet beginnen met http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Tekenreeks | [optioneel] <br> De gebruikersnaam die u wilt gebruiken om verbinding te maken met de server. <br> Als deze niet bestaat, wordt de gebruiker gevraagd de gebruikersnaam voor de verbinding in te voeren.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Tekenreeks | [optioneel] <br> De standaardwaarde is rapportserver <br> Een beschrijvende naam die in de app wordt gebruikt als naam voor de server | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | De standaardwaarde is Waar <br>Als deze optie is ingesteld op Waar, worden hiermee alle eventuele definities van de rapportserver overschreven die al op het mobiele apparaat bestaan. Bestaande servers die al zijn geconfigureerd, worden verwijderd. <br> Wanneer overschrijven is ingesteld op Waar, voorkomt u hiermee ook dat gebruikers die configuratie kunnen verwijderen. <br> Wanneer de optie is ingesteld op Onwaar, worden de gepushte waarden toegevoegd en blijven bestaande instellingen bestaan. <br> Als dezelfde server-URL al is geconfigureerd in de mobiele app, blijft deze configuratie bestaan. De app vraagt niet of de gebruiker zich opnieuw verifieert voor dezelfde server. |

Hier ziet u een voorbeeld van het instellen van het configuratiebeleid met behulp van Intune.

![Configuratie-instellingen voor Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Eindgebruikers maken verbinding met een rapportserver

 Stel dat u het app-configuratiebeleid voor een distributielijst publiceert. Wanneer gebruikers en apparaten in die distributielijst de mobiele iOS-app starten, gebeurt het volgende. 

1. Ze zien een bericht dat hun mobiele app is geconfigureerd met een rapportserver en tikken op **Aanmelden**.

    ![Aanmelden bij de rapportserver](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Op de pagina **Verbinding maken met server** zijn de details over de rapportserver al ingevuld. Ze tikken op **Verbinding maken**.

    ![Ingevulde details rapportserver](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Ze voeren een wachtwoord ter verificatie in en tikken op **Aanmelden**. 

    ![Ingevulde details rapportserver](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Ze kunnen nu KPI's en Power BI-rapporten zien en gebruiken die zijn opgeslagen op de rapportserver.

## <a name="next-steps"></a>Volgende stappen
[Administratoroverzicht](admin-handbook-overview.md)  
[Power BI Report Server installeren](install-report-server.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

