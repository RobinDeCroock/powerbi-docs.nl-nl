---
title: Het gebruik van gegevenssets in meerdere werkruimten beheren - Power BI
description: Informatie over het beperken van de gegevensstroom in de Power BI-tenant.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 0caaf46956656c141992482ae39773d19e8fc550
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374145"
---
# <a name="control-the-use-of-datasets-across-workspaces"></a>Het gebruik van gegevenssets in meerdere werkruimten beheren

Het gebruik van gegevenssets in werkruimten is een krachtige manier om de gegevenscultuur en gegevensdemocratisering binnen een organisatie te stimuleren. Maar soms wilt u, als u een Power BI-beheerder bent, de gegevensstroom in uw Power BI-tenant beperken. Met de tenantinstelling **Gegevenssets gebruiken in werkruimten** kunt u hergebruik van gegevenssets volledig of gedeeltelijk per-beveiligingsgroep beperken.

![Werkruimte-instellingen Power BI-beheerder](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Als u deze instelling uitschakelt, zijn dit de gevolgen voor de makers van rapporten:

- De knop voor het kopiëren van rapporten in werkruimten is niet beschikbaar. 
- In een rapport op basis van een gedeelde gegevensset is de knop **Rapport bewerken** niet beschikbaar.
- In de Power BI-service geeft de interface voor detectie alleen gegevenssets in de huidige werkruimte weer.
- In Power BI Desktop geeft de interface voor detectie alleen gegevenssets van werkruimten weer waarvan u lid bent.
- Als gebruikers in Power BI Desktop een pbix-bestand openen met een live-verbinding met een gegevensset buiten werkruimten waarvan zij lid zijn, krijgen ze een foutbericht te zien waarin ze worden gevraagd om verbinding maken met een andere gegevensset.

## <a name="provide-a-link-for-the-certification-process"></a>Een koppeling opgeven voor het certificeringsproces

Als Power BI-beheerder kunt u voorzien in een URL voor de koppeling **Meer informatie** op de instellingspagina **Onderschrijving**.  Met deze koppeling kunt u naar de documentatie over het certificeringsproces gaan. Als u geen doel voor de koppeling **Meer informatie** opgeeft, wordt standaard naar het artikel [Certificering gegevensset](service-datasets-certify.md) verwezen.

![Meer informatie over certificering van gegevenssets](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in werkruimten gebruiken](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
