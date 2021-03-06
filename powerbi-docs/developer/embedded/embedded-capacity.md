---
title: Capaciteit en SKU‘s in ingesloten analyses in Power BI om betere ingesloten BI-inzichten mogelijk te maken
description: Inzicht krijgen in capaciteit en SKU's voor ingesloten analyse in Power BI. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/15/2021
ms.openlocfilehash: 0c6686b667f96e45fc1e21d4cb9512196053f288
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531948"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capaciteit en SKU's in Power BI Embedded-analyses

Bij de overgang naar de productieomgeving heeft de functie voor ingesloten analyse in Power BI een capaciteit nodig (*A-* , *EM-* of *P*-SKU) voor het publiceren van ingesloten Power BI-inhoud.

De capaciteit is de toegewezen set resources die exclusief hiervoor is gereserveerd. Hiermee kunt u dashboards, rapporten en gegevenssets publiceren voor gebruikers zonder dat u een licentie per gebruiker hoeft aan te schaffen. Daarnaast krijgt u betrouwbare en consistente prestaties voor uw inhoud.

>[!NOTE]
>Voor het publiceren hebt u een Power BI Pro-account nodig.

## <a name="what-is-embedded-analytics"></a>Wat is ingesloten analyse?

Ingesloten analyse van Power BI bevat twee oplossingen:

* *Power BI Embedded*: Azure-aanbieding

* Power BI insluiten als onderdeel van *Power BI Premium*: Microsoft Office-aanbieding

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded is bedoeld voor ISV's en ontwikkelaars die visuals in hun toepassingen willen insluiten.

Toepassingen die gebruikmaken van Power BI Embedded staan gebruikers toe om inhoud te gebruiken die is opgeslagen op Power BI Embedded-capaciteit.

>[!NOTE]
>Er is van Power BI Embedded onlangs een nieuwe versie uitgebracht: **Embedded Gen2**. Met Embedded Gen2 wordt het beheer van ingesloten capaciteiten vereenvoudigd en wordt de Power BI Embedded-ervaring verbeterd. Zie [Power BI Embedded Generation 2](power-bi-embedded-generation-2.md) voor meer informatie.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../admin/service-premium-what-is.md) is afgestemd op ondernemingen die de beschikking willen over een volledige BI-oplossing met één weergave van de organisatie, partners, klanten en leveranciers.

Power BI Premium is een SaaS-product waarmee gebruikers inhoud kunnen gebruiken via mobiele apps, en intern ontwikkelde apps en in de Power BI-portal (Power BI-service). Hierdoor kan Power BI Premium een oplossing bieden voor zowel interne als externe klantgerichte toepassingen.

## <a name="capacity-and-skus"></a>Capaciteit en SKU's

Elke capaciteit biedt een aantal SKU's en elke SKU biedt verschillende resourcelagen voor geheugen en rekenkracht. Het type SKU dat u nodig hebt, is afhankelijk van het type oplossing dat u wilt implementeren.

Als u wilt weten welke workloads worden ondersteund voor elke laag, raadpleegt u het artikel [Workloads configureren in een Premium-capaciteit](../../admin/service-admin-premium-workloads.md)

