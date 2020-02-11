---
title: Publiceren op internet vanuit Power BI
description: Met Power BI publiceren op internet kunt u eenvoudig interactieve Power BI-visualisaties op elk apparaat online invoegen, zoals blogberichten, websites, e-mailberichten of sociale media.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/06/2020
LocalizationGroup: Share your work
ms.openlocfilehash: a9417e7de98e0fa1867aa0561743c1ed6c5b63e2
ms.sourcegitcommit: 578d43aeb7cebf40f3caf03a614bc885cc039488
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/07/2020
ms.locfileid: "77076694"
---
# <a name="publish-to-web-from-power-bi"></a>Publiceren op internet vanuit Power BI

Met de Power BI-optie **Publiceren op internet** kunt u eenvoudig interactieve Power BI-visualisaties online invoegen, bijvoorbeeld in blogberichten, websites, e-mailberichten of sociale media. U kunt uw gepubliceerde visuele elementen ook eenvoudig bewerken, bijwerken en vernieuwen of het delen ervan stoppen.

> [!WARNING]
> Als u **Publiceren op internet** gebruikt, kan het door u gepubliceerde rapport of visuele element door iedereen op internet worden bekeken. Er is geen verificatie vereist en er kunnen gedetailleerde gegevens worden weergegeven die met uw rapporten worden geaggregeerd. Voordat u een rapport publiceert, moet u controleren of u de gegevens visualisaties openbaar mag delen. Publiceer geen vertrouwelijke gegevens of eigendomsinformatie. Controleer bij twijfel vóór publicatie de beleidsregels van uw organisatie.

>[!Note]
>Als u uw inhoud veilig wilt insluiten in een interne portal of website, gebruik dan de optie [Insluiten](service-embed-secure.md) of [Insluiten in SharePoint Online](service-embed-report-spo.md). Hiermee zorgt u ervoor dat alle machtigingen en gegevensbeveiliging worden afgedwongen wanneer uw gebruikers uw interne gegevens bekijken.

## <a name="how-to-use-publish-to-web"></a>Publiceren op internet gebruiken

**Publiceren op internet** is beschikbaar voor rapporten die u kunt bewerken in uw persoonlijke en groepswerkruimten.  De optie is niet beschikbaar voor rapporten die met u zijn gedeeld of rapporten die op rijniveau zijn beveiligd om gegevens te beveiligen. Zie de sectie [**Beperkingen**](#limitations) hieronder voor een volledige lijst met aanvragen waarbij **Publiceren op internet** niet wordt ondersteund. Bekijk de **waarschuwing** eerder in dit artikel voordat u **Publiceren op internet** gebruikt.

U kunt in de volgende korte video zien hoe deze functie werkt. Probeer het in de onderstaande stappen vervolgens zelf.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

In de volgende stappen wordt het gebruik van **Publiceren op internet** beschreven.

1. Open een rapport in uw werkruimte dat u kunt bewerken en selecteer **Bestand > Publiceren op internet**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)
   
