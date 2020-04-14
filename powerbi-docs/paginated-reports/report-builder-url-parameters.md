---
title: URL-parameters in gepagineerde rapporten - Power BI Report Builder
description: In dit onderwerp worden de gebruikelijke toepassingen van rapportparameters van Power BI Report Builder, de eigenschappen die u kunt instellen, en nog veel meer beschreven.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 04/02/2020
ms.openlocfilehash: df59d09a1e8557842904b46eded0a83c86448224
ms.sourcegitcommit: e0833ec22b263f919025acae88551570b4def0cd
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80647714"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>URL-parameters in gepagineerde rapporten in Power BI

U kunt opdrachten naar gepagineerde rapporten in Power BI verzenden door een parameter aan een URL toe te voegen. Stel bijvoorbeeld dat u het rapport hebt bekeken met behulp van een specifieke set met rapportparameterwaarden. U sluit deze informatie in de URL in aan de hand van vooraf gedefinieerde URL-toegangsparameters. Verder past u aan hoe het rapport door Power BI moet worden verwerkt door parameters in te sluiten voor het weergeven van indelingen of voor de vormgeving van de werkbalk in het rapport. Vervolgens plakt u deze URL rechtstreeks in een e-mailbericht of op een webpagina, zodat anderen uw rapport net zo zien als in de browser. 

U kunt de volgende acties uitvoeren met behulp van URL-toegangsparameters: 

- Rapportparameters naar een rapport verzenden. 
- De export van de rapportinhoud initiëren in een ondersteunde bestandsindeling. 
- Het deelvenster Parameters verbergen of weergeven. 
- De DeviceInfo-instelling opgeven. 

Voor de complete lijst met opdrachten en instelling die via URL-toegang beschikbaar zijn, leest u  [Verwijzingen voor URL-toegangsparameters](#url-access-parameter-reference) verderop in dit artikel. 

## <a name="url-access-concepts"></a>URL-toegangsconcepten 

URL-aanvragen voor Power BI bevatten parameters die door de service worden verwerkt. De manier waarop de URL-aanvragen door de service worden verwerkt, hangt af van de parameters, de parametervoorvoegsels en het type items dat in de URL is opgenomen. De URL-functionaliteit voor gepagineerde rapporten is compatibel met de meeste browsers en toepassingen die standaardadressering met URL's ondersteunen. 

## <a name="url-access-syntax"></a>De syntaxis voor URL-toegang 

URL-aanvragen kunnen meerdere parameters bevatten, die in elke willekeurige volgorde worden vermeld. Parameters moeten worden gescheiden door een en-teken (&). Naam- en waardeparen moeten worden gescheiden door een is-gelijkteken (=). Bijvoorbeeld:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Beschrijving van de syntaxis 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Dit is de webservice-URL van uw Power BI-tenant. Bijvoorbeeld: 

**&** Wordt gebruikt om naam- en waardeparen te scheiden van URL-toegangsparameters.

**prefix** Een voorvoegsel voor de URL-parameter (bijvoorbeeld rp: of rdl:) waarmee een actie in de Power BI-service wordt aangeduid. 

> [!NOTE]
> Rapportparameters hebben een parametervoorvoegsel nodig en zijn hoofdlettergevoelig. 

**parameter** De naam van de parameter. 

### <a name="value"></a>waarde 

De URL-tekst volgens de waarde van de gebruikte parameter. 

Zie  [Een rapportparameter doorsturen in een URL](report-builder-url-pass-parameters.md) voor voorbeelden van het doorsturen van rapportparameters in een URL.

## <a name="url-access-parameter-reference"></a>Verwijzingen voor URL-toegangsparameters

U kunt de volgende parameters gebruiken als onderdeel van een URL om de vormgeving van uw gepagineerde rapporten in Power BI te configureren. De meest gebruikte parameters vindt u in deze sectie. Parameters zijn hoofdlettergevoelig en beginnen met het parametervoorvoegsel `rdl:` indien ze aan de uitvoerindeling zijn gerelateerd.  

### <a name="report-commands-rdl"></a>Rapportopdrachten (`rdl:`) 

**Exportindeling** Hiermee geeft u de indeling op waarin een rapport moet worden weergegeven en geëxporteerd. Beschikbare waarden zijn:
 
- PPTX (PowerPoint)
- MHTML 
- AFBEELDING 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

**De status van het parameterpaneel** geeft aan of het parameterpaneel gesloten is of geopend wanneer het rapport wordt geladen, of dat het helemaal verborgen is.

-   rdl:parameterPanelState

    - samengevouwen: het rapport wordt geladen met gesloten parameterpaneel. De parameterknop is ingeschakeld zodat gebruikers op de knop kunnen klikken om uit te breiden;
    - verborgen: het rapport wordt geladen met gesloten parameterpaneel en uitgeschakelde parameterknop;
    - uitgebreid (standaard): het rapport wordt geladen met geopend parameterpaneel en ingeschakelde parameterknop;

**Apparaatgegevens** U kunt aanvullende uitvoerparameters opgeven voor de volgende exportindelingen. 

PDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:FileExtension=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:FileExtension=string
- rdl:Schema=true/false

## <a name="next-steps"></a>Volgende stappen

- [Een rapportparameter doorsturen in een URL voor een gepagineerd rapport in Power BI](report-builder-url-pass-parameters.md)
- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
