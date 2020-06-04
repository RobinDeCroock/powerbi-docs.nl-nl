---
title: Certificering van gegevenssets en gegevensstromen instellen (preview)
description: Meer informatie over het instellen van het certificeringsproces voor gegevenssets en gegevensstromen in uw organisatie.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/22/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: ae47c6ea0c7b9bf629f55701ba4242a195dc164d
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274392"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Certificering van gegevenssets en gegevensstromen instellen (preview)

Uw organisatie kan gegevenssets en gegevensstromen certificeren die de gezaghebbende bronnen voor essentiële informatie zijn.

Als Power BI-tenantbeheerder bent u verantwoordelijk voor het instellen van het certificeringsproces voor uw organisatie. Dit betekent:
* Certificering inschakelen voor uw tenant.
* Een lijst met groepen en gebruikers definiëren die gemachtigd zijn om gegevenssets en gegevensstromen te certificeren.
* Voor gegevenssets de URL van het beleid voor gegevenscertificering van de organisatie verstrekken, indien aanwezig.

Certificering van gegevenssets en gegevensstromen maakt deel uit van *goedkeuring* van gegevenssets en gegevensstromen. Zie [goedkeuring van gegevenssets](../connect-data/service-datasets-promote.md) en [goedkeuring van gegevensstromen](../transform-model/service-dataflows-promote-certify.md) voor meer informatie.


## <a name="set-up-certification"></a>Certificering instellen

1. Ga naar Tenantinstellingen in de beheerportal.
1. Vouw onder de sectie Instellingen voor exporteren en delen de sectie Certificering uit.

   ![Certificering van gegevensset en gegevensstroom instellen](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Stel de wisselknop in op **Ingeschakeld**.
1. Als uw organisatie gepubliceerd certificeringsbeleid heeft, kunt u voor certificering van gegevenssets hier de URL ervan opgeven. Dit wordt de koppeling **Meer informatie** in de sectie Certificering van het dialoogvenster [Goedkeuringsinstellingen voor gegevensstromen](../connect-data/service-datasets-promote.md#request-dataset-certification) 
1. Geef de gebruikers of groepen op die gemachtigd zijn om gegevenssets en gegevensstromen te certificeren. Deze geautoriseerde certificeerders kunnen gebruikmaken van de knop Certificering in de sectie Certificering van het dialoogvenster met goedkeuringsinstellingen voor [gegevenssets](../connect-data/service-datasets-promote.md#request-dataset-certification) of [gegevensstromen](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow).
1. Klik op **Toepassen**.

## <a name="next-steps"></a>Volgende stappen
* [Gegevenssets promoten](../connect-data/service-datasets-promote.md)
* [Gegevenssets certificeren](../connect-data/service-datasets-certify.md)
* [Het niveau van gegevensstromen verhogen](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [Gegevensstromen certificeren](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
