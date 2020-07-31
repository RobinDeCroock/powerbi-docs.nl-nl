---
title: Toegang tot aanbevolen Power BI-tabellen in Excel (preview)
description: In Excel kunt u gegevens uit aanbevolen tabellen in Power BI-gegevenssets vinden in de galerie Gegevenstypen.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00fba391a6ad92f1e3edaf0e2af9691452724f6e
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251477"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Toegang tot aanbevolen Power BI-tabellen in Excel (preview)

In de galerie Gegevenstypen in Excel kunt u gegevens uit *aanbevolen tabellen* in Power BI-gegevenssets vinden. Met aanbevolen tabellen kunt u gemakkelijker zakelijke gegevens toevoegen aan uw Excel-werk bladen. Hier volgen de stappen om van Power BI-gegevens naar Excel-werkbladen te gaan.

- Met een Power BI gegevensmodelleerder wordt [een gegevensset in Power BI](../connect-data/service-datasets-promote.md) gepromoot of gecertificeerd.
- Met de gegevensmodelleerder [ worden de aanbevolen tabellen](service-create-excel-featured-tables.md) in de gegevensset geïdentificeerd en wordt deze gegevensset opgeslagen in de Power BI-service.
- De rest van de organisatie kan verbinding maken met die aanbevolen tabellen in Excel voor relevante en vernieuwbare gegevens. Excel verwijst naar deze tabellen als *gegevenstypen* en vermeldt deze in de galerie Gegevenstypen.

> [!NOTE]
> U kunt in Excel gegevens ophalen uit elke gegevensset die u kunt openen in Power BI. Selecteer op het lint **Gegevens** de optie **Gegevens ophalen** > **Uit Power BI (Microsoft)** .
> :::image type="content" source="media/service-excel-featured-tables/excel-get-data-power-bi.png" alt-text="Schermopname van de optie Gegevens ophalen uit Power BI op het lint Gegevens.":::

## <a name="the-excel-data-types-gallery"></a>De galerie Gegevenstypen van Excel
Aanbevolen tabellen in Power BI-gegevenssets worden weergegeven als *gegevenstypen* op het lint **Gegevens** in de galerie **Gegevenstypen** van Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Schermopname van de galerie Gegevenstypen in het lint Gegevens van Excel.":::

Wanneer de galerie is uitgevouwen, worden hierin de generieke gegevenstypen weergegeven, zoals **Voorraden** en **Geografie**, plus de bekendste 10 **Organisatie**-gegevenstypen die voor u beschikbaar zijn - aanbevolen tabellen uit Power BI-gegevenssets.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Schermopname van de galerie Gegevenstypen van Excel.":::

## <a name="format-a-range-of-cells-as-a-table-optional"></a>Een reeks cellen opmaken als tabel (optioneel)

 Voordat u begint, is het raadzaam om uw gegevens op te maken als Excel-tabel. Op die manier worden wijzigingen die u aanbrengt in één rij van toepassing op de andere rijen in de tabel. 

1. Voeg een kolomkop toe. 
2. Selecteer vervolgens een cel in uw gegevens en druk op Ctrl + T. 
3. Schakel **Mijn tabel bevat kopteksten** > **OK** in.

    :::image type="content" source="media/service-excel-featured-tables/excel-format-table.png" alt-text="Schermopname van het converteren van een reeks naar een tabel.":::

## <a name="search-for-power-bi-data-in-the-excel-data-types-gallery"></a>Zoeken naar Power BI-gegevens via de galerie Gegevenstypen van Excel

Als u naar gegevens in een aanbevolen Power BI-tabel wilt zoeken, selecteert u een cel of een reeks in uw Excel-werkblad met een waarde die overeenkomt met de waarde in een aanbevolen tabel. Selecteer **Organisatie**. Excel doorzoekt alle aanbevolen tabellen waartoe u toegang hebt, op zoek naar een overeenkomst.

:::image type="content" source="media/service-excel-featured-tables/excel-table-organization.png" alt-text="Schermopname van Een cel of een reeks cellen selecteren.":::
 
