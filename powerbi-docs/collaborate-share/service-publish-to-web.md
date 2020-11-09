---
title: Publiceren op internet vanuit Power BI
description: Met de Power BI-optie Publiceren op internet kunt u eenvoudig interactieve Power BI-inhoud in blogberichten, websites, e-mailberichten of sociale media insluiten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/02/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 7980057ae35637f06aeec3d241b074fcc41564b7
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297654"
---
# <a name="publish-to-web-from-power-bi"></a>Publiceren op internet vanuit Power BI

Met de Power BI-optie **Publiceren op internet** kunt u eenvoudig interactieve Power BI-inhoud in blogberichten, websites, e-mailberichten of sociale media insluiten. U kunt uw gepubliceerde visuele elementen ook eenvoudig bewerken, bijwerken en vernieuwen of het delen ervan stoppen.

> [!WARNING]
> Als u **Publiceren op internet** gebruikt, kan het door u gepubliceerde rapport of visuele element door iedereen op internet worden bekeken. Voor weergave is geen authenticatie vereist. Dit betreft onder meer de weergave van gegevens op detailniveau die in uw rapporten zijn opgenomen. Voordat u een rapport publiceert, moet u controleren of u de gegevens en visualisaties openbaar mag delen. Publiceer geen vertrouwelijke gegevens of eigendomsinformatie. Controleer bij twijfel vóór publicatie de beleidsregels van uw organisatie.

>[!Note]
>U kunt uw inhoud veilig insluiten in een interne portal of website. Gebruik de opties [Insluiten](service-embed-secure.md) of [Insluiten in SharePoint Online](service-embed-report-spo.md). Met deze opties zorgt u ervoor dat alle machtigingen en gegevensbeveiliging worden afgedwongen wanneer uw gebruikers uw interne gegevens bekijken.

## <a name="create-embed-codes-with-publish-to-web"></a>Invoegcodes maken met Publiceren op internet

