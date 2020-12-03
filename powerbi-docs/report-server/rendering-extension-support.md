---
title: Conformiteit van PDF-renderingextensie met ISO 14289-1 - Power BI Report Server en SSRS
description: In dit document wordt de conformiteit van de PDF-renderingextensie van Power BI Report Server en SQL Server Reporting Services met ISO 14289-1 (PDF/UA) beschreven.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.openlocfilehash: eb2e3e599afad20401bfba0563041f8a7e442041
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418297"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Conformiteit van PDF-renderingextensie met ISO 14289-1 - Power BI Report Server en SSRS

Van toepassing op: Power BI Report Server en SQL Server Reporting Services (SSRS)

In dit document wordt de conformiteit van de PDF-renderingextensie van Power BI Report Server en SQL Server Reporting Services met [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) beschreven.

> [!NOTE]
> U kunt dit technische document opslaan of afdrukken door in uw browser **Afdrukken** en vervolgens **Opslaan als PDF-bestand** te selecteren.

## <a name="1--scope"></a>1.  Bereik

Niet van toepassing

## <a name="2--normative-references"></a>2.  Normatieve verwijzingen

Niet van toepassing

## <a name="3--terms-and-definitions"></a>3.  Voorwaarden en definities

Niet van toepassing

## <a name="4--notation"></a>4.  Notatie

Niet van toepassing

## <a name="5-version-identification"></a>5. Versie-identificatie

De PDF-renderingsextensie biedt ondersteuning voor PDF/UA, zoals beschreven in dit document. In sommige gevallen, die hieronder worden vermeld, is het aan de gebruiker om de stappen uit te voeren om ervoor te zorgen dat een PDF volledig compatibel is met PDF/UA.  We verwachten dat de gebruiker de juiste PDF/UA-versie en conformiteit-id's toevoegt als de laatste stap in dit proces. Dit geeft aan dat alles in het werk is gesteld om de PDF volledig PDF/UA-compatibel te maken.

Alles wat in dit document wordt vermeld, is gebaseerd op het weergeven van een PDF-document met de instelling voor apparaatgegevens AccessiblePdf ingesteld op `true`. In sommige gevallen worden conformiteitsbeperkingen veroorzaakt door beperkingen in de Report Definition Language (RDL).

## <a name="6--conformance-requirements"></a>6.  Conformiteitsvereisten

|     Criteria     |     Ondersteunende functie     |     Opmerkingen      |
|----|--------|--------|
|    6.1 Algemeen    |                 Ondersteund    |    PDF-renderingsextensie maakt PDF-versie 1.7.    |
|    6.2 Bestanden conform maken    |                 Ondersteund met uitzonderingen    |    Zie de opmerkingen in sectie 7: vereisten voor bestandsindelingen.    |
|    6.3 Lezer conform maken    |     Niet van toepassing     |         |
|    6.4 Ondersteunende technologie conform maken    |     Niet van toepassing     |         |

## <a name="7--file-format-requirements"></a>7.  Vereisten voor bestandsindelingen