Als u weet welke aanbevolen tabel u zoekt, selecteert u **Van uw organisatie (preview)** in de galerie en selecteert u deze.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data-table.png" alt-text="Schermopname van het gegevenstype tabel: Organisatiegegevens, Leveranciers in Excel.":::
 
Bij het zoeken worden, als in Excel overeenkomende rijen met hoge betrouwbaarheid worden gevonden, de cellen direct aan die rijen gekoppeld. Het pictogram van het gekoppeld item geeft aan dat de cellen zijn gekoppeld aan de rijen in Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Schermopname van het pictogram Gekoppeld item.":::

Als een cel meer dan één mogelijke overeenkomende rij bevat, wordt in de cel een pictogram met een vraagteken weergegeven en wordt het deelvenster **Gegevenskiezer** geopend. In het volgende voorbeeld heeft de gebruiker een reeks geselecteerd in B2:B10 en doorzocht op een aanbevolen Power BI-tabel. Alle rijen hebben overeenkomsten, behalve cel B5, 'Ma Maison'. In de **Gegevenskiezer** worden twee mogelijke overeenkomsten weergegeven.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Schermopname van het deelvenster Gegevenskiezer in Excel.":::
 
Met de optie Organisatiegegevens kunnen rijen uit verschillende aanbevolen tabellen worden geretourneerd. Excel groepeert de mogelijk overeenkomende rijen op basis van het gegevenstype waaruit ze afkomstig zijn. Excel sorteert de gegevenstypen op basis van de rij die mogelijk het meest overeenkomt. Gebruik de naar rechts wijzende pijlen om de gegevenstypen voor overeenkomende rijen samen en uit te vouwen.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Schermopname van het deelvenster Gegevenskiezer in Excel met meerdere mogelijkheden.":::
 
Selecteer voor elke rij de rijnaam om meer details weer te geven binnen de rij om u te helpen de juiste rij te kiezen. Als u deze hebt gevonden, klikt u op **Selecteren** om de rij aan de cel in Excel te koppelen. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Schermopname van Gegevenskiezer-gegevens.":::
 
Als u het pictogram **Kaart** selecteert, ziet u een kaart met gegevens uit alle velden en berekende velden in de aanbevolen tabel. De titel van de kaart toont de waarde van het veld Rijlabel in de aanbevolen tabel.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Schermopname van Gekoppeld item-gegevens.":::

Selecteer het pictogram **Gegevens invoegen** en selecteer daarna een veldnaam in de lijst met velden om de waarde ervan toe te voegen aan het raster.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Schermopname van Een veldnaam selecteren.":::

De veldwaarde of -waarden wordt/worden in aangrenzende cellen geplaatst. De celformule verwijst naar de gekoppelde cel en de veldnaam, zodat u de gegevens kunt gebruiken in Excel-functies.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Schermopname van de Excel-celformule.":::

## <a name="cell-formulas"></a>Celformules

Wanneer u een Excel-tabel gebruikt, kunt u verwijzen naar de gekoppelde tabelkolom en vervolgens gegevensvelden toevoegen met behulp van de verwijzing `.` (punt).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Schermopname van de puntverwijzing in Excel.":::

Op dezelfde manier kunt u bij gebruik van een cel verwijzen naar de cel en de verwijzing `.` (punt) gebruiken om velden op te halen.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Schermopname van Puntverwijzing naar cellen.":::
 
## <a name="data-caching-and-refresh"></a>Gegevens in cache opslaan en vernieuwen

Als Excel een cel koppelt aan een rij in een aanbevolen tabel van Power BI, worden alle veldwaarden opgehaald en opgeslagen in het Excel-bestand. Iedereen met wie u het bestand deelt, kan verwijzen naar een van de velden, zonder dat er gegevens worden aangevraagd bij Power BI.  

Gebruik de knop **Alles vernieuwen** op het lint **Gegevens** om gegevens in gekoppelde cellen te vernieuwen. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Schermopname van Alles vernieuwen.":::
 
U kunt ook afzonderlijke cellen vernieuwen. Klik met de rechtermuisknop op de cel en selecteer **Gegevenstypen** > **Vernieuwen**.

