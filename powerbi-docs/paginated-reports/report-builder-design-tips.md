---
title: Tips voor het ontwerpen van rapporten in Power BI Report Builder
description: Gebruik de volgende tips om uw gepagineerde rapporten te ontwerpen in Power BI Report Builder.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921166"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Tips voor het ontwerpen van rapporten in Power BI Report Builder
  Gebruik de volgende tips om uw gepagineerde rapporten te ontwerpen in Power BI Report Builder.  
  
   
  
##  <a name="DesigningReports"></a> Rapporten ontwerpen  
  
-   In een goed ontworpen rapport staat informatie die tot actie aanzet. Identificeer de vragen die in het rapport worden beantwoord. Houd die vragen in gedachte wanneer u het rapport ontwerpt.  
  
-   Voor het ontwerpen van effectieve gegevensvisualisaties moet u bedenken op welke manier u informatie gaat weergeven zodat gebruikers het rapport gemakkelijk kunnen begrijpen. Kies een gegevensgebied dat goed overeenkomt met de gegevens die u wilt visualiseren. In een grafiek kunt u bijvoorbeeld effectiever samenvattingen en geaggregeerde informatie weergeven dan in een tabel met vele pagina's met gedetailleerde informatie. U kunt gegevens uit een gegevensset uit eender welk gegevensgebied visualiseren, zoals in grafieken, kaarten, indicatoren, sparklines, gegevensbalken en gegevens in tabbladen in verschillende rasterindelingen, op basis van een tablix. 
  
-   Als u van plan bent om het rapport in een specifieke exportindeling aan te bieden, moet u deze exportindeling al vroeg in de ontwerpfase testen. Welke functies worden ondersteund, hangt af van het weergaveprogramma dat u kiest.  
  
-   Als u complexe indelingen bouwt, moet u deze in fasen opbouwen. U kunt rechthoeken als containers gebruiken om rapportitems te ordenen. Gegevensgebieden kunnen rechtstreeks in de ontwerpweergave worden gebouwd, zodat u maximaal van uw werkgebied kunt profiteren. Vervolgens kunt u elk gegevensgebied, zodra dit is voltooid, naar de container in de rechthoek slepen. Door rechthoeken als containers te gebruiken, kunt u de volledige inhoud in één stap op de goede plaats zetten. Met behulp van rechthoeken kunt u bepalen hoe rapportitems op elke pagina worden weergegeven.  
  
-   Als u rapporten overzichtelijker wilt maken, kunt u voorwaardelijke zichtbaarheid op specifieke rapportitems toepassen en gebruikers zelf laten kiezen of ze de items willen zien. U kunt de zichtbaarheid instellen op basis van een parameter of door een tekstvak in of uit te schakelen. Er kunnen voorwaardelijke verborgen tekstvakken worden toegevoegd om tussentijdse expressieresultaten weer te geven. Wanneer onverwachte gegevens in een rapport worden weergegeven, kunt u deze tussentijdse resultaten weergeven om fouten in expressies op te sporen.  
  
-   Als u met geneste items in tablix-cellen of rechthoeken werkt, kunt u verschillende achtergrondkleuren instellen voor de container en de items in die container. De achtergrondkleur is standaard ingesteld op **Geen kleur**. Items met een specifieke achtergrondkleur worden door items heen weergegeven waarvoor de achtergrondkleur op **Geen kleur** is ingesteld. Door deze techniek kunt u het juiste item selecteren waarvoor u de weergave-eigenschappen wilt instellen, zoals zichtbaarheid van de rand op tablix-cellen.  
  
 Zie [Een rapport plannen in Report Builder](report-builder-planning-report.md) voor meer informatie over aandachtspunten bij het ontwerpen van rapporten.  
  
##  <a name="NamingConventions"></a> Naamconventies voor rapporten, gegevensbronnen en gegevenssets  
  
-   Gebruik naamconventies voor gegevensbronnen en gegevenssets waarin de bron van gegevens is vastgelegd.  
  
    1.  **Gegevensbronnen.** Als u met het oog op de beveiliging geen fysieke server of database wilt gebruiken, kunt u een alias gebruiken die gebruikers vertelt wat de gegevensbron is.  
  
    2.  **Gegevenssets.** Gebruik een naam die aangeeft welke gegevensbron als basis is gebruikt.  
  
