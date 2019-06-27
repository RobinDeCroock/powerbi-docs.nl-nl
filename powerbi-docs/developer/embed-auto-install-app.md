---
title: Power BI-apps automatisch installeren wanneer u ze insluit voor uw organisatie
description: Lees meer over het automatisch installeren van Power BI-apps wanneer u ze insluit voor uw organisatie.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: conceptual
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: 50040731ec5602dc38d9d323fe916e4e2e239d27
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751065"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Power BI-apps automatisch installeren wanneer u ze insluit voor uw organisatie

Als gebruikers die een app insluiten inhoud uit een app willen insluiten, moeten ze [toegang tot die app](../service-create-distribute-apps.md) hebben. Als de app voor de gebruiker is geïnstalleerd, betekent dit dat het insluitingsproces goed verloopt. Zie [Rapporten of dashboards uit apps insluiten](embed-from-apps.md) voor meer informatie. Het is mogelijk om in PowerBI.com te definiëren dat alle apps [automatisch kunnen worden geïnstalleerd](https://powerbi.microsoft.com/blog/automatically-install-apps/). Deze actie wordt echter op het tenantniveau uitgevoerd en is van toepassing op alle apps.

## <a name="auto-install-app-on-embedding"></a>Apps automatisch installeren tijdens insluiten

Als gebruikers toegang tot een app hebben maar die app niet is geïnstalleerd, kan de inhoud niet worden ingesloten. U kunt deze fouten dus voorkomen wanneer u inhoud uit een app insluit: u kunt toestaan dat apps automatisch worden geïnstalleerd wanneer ze worden ingesloten. Dit houdt in dat de app door deze actie automatisch wordt geïnstalleerd wanneer de app die de gebruiker probeert in te sluiten, niet is geïnstalleerd. De inhoud die u wilt insluiten wordt dus direct ingesloten; dit biedt de gebruiker een vlekkeloze ervaring.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Insluiten voor Power BI-gebruikers (gebruikers is eigenaar van gegevens)

Als u de automatische installatie van apps voor uw gebruikers wilt toestaan, moet u de machtiging 'Inhoud maken' voor uw toepassing instellen tijdens het [registreren van uw toepassing](register-app.md#register-with-the-power-bi-application-registration-tool) of deze machtiging toevoegen als u de app al hebt geregistreerd.

![Inhoud maken door apps te registreren](media/embed-auto-install-app/register-app-create-content.png)

Vervolgens moet u de app-id opgeven in de insluitings-URL. Voor het opgeven van de app-id moet de app-ontwikkelaar de app eerst installeren en vervolgens een van de ondersteunde [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)-aanroepen ([Rapporten ophalen](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) of [Dashboards ophalen](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards)) gebruiken. Vervolgens moet de app-ontwikkelaar de insluitings-URL uit het REST API-antwoord halen. De app-id wordt in de URL weergegeven als de inhoud afkomstig is uit een app.  Als u de insluitings-URL hebt, kunt u deze gebruiken om inhoud regelmatig in te sluiten.

## <a name="secure-embed"></a>Beveiligd insluiten

Voor het gebruik van automatische installatie van apps moet de app-ontwikkelaar eerst de app installeren en vervolgens naar de app op PowerBI.com gaan, naar het rapport navigeren en de koppeling op de gebruikelijke manier ophalen. Alle andere gebruikers met toegang tot de app die de koppeling kunnen gebruiken, kunnen het rapport insluiten.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Voor dit scenario kunt u alleen rapporten en dashboards insluiten.

* Deze functie wordt momenteel niet ondersteund voor de scenario's voor apps die gegevens hebben en voor het insluiten van SharePoint.