## <a name="show-a-card-change-or-convert-to-text"></a>Een kaart weergeven, wijzigen of converteren naar tekst

Gekoppelde cellen hebben extra opties die u kunt weergeven door met de rechtermuisknop te klikken. Klik met de rechtermuisknop op een cel. Naast de gebruikelijke opties ziet u ook:

- **Kaart-gegevenstype weergeven**.
- **Vernieuwen**.
- **Wijzigen**.
- **Converteren naar tekst**

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Schermopname van Klikken met de rechtermuisknop, Converteren naar tekst.":::
 
Met **Converteren naar tekst** wordt de koppeling naar de rij in de aanbevolen tabel van Power BI verwijderd. Belangrijk: de tekst in de cel is de waarde voor het rijlabel van de gekoppelde cel. Als u per ongeluk een cel hebt gekoppeld aan een rij, selecteert u **Ongedaan maken** in Excel om de oorspronkelijke celwaarden te herstellen.

## <a name="licensing"></a>Licentieverlening

De galerie Gegevenstypen van Excel en verbonden ervaringen voor aanbevolen tabellen van Power BI zijn alleen beschikbaar voor klanten met Excel E5 of G5. 

## <a name="security"></a>Beveiliging

U ziet alleen aanbevolen tabellen uit gegevenssets waarvoor u gemachtigd bent in Power BI. Bij het vernieuwen van gegevens moet u toegang hebben tot de gegevensset in Power BI om de rijen op te halen. Hiervoor is de machtiging Samenstellen of Schrijven vereist voor de gegevensset. De gegevens die voor de hele rij worden geretourneerd, worden door Excel opgeslagen in de cache. Iedereen met wie u het Excel-bestand deelt, kan de gegevens voor alle velden in alle gekoppelde cellen zien.

Als voor een Power BI-gegevensset beveiliging op rijniveau is ingesteld of als de set is voorzien van een vertrouwelijkheidslabel van Microsoft Information Protection, worden aanbevolen tabellen uit die gegevensset niet opgenomen in de galerie Gegevenstypen in Excel. Dit is een beperking van de eerste preview.

## <a name="administrative-control"></a>Beheer