##  <a name="Data"></a> Werken met gegevens  
  
-   De eerste stap bestaat uit het verzamelen van alle gegevens waarmee u wilt werken in het deelvenster Rapportgegevens. Wanneer u de vragen verfijnt die in het rapport moeten worden beantwoord, moet u bedenken hoe u de gegevens in de rapportgegevenssets beperkt tot alleen de gegevens die u nodig hebt.  
  
-   Over het algemeen gebruikt u alleen gegevens die in een rapport worden weergegeven. Gebruik queryvariabelen in uw query's voor gegevenssets om gebruikers te laten kiezen welke gegevens ze in het rapport willen zien. Als u gedeelde gegevenssets maakt, moet u filters opgeven op basis van rapportparameters om dezelfde functionaliteit te bieden.  
  
-   Indien u veel ervaring hebt met het schrijven van query's, moet u weten dat u tussenliggende hoeveelheden gegevens het beste in het rapport kunt groeperen, niet in de query zelf. Als u alle gegevens in de query groepeert, is het rapport eerder een presentatie van de resultatenset van de query. Aan de andere kant hoeft u geen gedetailleerde gegevens op te nemen om geaggregeerde waarden voor grote hoeveelheden gegevens in een grafiek of matrix weer te geven.  
  
-   Afhankelijk van uw vereisten kunt u namen en locaties van rapportgegevensbronnen, de queryopdrachttekst van de gegevensset en parameterwaarden in het rapport weergeven. Nieuwe gebruikers willen vaak als eerste weten waar de gegevens van afkomstig zijn. Als u overbodige informatie in het rapport wilt verminderen, kunt u tekstvakken met dit type informatie voorwaardelijk verbergen en gebruikers zelf laten kiezen of ze die willen zien. Voeg deze informatie bijvoorbeeld toe op de laatste pagina van het rapport. Stel de zichtbaarheid van het tekstvak in op basis van een parameter die door gebruikers kan worden gewijzigd.  
  
##  <a name="DesignSurface"></a> Interactie met de ontwerpweergave van rapporten  
 Voor de ontwerpweergave voor rapporten geldt niet dat u alleen krijgt wat u ziet. Wanneer u rapportitems in de ontwerpweergave plaatst, heeft hun relatieve locatie invloed op de manier waarop de items op de weergegeven rapportpagina worden getoond. Witruimte blijft behouden.  
  
-   Gebruik de knoppen voor snaplines en indeling om items uit te lijnen en te rangschikken in de ontwerpweergave van het rapport. U kunt bijvoorbeeld de boven- of onderkant van geselecteerde items uitlijnen, een item vergroten zodat deze overeenkomt met de grootte van een ander item of de spatiëring tussen items aanpassen.  
  
-   Gebruik de pijltoetsen om de positie en grootte van de geselecteerde items in de ontwerpweergave aan te passen. De volgende toetsencombinaties zijn bijvoorbeeld erg nuttig:  
  
    -   **Pijltoetsen**: hiermee kunt u het geselecteerde rapportitem verplaatsen.  
  
    -   **CTRL+pijltoetsen**: hiermee kunt u het geselecteerde rapportitem verschuiven.  
  
    -   **CTRL+SHIFT+pijltoetsen**: hiermee kunt u het geselecteerde rapportitem groter of kleiner maken.  
  
-   Als u een item aan een rechthoek wilt toevoegen, gebruikt u de linkermuisknop om de oorspronkelijke locatie van het item in de rechthoekige container aan te wijzen. Gebruik sneltoetsen om de positie van de geselecteerde objecten aan te passen. De grootte van de rechthoek wordt automatisch aangepast aan de grootte van de items in de rechthoek.  
  
-   Als u meerdere items aan een tablix-cel wilt toevoegen, moet u eerst een rechthoek toevoegen en daar vervolgens de items aan toevoegen.  
  
     Standaard bevat elke tablix-cel een tekstvak. Wanneer u een rechthoek aan een cel toevoegt, wordt het tekstvak door de rechthoek vervangen. Plaats bijvoorbeeld geneste indicatoren in een rechthoek in een tablix-cel om te bepalen op welke manier een grafiek of indicator groter moet worden gemaakt wanneer u de hoogte wijzigt van de rij waarin de cel zich bevindt.  
  