2. Neem contact op met uw [Power BI-beheerder](service-admin-role.md) als u niet bevoegd bent om invoegcodes te maken

   ![PtW1](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   Voor hulp bij het vinden van de persoon die een publicatie naar het web in uw organisatie kan inschakelen, [raadpleegt u deze tips](#how-to-find-your-power-bi-administrator).

3. Bekijk de inhoud van het dialoogvenster en selecteer **Een invoegcode maken**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

4. Bekijk de waarschuwing die hier wordt weergegeven en controleer of de gegevens op een openbare website mogen worden geplaatst. Als dit het geval is, selecteert u **Publiceren**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

5. Er wordt een dialoogvenster met een koppeling weergegeven. U kunt deze koppeling in een e-mailbericht verzenden, in code, zoals een iFrame, insluiten of rechtstreeks in een webpagina of blog of plakken.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

6. Als u eerder een invoegcode voor een rapport hebt gemaakt en u **Publiceren op Internet** selecteert, krijgt u de dialoogvensters in stap 2 tot en met 4 niet te zien. In plaats daarvan wordt het dialoogvenster **Invoegcode** weergegeven:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   U kunt slechts één invoegcode per rapport maken.


## <a name="tips-and-tricks-for-view-modes"></a>Tips en trucs voor weergavemodi

Wanneer u inhoud in een blogbericht wilt invoegen, moet deze doorgaans binnen een bepaalde schermgrootte passen.  U kunt indien nodig de hoogte en breedte in de iFrame-code aanpassen. U moet echter controleren of uw rapport in het opgegeven iFrame-gebied past. U moet dus ook een geschikte weergavemodus instellen wanneer u het rapport bewerkt.

De volgende tabel bevat richtlijnen over de weergavemodus en hoe deze wordt weergegeven als deze is ingesloten.

| Weergavemodus | Voorbeelden van invoegen |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Aan pagina aanpassen** houdt rekening met de paginahoogte en -breedte van uw rapport. Als u uw pagina instelt op *dynamische* verhoudingen, zoals 16:9 of 4:3, wordt uw inhoud passend gemaakt binnen het iFrame. Bij opname in een iFrame kan het gebruiken van **Passend op pagina** leiden tot *letterboxing*, waarbij een grijze achtergrond wordt weergegeven in de iFrame-gebieden nadat de inhoud passend is gemaakt voor weergave binnen het iFrame. Stel de juiste hoogte en breedte van het iFrame in om letterboxing te minimaliseren. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Ware grootte** zorgt ervoor dat het rapport de grootte zoals ingesteld op de rapportpagina behoudt. Dit kan ertoe leiden dat er schuifbalken in uw iFrame worden weergegeven. Stel de hoogte en breedte van het iFrame in om schuifbalken te vermijden. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Passend in breedte** zorgt ervoor dat de inhoud binnen het horizontale gebied van uw iFrame past. Er wordt wel een rand weergegeven, maar de inhoud wordt zodanig geschaald dat alle beschikbare horizontale ruimte wordt gebruikt. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tips en trucs voor de hoogte en breedte van uw iFrame

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

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Uw invoegcodes worden weergegeven.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. U kunt een invoegcode ophalen of verwijderen. Als u de invoegcode verwijdert, worden alle koppelen naar het desbetreffende rapport of visuele element uitgeschakeld.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Als u **Verwijderen**, wordt u gevraagd om een bevestiging.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Updates voor rapporten en gegevens vernieuwen

Nadat u de invoegcode voor **Publiceren op internet** hebt gemaakt en gedeeld, wordt het rapport bijgewerkt met de wijzigingen die u aanbrengt en is de invoegcode onmiddellijk actief. Iedereen die de koppeling opent, kan het rapport bekijken. Na deze eerste actie kan het echter ongeveer één uur duren voordat rapporten of visuals zichtbaar zijn voor uw gebruikers. Zie de sectie [**Hoe werkt het**](#howitworks) verderop in dit artikel voor meer informatie. 

## <a name="data-refresh"></a>Gegevens vernieuwen

Vernieuwde gegevens worden automatisch in uw ingevoegde rapport of visuele element verwerkt. Het kan ongeveer één uur duren voordat vernieuwde gegevens zichtbaar zijn in invoegcodes. Als u automatisch vernieuwen wilt uitschakelen, selecteert u in het schema voor de gegevensset die door het rapport wordt gebruikt, de optie **Niet vernieuwen**.  

## <a name="custom-visuals"></a>Aangepaste visuals

Aangepaste visuele elementen worden ondersteund in **Publiceren op internet**. Wanneer u **Publiceren op internet** gebruikt, hoeven gebruikers met wie u uw gepubliceerde visual deelt, aangepaste visuals niet in te schakelen om het rapport te bekijken.

## <a name="limitations"></a>Beperkingen

**Publiceren op internet** wordt ondersteund voor de meeste gegevensbronnen en rapporten in de Power BI-service. De volgende opties worden momenteel echter niet ondersteund of zijn niet beschikbaar voor **Publiceren op internet**:

- Rapporten met beveiliging op rijniveau.
- Rapporten die als gegevensbron gebruikmaken van Live Connection, waaronder Analysis Services Tabular dat on-premises wordt gehost, Analysis Services Multidimensional en Azure Analysis Services.
- Rapporten die direct of via een organisatie-inhoudspakket met u worden gedeeld.
- Rapporten in een groep waarvan u geen lid bent met machtigingen voor bewerken.
- R-visuals worden momenteel niet ondersteund in **Publiceren op internet**-rapporten.
- Exporteren van gegevens uit de visuals in een rapport dat is gepubliceerd naar internet.
- ArcGIS Maps for Power BI-visuals.
- Rapporten met DAX-metingen op rapportniveau.
- Gegevensquerymodellen voor eenmalige aanmelding.
- Beveiligde vertrouwelijke of eigendomsinformatie.
- [Gedeelde en gecertificeerde gegevenssets](service-datasets-share.md).
- De mogelijkheid van automatische verificatie die bij de optie **Insluiten** wordt verstrekt, werkt niet met de Power BI JavaScript-API. Gebruik voor de Power BI JavaScript-API de benadering [Gebruiker is eigenaar van gegevens](developer/embed-sample-for-your-organization.md) voor het insluiten van inhoud.

## <a name="tenant-setting"></a>Tenantinstelling

De instelling **Publiceren op internet** bevat opties waarvoor gebruikers invoegcodes kunnen maken.

![Instelling 'Publiceren op internet'](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

U wordt gevraagd om contact op te nemen met de Power BI-beheerder, zodat u een invoegcode kunt maken wanneer de optie **Kiezen hoe invoegcodes werken** is ingesteld op **Alleen bestaande invoegcodes toestaan** en **Publiceren op internet** op **Ingeschakeld** staat.

![Prompt voor publiceren op internet](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Power BI-beheerders kunnen de functie voor **Publiceren op internet** in- of uitschakelen. Ze kunnen ook de toegang beperken tot specifieke groepen die van invloed kunnen zijn op uw mogelijkheid om een invoegcode te maken. U ziet verschillende opties in de gebruikersinterface, afhankelijk van de instelling **Publiceren op internet**.

|Functie |Ingeschakeld voor de hele organisatie |Uitgeschakeld voor de hele organisatie |Specifieke beveiligingsgroepen   |
|---------|---------|---------|---------|
|**Publiceren op internet** in het menu **Bestand** van het rapport.|Ingeschakeld voor iedereen|Niet voor iedereen zichtbaar|Alleen zichtbaar voor gemachtigde gebruikers of groepen.|
|**Invoegcodes beheren** onder **Instellingen**|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen.<br><br>Optie * **Verwijderen** alleen voor gemachtigde gebruikers of groepen.<br>* **Ophalen van codes** ingeschakeld voor iedereen.|
|**Codes invoegen** binnen de beheerportal|De status geeft een van de volgende toestanden aan:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd|De status geeft **Uitgeschakeld** weer|De status geeft een van de volgende toestanden aan:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd<br><br>Als een gebruiker niet is geautoriseerd op basis van de tenantinstelling, wordt de status weergegeven als **geschonden**.|
|Bestaande gepubliceerde rapporten|Iedereen ingeschakeld|Iedereen uitgeschakeld|Rapporten blijven weergeven voor iedereen.|

## <a name="understanding-the-embed-code-status-column"></a>Inzicht in de kolom met de invoegcodestatus

>[!Note]
>Controleer regelmatig de invoegcodes die u hebt gepubliceerd en verwijder alle codes die niet meer openbaar beschikbaar hoeven te zijn. 

De pagina **Invoegcodes beheren** bevat een statuskolom. De invoegcodes zijn standaard **Actief**, maar kunnen ook een van de onderstaande statussen hebben.

| Status | Beschrijving |
| --- | --- |
| **Actief** |Het rapport is beschikbaar voor internetgebruikers die het kunnen weergeven en ermee kunnen werken. |
| **Geblokkeerd** |De inhoud van het rapport maakt inbreuk op de [Servicevoorwaarden van Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft heeft het rapport geblokkeerd. Neem contact op met de ondersteuning als u denkt dat de inhoud ten onrechte is geblokkeerd. |
| **Niet ondersteund** |De gegevensset van het rapport maakt gebruik van beveiliging op rijniveau of een andere niet-ondersteunde configuratie. Zie de sectie [**Beperkingen**](#limitations) voor een volledige lijst. |
| **Geschonden** |De invoegcode valt buiten het opgegeven tenantbeleid. Dit gebeurt meestal wanneer een invoegcode is gemaakt en de tenantinstelling voor **Publiceren op internet** wordt gewijzigd om de gebruiker die de invoegcode beheert, uit te sluiten. Wanneer de tenantinstelling is uitgeschakeld of wanneer de gebruiker geen invoegcodes meer mag maken, krijgen bestaande invoegcodes de status **Geschonden**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Een probleem met Publiceren op internet melden

Als u een probleem wilt melden dat is gerelateerd aan **Publiceren op internet**-inhoud die is ingesloten in een website of blog, gebruikt u het **vlag**-pictogram in de onderste balk, zoals wordt weergegeven in de volgende afbeelding. U wordt gevraagd om een e-mail te sturen naar Microsoft waarin u het probleem toelicht. Microsoft evalueert de inhoud op basis van de Servicevoorwaarden voor Power BI en zal passende actie ondernemen.

Als u een probleem wilt melden, selecteert u het **vlag**-pictogram in de onderste balk van het **Publiceren op internet**-rapport dat wordt weergegeven.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenties en prijzen

U kunt **Publiceren op internet** allen gebruiken als u gebruiker van Microsoft Power BI bent. Uw rapport kan ook worden weergegeven door personen die geen gebruik van Power BI maken.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Hoe het werkt (technische details)

Wanneer u een invoegcode maakt met **Publiceren op internet**, wordt het rapport zichtbaar voor het internetgebruikers. Het is openbaar beschikbaar, dus u kunt verwachten dat bezoekers het rapport eenvoudig via sociale media zullen delen. Terwijl gebruikers het rapport bekijken, doordat ze de directe openbare URL openen of de ingesloten versie op een webpagina of blog bekijken, worden de rapportdefinitie en de resultaten van de query's die nodig zijn om het rapport weer te geven door Power BI in de cache opgeslagen. Dit zorgt ervoor dat duizenden gebruikers het rapport gelijktijdig kunnen bekijken, zonder dat dit ten koste gaat van de prestaties.

De cache heeft een lange levensduur. Als u de rapportdefinitie bijwerkt (bijvoorbeeld als u de weergavemodus wijzigt) of de rapportgegevens vernieuwt, duurt het ongeveer een uur voordat wijzigingen worden doorgevoerd in de versie van het rapport die uw gebruikers weergeven. U kunt daarom het beste uw werkzaamheden ver van tevoren plannen en de invoegcode voor **Publiceren op internet** alleen maken wanneer u tevreden bent met de instellingen.

## <a name="how-to-find-your-power-bi-administrator"></a>Uw Power BI-beheerder vinden

Als u de [webtenantinstellingen voor publicatie](#tenant-setting) naar het web wilt aanpassen, moet u samenwerken met de [Power BI-beheerder](service-admin-role.md) van uw organisatie.

Kleinere organisaties of individuen die zich hebben geregistreerd, hebben mogelijk nog geen Power BI-beheerder. U moet ons [proces voor het overnemen van tenantbeheer](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover) volgen. Nadat u een Power BI-beheerder hebt, kan de beheerder inschakelen dat u invoegcodes kunt maken.

Grotere organisaties hebben vaak al een Power BI-beheerder. Mensen in een van de volgende rollen kunnen optreden als Power BI-beheerder:

- Office 365-beheerders
- Azure Active Directory-beheerders
- Gebruikers met de beheerdersrol van de Power BI-service in Azure Active Directory

U hebt [een van deze mensen](https://docs.microsoft.com/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) in uw organisatie nodig, zij kunnen de instelling bijwerken.


## <a name="next-steps"></a>Volgende stappen

- [Webonderdeel Rapport in SharePoint Online](service-embed-report-spo.md) 

- [Rapport insluiten in een beveiligde portal of website](service-embed-secure.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