Gebruik deze koppelingen om uw capaciteit te plannen en te testen:
* [Capaciteitsplanning](embedded-capacity-planning.md)
* [Testmethoden](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded-SKU's

Power BI Embedded wordt geleverd met een [*a*-SKU](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>Power BI Premium-SKU's

Power BI Premium biedt twee SKU's: *P* en *EM*.
* [Inzicht in de verschillen tussen de *P*- en *EM*-SKU's](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Een Premium SKU kopen](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Welke SKU moet ik gebruiken?

De onderstaande tabel bevat een overzicht van de functies, de capaciteit die nodig is en de specifieke SKU die voor elke functie is vereist.

In deze tabel verwijst een aangepaste app naar een web-app die is gemaakt met behulp van ingesloten analyses. Wanneer u als een ontwikkelaar iets insluit in een aangepaste web-app (met behulp van de JavaScript- of .NET-SDK's, of de REST-API's), hebt u de mogelijkheid om de UX te beheren en aan te passen. Deze mogelijkheid is niet beschikbaar wanneer u andere insluitingsopties gebruikt, zoals de Power BI-service en Power BI Mobile.

| Scenario | Azure   | Office          |
|----------|---------|-----------------|
|          | (A-SKU) | (P- en EM-SKU's) |
|[Insluiten voor uw klanten](embed-sample-for-customers.md)</br>(app is eigenaar van gegevens)     |✔        |✔        |
|[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)</br>(gebruiker is eigenaar van gegevens)     |✖        |✔         |
|Microsoft 365-apps</br>(eerder bekend als Office 365-apps)<ul><li>[Insluiten in Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Insluiten in SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Beveiligde URL insluiten](../../collaborate-share/service-embed-secure.md)</br>(insluiten vanuit de Power BI-service)     |✖        |✔        |

>[!NOTE]
>* Een [Power BI Pro-licentie](../../admin/service-admin-purchasing-power-bi-pro.md) is vereist voor het publiceren van inhoud naar een werkruimte van een Power BI-app.
>* Alleen met de **P-SKU** kunnen gebruikers van de gratis Power BI-versie Power BI-apps en gedeelde inhoud gebruiken in de Power BI-service.

### <a name="capacity-considerations"></a>Overwegingen bij capaciteitsbepaling

De volgende tabel bevat een overzicht van de overwegingen met betrekking tot betalingen en gebruik per capaciteit.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Aanbieding</strong></p></td>
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Facturering</strong></td>
<td style="text-align: center">Per uur</td>
<td style="text-align: center">Maandelijks</td>
<td style="text-align: center">Maandelijks</td>
</tr>
<tr>
<td><p><strong>Min. periode</strong></td>
<td style="text-align: center">Geen</td>
<td style="text-align: center">Jaar</td>
<td style="text-align: center">Maandelijks of jaarlijks</td>
</tr>
<tr>
<td valign="top"><p><strong>Gebruik</strong></td>
<td style="text-align: center">Azure-resources kunnen:<li><a href="azure-pbie-scale-capacity.md">Omhoog of omlaag worden geschaald</a></li><li><a href="azure-pbie-pause-start.md">Worden onderbroken en hervat</a>
</td></li>
<td style="text-align: center">Worden ingesloten in apps en in</br> Microsoft-toepassingen</td>
<td style="text-align: center">Worden ingesloten in apps en in</br> de Power BI-service</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU-geheugen en rekenkracht

In de onderstaande tabel worden de resources en limieten van elke SKU beschreven.

| Capaciteitsknooppunten | Totaal aantal v-cores | v-cores voor back-end | RAM (GB) | v-cores voor front-end | DirectQuery/liveverbinding (per sec) | Model voor parallelle vernieuwing |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

#### <a name="embedded-gen-2-memory-enhancements-preview"></a>Uitgebreide verbeteringen in het geheugen van gen 2 (preview-versie)

De hoeveelheid beschikbaar geheugen op elke knooppunt grootte wordt beschreven in de kolom *RAM (GB)* in de Power tabel van het [SKU-geheugen en de computer](#sku-memory-and-computing-power) . Met [Power bi embedded Generation 2](power-bi-embedded-generation-2.md) (ook wel embedded gen 2 genoemd), wordt deze hoeveelheid geheugen ingesteld op de geheugen limiet van één Power bi item (zoals een gegevensset, rapport of dash board) en niet op basis van het cumulatieve verbruik van het geheugen. In een Inge sloten Gen2 A4-capaciteit wordt slechts één gegevensset beperkt tot 25 GB, ten opzichte van de oorspronkelijke Power BI Embedded capaciteit, waarbij het totale geheugen verschil van de gegevens sets die tegelijkertijd worden verwerkt, beperkt is tot 25 GB.

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Insluiten vanuit apps](./index.yml)