Power BI-beheerders kunnen bepalen wie in de organisatie aanbevolen tabellen kan gebruiken in de galerie Gegevenstypen van Excel. Zie [Instellingen voor de aanbevolen tabellen](../admin/service-admin-portal.md#featured-tables-settings) in het artikel over de beheerportal voor meer informatie. 
 
### <a name="auditing"></a>Controleren

Controlelogboeken voor beheerders bevatten deze gebeurtenissen voor aanbevolen tabellen:

- **AnalyzedByExternalApplication**: geeft beheerders inzicht in welke gebruikers welke aanbevolen tabellen gebruiken.
- **UpdateFeaturedTables**: geeft beheerders inzicht in welke gebruikers aanbevolen tabellen publiceren en bijwerken.

Zie [Activiteiten van gebruikers bijhouden in Power BI](../admin/service-admin-auditing.md) voor een volledige lijst met gebeurtenissen in het controlelogboek.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Dit zijn de beperkingen voor de oorspronkelijke preview:

- De integratie is beschikbaar in builds voor Excel Insiders.
- De galerie Gegevenstypen van Excel bevat aanbevolen tabellen voor gebruikers met de juiste licentie in Power BI Desktop en de Power BI-service. Ondersteuning voor de Power BI-service is mogelijk niet beschikbaar bij de lancering van de preview, maar wordt dan later toegevoegd.
- Aanbevolen tabellen in Power BI-gegevenssets die gebruikmaken van de volgende mogelijkheden, worden niet weergegeven in Excel: 

    - Gegevenssets met beveiliging op rijniveau
    - Gegevenssets waarvoor Microsoft Information Protection is ingeschakeld
    - DirectQuery-gegevenssets
    - Gegevenssets met een liveverbinding

- In Excel worden alleen gegevens in kolommen en berekende kolommen uit de aanbevolen tabel weergegeven. Het volgende is niet beschikbaar in de oorspronkelijke preview:

    - Metingen die zijn gedefinieerd voor de functietabel.
    - Metingen die zijn gedefinieerd voor gerelateerde tabellen, en impliciete metingen die worden berekend op basis van relaties.

- In Excel worden alleen aanbevolen tabellen (*gegevenstypen*) weergegeven die zijn opgeslagen in de nieuwe Power BI-werkruimten. Aanbevolen tabellen die zijn opgeslagen in de klassieke werkruimten, of in Mijn werkruimte, worden niet weergegeven als gegevenstypen in Excel. U kunt [klassieke werkruimten bijwerken naar de nieuwe werkruimten](service-upgrade-workspaces.md) in Power BI.

De ervaring van gegevenstypen in Excel is vergelijkbaar met een opzoekfunctie. Er wordt een celwaarde aangeboden door het Excel-werkblad, waarna er wordt gezocht naar overeenkomende rijen in aanbevolen tabellen van Power BI. De zoekervaring heeft de volgende gedragskenmerken:

- Wanneer u de knop **Organisatiegegevens** gebruikt om te zoeken, doorzoekt Excel alleen aanbevolen tabellen in gecertificeerde gegevenssets.
- Overeenkomende rijen worden gebaseerd op tekstkolommen in de aanbevolen tabel. De ervaring maakt gebruik van dezelfde indexering als de functie Power BI Q&A, die is geoptimaliseerd voor het zoeken in de Engelse taal. Zoeken in andere talen levert mogelijk geen nauwkeurige overeenkomsten op. Numerieke kolommen worden niet meegenomen bij het vergelijken.
- Vergelijken is gebaseerd op exacte en voorvoegselovereenkomsten voor afzonderlijke zoektermen. De waarde van een cel wordt gesplitst op basis van spaties of andere witruimtetekens, zoals tabs. Vervolgens wordt elk woord beschouwd als zoekterm. De tekstveldwaarden van een rij worden vergeleken met de zoektermen voor exacte en voorvoegselovereenkomsten. Er wordt een voorvoegselovereenkomst geretourneerd als het tekstveld van de rij begint met de zoekterm. Als een cel bijvoorbeeld 'Geldersch Landschap' bevat, zijn 'Geldersch' en 'Landschap' unieke zoektermen. 

    - Rijen met tekstkolommen waarvan de waarde exact overeenkomt met 'Geldersch' of 'Landschap' worden geretourneerd. 
    - Rijen met tekstkolommen waarvan de waarde begint met 'Geldersch' of 'Landschap' worden geretourneerd. 
    - Belangrijk: rijen die 'Geldersch' of 'Landschap' bevatten, maar niet beginnen met deze termen worden niet geretourneerd.

- Power BI retourneert maximaal 100 rijsuggesties voor elke cel.
- Het instellen of bijwerken van de aanbevolen tabel wordt niet ondersteund in het XMLA-eindpunt.
- Excel-bestanden met een gegevensmodel kunnen worden gebruikt voor het publiceren van aanbevolen tabellen. Laad de gegevens in Power BI Desktop en publiceer vervolgens de aanbevolen tabel.
- Als u de tabelnaam, het rijlabel of de sleutelkolom wijzigt van de aanbevolen tabel, kan dit gevolgen hebben voor Excel-gebruikers met cellen die zijn gekoppeld aan rijen in de tabel. 
- Excel geeft aan wanneer de gegevens zijn opgehaald uit de Power BI-gegevensset. Dit hoeft niet de tijd te zijn dat de gegevens zijn vernieuwd in Power BI, of de tijd van het meest recente gegevenspunt in een gegevensset. Stel bijvoorbeeld dat een gegevensset in Power BI een week geleden is vernieuwd, maar dat de onderliggende brongegevens een week oud waren op het moment van vernieuwen. De gegevens zijn dan in werkelijkheid twee weken oud, maar in Excel wordt dan de datum/tijd weergegeven waarop de gegevens zijn binnengehaald in Excel.

## <a name="next-steps"></a>Volgende stappen

- [Aanbevolen tabellen in Power BI Desktop instellen](service-create-excel-featured-tables.md)
- Lees meer over [het gebruik van Excel-gegevenstypen vanuit Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) in de Excel-documentatie.
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

