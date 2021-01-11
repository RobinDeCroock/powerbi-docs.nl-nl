---
title: Prestatietips in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: Een High Performance Power BI-visual maken. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c8bcf5e13ba769b976ab123adb3ba37f46b0359e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885931"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Een High Performance Power BI-visual maken
Dit artikel heeft betrekking op technieken voor de manier waarop een ontwikkelaar hoge prestaties kan bereiken bij het renderen van visuals. 

Niemand wil dat een visual er tijdens de rendering lang over doet wanneer de rendering en de inspanning om zo hoog mogelijke prestaties te behalen uit de codering van essentieel belang worden. 

> [!NOTE]
> Al naargelang wij het platform blijven verbeteren, worden voortdurend nieuwe versies van de API uitgebracht. Als u optimaal gebruik wilt kunnen maken van het platform en de functieset van Power BI-visuals, wordt u aangeraden up-to-date te blijven met de meest recente versie.
>
> Sinds de nieuwste **versie 2.1** zijn de laadtijden van Power BI-visuals gemiddeld 20% korter.

## <a name="power-bi-visual-performance-tips"></a>Tips voor prestaties van Power BI-visuals
Hier volgen enkele aanbevelingen over hoe u optimale prestaties kunt bereiken voor visuals. 

### <a name="use-user-timing-api"></a>Timing-API van gebruiker gebruiken
Met de **timing-API van de gebruiker** kunt u JavaScript-prestaties van uw app meten, waarmee u kunt bepalen welke onderdelen van het script moeten worden geoptimaliseerd.

Zie de [Timing-API van de gebruiker](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx) voor meer informatie.

### <a name="review-animation-loops"></a>Animatielussen bekijken
Worden ongewijzigde elementen opnieuw getekend door de animatielus? 

 - Probleem: Er wordt tijd verspild met het tekenen van elementen die van het ene naar het andere frame geen wijziging ondergaan.

 - Oplossing: Werk de frames selectief bij. 
 
Wanneer het tijd is om statische visualisaties te animeren, is het verleidelijk om code ineens in één updatefunctie te tekenen en deze herhaaldelijk aan te roepen met nieuwe gegevens voor elke iteratie van de animatielus.

Neem in plaats daarvan het volgende updatepatroon: teken alles statisch met behulp van een constructor-methode voor visuals om alles statisch te tekenen. Vervolgens hoeft de updatefunctie alleen visualisatie-elementen te tekenen die een wijziging ondergaan. 

   > [!TIP]
   > Inefficiënte animatielussen zijn meestal in assen en legenda's te vinden.

### <a name="cache-dom-nodes"></a>Cache DOM-knooppunten 
Wanneer een knooppunt of een lijst met knooppunten uit het DOM wordt opgehaald, moet u bedenken of u deze opnieuw kunt gebruiken in latere berekeningen (soms zelfs de iteratie van de volgende lus). Zolang u geen extra knooppunten in het relevante gebied hoeft toe te voegen of te verwijderen, kan het beter zijn voor de algehele efficiëntie van uw toepassing om deze in de cache op te slaan.

Houdt de toegang tot een minimum beperkt, zodat uw code snel verloopt en de browser niet wordt vertraagd. 

- Voor: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Na: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>DOM-manipulatie vermijden 
Beperk DOM-manipulatie zoveel mogelijk.  Invoegbewerkingen zoals `prepend()`, `append()` en `after()` zijn tijdrovend en mogen alleen worden gebruikt als dat noodzakelijk is.

Bijvoorbeeld:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

Het bovenstaande voorbeeld kan sneller verlopen met `html()` en door de lijst vooraf samen te stellen: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>JQuery opnieuw bekijken

Wanneer u uw JS-Frameworks zo mogelijk beperkt en van het systeemeigen JS gebruikmaakt, kan de beschikbare bandbreedte toenemen en de verwerkingsoverhead lager worden. Dit kan ook compatibiliteitsproblemen met oudere browsers beperken. 

Zie [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) voor andere voorbeelden van functies, zoals `show`, `hide` en `addClass` van JQuery en meer, voor meer informatie.  

### <a name="use-canvas-or-webgl"></a>Canvas of WebGL gebruiken 
Voor herhaald gebruik van animaties kunt u het beste **Canvas** of **WebGL** gebruiken in plaats van SVG. In tegenstelling tot SVG worden de prestaties van deze opties bepaald door de grootte in plaats van de inhoud. 

U kunt meer lezen over de verschillen in [SVG versus Canvas: Hoe u kunt kiezen](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85)). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>RequestAnimationFrame gebruiken in plaats van setTimeout 
Als u [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) gebruikt om uw animaties op het scherm bij te werken, worden uw animatiefuncties aangeroepen **voordat** de browser een andere nieuwe vorm aanroept.

Zie dit [voorbeeld](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) over een vloeiende animatie met behulp van `requestAnimationFrame` voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

Meer informatie over optimalisatietechnieken vindt u in de [Optimalisatiegids voor Power BI](../../guidance/power-bi-optimization.md).