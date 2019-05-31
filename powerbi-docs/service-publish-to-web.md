---
title: Publiceren op internet vanuit Power BI
description: Met Power BI publiceren op internet kunt u eenvoudig interactieve Power BI-visualisaties op elk apparaat online invoegen, zoals blogberichten, websites, e-mailberichten of sociale media.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051561"
---
# <a name="publish-to-web-from-power-bi"></a>Publiceren op internet vanuit Power BI

Met Power BI **publiceren op Internet** optie, kunt u eenvoudig interactieve Power BI-visualisaties online, bijvoorbeeld insluiten blogberichten, websites, e-mailberichten of sociale media, vanaf elk apparaat. U kunt uw gepubliceerde visuele elementen ook eenvoudig bewerken, bijwerken en vernieuwen of het delen ervan opheffen.

> [!WARNING]
> Bij het gebruik **publiceren op Internet**, iedereen op Internet uw gepubliceerde rapport of visueel element kunt bekijken. Dit is geen verificatie vereist en bevat het weergeven van gegevens op detailniveau cumulatieve rapporten. Voordat u een rapport publiceert, zorgt u ervoor dat deze ok voor u de gegevens en visualisaties openbaar delen. Publiceer geen vertrouwelijke gegevens of eigendomsinformatie. Controleer bij twijfel vóór publicatie de beleidsregels van uw organisatie.

>[!Note]
>Als u uw inhoud veilig wilt insluiten in een interne portal of website, gebruik dan de optie [Insluiten](service-embed-secure.md) of [Insluiten in SharePoint Online](service-embed-report-spo.md). Hiermee zorgt u ervoor dat alle machtigingen en gegevensbeveiliging worden afgedwongen wanneer uw gebruikers uw interne gegevens bekijken.

## <a name="how-to-use-publish-to-web"></a>Publiceren op internet gebruiken

