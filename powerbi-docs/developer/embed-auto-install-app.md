---
title: Automatisch installeren van Power BI-apps voor uw organisatie
description: Informatie over het installeren van Power BI-apps automatisch voor uw organisatie.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376196"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Automatische installatie Power BI-apps voor uw organisatie

Voor het insluiten van inhoud van een app, moet de gebruiker die is ingesloten hebben [toegang tot de app](../service-create-distribute-apps.md). Als de app is geïnstalleerd voor de gebruiker, werkt klikt u vervolgens insluiten probleemloos. Zie voor meer informatie, [insluiten van rapporten of dashboards vanuit app](embed-from-apps.md). Het is mogelijk om te definiëren in PowerBI.com die alle apps kunnen worden [automatisch geïnstalleerd](https://powerbi.microsoft.com/blog/automatically-install-apps/). Maar deze actie wordt uitgevoerd op het tenantniveau van de en is van toepassing op alle apps.

## <a name="auto-install-app-on-embedding"></a>De app automatisch installeren voor het insluiten van

Als een gebruiker toegang tot een app heeft, maar de app niet is geïnstalleerd, klikt u vervolgens insluiten mislukt. Zodat u deze fouten voorkomen kunt bij het insluiten van een app, kunt u automatische installatie van de app bij het insluiten van inhoud. Deze actie betekent dat als de app die de gebruiker wil insluiten niet is geïnstalleerd, wordt deze automatisch geïnstalleerd voor u. De inhoud die u wilt wordt dus onmiddellijk, wat resulteert in een goede ervaring voor de gebruiker ingesloten.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Insluiten voor Power BI-gebruikers (gebruiker is eigenaar van gegevens)

Als u wilt dat automatische installatie van apps voor uw gebruikers, moet u uw toepassing de inhoud maken om toestemming te geven wanneer [registreren van uw toepassing](register-app.md#register-with-the-power-bi-application-registration-tool), of toe te voegen als u uw app al hebt geregistreerd.

![App registreren maken inhoud](media/embed-auto-install-app/register-app-create-content.png)

Vervolgens moet u de app-ID in de ingesloten URL opgeven. Voor de app-ID, de maker van de app eerst moet de app installeert en vervolgens gebruikt u een van de ondersteunde [Power BI Rest-API](https://docs.microsoft.com/rest/api/power-bi/) aanroepen - [Get Reports](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) of [Dashboards ophalen](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). De app-ontwikkelaar moet nemen van de ingesloten Url van de REST-API-reactie. De app-ID in de URL wordt weergegeven als de inhoud van een app.  Nadat u de ingesloten URL hebt, kunt u deze kunt gebruiken om in te sluiten regelmatig.

## <a name="secure-embed"></a>Beveiligde insluiten

Voor het gebruik van automatisch installeren van apps, moet de maker van de app eerst de app installeert en vervolgens gaat u naar de app in PowerBI.com, gaat u naar het rapport en haal de koppeling in een gebruikelijke manier. Alle andere gebruikers met toegang tot de app die u kunt de koppeling gebruiken, kunnen het rapport insluiten.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* U kunt alleen insluiten rapporten en dashboards voor dit scenario.

* Deze functie is momenteel niet ondersteund voor de app is eigenaar van gegevens en insluitscenario's voor SharePoint.