**Publiceren op internet** is beschikbaar voor rapporten die u kunt bewerken in uw persoonlijke en groepswerkruimten.  De optie is niet beschikbaar voor rapporten die met u zijn gedeeld of rapporten die op rijniveau zijn beveiligd om gegevens te beveiligen. Zie de sectie [**Beperkingen**](#limitations) hieronder voor een volledige lijst met aanvragen waarbij **Publiceren op internet** niet wordt ondersteund. Bekijk de **waarschuwing** eerder in dit artikel voordat u **Publiceren op internet** gebruikt.

In de volgende stappen wordt het gebruik van **Publiceren op internet** beschreven.

1. Open in uw werkruimte een rapport dat u kunt bewerken en selecteer **Meer opties (...)**   > **Insluiten** > **Publiceren op internet (openbaar)** .

   ![Publiceren op internet met Meer opties](media/service-publish-to-web/power-bi-more-options-publish-web.png)
   
2. Als uw Power BI-beheerder u niet toestaat om invoegcodes te maken, moet u mogelijk met hem/haar contact opnemen.

   ![Contact opnemen met uw Power BI-beheerder](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   Zie [Uw Power BI beheerder vinden](#find-your-power-bi-administrator) verderop in dit artikel voor meer informatie over het vinden van de persoon die de functie Publiceren op internet kan inschakelen in uw organisatie.

3. Bekijk de inhoud van het dialoogvenster en selecteer **Een invoegcode maken**.

   ![Controleren of insluiten in een openbare website mogelijk is](media/service-publish-to-web/publish_to_web2_ga.png)

4. Bekijk de waarschuwing die hier wordt weergegeven en controleer of de gegevens op een openbare website mogen worden geplaatst. Als dit het geval is, selecteert u **Publiceren**.

   ![De waarschuwing bekijken](media/service-publish-to-web/publish_to_web3_ga.png)

5. Er wordt een dialoogvenster met een koppeling weergegeven. Selecteer de koppeling om deze in een e-mailbericht te verzenden of kopieer de HTML. U kunt deze in code, zoals een iFrame, insluiten of rechtstreeks in een webpagina of blog plakken.

   ![Geslaagd: een koppeling en HTML](media/service-publish-to-web/publish_to_web4.png)

6. Als u eerder een invoegcode voor een rapport hebt gemaakt en u **Publiceren op Internet** selecteert, krijgt u de dialoogvensters in stap 2 tot en met 4 niet te zien. In plaats daarvan wordt het dialoogvenster **Invoegcode** weergegeven:

   ![Het dialoogvenster Invoegcode](media/service-publish-to-web/publish_to_web5.png)

   U kunt slechts één invoegcode per rapport maken.

Als u wijzigingen aanbrengt in het dialoogvenster, moet u de bijgewerkte URL of iFrame kopiëren om de bijgewerkte instellingen op uw pagina te gebruiken.


### <a name="tips-for-view-modes"></a>Tips voor weergavemodi

Wanneer u inhoud in een blogbericht wilt invoegen, moet deze doorgaans binnen een bepaalde schermgrootte passen.  U kunt indien nodig de hoogte en breedte in de iFrame-code aanpassen. U moet echter controleren of uw rapport in het opgegeven iFrame-gebied past. U moet dus ook een geschikte weergavemodus instellen wanneer u het rapport bewerkt.

De volgende tabel bevat richtlijnen over de weergavemodus en hoe deze wordt weergegeven als deze is ingesloten.

| Weergavemodus | Voorbeelden van invoegen |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Aan pagina aanpassen** houdt rekening met de paginahoogte en -breedte van uw rapport. Als u uw pagina instelt op *dynamische* verhoudingen, zoals 16:9 of 4:3, wordt uw inhoud passend gemaakt binnen het iFrame. Bij insluiting in een iFrame kan het gebruiken van **Passend op pagina** leiden tot *letterboxing* : een grijze achtergrond wordt weergegeven in de iFrame-gebieden nadat de inhoud passend is gemaakt voor weergave binnen het iFrame. Stel de juiste hoogte en breedte van het iFrame in om letterboxing te minimaliseren. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Ware grootte** zorgt ervoor dat het rapport de grootte zoals ingesteld op de rapportpagina behoudt. Dit kan ertoe leiden dat er schuifbalken in uw iFrame worden weergegeven. Stel de hoogte en breedte van het iFrame in om schuifbalken te vermijden. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Passend in breedte** zorgt ervoor dat de inhoud binnen het horizontale gebied van uw iFrame past. Er wordt wel een rand weergegeven, maar de inhoud wordt zodanig geschaald dat alle beschikbare horizontale ruimte wordt gebruikt. |

### <a name="tips-for-iframe-height-and-width"></a>Tips voor de hoogte en breedte van uw iFrame

Een invoegcode voor **Publiceren op internet** ziet er ongeveer als volgt uit:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
U kunt de breedte en hoogte handmatig bewerken om er zeker van te zijn dat de inhoud precies past op de pagina waarop u deze invoegt.

Als u de weergave beter passend wilt maken, kunt u 56 pixels aan de hoogte van het iFrame toevoegen om het iFrame geschikt te maken voor het huidige formaat van de onderste balk. Als uw rapportagepagina gebruik maakt van dynamische verhoudingen, biedt de onderstaande tabel enkele afmetingen die u kunt gebruiken om het beeld passend te krijgen zonder letterboxing.

| Verhouding | Grootte | Dimensie (breedte x hoogte) |
| --- | --- | --- |
| 16:9 |Klein |640 x 416 px |
| 16:9 |Gemiddeld |800 x 506 px |
| 16:9 |Groot |960 x 596 px |
| 4:3 |Klein |640 x 536 px |
| 4:3 |Normaal |800 x 656 px |
| 4:3 |Groot |960 x 776 px |

## <a name="manage-embed-codes"></a>Invoegcodes beheren

Als u een invoegcode voor **Publiceren op internet** hebt gemaakt, kunt u de codes beheren via het menu **Instellingen** in Power BI. Met de optie Invoegcodes beheren kan het beoogde visuele element of rapport voor een code worden verwijderd (waardoor de invoegcode onbruikbaar wordt) of kan de invoegcode worden verkregen.

1. Als u de invoegcode voor **Publiceren op internet** wilt beheren, opent u het tandwiel **Instellingen** en selecteert u **Invoegcodes beheren**.

   ![Invoegcodes beheren](media/service-publish-to-web/publish_to_web8.png)

2. Uw invoegcodes worden weergegeven.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. U kunt een invoegcode ophalen of verwijderen. Als u de invoegcode verwijdert, worden alle koppelen naar het desbetreffende rapport of visuele element uitgeschakeld.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Als u **Verwijderen** selecteert, wordt u gevraagd om een bevestiging.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Updates voor rapporten en gegevens vernieuwen

Nadat u de invoegcode voor **Publiceren op internet** hebt gemaakt en gedeeld, wordt het rapport bijgewerkt met de wijzigingen die u aanbrengt. De koppeling naar de invoegcode is onmiddellijk actief. Iedereen die de koppeling opent, kan het rapport bekijken. De gegevens worden gedurende één uur in de cache geplaatst vanaf het moment dat deze worden opgehaald. Het is niet raadzaam om Publiceren op internet te gebruiken voor gegevens die regelmatig moeten worden vernieuwd. Zie de sectie [**Hoe werkt het**](#howitworks) verderop in dit artikel voor meer informatie. 

### <a name="data-refresh"></a>Gegevens vernieuwen

Vernieuwde gegevens worden automatisch in uw ingevoegde rapport of visuele element verwerkt. Wanneer gegevens worden vernieuwd voor een importgegevensmodel in de Power BI-service, wist de service de gegevenscache, waardoor gegevens snel worden bijgewerkt. Als u automatisch vernieuwen wilt uitschakelen, selecteert u in het schema voor de gegevensset die door het rapport wordt gebruikt, de optie **Niet vernieuwen**.  

### <a name="heavy-usage"></a>Intensief gebruik

Een ervaring met intensief gebruik kan optreden wanneer een rapport in korte tijd te veel query's ontvangt. Bij intensief gebruik kunnen gebruikers het rapport pas bekijken of ermee communiceren als de periode van intensief gebruik voorbij is. 

Het wordt aanbevolen een tijdelijke afbeelding voor uw rapport in te stellen. Bij intensief gebruik zien gebruikers de afbeelding van de tijdelijke aanduiding. 

Beperk het aantal afzonderlijke query's dat in uw rapport kan worden gegenereerd en de frequentie waarmee gegevens moeten worden vernieuwd, om het intensieve gebruik te voorkomen.

## <a name="power-bi-visuals"></a>Power BI-visuals

Power BI-visuals worden ondersteund in **Publiceren op internet**. Wanneer u **Publiceren op internet** gebruikt, hoeven gebruikers met wie u uw gepubliceerde visual deelt, Power BI-visuals niet in te schakelen om het rapport te bekijken.

## <a name="understanding-the-embed-code-status-column"></a>Inzicht in de kolom met de invoegcodestatus

>[!Note]
>Controleer de invoegcodes die u vaak hebt gepubliceerd. Verwijder alle code die niet meer openbaar beschikbaar hoeft te zijn.

De pagina **Invoegcodes beheren** bevat een statuskolom. De invoegcodes zijn standaard **Actief** , maar kunnen ook een van de onderstaande statussen hebben.

| Status | Beschrijving |
| --- | --- |
| **Actief** |Het rapport is beschikbaar voor internetgebruikers die het kunnen weergeven en ermee kunnen werken. |
| **Geblokkeerd** |De inhoud van het rapport maakt inbreuk op de [Servicevoorwaarden van Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft heeft het rapport geblokkeerd. Neem contact op met de ondersteuning als u denkt dat de inhoud ten onrechte is geblokkeerd. |
| **Niet ondersteund** |De gegevensset van het rapport maakt gebruik van beveiliging op rijniveau of een andere niet-ondersteunde configuratie. Zie de sectie [**Beperkingen**](#limitations) voor een volledige lijst. |
| **Geschonden** |De invoegcode valt buiten het opgegeven tenantbeleid. Deze status komt meestal voor wanneer een invoegcode is gemaakt en de tenantinstelling voor **Publiceren op internet** is gewijzigd, waarbij de gebruiker die de invoegcode beheert, wordt uitgesloten. Wanneer de tenantinstelling is uitgeschakeld of wanneer de gebruiker geen invoegcodes meer mag maken, krijgen bestaande invoegcodes de status **Geschonden**. Zie de sectie [Uw Power BI-beheerder vinden](#find-your-power-bi-administrator) in dit artikel voor meer informatie. |

## <a name="report-a-concern-with-publish-to-web-content"></a>Een probleem melden met Publiceren op internet

Als u een probleem wilt melden dat is gerelateerd aan **Publiceren op internet** -inhoud die is ingesloten in een website of blog, selecteert u het **vlag** -pictogram in de onderste balk van het **Publiceren op internet** -rapport.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

U wordt gevraagd om een e-mail te sturen naar Microsoft waarin u het probleem toelicht. Microsoft evalueert de inhoud op basis van de [Servicevoorwaarden voor Power BI](https://powerbi.microsoft.com/terms-of-service) en zal passende actie ondernemen.

## <a name="licensing"></a>Licentieverlening

U kunt **Publiceren op internet** allen gebruiken als u gebruiker van Microsoft Power BI bent. Uw rapport kan ook worden bekeken door personen die geen gebruik van Power BI maken.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Hoe het werkt (technische details)

Wanneer u een invoegcode maakt met **Publiceren op internet** , wordt het rapport zichtbaar voor het internetgebruikers. Het is openbaar beschikbaar, dus u kunt verwachten dat bezoekers het rapport eenvoudig via sociale media zullen delen. Gebruikers bekijken het rapport door de directe openbare URL te openen of deze ingesloten te bekijken in een webpagina of blog. Als dit het geval is, slaat Power BI de definitie van het rapport en de resultaten van de vragen die nodig zijn om het rapport te bekijken, op in een cache. Met Opslaan in de cache kunnen duizenden gebruikers het rapport gelijktijdig bekijken, zonder dat dit ten koste gaat van de prestaties.

De gegevens worden gedurende één uur in de cache geplaatst vanaf het moment dat deze worden opgehaald. Als u de rapportdefinitie bijwerkt (bijvoorbeeld als u de weergavemodus wijzigt) of de rapportgegevens vernieuwt, duurt het even voordat wijzigingen worden doorgevoerd in de versie van het rapport die uw gebruikers weergeven. Wanneer een gegevensvernieuwing plaatsvindt voor een importgegevensmodel, wist de service de gegevens in de cache en worden nieuwe gegevens opgehaald. In de meeste gevallen worden de gegevens bijna gelijktijdig bijgewerkt met de import van de gegevens. Voor rapporten met veel verschillende query's kan het echter enige tijd duren voordat deze zijn bijgewerkt. Omdat element- en gegevenswaarden onafhankelijk in de cache wordt opgeslagen, kan bij een gegevenswijziging een combinatie van huidige en eerdere waarden worden weergegeven aan een gebruiker. U kunt daarom het beste uw werkzaamheden ver van tevoren plannen en de invoegcode voor **Publiceren op internet** alleen maken wanneer u tevreden bent met de instellingen. Minimaliseer het aantal vernieuwingen van gegevens, en voer de vernieuwingen uit buiten piekuren. Het is niet raadzaam om Publiceren op internet te gebruiken voor gegevens die regelmatig moeten worden vernieuwd.

## <a name="find-your-power-bi-administrator"></a>Uw Power BI-beheerder vinden

De Power BI-beheerportal bevat instellingen waarmee wordt bepaald wie op internet kunnen publiceren. Als u de [tenantinstellingen voor publiceren op internet](../admin/service-admin-role.md) wilt aanpassen, moet u samenwerken met de [Power BI-beheerder](../admin/service-admin-portal.md#publish-to-web) van uw organisatie.

Kleinere organisaties of individuen die zich hebben geregistreerd, hebben mogelijk nog geen Power BI-beheerder. Volg ons [proces voor het overnemen van beheer](/azure/active-directory/users-groups-roles/domains-admin-takeover). Nadat u een Power BI-beheerder hebt, kan de beheerder inschakelen dat u invoegcodes kunt maken.

Grotere organisaties hebben vaak al een Power BI-beheerder. Mensen in een van de volgende rollen kunnen optreden als Power BI-beheerder:

- Hoofdbeheerders
- Gebruikers met de beheerdersrol van de Power BI-service in Azure Active Directory

U moet [een van deze personen](/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) in uw organisatie vinden en vragen om de [tenantinstellingen voor publiceren op internet](../admin/service-admin-portal.md#publish-to-web) bij te werken in de beheerportal.

## <a name="limitations"></a>Beperkingen

**Publiceren op internet** wordt ondersteund voor de meeste gegevensbronnen en rapporten in de Power BI-service. De volgende soorten rapporten worden momenteel echter niet ondersteund of zijn niet beschikbaar bij **Publiceren op internet** :

- Rapporten met beveiliging op rijniveau.
- Rapporten die als gegevensbron gebruikmaken van Live Connection, waaronder Analysis Services Tabular dat on-premises wordt gehost, Analysis Services Multidimensional en Azure Analysis Services.
- Rapporten die gebruikmaken van een [gedeelde gegevensset](../connect-data/service-datasets-across-workspaces.md) die is opgeslagen in een andere werkruimte dan het rapport.
- [Gedeelde en gecertificeerde gegevenssets](../connect-data/service-datasets-share.md).
- Rapporten die direct of via een organisatie-inhoudspakket met u worden gedeeld.
- Rapporten in een werkruimte waarvan u geen lid bent met machtigingen voor bewerken.
- R- en Python-visuals worden momenteel niet ondersteund in **Publiceren op internet** -rapporten.
- Exporteren van gegevens uit de visuals in een rapport dat is gepubliceerd op internet.
- ArcGIS Maps for Power BI-visuals.
- Q&A voor Power BI-visuals.
- Rapporten met DAX-metingen op rapportniveau.
- Gegevensquerymodellen voor eenmalige aanmelding.
- Beveiligde vertrouwelijke of eigendomsinformatie.
- De mogelijkheid van automatische verificatie die bij de optie **Insluiten** wordt verstrekt, werkt niet met de Power BI JavaScript-API. Gebruik voor de Power BI JavaScript-API de benadering [Gebruiker is eigenaar van gegevens](../developer/embedded/embed-sample-for-your-organization.md) voor het insluiten van inhoud.

## <a name="next-steps"></a>Volgende stappen

- [Webonderdeel Rapport in SharePoint Online](service-embed-report-spo.md) 

- [Rapport insluiten in een beveiligde portal of website](service-embed-secure.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