-   Gebruik het besturingselement **Zoomen** om uw weergave van de ontwerpweergave aan te passen. U kunt met de hele pagina werken of met kleinere gedeelten van de pagina.  
  
-   Als u velden van het deelvenster Rapportgegevens naar het deelvenster Groepering wilt slepen, moet u voorkomen dat u het veld over andere rapportitems in de ontwerpweergave sleept; hiermee zou u namelijk de andere items selecteren en wordt uw selectie van het tablix-gegevensgebied verwijderd. Sleep het veld omlaag naar het deelvenster Rapportgegevens en vervolgens overdwars naar het deelvenster Groepering.  
  
###  <a name="Selecting"></a> Items selecteren  
 Gebruik de ESC-toets, het contextmenu bij de rechtermuisknop, het deelvenster Eigenschappen en het deelvenster Groepering om het gewenste object te selecteren in de ontwerpweergave voor rapporten.  
  
-   -   Druk op ESC om door de stack rapportitems te bladeren waarvoor dezelfde ruimte in de ontwerpweergave wordt gebruikt.  
  
    -   Bij een aantal rapportitems kunt u het contextmenu bij de rechtermuisknop gebruiken om het rapportitem of het gewenste deel van een rapportitem te selecteren.  
  
    -   In het deelvenster Eigenschappen worden de eigenschappen van de huidige selectie weergegeven.  
  
    -   Als u met rij- en kolomgroepen in een tablix-gegevensgebied wilt werken, selecteert u de groep in het deelvenster Groepering.  

  
##  <a name="ReportItems"></a> Werken met specifieke typen rapportitems  
  
###  <a name="Parameters"></a> Werken met parameters  
  
-   Rapportparameters zijn met name bedoeld om gegevens op de gegevensbron te filteren en alleen die informatie op te halen die nodig is voor het rapport.  
  
-   Zoek voor rapportparameters een goede balans tussen het inschakelen van interactiviteit en gebruikers helpen de gewenste resultaten te krijgen. U kunt bijvoorbeeld standaardwaarden voor een parameter instellen op waarden die veel worden gebruikt.  
  
###  <a name="Text"></a> Werken met tekst  
  
-   Wanneer u meerdere regels in een tekstvak plakt, wordt de tekst als één tekstuitvoering toegevoegd. Elke tekstuitvoering kan uitsluitend als een eenheid worden opgemaakt. Als u elke regel afzonderlijk wilt opmaken, moet u een nieuwe regel invoegen door op de gewenste locatie in de tekstuitvoering op Enter te drukken. Vervolgens kunt u opmaak en stijlen toepassen op elke afzonderlijke regel tekst in het tekstvak.  
  
-   U kunt opmaakeigenschappen en acties instellen voor tekstvakken of tijdelijke aanduidingen in het tekstvak. Als u maar één regel tekst hebt, is het efficiënter om eigenschappen voor het tekstvak in te stellen in plaats van voor de tekst zelf.  
  
###  <a name="Expressions"></a> Werken met expressies  
  
-   Krijg informatie over eenvoudige en complexe expressie-indelingen. U kunt eenvoudige expressie-indelingen rechtstreeks typen in tekstvakken, eigenschappen in het deelvenster Eigenschap of in locaties in dialoogvensters die geschikt zijn voor expressies.
  
-   Wanneer u een expressie maakt, is het handig om elk deel onafhankelijk te maken en de waarde ervan te verifiëren. Vervolgens kunt u alle onderdelen combineren in de uiteindelijke expressie. Het is handig om een tekstvak in een matrixcel toe te voegen, elk deel van de expressie weer te geven en voorwaardelijke zichtbaarheid voor het tekstvak in te stellen. Als u wilt beheren welke randstijl en -kleur moeten worden gebruikt wanneer het tekstvak verborgen is, plaatst u het tekstvak eerst in een rechthoek en stelt u vervolgens de randstijl en -kleur van de rechthoek in zodat die met de matrix overeenkomt.  
  
