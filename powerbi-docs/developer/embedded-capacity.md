---
title: Capaciteit en SKU's in Power BI Embedded-analyses
description: Inzicht krijgen in capaciteit en SKU's voor ingesloten analyse in Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: f8c3bdf3e3f92d570205551a97389def2921fe98
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77260452"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capaciteit en SKU's in Power BI Embedded-analyses

Bij de overgang naar de productieomgeving heeft de functie voor ingesloten analyse in Power BI een toegewezen capaciteit nodig (*A-* , *EM-* of *P*-SKU) voor het publiceren van ingesloten Power BI-inhoud.

De capaciteit is de toegewezen set resources die exclusief hiervoor is gereserveerd. Hiermee kunt u dashboards, rapporten en gegevenssets publiceren voor gebruikers zonder dat u een licentie per gebruiker hoeft aan te schaffen. Daarnaast krijgt u betrouwbare en consistente prestaties voor uw inhoud.

>[!NOTE]
>Voor het publiceren hebt u een Power BI Pro-account nodig.

## <a name="what-is-embedded-analytics"></a>Wat is ingesloten analyse?

Ingesloten analyse van Power BI bevat twee oplossingen:
* *Power BI Embedded*: Azure-aanbieding
* Power BI insluiten als onderdeel van *Power BI Premium*: Office-aanbieding

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded is bedoeld voor ISV's en ontwikkelaars die visuals in hun toepassingen willen insluiten.

Toepassingen die gebruikmaken van Power BI Embedded staan gebruikers toe om inhoud te gebruiken die is opgeslagen op Power BI Embedded-capaciteit.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../service-premium-what-is.md) is afgestemd op ondernemingen die de beschikking willen over een volledige BI-oplossing met één weergave van de organisatie, partners, klanten en leveranciers.

Power BI Premium is een SaaS-product waarmee gebruikers inhoud kunnen gebruiken via mobiele apps, en intern ontwikkelde apps en in de Power BI-portal (Power BI-service). Hierdoor kan Power BI Premium een oplossing bieden voor zowel interne als externe klantgerichte toepassingen.

## <a name="capacity-and-skus"></a>Capaciteit en SKU's

Elke capaciteit biedt een aantal SKU's en elke SKU biedt verschillende resourcelagen voor geheugen en rekenkracht. Het type SKU dat u nodig hebt, is afhankelijk van het type oplossing dat u wilt implementeren.

Lees de informatie in deze sectie voordat u besluit welke SKU u moet aanschaffen.
* Als u wilt weten welke workloads worden ondersteund voor elke laag, raadpleegt u het artikel [Workloads configureren in een Premium-capaciteit](../service-admin-premium-workloads.md)
* Gebruik deze koppeling om [uw capaciteit te plannen en te testen](../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded-SKU's

Power BI Embedded wordt geleverd met een *A*-SKU.
* [Weten wat uw Power BI Embedded-capaciteit kan verwerken](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan)
* [Een *A*-SKU kopen](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>Power BI Premium-SKU's

Power BI Premium biedt twee SKU's: *P* en *EM*.
* [Inzicht in de verschillen tussen de *P*- en *EM*-SKU's](../service-premium-what-is.md#subscriptions-and-licensing)
* [Een Premium SKU kopen](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Welke SKU moet ik gebruiken?

Deze tabel bevat een overzicht van de functies, de capaciteit die nodig is en de specifieke SKU die voor elke functie is vereist. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Functie</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>Wat wordt er verbruikt?</em><p></td>
<td><p><em>Wat verbruikt er?</em><p></td>
<td style="text-align: center"><p><em>A-SKU's</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM-SKU's</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P-SKU's</br>(Office)</em></p></td>
</tr>
<tr>
<td>Artefacten uit een Power BI-werkruimte insluiten</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI-rapporten</td>
<td>Een ingesloten toepassing voor uw organisatie</br>(gebruiker is eigenaar van gegevens)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Een ingesloten toepassing voor uw klanten</br>(app is eigenaar van gegevens)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI-inhoud<br>(met een gratis Power BI-licentie)</td>
<td>Power BI-service</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI mobiel</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office-apps</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

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
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Facturering</strong></td>
<td style="text-align: center;">Per uur</td>
<td style="text-align: center;">Maandelijks</td>
<td style="text-align: center;">Maandelijks</td>
</tr>
<tr>
<td><p><strong>Min. periode</strong></td>
<td style="text-align: center;">Geen</td>
<td style="text-align: center;">Maandelijks of jaarlijks</td>
<td style="text-align: center;">Maandelijks of jaarlijks</td>
</tr>
<tr>
<td valign="top"><p><strong>Gebruik</strong></td>
<td style="text-align: center;">Azure-resources kunnen:</br>- <a href="azure-pbie-scale-capacity.md">Omhoog of omlaag worden geschaald</a></br>- <a href="azure-pbie-pause-start.md">Worden onderbroken en hervat</a>
</td>
<td style="text-align: center;">Worden ingesloten in apps en in</br> Microsoft-toepassingen</td>
<td style="text-align: center;">Worden ingesloten in apps en in</br> de Power BI-service</td>
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

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Insluiten vanuit apps](embed-from-apps.md)