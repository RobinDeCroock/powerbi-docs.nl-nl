---
title: Fouten opsporen in Power BI-visuals
description: In dit artikel wordt beschreven hoe u fouten in Power BI-visuals opspoort.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4ce61fcd4f322abc0362956453d76ced9b78d887
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264238"
---
# <a name="how-to-debug-power-bi-visuals"></a>Fouten opsporen in Power BI-visuals

Op deze pagina worden enkele tips weergegeven voor het opsporen van fouten tijdens het bouwen van een visual. Het artikel omvat eenvoudige stappen en laat de verschillen in foutopsporing zien tussen de standaard-front-endtoepassingen en Power BI-visual.
Na het lezen van het artikel, kunt u fouten in aangepaste visuals opsporen met behulp van onderbrekingspunten, uitzonderingen vastleggen, en uitzonderingen in Chrome en Edge constateren.

## <a name="using-breakpoints"></a>Onderbrekingspunten gebruiken

Omdat JavaScript van de visual helemaal opnieuw wordt geladen telkens wanneer de visual wordt bijgewerkt, gaan alle onderbrekingspunten die u toevoegt, verloren wanneer de visual voor foutopsporing wordt vernieuwd. Gebruik `debugger`-instructies in uw code als tijdelijke oplossing. U wordt aangeraden om automatisch opnieuw laden uit te schakelen, tijdens het gebruik van `debugger` in uw code.

```typescript
public update(options: VisualUpdateOptions) {
    console.log('Visual update', options);
    debugger;
    this.target.innerHTML = `<p>Update count: <em>${(this.updateCount</em></p>`;
}
```


## <a name="showing-exceptions"></a>Uitzonderingen weergeven

Wanneer u werkt met uw visual, ziet u dat alle fouten worden ‘opgenomen’ in de Power BI-service. Dit is een doelbewuste functie van Power BI om te voorkomen dat visuals niet goed werken, waardoor de hele app instabiel wordt.

Als tijdelijke oplossing kunt u code toevoegen om de uitzonderingen te constateren en vast te leggen, of uw foutopsporingsprogramma instellen op het onderbreken van geconstateerde uitzonderingen.


## <a name="log-exceptions"></a>Uitzonderingen vastleggen

Als u uitzonderingen in uw Power BI-visual wilt vastleggen, voegt u de volgende code toe aan de visual om een decorator voor het vastleggen van uitzonderingen te definiëren.

```typescript
export function logExceptions(): MethodDecorator {
     return function (target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<Function>)
    : TypedPropertyDescriptor<Function> {
            
        return {
            value: function () {
                try {
                    return descriptor.value.apply(this, arguments);
                } catch (e) {
                    console.error(e);
                    throw e;
                }
            }
        }
    }
}
```
Vervolgens kunt u deze decorator gebruiken voor elke functie, om de logboekregistratie van fouten te bekijken.

```typescript
@logExceptions()
public update(options: VisualUpdateOptions) {
```

## <a name="break-on-exceptions"></a>Onderbreken bij uitzonderingen

U kunt de browser ook zo instellen dat deze geconstateerde uitzonderingen onderbreekt. Hiermee wordt de uitvoering van code gestopt als er een fout optreedt, en kunt u vanaf dit punt fouten gaan opsporen.

### <a name="edge"></a>Edge

1. Open ontwikkelhulpprogramma's (F12).
2. Ga naar het tabblad **Foutopsporing**.
3. Klik op het pictogram **Onderbreken bij uitzonderingen** (zeshoek met een onderbrekingssymbool).
4. Selecteer **Onderbreken bij alle uitzonderingen**.

![Gegevensrolvelden](./media/how-to-debug-edge.png)

## <a name="chrome"></a>Chrome

1. Open ontwikkelhulpprogramma's (F12).
2. Ga naar het tabblad **Bron**.
3. Klik op het pictogram **Onderbreken bij uitzonderingen** (stopsymbool met een onderbrekingssymbool).
4. Schakel het selectievakje **Geconstateerde uitzonderingen onderbreken** in.

![Gegevensrolvelden](./media/how-to-debug-chrome.png)

## <a name="next-steps"></a>Volgende stappen
* [Problemen met Power BI-visuals oplossen](../power-bi-custom-visuals-troubleshoot.md)
* Ga naar [Veelgestelde vragen over Power BI-visuals](../power-bi-custom-visuals-faq.md#organizational-power-bi-visuals) voor meer informatie en antwoorden op vragen
