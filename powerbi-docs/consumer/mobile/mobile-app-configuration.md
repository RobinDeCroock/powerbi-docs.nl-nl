---
title: Configuratie-instellingen voor de Power BI-app voor iOS
description: Het gedrag van Power BI voor iOS aanpassen met het hulpprogramma MDM
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: a0883927f3a0a09bbe4d1ed618b7d5f708807464
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66817002"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>De Power BI-app voor iOS extern configureren met behulp van het hulpprogramma Mobile Device Management (MDM)

De mobiele Power BI-app voor iOS biedt ondersteuning voor app-instellingen waarmee beheerders voor Office 365 en Mobile Device Management (MDM), zoals Intune, het gedrag van de app kunnen aanpassen.

De mobiele Power BI-app voor iOS ondersteunt de volgende configuratiescenario's:

- Configuratie van de rapportserver
- Instellingen voor gegevensbeveiliging

## <a name="report-server-configuration"></a>Configuratie van de rapportserver

Met de Power BI-app voor iOS kunnen beheerders de configuratie van de rapportserver extern pushen naar ingeschreven apparaten.

| Sleutel | Type | Beschrijving |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Tekenreeks | Rapportserver-URL.<br><br>Moet beginnen met http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Tekenreeks | [optioneel]<br><br>De gebruikersnaam die u wilt gebruiken om verbinding te maken met de server.<br><br>Als deze niet bestaat, wordt de gebruiker gevraagd de gebruikersnaam voor de verbinding in te voeren.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Tekenreeks | [optioneel]<br><br>De standaardwaarde is rapportserver<br><br>Een beschrijvende naam die in de app wordt gebruikt als naam voor de server. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | [optioneel]<br><br>De standaardwaarde is Waar. Als deze optie is ingesteld op Waar, worden hiermee alle eventuele definities van de rapportserver overschreven die al op het mobiele apparaat bestaan. Bestaande servers die al zijn geconfigureerd, worden verwijderd. Wanneer overschrijven is ingesteld op Waar, voorkomt u hiermee ook dat gebruikers die configuratie kunnen verwijderen.<br><br>Als deze optie is ingesteld op Onwaar, worden de gepushte waarden toegevoegd en blijven alle bestaande instellingen behouden. Als dezelfde server-URL al is geconfigureerd in de mobiele app, blijft deze configuratie bestaan. De gebruiker wordt niet vanuit de app gevraagd zich opnieuw te verifiëren voor dezelfde server. |

## <a name="data-protection-setting"></a>Instelling voor gegevensbescherming

De Power BI-app voor iOS biedt beheerders de mogelijkheid de standaardconfiguratie aan te passen voor beveiliging en privacy-instellingen. U kunt afdwingen dat gebruikers hun Face ID, Touch ID of een wachtwoordcode opgeven bij het openen van de Power BI-app.

| Sleutel | Type | Beschrijving |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolean | De standaardwaarde is Onwaar. <br><br>Biometrie, zoals Touch ID of Face ID, kan vereist zijn voor gebruikers om toegang te krijgen tot de app op hun apparaat. Indien vereist, wordt er biometrie naast verificatie gebruikt.<br><br>Als u gebruikmaakt van beveiligingsbeleid voor apps, is het aan te raden deze instelling uit te schakelen om te voorkomen dat er dubbel om toegang wordt gevraagd. |

## <a name="deploying-app-configuration-settings"></a>Configuratie-instellingen voor de app implementeren

Met de volgende stappen kunt u configuratiebeleid voor de app maken. Na het maken van het configuratiebeleid kunt u de instellingen ervan toewijzen aan groepen gebruikers.

1. Maak verbinding met uw MDM-hulpprogramma.

2. Maak en benoem een nieuw app-configuratiebeleid.

3. Kies naar welke gebruikers u dit app-configuratiebeleid wilt distribueren.

4. Maak sleutel-waardeparen voor de instelling die u wilt pushen naar uw gebruikers.

Vanuit de Intune-portal kunnen beheerders deze instellingen via app-configuratiebeleid eenvoudig implementeren in de Power BI-app voor iOS.
Elke MDM-provider wordt echter ondersteund. Als u Intune niet gebruikt, moet u uw MDM-documentatie raadplegen voor het implementeren van deze instellingen.

## <a name="next-steps"></a>Volgende stappen

* de [mobiele Power BI-app voor de iPhone](http://go.microsoft.com/fwlink/?LinkId=522062) downloaden
* Volg [@MSPowerBI op Twitter](https://twitter.com/MSPowerBI)
* Deelnemen aan conversaties in de [Power BI-community](http://community.powerbi.com/)
