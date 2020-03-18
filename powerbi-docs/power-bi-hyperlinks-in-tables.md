---
title: Hyperlinks (URL's) toevoegen aan een tabel of matrix
description: In dit onderwerp leert u hoe u hyperlinks (URL's) toevoegt aan een tabel. U gebruikt Power BI Desktop om hyperlinks (URL's) toe te voegen aan een gegevensset. Vervolgens kunt u in Power BI Desktop of de Power BI-service deze hyperlinks toevoegen aan uw rapporttabellen en matrices.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 021aeafab4deb5afb39cd3986b3fb68b62b483f0
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381256"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>Hyperlinks (URL's) toevoegen aan een tabel of matrix
In dit onderwerp leert u hoe u hyperlinks (URL's) toevoegt aan een tabel. U gebruikt Power BI Desktop om hyperlinks (URL's) toe te voegen aan een gegevensset. U kunt deze hyperlinks toevoegen aan uw rapporttabellen en matrices in Power BI Desktop of de Power BI-service. Vervolgens kunt u de URL of een koppelingspictogram weergeven, of een andere kolom opmaken als koppelingstekst.

![Tabel met hyperlinks](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

In de Power BI-service en in Power BI Desktop kunt u ook hyperlinks maken in [tekstvakken in rapporten](service-add-hyperlink-to-text-box.md). En in de Power BI-service kunt u hyperlinks toevoegen aan de [tegels op dashboards](service-dashboard-edit-tile.md) en aan [tekstvakken op dashboards](service-dashboard-add-widget.md). 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>Een URL opmaken als een hyperlink in Power BI Desktop

U kunt een veld met URL’s opmaken als hyperlinks in Power BI Desktop, maar niet in de Power BI-service. U kunt ook [hyperlinks opmaken in Excel Power Pivot](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot) voordat u de werkmap importeert in Power BI.

1. Als in Power BI Desktop nog geen veld met een hyperlink bestaat in uw gegevensset, voegt u deze toe als een [aangepaste kolom](desktop-common-query-tasks.md).

    > [!NOTE]
    > U kunt geen kolom maken in de DirectQuery-modus.  Als uw gegevens al URL's bevatten, kunt u deze omzetten in hyperlinks.

2. Selecteer de kolom in de gegevens- of rapportweergave. 

3. Selecteer op het tabblad **Model maken** de optie **Gegevenscategorie** > **Web-URL**.
   
    ![Vervolgkeuzelijst Gegevenscategorie](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > URL's moeten beginnen met bepaalde voorvoegsels. Raadpleeg [Aandachtspunten en probleemoplossing](#considerations-and-troubleshooting) in dit artikel voor de volledige lijst.

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>Een tabel of matrix met een hyperlink maken

1. Nadat u een [hyperlink hebt opgemaakt als een URL](#format-a-url-as-a-hyperlink-in-power-bi-desktop), schakelt u over naar de rapportweergave.
2. Maak een tabel of matrix met het veld dat u hebt gecategoriseerd als web-URL. De hyperlinks zijn blauw en onderstreept.

    ![Blauwe en onderstreepte koppelingen](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>Een hyperlinkpictogram weergeven in plaats van een URL

Als u geen lange URL in een tabel wilt weergeven, kunt u in plaats daarvan een hyperlinkpictogram ![Hyperlinkpictogram](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) weergeven. 

> [!NOTE]
> U kunt geen pictogrammen weergeven in een matrix.
   
1. [Maak eerst een tabel met een hyperlink](#create-a-table-or-matrix-with-a-hyperlink).

2. Selecteer de tabel om deze te activeren.

    Selecteer het pictogram **Opmaak** en het pictogram ![Verfroller](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) om het tabblad Opmaak te openen.

    Vouw **Waarden** uit, zoek **URL-pictogram** en stel deze in op **Aan**.

    ![URL-pictogram inschakelen](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. [Publiceer het rapport](desktop-upload-desktop-files.md) vanuit Power BI Desktop naar de Power BI-service. (optioneel). Wanneer u het rapport opent in de Power BI-service, werken de hyperlinks ook.

## <a name="format-link-text-as-a-hyperlink"></a>Koppelingstekst opmaken als een hyperlink

U kunt ook een ander veld in een tabel opmaken als de hyperlink, en helemaal geen kolom voor de URL hebben. In dit geval maakt u de kolom niet op als een web-URL.

> [!NOTE]
> U kunt niet nog een veld opmaken als de hyperlink in een matrix.

1. Als een veld met een hyperlink niet al voorkomt in uw gegevensset, gebruikt u Power BI Desktop om het toe te voegen als een [aangepaste kolom](desktop-common-query-tasks.md). U kunt geen kolom maken in de DirectQuery-modus.  Als uw gegevens al URL's bevatten, kunt u deze omzetten in hyperlinks.

2. Selecteer de kolom met de URL in de gegevens- of rapportweergave. 

3. Selecteer op het tabblad **Model maken** de optie **Gegevenscategorie**. Zorg ervoor dat de kolom is opgemaakt als **Niet-gecategoriseerd**.

2. Maak in de rapportweergave een tabel of matrix met de URL-kolom en de kolom die u wilt opmaken als koppelingstekst.

3. Zorg dat de tabel is geselecteerd, en selecteer vervolgens het pictogram **Opmaak** en het pictogram ![Verfroller](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) om het tabblad Opmaak te openen.

4. Vouw **Voorwaardelijke opmaak** uit en zorg ervoor dat de naam in het vak de kolom is die u als koppelingstekst wilt. Zoek **Web-URL** op en stel deze in op **Aan**.

    ![Web-URL voor voorwaardelijke opmaak](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

    > [!NOTE]
    > Als de optie **Web-URL** niet wordt weergegeven, controleert u of de kolom met de hyperlinks *niet* als **Web URL** is opgemaakt in de vervolgkeuzelijst **Gegevenscategorie**.

5. Selecteer in het dialoogvenster **Web-URL** het veld met de URL in het vak **Gebaseerd op veld** > **OK**.

    ![Het dialoogvenster Web-URL](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    De tekst in deze kolom wordt nu opgemaakt als de koppeling.

    ![Tekst opgemaakt als hyperlink](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. [Publiceer het rapport](desktop-upload-desktop-files.md) vanuit Power BI Desktop naar de Power BI-service. (optioneel). Wanneer u het rapport opent in de Power BI-service, werken de hyperlinks ook.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Een hyperlink in een tabel of matrix maken in Excel Power Pivot

Een andere manier om hyperlinks toe te voegen aan uw Power BI-tabellen en -matrices is het maken van de hyperlinks in de gegevensset voordat u deze gegevensset uit Power BI importeert of hiermee verbinding maakt. In dit voorbeeld wordt een Excel-werkmap gebruikt.

1. Open de werkmap in Excel.
2. Selecteer het tabblad **PowerPivot** en kies vervolgens **Beheren**.
   
   ![PowerPivot openen in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Als PowerPivot wordt geopend, selecteert u het tabblad **Geavanceerd**.
   
   ![Tabblad Geavanceerd in PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Plaats de cursor in de kolom met de URL's die u wilt omzetten in hyperlinks in Power BI-tabellen.
   
   > [!NOTE]
   > URL's moeten beginnen met bepaalde voorvoegsels. Zie [Aandachtspunten en probleemoplossing](#considerations-and-troubleshooting) voor de volledige lijst.
   > 
   
5. Selecteer in de groep **Rapportage-eigenschappen** de vervolgkeuzelijst **Gegevenscategorie** en kies **Web-URL**. 
   
   ![Vervolgkeuzelijst Gegevenscategorie in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Maak vanuit de Power BI-service of Power BI Desktop verbinding met deze werkmap of importeer de werkmap.
7. Maak een tabelvisualisatie die het URL-veld bevat.
   
   ![Een tabel maken in Power BI met het URL-veld](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

URL's moeten beginnen met een van de volgende voorvoegsels:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

V: Kan ik een aangepaste URL gebruiken als hyperlink in een tabel of matrix?    
A: Nee. U kunt een koppelingspictogram gebruiken. Als u aangepaste tekst nodig hebt voor uw hyperlinks en als uw lijst met URL’s kort is, kunt u overwegen om in plaats daarvan een tekstvak te gebruiken.


## <a name="next-steps"></a>Volgende stappen
[Visualisaties in Power BI-rapporten](visuals/power-bi-report-visualizations.md)

[Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