|     Criteria     |     Ondersteunende functie     |     Opmerkingen      |
|-----|-------|------------------------|
|    7.1 Algemeen    |                 Ondersteund met uitzonderingen    |    Alle werkelijke inhoud moet worden getagd zoals gedefinieerd in ISO 32000-1:2008, 14.8. Artefacten (ISO 32000-1:2008, 14.8.2.2.2) moeten niet worden getagd in de boomstructuur. <li> De PDF-renderingsextensie biedt geen flexibiliteit om afzonderlijke items expliciet als artefacten te markeren, dus in plaats daarvan wordt alles dat overeenkomt met de criteria in ISO 32000-1:2008, 14.8.2.2.2 als artefact toegewezen.<br>Inhoud moet in de boomstructuur worden gemarkeerd met semantisch geschikte tags in een logische leesvolgorde. <br> **Opmerking** 4 WCAG 2.0, richtlijn 1.4 bevat een uitleg over problemen met betrekking tot contrast, kleur en andere opmaak voor toegankelijkheid. <br><li> De gebruiker moet er zeker van zijn dat het document niet een van deze problemen bevat. <br>Standaardtags, gedefinieerd in ISO 32000-1:2008, 14.8.4, mogen niet opnieuw worden toegewezen. <li> Door de PDF-renderingsextensie worden standaardtags niet opnieuw toegewezen. Documenten beginnen met het hoofdniveau van het document. <br>Bestanden die conformiteit met deze internationale norm claimen, hebben een Suspects-waarde van 'niet waar' (ISO 32000-1:2008, tabel 321). <li> De PDF-renderingsextensie bevat de Suspects-vermelding niet. Deze eigenschap is optioneel.    |
|    7.2 Tekst    |                 Ondersteund met uitzonderingen    |    Inhoud moet worden gelabeld in een logische leesvolgorde. De semantisch meest geschikte tag moet worden gebruikt voor elk logische element in de documentinhoud. <br><li> De PDF-renderingsextensie tagt inhoud zoveel mogelijk in een logische leesvolgorde.<br>Tekencodes moeten worden toegewezen aan Unicode, zoals beschreven in ISO 32000-1:2008, 14.8.2.4.2. Tekens die niet zijn opgenomen in de Unicode-specificatie kunnen gebruikmaken van het gebied voor persoonlijk gebruik in Unicode of een andere tekencodering declareren. <br>Natuurlijke taal moet worden gedeclareerd zoals beschreven in ISO 32000-1:2008, 14.9.2 en/of zoals beschreven in ISO 32000-1:2008, 7.9.2. Wijzigingen in natuurlijke taal moeten worden gedeclareerd. Wijzigingen in natuurlijke taal in tekstreeksen (bijvoorbeeld binnen alternatieve beschrijvingen) moeten worden gedeclareerd met een taal-id zoals beschreven in ISO 32000-1:2008, 14.9.2.2. <br><li> De PDF-renderingsextensie declareert natuurlijke taal alleen op documentniveau    |
|    7.3 Grafische elementen    |                 Ondersteund met uitzonderingen    |    Grafische objecten, met uitzondering van tekstobjecten, moeten worden getagd met een afbeeldingscode, zoals beschreven in ISO 32000-1:2008, 14.8.4.5, tabel 340. Als een van de volgende uitzonderingen waar is, wordt de afbeelding als een artefact getagd: <br><li> het grafische element vertegenwoordigt geen zinvolle inhoud of <li>  het grafische element wordt weergegeven als een achtergrond van een aantekening bij een koppeling, in welk geval de alternatieve tekst in de koppeling zowel het grafische element als de koppeling beschrijft. <li> De PDF-renderingsextensie tagt grafische objecten met de tag 'Afbeelding'. <br>Een bijschrift bij een afbeelding moet worden getagd met de tag 'Bijschrift'. <li> De PDF-renderingsextensie tagt momenteel geen bijschriften voor afbeeldingen met de tag 'Bijschrift'. <br>Afbeeldingstags moeten een alternatieve weergave of vervangende tekst bevatten die staat voor de inhoud die is gemarkeerd met de tag 'Afbeelding', zoals aangegeven in ISO 32000-1:2008, 14.7.2, tabel 323. <br>**Opmerking** 1 zie ook WCAG 2,0, richtlijn 1.1. <br>Als tekst die in een afbeelding wordt weergegeven, geen tekst in een natuurlijke taal is die bedoeld is om te worden gelezen door een menselijke lezer, moeten alternatieve teksten worden verstrekt waarin de aard of het doel van de afbeelding wordt beschreven. <br>**Opmerking** 2 tekst die een typevoorbeeld is of een voorbeeld van het schrijfsysteem dat wordt gebruikt door een taal, zijn voorbeelden van tekst die niet in een natuurlijke taal zijn.   De PDF-renderingsextensie ondersteunt alternatieve tekst voor afbeeldingen, maar het is aan de gebruiker om de ALT-tekst toe te voegen. <br>Aanvullende opmerking over het kenmerk BBox: <br><li> Door de PDF-renderingsextensie wordt het kenmerk BBox momenteel niet geschreven. <li> Een tijdelijke oplossing is het handmatig opnieuw taggen van illustraties als nieuwe afbeeldingen of als artefacten.    |
|    7.4 Kopteksten    |                 Niet van toepassing    |    RDL biedt geen ondersteuning voor het markeren van kopteksten op enigerlei wijze. Het is aan de gebruiker om deze naar wens te taggen.    |
|    7.5 Tabellen    |                 Ondersteund met uitzonderingen    |    Tabellen moeten kopteksten bevatten. Tabelkopteksten moeten worden gelabeld volgens ISO 32000-1:2008, tabel 337 en tabel 349. <br>**Opmerking** 1 tabellen kunnen kolomkopteksten, rijkopteksten of beide bevatten. <br>**Opmerking** 2 er moet zo veel mogelijk informatie over de structuur van tabellen beschikbaar zijn wanneer gebruik wordt gemaakt van ondersteunende technologie. Kopteksten spelen een belangrijke rol bij het leveren van structurele informatie. <br><li> Het is aan de gebruiker kopteksten toe te voegen aan de tabellen. RDL en de PDF-renderingsextensie bieden ondersteuning voor rijkopteksten. <br>  Structuurelementen van het type TH hebben het kenmerk 'Bereik'.   <li> De PDF-renderingsextensie bevat een kenmerk 'Bereik' in TH-elementen voor kolom- en rijleden, maar niet voor hoekcellen.<br>Structuren voor het taggen van tabellen worden alleen gebruikt voor het taggen van inhoud die wordt weergegeven in logische rij- en/of kolomrelaties.   <li> Dit is afhankelijk van de manier die de gebruiker heeft gekozen om tabellen in de RDL te gebruiken.    |
|    7.6 Lijsten    |                 Niet van toepassing    |    RDL biedt geen ondersteuning voor de markering van lijsten. In RDL zijn ze structureel een tabel met een enkele tabelcel. <br>Het is aan de gebruiker om deze naar wens opnieuw te taggen.    |
|    7.7 Wiskundige expressies    |                 Ondersteund met uitzonderingen    |    Alle wiskundige expressies moeten worden ingesloten in een formuletag zoals beschreven in ISO 32000-1:2008, 14.8.4.5 en moeten een Alt-kenmerk hebben. <br><li> De PDF-renderingsextensie sluit momenteel geen wiskundige expressies binnen een formuletag in. <br>De vereisten met betrekking tot het toewijzen van tekens aan Unicode zijn van toepassing op wiskundige expressies zoals uiteengezet in ISO 32000-1:2008, 9.10.2 en 14.8.2.4. <br><li> Dit wordt ondersteund door de PDF-renderingsextensie.    |
|    7.8 Paginakop- en voetteksten    |                 Ondersteund    |    Kop-en voetteksten worden aangeduid als pagineringsartefacten en worden geclassificeerd als een kop- of voettekstsubtype volgens ISO 32000-1:2008, 14.8.2.2.2, tabel 330. <br><li> Kop- of voetteksten worden behandeld en getagd als artefacten.    |
|    7.9 Opmerkingen en naslaginformatie    |                 Niet van toepassing    |    De PDF-renderingsextensie biedt geen ondersteuning voor het taggen van notities en verwijzingen. <br>Het is aan de gebruiker om deze naar wens te taggen.    |
|    7.10 Optionele inhoud    |                 Niet van toepassing    |         |
|    7.11 Ingesloten bestanden    |                 Niet van toepassing    |         |
|    7.12 Artikelthreads    |                 Niet van toepassing    |         |
|    7.13 Digitale handtekeningen    |                 Niet van toepassing    |         |
|    7.14 Niet-interactieve formulieren    |                 Niet van toepassing    |         |
|    7.15 XFA    |                 Niet van toepassing    |         |
|    7.16 Beveiliging    |                 Niet van toepassing    |         |
|    7.17 Navigatie    |                 Ondersteund    |    Een document moet een documentoverzicht bevatten dat overeenkomt met de leesvolgorde en het niveau van de navigatiedoelen (ISO 32000-1:2008, 12.3.3). <br><li> RDL ondersteunt bladwijzers voor een rapportitem, maar de gebruiker moet deze optie selecteren. Deze bladwijzers worden vervolgens door de PDF-renderingsextensie weergegeven als documentoverzicht. <br>Indien aanwezig, moeten de vermeldingen in de PageLabels-nummerstructuur (ISO 32000-1:2008, 7.7.2, tabel 28) semantisch geschikt zijn. <br><li> De PDF-renderingsextensie bevat geen PageLabels-nummerstructuur.    |
|    7.18 Aantekeningen    |                 Niet van toepassing    |    RDL biedt geen ondersteuning voor aantekeningen    |
|    7.21 Lettertypen    |                 Ondersteund    |         |
|    7.21.1 Algemeen    |                 Ondersteund    |         |
|    7.21.2 Soorten lettertypen    |                 Ondersteund    |         |
|    7.21.3 Samengestelde lettertypen    |                 Ondersteund    |         |
|    7.21.3.1 Algemeen    |                 Ondersteund    |         |
|    7.21 3.2 CIDFonts    |                 Ondersteund    |         |
|    7.21.3.3 CMaps    |                 Ondersteund    |         |
|    7.21.4 Insluiten    |                 Ondersteund    |         |
|    7.21.4.1 Algemeen    |                 Ondersteund    |         |
|    7.21.4.2 Subset insluiten    |                 Ondersteund    |         |
|    7.21.5 Metrische gegevens van lettertypen    |                 Ondersteund    |         |
|    7.21.6 Tekencoderingen    |                 Ondersteund    |         |
|    7.21.7 Toewijzing van Unicode-tekens    |                 Ondersteund    |         |
|    7.21.8 Gebruik van .notdef glyph    |                 Ondersteund    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Vereisten voor het conform maken van de lezer

Niet van toepassing

## <a name="9--at-requirements"></a>9.  Vereisten ondersteunende technologie

Niet van toepassing

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Volgende stappen
[Administratoroverzicht](admin-handbook-overview.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

