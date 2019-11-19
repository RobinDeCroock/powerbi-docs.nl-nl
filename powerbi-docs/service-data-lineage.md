---
title: Gegevensherkomst (preview)
description: In moderne projecten die gaan over business intelligence (BI) is het begrijpen van de gegevensstroom van de gegevensbron naar de bestemming een grote uitdaging voor veel klanten.
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: c2cc5f9da8ea12709d8244a1e82d8283f66f2413
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73021022"
---
# <a name="data-lineage-preview"></a>Gegevensherkomst (preview)
In moderne projecten die gaan over business intelligence (BI) kan het begrijpen van de gegevensstroom van de gegevensbron naar de bestemming een grote uitdaging zijn. De uitdaging is zelfs groter als u geavanceerde analytische projecten hebt gebouwd die uit meerdere gegevensbronnen, artefacten en afhankelijkheden bestaan.  Vragen als "Wat gebeurt er als ik deze gegevens wijzig?" of "Waarom is dit rapport niet bijgewerkt?" kunnen moeilijk te beantwoorden zijn. Misschien is er wel een team van deskundigen of een grondig onderzoek nodig om dit te begrijpen. We hebben de weergave gegevensherkomst ontworpen om u te helpen bij het beantwoorden van deze vragen.

[ ![Power BI herkomstweergave](media/service-data-lineage/power-bi-lineage-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-view-full-size.png#lightbox)
 
Power BI heeft verschillende typen artefacts, zoals dashboards, rapporten, gegevenssets en gegevensstromen. Veel gegevenssets en gegevensstromen maken verbinding met externe gegevensbronnen, zoals SQL Server, en met externe gegevenssets in andere werkruimten. Wanneer een gegevensset zich buiten uw eigen werkruimte bevindt, kan deze zich mogelijk in een werkruimte bevinden die eigendom is van iemand van IT of van een andere analist. Externe gegevensbronnen en gegevenssets maken het moeilijker om te weten waar de gegevens uiteindelijk vandaan komen. Voor complexe en eenvoudigere projecten introduceren we herkomstweergave. 

In de herkomstweergave ziet u de herkomstrelaties tussen alle artefacten in een werkruimte en alle bijbehorende externe afhankelijkheden. Gegevensstromen hadden al een diagramweergave en de herkomstweergave breidt die weergave uit. Er worden verbindingen weergegeven tussen alle werkruimte-artefacten, waaronder verbindingen met gegevensstromen, zowel upstream als downstream. De diagramweergave van de afzonderlijke gegevensstromen verdwijnt vanaf november.

## <a name="explore-lineage-view"></a>Herkomstweergave verkennen

Elke werkruimte, hetzij nieuw of klassiek, heeft automatisch een herkomstweergave, met uitzondering van Mijn werkruimte. U hebt minimaal een rol Inzender in de werkruimte nodig om deze weer te geven. Zie [Machtigingen](#permissions) in dit artikel voor meer informatie. 

- Ga naar de herkomstweergave om toegang te krijgen tot de weergave werkruimtelijst. Tik op de pijl naast **Lijstweergave** en selecteer **Herkomstweergave**.

    [ ![Overschakelen naar de herkomstweergave](media/service-data-lineage/power-bi-lineage-list-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-list-view.png#lightbox)

    In deze weergave ziet u alle werkruimte-artefacten en hoe de gegevens van de ene naar de andere stromen.

**Gegevensbronnen**

U ziet de gegevensbronnen waaruit de gegevenssets en de gegevensstromen hun gegevens halen. Op de kaarten van de gegevensbron ziet u meer informatie die u kan helpen bij het identificeren van de bron. U ziet voor Azure SQL Server bijvoorbeeld ook de naam van de database.

![Herkomstweergave gegevensbron zonder gateway](media/service-data-lineage/power-bi-lineage-data-source-no-gateway.png)
 
**Gateways**

Als een gegevensbron via een on-premises gateway is verbonden, worden de gatewaygegevens toegevoegd aan de gegevensbronkaart. Als u een machtiging hebt als gatewaybeheerder of als gegevensbrongebruiker, ziet u meer informatie, zoals de naam van de gateway.

![Herkomstweergave gegevensbron met gateway](media/service-data-lineage/power-bi-lineage-data-source-with-gateway.png)

**Gegevenssets en gegevensstromen**
 
In gegevenssets ziet u het tijdstip van de laatste vernieuwing en of een gegevensset is gecertificeerd of in niveau is verhoogd.

![Gecertificeerde gegevensset in herkomstweergave](media/service-data-lineage/power-bi-lineage-external-certified-dataset.png)
 
Als een rapport in de werkruimte is gebouwd op een gegevensset in een andere werkruimte, ziet u de naam van de bron van de werkruimte op de kaart van de gegevensset. Selecteer de naam van de bronwerkruimte om naar die werkruimte te gaan.
 
- Voor elk artefact selecteert u **Meer opties** (...) om het menu Opties weer te geven. Het bevat allemaal dezelfde acties die beschikbaar zijn in de lijstweergave.
  
Selecteer de gegevenssetkaart zelf voor meer informatie over de metagegevens van de gegevensset. Aanvullende informatie over de gegevensset wordt weergegeven in een zijvenster.

![Zijvenster met meer informatie](media/service-data-lineage/power-bi-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Toon herkomst van elk artefact 

Stel dat u de herkomst van een specifiek artefact wilt zien.

- Selecteer de dubbele pijlen onder een artefact.

    [ ![Herkomst markeren van een specifiek artefact](media/service-data-lineage/power-bi-lineage-highlight-cropped.png) ](media/service-data-lineage/power-bi-lineage-highlight-full-size.png#lightbox)

    Power BI markeert alle artefacten die betrekking hebben op dat artefact en dimt de rest. 

## <a name="navigation-and-full-screen"></a>Navigatie en volledig scherm 

Herkomstweergave is een interactief canvas. U kunt de muis en touchpad gebruiken om te navigeren in het canvas en in- of uit te zoomen.  

- Als u wilt in- en uitzoomen, gebruikt u het menu in de rechter benedenhoek of uw muis of touchpad. 

- Als u meer ruimte nodig hebt voor de grafiek zelf, gebruikt u de optie volledig scherm in de rechter benedenhoek. 

    ![In- of uitzoomen of volledig scherm](media/service-data-lineage/power-bi-lineage-zoom-full-screen.png)

## <a name="permissions"></a>Machtigingen

- U hebt een Power BI Pro-licentie nodig om de herkomstweergave te bekijken.
- Herkomstweergave is alleen beschikbaar voor gebruikers die toegang hebben tot de werkruimte.
- Gebruikers moeten beschikken over een rol Beheerder, Lid of Inzender in de werkruimte. Gebruikers met de rol Kijker kunnen niet overschakelen naar de herkomstweergave.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

- De herkomstweergave is niet beschikbaar in Internet Explorer. Zie [Ondersteunde browsers voor Power BI](power-bi-browsers.md) voor meer informatie.
- De herkomstweergave is niet beschikbaar in Mijn werkruimte.

## <a name="next-steps"></a>Volgende stappen

- [Introductie van gegevenssets in meerdere werkruimten (preview)](service-datasets-across-workspaces.md)