###  <a name="Indicators"></a> Werken met indicatoren  
  
-   Standaard worden ten minste drie statussen aangegeven door een indicator. Nadat u een indicator aan een rapport toevoegt, kunt u deze configureren door statussen toe te voegen of te verwijderen. Kies een indicator die een andere kleur en vorm heeft, zodat uw gebruikers deze beter kunnen zien.  
  
##  <a name="Rendering"></a> De weergave van rapportitems op de rapportpagina beheren  
  
-   In de ontwerpweergave voor rapporten wordt de inhoud ingevuld met steeds meer rapportitems uit bijbehorende gegevenssets, expressies, subrapporten of tekst.  
  
    -   Wanneer u een item op de rapportpagina plaatst, wordt de afstand tussen het item en alle items rechts naast dat item de minimale afstand die moet worden gehandhaafd naarmate een rapportitem horizontaal wordt uitgebreid. Op deze manier wordt ook de afstand tussen een item en het item daarboven een minimale afstand die moet worden gehandhaafd naarmate het bovenste item verticaal wordt uitgebreid.  
  
    -   Een item in een rapport wordt uitgebreid om ruimte te bieden aan de bijbehorende gegevens. Peer-items (items in dezelfde bovenliggende container) worden volgens de volgende regels uit de weg gedrukt:  
  
    -   Elk item wordt omlaag verplaatst om de minimale ruimte te handhaven tussen dit item en de items die erboven eindigen.  
  
    -   Elk item wordt naar rechts verplaatst om de minimale ruimte te handhaven tussen dit item en de items die links ervan eindigen. Voor systemen met een indeling van rechts naar links wordt elk item naar links verplaatst om de minimale ruimte te handhaven tussen dit item en de items die rechts ervan eindigen.  
  
    -   Containers worden uitgebreid om ruimte te bieden aan het toenemende aantal onderliggende items. Voor een geselecteerd item wordt de container voor dat item in het deelvenster Eigenschappen geïdentificeerd door de eigenschap Bovenliggend. U kunt ook het deelvenster Documentoverzicht gebruiken om de insluitingshiërarchie van rapportitems te zien.  
  
    -   De werkbalk **Indeling** bevat meerdere knoppen waarmee u randen, middelpunten en spatiëring voor rapportitems kunt uitlijnen. Als u de werkbalk **Indeling** wilt inschakelen, gaat u naar het menu **Weergave**. Wijs naar **Werkbalken** en klik vervolgens op **Indeling**.  
  
-   Wanneer u het rapport als .pdf-bestand wilt opslaan, moet de breedte van het rapport expliciet zijn ingesteld op een waarde die de resultaten oplevert die u in de bestandsindeling voor exporteren nodig hebt. Stel de breedte van de rapportpagina bijvoorbeeld in op exact 7,9375 inch en de linker- en rechtermarges op 0,5 inch.  
  
-   Gebruik **Afdrukindeling** en **Pagina-instelling** op de werkbalk van de rapportweergave om een rapport weer te geven in een afdrukbare weergave. U kunt onnodige lege pagina's als volgt verwijderen:  
  
    1.  Verwijder alle extra spaties tussen gegevensgebieden en op de randen van het rapport.  
  
    2.  Verklein de paginamarges in het dialoogvenster **Rapporteigenschappen**.  
  
    3.  Gebruik **Rechthoeken** als containers om te bepalen hoe rapportitems op elke pagina worden weergegeven.  
  
    4.  Wijzig de tekstvakeigenschap WritingMode in kolomkoppen zodat verticale tekst wordt gebruikt.  

 Raadpleeg [Lege pagina's voorkomen bij het afdrukken van gepagineerde rapporten](../guidance/report-paginated-blank-page.md) voor meer hulp.

 De combinatie van dit gedrag, de breedte- en hoogte-eigenschappen van rapportitems, de grootte van de rapporttekst, de definitie van de paginahoogte en -breedte, de marge-instellingen van het bovenliggende rapport en de ondersteuning voor specifieke weergaven voor paginering bepaalt welke rapportitems bij elkaar worden geplaatst op een weergegeven pagina.
 
## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
