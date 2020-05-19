---
title: Visual API
description: In dit artikel wordt beschreven hoe u IVisual API gebruikt voor Power BI-visuals
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302961"
---
# <a name="visual-api"></a>Visual API
Alle visuals beginnen met een klasse die de interface `IVisual` implementeert. U kunt de klasse elke gewenste naam geven, zolang er maar één klasse is die de interface `IVisual` implementeert.

> [!NOTE]
> De naam van de visualklasse moet overeenkomen met de definitie in het bestand *pbiviz.json*.

Bekijk de voorbeeldvisualklasse met de volgende methoden die moeten worden geïmplementeerd:

* `constructor`, een standaardconstructor voor het initialiseren van de status van de visual
* `update`, voor het bijwerken van de gegevens van de visual
* `enumerateObjectInstances`, voor het retourneren van objecten om het eigenschappenvenster (opmaakopties) te vullen, waar u deze zo nodig kunt wijzigen
* `destroy`, een standaarddestructor voor opschoning

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>constructor

De constructor van de visualklasse wordt aangeroepen wanneer de visual wordt geïnstantieerd. Deze kan worden gebruikt voor elke set bewerkingen die nodig zijn voor de visual.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, een verwijzing naar het DOM-element dat uw visual bevat
* `host: IVisualHost`, een verzameling eigenschappen en services die kunnen worden gebruikt voor interactie met de visual-host (Power BI)

   `IVisualHost` bevat de volgende services:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, voor het genereren en opslaan van metagegevens voor selecteerbare items in uw visual
   * `createSelectionManager`, voor de communicatie waarmee de host van de visual op de hoogte wordt gesteld van wijzigingen in de selectiestatus. Zie [Selectie-API](./selection-api.md) voor meer informatie.
   * `createLocalizationManager`, voor het genereren van een manager als hulpmiddel bij [lokalisatie](./localization.md)
   * `allowInteractions: boolean`, een Booleaanse vlag die aangeeft of de visual interactief moet zijn
   * `applyJsonFilter`, voor het toepassen van specifieke filtertypen. Zie [Filter-API](./filter-api.md) voor meer informatie
   * `persistProperties`, dat gebruikers toestaat eigenschappen persistent te maken en samen met de definitie van de visual op te slaan, zodat ze beschikbaar zijn als de visual opnieuw wordt geladen
   * `eventService`, voor het retourneren van een [gebeurtenisservice](./event-service.md) ter ondersteuning van **rendering**-gebeurtenissen
   * `storageService`, voor het retourneren van een service voor het gebruik van [lokale opslag](./local-storage.md) in de visual
   * `authenticationService`, voor het genereren van een service voor gebruikersverificatie
   * `tooltipService`, voor het retourneren van een [knopinfo-service](./add-tooltips.md) voor het gebruik van knopinfo in de visual
   * `launchUrl`, voor de [start-URL](./launch-url.md) in het volgende tabblad
   * `locale`, voor het retourneren van een tekenreeks voor de landinstelling. Zie [Lokalisatie](./localization.md) voor meer informatie
   * `instanceId`, voor het retourneren van een tekenreeks om het huidige exemplaar van de visual te identificeren
   * `colorPalette`, voor het retourneren van het kleurenpalet dat nodig is om kleuren toe te passen op uw gegevens
   * `fetchMoreData`, voor ondersteuning van het gebruik van meer gegevens dan de standaardlimiet (1000 rijen)
   * `switchFocusModeState`, voor het wijzigen van de status van de focusmodus

## <a name="update"></a>update

Alle visuals moeten een openbare bijwerkmethode implementeren die wordt aangeroepen bij elke wijziging in de gegevens of hostomgeving.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, afmetingen van de viewport waarin de visual moet worden weergegeven
* `dataViews: DataView[]`, het dataView-object dat alle gegevens bevat die nodig zijn om uw visual weer te geven (in uw visual wordt meestal de categorische eigenschap onder DataView gebruikt)
* `type: VisualUpdateType`, vlaggen om het soort wijziging(en) aan te geven (**Data (gegevens)**  | **Resize (formaatwijziging)**  | **ViewMode (weergavemodus)**  | **Style (stijl)**  | **ResizeEnd (einde van formaatwijziging)** )
* `viewMode: ViewMode`, vlaggen om de weergavemodus van de visual (**Weergeven** | **Bewerken** | **InFocusEdit**) aan te geven
* `editMode: EditMode`, vlag om de bewerkingsmodus van de visual (**Default (standaard)**  | **Advanced (geavanceerd)** ) aan te geven (als de visual **AdvancedEditMode (geavanceerde bewerkingsmodus)** ondersteunt, moeten de geavanceerde gebruikersinterface-elementen alleen worden weergegeven wanneer **editMode (bewerkingsmodus)** is ingesteld op **Advanced**. Zie [AdvancedEditMode](./advanced-edit-mode.md) voor meer informatie)
* `operationKind?: VisualDataChangeOperationKind`, vlag om het soort gegevenswijziging (**Create (maken)**  | **Append (toevoegen)** ) aan te geven
* `jsonFilters?: IFilter[]`, verzameling toegepaste JSON-filters
* `isInFocus?: boolean`, vlag om aan te geven of de visual zich in de focusmodus bevindt
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Deze methode wordt aangeroepen voor elk object dat in de mogelijkheden wordt vermeld. U kunt met behulp van de opties (momenteel alleen de naam) een `VisualObjectInstanceEnumeration` retourneren met informatie over het weergeven van deze eigenschap.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, naam van het object

## <a name="destroy-optional"></a>destroy `optional`

De functie destroy wordt aangeroepen wanneer uw visual uit het geheugen wordt verwijderd en kan worden gebruikt voor opschoontaken, zoals het verwijderen van gebeurtenislisteners.

``` typescript
public destroy(): void
```

> [!Note]
> In Power BI wordt `destroy` doorgaans niet aanroepen, omdat het sneller is om het hele IFrame met de visual te verwijderen.