**Publiceren op Internet** is beschikbaar voor rapporten in uw persoonlijke of groep werkruimten die u kunt bewerken.  Het is niet beschikbaar voor rapporten die worden gedeeld met u, of die afhankelijk zijn van beveiliging op rijniveau om gegevens te beveiligen. Zie de [ **beperkingen** ](#limitations) sectie hieronder voor een volledige lijst van de gevallen waarbij **publiceren op Internet** wordt niet ondersteund. Controleer de **waarschuwing** eerder in dit artikel voordat u **publiceren op Internet**.

De volgende *korte video* laat zien hoe deze functie werkt. Probeer deze zelf in de onderstaande stappen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

In de volgende stappen wordt het gebruik van **Publiceren op internet** beschreven.

1. Open een rapport in uw werkruimte die u kunt bewerken en selecteer **bestand > publiceren op Internet**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Controleer het dialoogvenster inhoud en selecteert u een **invoegcode maken**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Bekijk de waarschuwing, zoals hier wordt weergegeven en Bevestig dat de gegevens mogen worden geplaatst in een openbare website. Als dit het geval is, selecteert u **publiceren**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Er wordt een dialoogvenster weergegeven met een koppeling. U kunt deze koppeling in een e-mailbericht verzenden, sluit dit in code, zoals een iFrame of plak deze rechtstreeks in een webpagina of blog.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Als u eerder een invoegcode voor een rapport hebt gemaakt en u selecteert **publiceren op Internet**, ziet u niet de dialoogvensters in stap 2-4. In plaats daarvan de **invoegcode** dialoogvenster wordt weergegeven:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   U kunt slechts één invoegcode per rapport maken.


## <a name="tips-and-tricks-for-view-modes"></a>Tips en trucs voor weergavemodi

Wanneer u inhoud binnen een blogbericht insluiten, moet u meestal zodat deze past binnen een specifieke schermgrootte.  U kunt de hoogte en breedte in de iFrame-code naar behoefte kunt aanpassen. U moet echter om te controleren of dat uw rapport in het gebied opgegeven iFrame past, zodat u ook een juiste weergavemodus instellen moet tijdens het bewerken van het rapport.

De volgende tabel bevat richtlijnen over de weergavemodus en hoe deze wordt weergegeven als deze is ingesloten.

| Weergavemodus | Voorbeelden van invoegen |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Passend op pagina** houdt zich aan de paginahoogte en breedte van uw rapport. Als u uw pagina op 'Dynamische' verhoudingen, zoals 16:9 of 4:3 instelt wordt uw inhoud passend gemaakt binnen de iFrame schalen. Wanneer een ingesloten in een iFrame gebruikt **passend op pagina** kan leiden tot **letterboxing**, waar een grijze achtergrond wordt weergegeven in de gebieden van de iFrame achter de inhoud als geschaald om te passen binnen de iFrame. Ingesteld op de juiste wijze de hoogte en breedte van uw iFrame om letterboxing te minimaliseren. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Werkelijke grootte** zorgt ervoor dat het rapport de grootte zoals ingesteld op de rapportpagina behoudt. Dit kan resulteren in schuifbalken worden weergegeven in uw iFrame. Stel de iFrame hoogte en breedte om te voorkomen dat er schuifbalken. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Passend in breedte** zorgt ervoor dat de inhoud binnen het horizontale gebied van het iFrame past. Een rand nog steeds wordt weergegeven, maar de inhoud kan worden geschaald voor het gebruik van alle beschikbare horizontale ruimte. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tips en trucs voor de hoogte en breedte van uw iFrame

Een **publiceren op Internet** embed code ziet er als volgt:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
U kunt de breedte en hoogte handmatig om ervoor te zorgen er precies hoe u aan op de pagina waar u deze invoegt wilt bewerken.

Als u wilt bereiken beter passend, kunt u proberen 56 pixels aan de hoogte van de iFrame aan de huidige grootte van de onderste balk toe te voegen. Als uw rapportagepagina gebruik maakt van dynamische verhoudingen, biedt de onderstaande tabel enkele afmetingen die u kunt gebruiken om het beeld passend te krijgen zonder letterboxing.

| Verhouding | Grootte | Dimensie (breedte x hoogte) |
| --- | --- | --- |
| 16:9 |Klein |640 x 416 px |
| 16:9 |Normaal |800 x 506 px |
| 16:9 |Groot |960 x 596 px |
| 4:3 |Klein |640 x 536 px |
| 4:3 |Normaal |800 x 656 px |
| 4:3 |Groot |960 x 776 px |

## <a name="manage-embed-codes"></a>Insluitcodes beheren

Zodra u hebt gemaakt een **publiceren op Internet** invoegcode, kunt u de codes uit beheren de **instellingen** in het menu in Power BI. Invoegcodes beheren, biedt de mogelijkheid om de beoogde visuele element of rapport voor een code (waardoor de invoegcode onbruikbaar wordt), te verwijderen of de invoegcode.

1. Als u de invoegcode voor **Publiceren op internet** wilt beheren, opent u het tandwiel **Instellingen** en selecteert u **Invoegcodes beheren**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Uw invoegcodes worden weergegeven.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. U kunt ophalen of een ingesloten code verwijderen. Deze worden verwijderd, schakelt een koppeling maakt naar dat rapport of visueel element.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Als u selecteert **verwijderen**, u wordt gevraagd om een bevestiging.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Updates voor rapporten en gegevens vernieuwen

Nadat u uw **publiceren op Internet** invoegcode en delen, het rapport wordt bijgewerkt met de wijzigingen die u aanbrengt en koppeling voor de invoegcode direct actief is en iedereen die de koppeling wordt geopend, het kan bekijken. Na deze eerste actie echter kunnen updates voor rapporten of visuele elementen duurt ongeveer één uur voordat het zichtbaar is voor uw gebruikers. Als u wilt dat uw updates onmiddellijk beschikbaar zijn, kunt u de invoegcode verwijderen en een nieuwe maken. Zie voor meer informatie, de [ **hoe het werkt** ](#howitworks) verderop in dit artikel. 

## <a name="data-refresh"></a>Gegevens vernieuwen

Vernieuwde gegevens worden automatisch in uw ingevoegde rapport of visuele element verwerkt. Het kan ongeveer 1 uur duren voordat vernieuwde gegevens zichtbaar zijn in invoegcodes. Voor het automatisch vernieuwen uitschakelen, kunt u **niet vernieuwen** volgens de planning voor de gegevensset wordt gebruikt voor het rapport.  

## <a name="custom-visuals"></a>Aangepaste visuals

Aangepaste visuele elementen worden ondersteund in **Publiceren op internet**. Bij het gebruik **publiceren op Internet**, gebruikers met wie u uw gepubliceerde visuele delen niet wilt inschakelen, aangepaste visuele elementen om het rapport weer te geven.

## <a name="limitations"></a>Beperkingen

**Publiceren op Internet** wordt ondersteund voor de meeste gegevens gegevensbronnen en in de Power BI-service echter de volgende zijn rapporten **niet op dit moment ondersteund of beschikbaar** met **publiceren op Internet** :

- Rapporten met beveiliging op rijniveau.
- Rapporten die als gegevensbron gebruikmaken van Live Connection, waaronder Analysis Services Tabular dat on-premises wordt gehost, Analysis Services Multidimensional en Azure Analysis Services.
- Rapporten die direct of via een organisatie-inhoudspakket met u worden gedeeld.
- Rapporten in een groep waarvan u geen lid bent met machtigingen voor bewerken.
- Visuele R-elementen worden momenteel niet ondersteund **publiceren op Internet** rapporten.
- Exporteren van gegevens van visuele elementen in een rapport, die is gepubliceerd op het web.
- ArcGIS Maps for Power BI-visuals.
- Rapporten met DAX-metingen op rapportniveau.
- Eenmalige aanmelding query gegevensmodellen.
- [Beveiligen van vertrouwelijke of eigendomsinformatie](#publish-to-web-from-power-bi).
- De mogelijkheid van automatische verificatie die bij de optie **Insluiten** wordt verstrekt, werkt niet met de Power BI JavaScript-API. Gebruik voor de Power BI JavaScript-API de benadering [Gebruiker is eigenaar van gegevens](developer/embed-sample-for-your-organization.md) voor het insluiten van inhoud. Meer informatie over [Gebruiker is eigenaar van gegevens](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Tenantinstelling

Power BI-beheerders kunnen inschakelen of uitschakelen de **publiceren op Internet** functie. Ze kunnen ook de toegang beperken tot specifieke groepen die kunnen invloed hebben op uw mogelijkheid voor het maken van een ingesloten code.

|Functie |Ingeschakeld voor de hele organisatie |Uitgeschakeld voor de hele organisatie |Specifieke beveiligingsgroepen   |
|---------|---------|---------|---------|
|**Publiceren op Internet** onder van het rapport **bestand** menu|Ingeschakeld voor iedereen|Niet voor iedereen zichtbaar|Alleen zichtbaar voor gemachtigde gebruikers of groepen.|
|**Invoegcodes beheren** onder **Instellingen**|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen.<br><br>Optie * **Verwijderen** alleen voor gemachtigde gebruikers of groepen.<br>* **Ophalen van codes** ingeschakeld voor iedereen.|
|**Codes invoegen** binnen de beheerportal|De status geeft een van de volgende opties weer:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd|De status geeft **Uitgeschakeld** weer|De status geeft een van de volgende opties weer:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd<br><br>Als een gebruiker niet is geautoriseerd op basis van de tenantinstelling, wordt de status weergegeven als **geschonden**.|
|Bestaande gepubliceerde rapporten|Iedereen ingeschakeld|Iedereen uitgeschakeld|Rapporten blijven weergeven voor iedereen.|

## <a name="understanding-the-embed-code-status-column"></a>Inzicht in de kolom met de invoegcodestatus

De **invoegcodes beheren** pagina bevat een statuskolom. Standaard invoegcodes zijn **Active**, maar kan ook worden voor een van de hieronder vermelde statussen.

| Status | Beschrijving |
| --- | --- |
| **Actief** |Het rapport is beschikbaar voor internetgebruikers die het kunnen weergeven en ermee kunnen werken. |
| **Geblokkeerd** |Inhoud van het rapport is in strijd met de [Power BI-servicevoorwaarden](https://powerbi.microsoft.com/terms-of-service). Microsoft heeft het geblokkeerd. Neem contact op met de ondersteuning als u denkt dat de inhoud ten onrechte is geblokkeerd. |
| **Niet ondersteund** |De gegevensset van het rapport maakt gebruik van beveiliging op rijniveau of een andere niet-ondersteunde configuratie. Zie de [ **beperkingen** ](#limitations) sectie voor een volledige lijst. |
| **Geschonden** |De invoegcode valt buiten het opgegeven tenantbeleid. Dit gebeurt meestal wanneer een invoegcode is gemaakt en vervolgens de **publiceren op Internet** tenantinstelling als u wilt uitsluiten van de gebruiker die eigenaar is van de ingesloten code is gewijzigd. Als de tenantinstelling is uitgeschakeld of de gebruiker niet meer mag maken invoegcodes, bestaande codes show insluiten een **geschonden** status. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Een probleem met Publiceren op internet melden

Rapport is een probleem met betrekking tot **publiceren op Internet** inhoud die is ingesloten in een website of blog, gebruikt u de **vlag** pictogram in de onderste balk, zoals wordt weergegeven in de volgende afbeelding. U wordt gevraagd een e-mailbericht verzenden naar Microsoft uitleg over uw probleem. Microsoft evalueert de inhoud op basis van de Power BI servicevoorwaarden en passende actie kunnen ondernemen.

Als u een probleem wilt melden, selecteert u de **vlag** pictogram in de onderste balk van de **publiceren op Internet** ziet u rapporteren.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenties en prijzen

U kunt **Publiceren op internet** allen gebruiken als u gebruiker van Microsoft Power BI bent. Van uw rapport viewers hoeft te worden van Power BI-gebruikers.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Hoe het werkt (technische details)

Wanneer u maakt een ingesloten code met **publiceren op Internet**, het rapport is zichtbaar voor gebruikers van Internet. Het is openbaar beschikbaar, zodat u kunt verwachten dat bezoekers het rapport via sociale media in de toekomst delen. Terwijl gebruikers het rapport bekijken, doordat ze de directe openbare URL openen of de ingesloten versie op een webpagina of blog bekijken, worden de rapportdefinitie en de resultaten van de query's die nodig zijn om het rapport weer te geven door Power BI in de cache opgeslagen. Dit zorgt ervoor dat duizenden gelijktijdige gebruikers het rapport bekijken kunnen zonder gevolgen voor prestaties.

De cache is lange levensduur hebben, dus als u de definitie van het rapport (bijvoorbeeld als u de weergavemodus wijzigt) bijwerken of de rapportgegevens vernieuwt, het ongeveer een uur duurt voordat wijzigingen worden doorgevoerd in de versie van het rapport weergeven van uw gebruikers. U kunt daarom het beste uw werkzaamheden ver van tevoren plannen en de invoegcode voor **Publiceren op internet** alleen maken wanneer u tevreden bent met de instellingen.

## <a name="next-steps"></a>Volgende stappen

- [Webonderdeel Rapport in SharePoint Online](service-embed-report-spo.md) 

- [Rapport insluiten in een beveiligde portal of website](service-embed-secure.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
