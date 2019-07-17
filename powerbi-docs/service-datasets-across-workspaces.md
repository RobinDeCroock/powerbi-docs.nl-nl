---
title: Gegevenssets in meerdere werkruimten gebruiken (preview) - Power BI
description: Ontdek hoe u een gegevensset kunt delen met gebruikers in de hele organisatie. Daarna kunnen ze rapporten samenstellen op basis van uw gegevensset in hun eigen werkruimten.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17a8e1c9e0d46a56d6b6ff3e46c0fda6da8ffe12
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567830"
---
# <a name="use-datasets-across-workspaces-preview"></a>Gegevenssets in meerdere werkruimten gebruiken (preview)

Business intelligence is een activiteit in samenwerkingsverband. Het is belangrijk dat gestandaardiseerde gegevenssets tot stand worden gebracht die 'één bron van waarheid' kan zijn. Om deze gestandaardiseerde gegevenssets vervolgens te detecteren en opnieuw te gebruiken. Wanneer deskundige modelleerders van gegevens in uw organisatie geoptimaliseerde gegevenssets maken en delen, kunnen makers van rapporten met deze gegevenssets nauwkeurige rapporten genereren. Uw organisatie beschikt vervolgens over consistente gegevens voor het nemen van beslissingen en een goed functionerende gegevenscultuur.

![Een gedeelde gegevensset selecteren](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI kunnen makers van gegevenssets *certificeren* of *promoten*, zodat anderen deze kunnen detecteren. Op die manier weten auteurs van rapporten welke gegevenssets van hoge kwaliteit en betrouwbaar zijn, en kunnen ze deze gegevenssets gebruiken wanneer ze inhoud maken in Power BI. Eigenaren van gegevenssets kunnen controle houden over wie toegang heeft tot hun gegevens met behulp van de [Samenstellingsmachtiging](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Tenantbeheerders hebben een nieuwe tenantinstelling voor het [bepalen van het gebruik van gegevenssets in werkruimten](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Gegevenssets delen en de nieuwe werkruimte-ervaring

Het maken van rapporten op basis van gegevenssets in verschillende werkruimten en het kopiëren van rapporten naar verschillende werkruimten zijn nauw verbonden met de [nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md):

- Wanneer u in de service de catalogus met gegevenssets van een nieuwe werkruimte-ervaring opent, bevat deze gegevenssets die zich in uw werkruimte (Mijn werkruimte) bevinden en in andere werkruimten met de nieuwe werkruimte-ervaring. 
- Wanneer u de gegevenssetcatalogus van een klassieke werkruimte opent, ziet u alleen de gegevenssets in deze werkruimte, niet die in andere werkruimten.
- U kunt in Desktop Live Connect-rapporten publiceren naar verschillende werkruimten zolang de bijbehorende gegevenssets zich in de nieuwe werkruimte-ervaring-werkruimten bevinden.
- Bij het kopiëren van rapporten naar werkruimten, moet de doelwerkruimte er eentje zijn met nieuwe werkruimte-ervaring.

## <a name="build-permission-for-datasets"></a>Samenstellingsmachtiging voor gegevenssets

Met het type samenstellingsmachtiging kunt u anderen in uw organisatie toestemming verlenen voor het bouwen van nieuwe inhoud, zoals rapporten, dashboards en vastgemaakte tegels vanuit Q&A, op basis van een bestaande gegevensset. Zij kunnen ook nieuwe inhoud ontwikkelen op basis van de gegevensset buiten Power BI, zoals Excel-bladen via Analyseren in Excel, XMLA en deze exporteren. Meer informatie over de [Samenstellingsmachtiging](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Gegevenssets detecteren (preview)

Bij het samenstellen van een rapport op basis van een bestaande gegevensset moet u eerst verbinding maken met de gegevensset, in de Power-service of Power BI Desktop. Lees over [het detecteren van gegevenssets afkomstig uit verschillende werkruimten (preview)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Een rapport kopiëren

Wanneer u in een werkruimte of een app een rapport hebt gevonden dat u leuk vindt, kunt u er een kopie van maken en deze vervolgens aanpassen aan uw behoeften. U hoeft zich geen zorgen te maken over het maken van het gegevensmodel. Dit is al voor u gemaakt. En het is veel gemakkelijker een bestaand rapport aan te passen dan een compleet nieuw rapport te maken. Meer informatie over [rapporten kopiëren](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Promotie en certificering

Als u gegevenssets maakt en eentje maakt waarvan anderen kunnen profiteren, kunt u het hen eenvoudiger maken om deze te detecteren door [uw gegevensset te promoten](service-datasets-promote.md). U kunt ook experts in uw organisatie vragen om [uw gegevensset te certificeren](service-datasets-certify.md).

## <a name="licensing"></a>Licentieverlening

Licentieverlening voor de specifieke functies en ervaringen die op functionaliteit van de gedeelde gegevensset zijn gebouwd, vindt plaats op basis van hun bestaande scenario's.  Bijvoorbeeld:

- Het detecteren en verbinding maken met gedeelde gegevenssets is in het algemeen beschikbaar voor iedereen. Gebruikers zonder een Pro-licentie kunnen echter alleen verbinding maken met gegevenssets die zich in hun persoonlijke werkruimte (Mijn werkruimte) of in de Premium-werkruimten bevinden.
- Voor het promoten en certificeren van gegevenssets buiten persoonlijke werkruimten is een Pro-licentie vereist, omdat u een Pro-licentie nodig hebt om lid van een app-werkruimte te zijn.
- Voor het kopiëren van rapporten van en naar gegevenssets buiten persoonlijke werkruimten is een Pro-licentie vereist, wederom omdat u een Pro-licentie nodig hebt om lid van een app-werkruimte te zijn.
- Voor het kopiëren van rapporten vanuit een app is een Pro-licentie vereist, zoals is vereist voor organisatie-inhoudspakketten.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

- Voor het samenstellen van een rapport op basis van een gegevensset in een andere werkruimte, is de nieuwe werkruimte-ervaring aan beide uiteinden vereist: Zowel het rapport als de gegevensset moeten zich in een nieuwe werkruimte-ervaring-werkruimte bevinden.
- In een klassieke werkruimte bevat de interface voor detectie van gegevenssets alleen de gegevenssets in die werkruimte.
- U kunt rapporten maken in app-werkruimten die zijn gebaseerd op gegevenssets in een andere werkruimte. U kunt echter geen app maken voor een werkruimte waarin deze gegevenssets zich bevinden.
- Gratis gebruikers in Desktop zien alleen gegevenssets uit Mijn werkruimte en Premium-werkruimten.
- Als u een rapport aan een app wilt toevoegen op basis van een gedeelde gegevensset, moet u lid zijn van de werkruimte van de gegevensset. Dit is een bekend probleem.
- Publiceren naar Internet werkt niet voor een rapport op basis van een gedeelde gegevensset. Dit ligt aan het ontwerp.
- Als twee personen lid zijn van een werkruimte die toegang geeft tot een gedeelde gegevensset, is het mogelijk dat slechts een van hen de betreffende gegevensset in de werkruimte kan zien. Alleen personen met ten minste leestoegang tot de gegevensset kunnen de gedeelde gegevensset zien. 

## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets promoten](service-datasets-promote.md)
- [Gegevenssets certificeren](service-datasets-certify.md)
- [Het gebruik van gegevenssets in meerdere werkruimten regelen](service-datasets-admin-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
