---
title: Externe hulpprogramma's in Power BI gebruiken (preview)
description: Het gebruik van Power BI Desktop met externe hulpprogramma's uitbreiden
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/29/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 8742a65f662433eb4330a9dedbca54f4445e992b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412961"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Externe hulpprogramma's in Power BI Desktop gebruiken (preview)

Vanaf de release van 2020 juli van Power BI Desktop kunt u externe hulpprogramma's gebruiken om extra functionaliteit en waarde toe te voegen aan Power BI Desktop. Dankzij ondersteuning voor externe hulpprogramma's kunt u gebruikmaken van de talrijke community-hulpprogramma's voor Analysis Services voor BI-professionals, een dergelijke DAX-query/-expressie-optimalisatie en -ontwerp en Application Lifecycle Management (ALM).

Het lint **Externe hulpprogramma's** in Power BI Desktop bevat knoppen voor externe hulpprogramma's die op de computer zijn geïnstalleerd en die zijn geregistreerd bij Power BI Desktop. Externe hulpprogramma's die vanaf Power BI Desktop worden gestart, worden automatisch verbonden met de Analysis Services-engine die als onderdeel van Power BI Desktop fungeert, waardoor gebruikers naadloos kunnen werken.

![Het lint Externe hulpprogramma's in Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Deze aanbevolen externe hulpprogramma's bevatten het volgende, met koppelingen naar de locatie van de installatie. Elk extern hulpprogramma wordt ondersteund door de respectieve makers van het hulpprogramma:

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [ALM Toolkit](http://alm-toolkit.com)


In de volgende secties worden de bewerkingen beschreven die worden ondersteund door externe hulpprogramma's, een lijst met aanbevolen hulpprogramma's die zijn opgenomen in Power BI Desktop en instructies voor het registreren van extra hulpprogramma's.

## <a name="supported-write-operations"></a>Ondersteunde schrijfbewerkingen

Externe hulpprogramma's kunnen verbinding maken met de Power BI Desktop-gegevensset (Analysis Services-model) om de volgende objecten te bewerken. Het bewerken van een Power BI Desktop-sjabloonbestand (PBIT) wordt niet ondersteund.

* [Metingen](/analysis-services/tabular-models/measures-ssas-tabular) voor berekeningen
* [Berekeningsgroepen](/analysis-services/tabular-models/calculation-groups) voor hergebruik van berekeningen in complexe modellen
* [Perspectieven](/analysis-services/tabular-models/perspectives-ssas-tabular) voor het definiëren van specifieke weergaven van metagegevens van gegevenssets voor specifieke bedrijfsdomeinen

Het beheren van metagegevensvertalingen met externe hulpprogramma's kan mogelijk zijn, maar wordt momenteel niet ondersteund in deze preview-versie. Als de landinstelling van de huidige gebruiker een vertaalde landinstelling is, werkt het bewerken van objecten in de lijst met velden niet naar behoren met de huidige versie van Power BI Desktop. 

Alle metagegevens van de gegevensset [Objectmodel in tabelvorm](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) zijn alleen toegankelijk voor alleen-lezen, maar objecten die niet worden vermeld in de lijst die wordt beschreven in het artikel [Objectmodel in tabelvorm](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) worden nog niet ondersteund voor bewerking in de Power BI Desktop Analysis Services-instantie.


## <a name="featured-external-tools"></a>Aanbevolen externe hulpprogramma's

De volgende open-source community-hulpprogramma's werken met Power BI Desktop. Deze worden ondersteund door de respectieve makers van de hulpprogramma's. Het installatieprogramma van elk hulpprogramma registreert dit met Power BI Desktop bij de installatie:

* Tabular Editor
* DAX Studio
* ALM Toolkit

We gaan deze verschillende hulpprogramma’s hieronder afzonderlijk bespreken.

### <a name="tabular-editor"></a>Tabular Editor

U kunt [Tabular Editor](https://tabulareditor.com/) installeren via de volgende koppeling: [Tabular Editor-website](https://tabulareditor.com/)

Met Tabular Editor kunnen BI-professionals eenvoudig modellen in tabelvorm bouwen, onderhouden en beheren met behulp van een intuïtieve en lichte editor. In een hiërarchische weergaven worden alle objecten in uw model in tabelvorm weergegeven en onderverdeeld in weergavemappen met ondersteuning voor meervoudige selectie en bewerking van eigenschappen en markering van DAX-syntaxis.

![Schermopname van de Tabular Editor](media/desktop-external-tools/desktop-external-tools-02.png)

De broncode voor de Tabular Editor vindt u in de volgende GitHub-opslagplaats: [Tabular Editor op GitHub](https://github.com/otykier/TabularEditor)

De belangrijkste auteur van het hulpprogramma voor Tabular Editor is [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

U kunt [DAX Studio](https://daxstudio.org) installeren via de volgende koppeling: [DAX Studio-website](https://daxstudio.org)

DAX Studio is een volledig hulpprogramma voor DAX-ontwerp en -diagnose en afstemming en analyse van DAX-prestaties. Het bevat onder andere functies voor bladeren door objecten, geïntegreerde tracering, uitsplitsing van uitvoerbewerkingen van query's met gedetailleerde statistieken en markering en opmaak van DAX-syntaxis. De volgende afbeelding toont een Dax Studio-scherm. 

![Schermopname van DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

De broncode voor de DAX Studio vindt u in de volgende GitHub-opslagplaats: [DAX Studio op GitHub](https://github.com/DaxStudio/DaxStudio)

De belangrijkste auteur van het hulpprogramma voor DAX Studio is [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM Toolkit

U kunt [ALM Toolkit](http://alm-toolkit.com) installeren via de volgende koppeling: [ALM Toolkit-website](http://alm-toolkit.com)

ALM Toolkit een hulpprogramma voor het vergelijken van schema's voor Power BI-gegevenssets. Het wordt gebruikt voor ALM-scenario's (Application Lifecycle Management). Hiermee kunt u eenvoudige implementaties uitvoeren in omgevingen en historische gegevens van incrementele vernieuwingen bewaren. Met ALM Toolkit kunt u metagegevensbestanden, vertakkingen en opslagplaatsen vergelijken en samenvoegen. U kunt ook algemene definities opnieuw gebruiken in gegevenssets.

![Schermopname van ALM Toolkit](media/desktop-external-tools/desktop-external-tools-04.png)

De broncode voor de ALM Toolkit vindt u in de volgende GitHub-opslagplaats: [ALM Toolkit op GitHub](https://github.com/microsoft/analysis-services)

Het belangrijkste auteur van het hulpprogramma voor ALM Toolkit is [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Externe hulpprogramma's registreren

Als u andere externe hulpprogramma's met Power BI Desktop wilt registreren, maakt u een JSON-bestand met de volgende inhoud:

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

De volgende lijst bevat een beschrijving van de lijst met elementen in het JSON-bestand:
 
* **naam:** Geef een naam op voor het hulpprogramma, deze wordt weergegeven als een bijschrift voor de knop in het lint Externe Hulpprogramma's in Power BI Desktop.
* **beschrijving:** (optioneel) Geef een beschrijving op die als knopinfo wordt weergegeven op het lint Externe hulpprogramma's in Power BI Desktop.
* **pad:** Geef het volledige pad naar het uitvoerbare bestand van het hulpprogramma op.
* **argumenten:** (optioneel) Geef een tekenreeks op van opdrachtregelargumenten waarmee het uitvoerbare bestand van het hulpprogramma moet worden gestart. U kunt een van de volgende tijdelijke aanduidingen gebruiken:
    * **%server%:** Vervangen door de servernaam en het poortnummer van het lokale exemplaar van Analysis Services Tabular voor geïmporteerde/DirectQuery-gegevensmodellen.
    * **%database%:** Vervangen door de databasenaam van het model dat wordt gehost in het lokale exemplaar van Analysis Services Tabular voor geïmporteerde/DirectQuery-gegevensmodellen.
* **iconData:** Geef instalaltiekopiegegevens op die worden weergegeven als een knoppictogram in het lint Externe hulpprogramma's in Power BI Desktop. De tekenreeks moet worden ingedeeld volgens de syntaxis voor gegevens-URI's zonder het voorvoegsel 'data:'.
 
Geef het bestand de naam `"<tool name>.pbitool.json"` en plaats het in de volgende map:

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

Voor omgevingen met 64-bits plaatst u de bestanden in de volgende map:

* **Programmabestanden (x86) \Veelvoorkomende bestanden\Microsoft Gedeeld\Power BI Desktop\Externe hulpprogramma's**

Bestanden op die opgegeven locatie met de extensie **.pbitool. json** worden door Power BI Desktop geladen bij het opstarten.

## <a name="disabling-external-tools-using-the-registry"></a>Externe hulpprogramma's uitschakelen met behulp van het register

Externe hulpprogramma's kunnen worden uitgeschakeld met **groepsbeleidsregels** of door het register te bewerken. Dit is vergelijkbaar met het proces voor het uitschakelen van **Aangepaste visuals**.

* Registersleutel: *Software\Policies\Microsoft\Power BI Desktop\\*

* Registerwaarde: *EnableExternalTools*

Met de waarde 1 (decimaal) schakelt u het gebruik van externe hulpprogramma's in Power BI in. Dit is de standaardwaarde.

Met de waarde 0 (decimaal) schakelt u het gebruik van externe hulpprogramma's in Power BI uit.


## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Analyseren gebruiken voor meerdere rapporten in Power BI-rapporten](desktop-cross-report-drill-through.md)
* [Slicers Power BI Desktop gebruiken](../visuals/power-bi-visualization-slicers.md)