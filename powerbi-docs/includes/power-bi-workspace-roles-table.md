---
title: Power BI-werkruimterollen
description: Tabel Power BI-werkruimterollen
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 05/26/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 708599eb3f39d4c627a11753cb964d6425f75640
ms.sourcegitcommit: 9c72ec6b2d6d4574c86e976a65c076764473482d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84120425"
---
|Mogelijkheid   | Beheerder  | Lid  | Inzender  | Lezer |
|---|---|---|---|---|
| De werkruimte bijwerken en verwijderen.  |  |   |   |   | 
| Personen, met inbegrip van andere beheerders, toevoegen/verwijderen.  |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Leden of anderen met minder machtigingen toevoegen.  |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Apps publiceren en bijwerken. |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Items en apps delen.<sup>1</sup> |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Anderen toestaan items opnieuw te delen.<sup>1</sup> |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Apps op de startpagina van collega's weergeven |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Dashboards en rapporten weergeven op de startpagina van collega's |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Inhoud in de werkruimte maken, bewerken en verwijderen.  |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Rapporten publiceren naar de werkruimte, inhoud verwijderen.  |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Een rapport in een andere werkruimte maken op basis van een gegevensset in deze werkruimte.<sup>2</sup> |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Een rapport kopiëren.<sup>2</sup> | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| De vernieuwing van gegevens plannen via de on-premises gateway.<sup>3</sup> | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Verbindingsinstellingen voor de gateway wijzigen.<sup>3</sup> | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Een item bekijken en ermee werken.<sup>4</sup> |  ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Gegevens lezen die zijn opgeslagen in gegevensstromen in de werkruimte | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja, vinkje](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Inzenders en kijkers kunnen ook items in een werkruimte delen als ze machtigingen voor opnieuw delen hebben.

<sup>2</sup> Als u een rapport wilt kopiëren en een rapport wilt maken in een andere werkruimte op basis van een gegevensset in deze werkruimte, hebt u [een machtiging nodig voor het maken van de gegevensset](../connect-data/service-datasets-build-permissions.md). Voor gegevenssets in deze werkruimte hebben de personen met de rollen Beheerder, Lid en Inzender automatisch een Samenstellingsmachtiging via hun werkruimterol.

<sup>3</sup> Houd er rekening mee dat u ook machtigingen nodig hebt voor de gateway. Deze machtigingen worden elders beheerd, onafhankelijk van werkruimterollen en -machtigingen. Zie [Een on-premises gateway beheren](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) voor meer informatie.

<sup>4</sup> Zelfs als u geen Power BI Pro-licentie hebt, kunt u items in de Power BI-service bekijken en ermee werken als de items zich in een werkruimte in een Premium-capaciteit bevinden.

