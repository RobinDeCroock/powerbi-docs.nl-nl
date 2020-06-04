---
title: Power BI-URL's voor opname in de whitelist
description: In dit artikel vindt u een overzicht van de URL-eindpunten en poorten die u moet opnemen in de whitelist voor verbinding met Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.custom: seodec18
ms.openlocfilehash: c3a3bd98dc65e3b73ffe04b95fa9001c90af1d53
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315920"
---
# <a name="power-bi-urls-for-whitelisting"></a>Power BI-URL's voor opname in de whitelist
[//]: # "suparnap, miwehnia zijn contactpersonen voor het onderhouden van deze lijst"

Voor de **online Power BI-service**, ook wel bekend als de toepassing Power BI SaaS (Software as a Service), is een internetverbinding vereist. De onderstaande eindpunten moeten bereikbaar zijn voor klanten die de online Power BI-service gebruiken.

Voor het gebruik van de online Power BI-service moet u verbinding kunnen maken met de eindpunten die als **Vereist** zijn gemarkeerd in de onderstaande tabellen en eindpunten die als **Vereist** zijn gemarkeerd op de gekoppelde sites. Als de koppeling naar een externe site naar een specifieke sectie verwijst, hoeft u alleen maar de eindpunten in die sectie te bekijken.

Eindpunten die zijn gemarkeerd als **Optioneel**, kunnen ook **in de lijst met toegestane items worden opgenomen** om een specifieke functionaliteit te laten werken.

Voor de online Power BI-service is alleen vereist dat TCP-poort 443 is geopend voor de vermelde eindpunten.

Jokertekens (*) weerspiegelen alle niveaus onder het hoofddomein, en er wordt N.v.t. gebruikt als gegevens niet beschikbaar zijn. De kolom **Bestemmingen** voorziet in een lijst met FQDN/domeinen en koppelingen naar externe sites met extra informatie over het eindpunt.

>[!Important]
>De informatie in de onderstaande tabellen betreft niet de **cloud van de Amerikaanse regering**, **de cloud van Duitsland** en **de cloud van China**.

## <a name="authentication"></a>Verificatie

Power BI is afhankelijk van de vereiste eindpunten in de Microsoft 365-secties voor verificatie en identiteit. Voor het gebruik van Power BI moet u verbinding kunnen maken met de eindpunten in de onderstaande gekoppelde site.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** Verificatie en identiteit | Raadpleeg de documentatie voor [Microsoft 365 Common en Office Online-URL's](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N.v.t. |

## <a name="general-site-usage"></a>Algemeen gebruik van de website

Voor algemeen gebruik van Power BI moet u verbinding kunnen maken met de eindpunten in de tabel en de gekoppelde sites eronder.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** Back-end API's | api.powerbi.com | TCP 443 |
| 2 | **Vereist:** Back-end API's | *.analysis.windows.net | TCP 443 |
| 3 | **Vereist:** Back-end API's | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Vereist:** Content Delivery Network (CDN) | content.powerapps.com | TCP 443 |
| 5 | **Vereist:** Integratie van Microsoft 365 | Raadpleeg de documentatie voor [Microsoft 365 Common en Office Online-URL's](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N.v.t. |
| 6 | **Vereist:** Portal | app.powerbi.com | TCP 443 |
| 7 | **Vereist:** Telemetrie naar service | dc.services.visualstudio.com | TCP 443 |
| 8 | **Optioneel:** Informatieve berichten | dynmsg.modpim.com | TCP 443 |
| 9 | **Optioneel:** NPS-enquêtes | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Beheer

Als u beheerfuncties wilt uitvoeren in Power BI, moet u verbinding kunnen maken met de eindpunten op de onderstaande gekoppelde sites.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** Voor het beheren van gebruikers en het bekijken van auditlogboeken | Raadpleeg de documentatie voor [Microsoft 365 Common en Office Online-URL's](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N.v.t. |
| | | |

## <a name="getting-data"></a>Gegevens ophalen

Als u gegevens wilt ophalen uit specifieke gegevensbronnen, zoals OneDrive, moet u verbinding kunnen maken met de eindpunten in de onderstaande tabel. Toegang tot extra internetdomeinen en URL's is mogelijk vereist voor specifieke gegevensbronnen die binnen uw organisatie worden gebruikt.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** AppSource (interne of externe apps in Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Optioneel:** Aanmelden en gegevens voor inhoudspakketten ophalen | Afhankelijk van de gebruikte inhoudspakketten | Afhankelijk van de gebruikte inhoudspakketten |
| 3 | **Optioneel:** Bestanden importeren uit OneDrive - Persoonlijk | Zie de [Vereiste URL's en poorten voor OneDrive-site](https://docs.microsoft.com/onedrive/required-urls-and-ports) | N.v.t. |
| 4 | **Optioneel:** Power BI in zelfstudievideo van 60 seconden | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Optioneel:** Bronnen voor PubNub-streaminggegevens | Zie de [PubNub-documentatie](https://support.pubnub.com/support/solutions/articles/14000043522) | N.v.t. |
| | | |

## <a name="dashboard-and-report-integration"></a>Integratie van dashboard en rapport

Power BI is afhankelijk van bepaalde eindpunten om uw dashboards en rapporten te kunnen ondersteunen. U moet verbinding kunnen maken met de eindpunten in de tabel en de gekoppelde sites eronder.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** Excel-integratie | Raadpleeg de documentatie voor [Microsoft 365 Common en Office Online-URL's](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N.v.t. |
| | | |

## <a name="power-bi-visuals"></a>Power BI-visuals

Power BI is afhankelijk van bepaalde eindpunten om aangepaste Power BI-visuals te kunnen weergeven en openen. U moet verbinding kunnen maken met de eindpunten in de tabel en de gekoppelde sites eronder.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Vereist:** Een aangepaste visual importeren uit de Microsoft Azure Marketplace-interface of uit een bestand | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Optioneel:** Bing Kaarten | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Optioneel:** PowerApps | Zie het [gedeelte Vereiste services](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) van de site met systeemvereisten voor PowerApps | N.v.t. |
| 4 | **Optioneel:** Visio | Zie de documentatie voor [Microsoft 365 Common en Office Online-URL's](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), en [SharePoint Online en OneDrive voor Bedrijven](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N.v.t. |
| | | |

## <a name="related-external-sites"></a>Verwante externe sites

Power BI-koppelingen naar andere gerelateerde sites. Deze sites hosten voor documentatie, ondersteuning, nieuwe functieaanvragen en meer. De toegang tot deze sites heeft geen invloed op de functionaliteit van Power BI, dus op de whitelist zetten is niet verplicht.

| Rij | Functie | Bestemming(en) | Poort(en) |
| --- | --- | --- | --- |
| 1 | **Optioneel:** Communitysite | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Optioneel:** Documentatiesite | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Optioneel:** Downloadsite (voor Power BI Desktop, enzovoort) | download.microsoft.com | TCP 443 |
| 4 | **Optioneel:** Externe omleidingen | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Optioneel:** Site met ideeënfeedback| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Optioneel:** Power BI-site - landingspagina, koppelingen voor meer informatie, ondersteuningssite, downloadkoppelingen, partnershowcase, enzovoort. | powerbi.microsoft.com | TCP 443 |
| 7 | **Optioneel:** Power BI-ontwikkelaarscentrum | dev.powerbi.com | TCP 443 |
| 8 | **Optioneel:** Ondersteuningssite | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
