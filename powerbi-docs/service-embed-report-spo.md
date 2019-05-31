---
title: Insluiten met webonderdeel Rapport in SharePoint Online
description: Met het nieuwe webonderdeel Rapport van Power BI voor SharePoint Online kunt u eenvoudig interactieve Power BI-rapporten insluiten in SharePoint Online-pagina's.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051270"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Insluiten met webonderdeel Rapport in SharePoint Online

Met het nieuwe webonderdeel Rapport van Power BI voor SharePoint Online kunt u eenvoudig interactieve Power BI-rapporten insluiten in SharePoint Online-pagina's.

Wanneer u de nieuwe **insluiten in SharePoint Online** optie, de ingesloten rapporten zijn volledig beveiligd, zodat u eenvoudig beveiligde interne portals kunt maken.

## <a name="requirements"></a>Vereisten

Voor **insluiten in SharePoint Online** rapporten werken, is het volgende vereist:

* Een Power BI Pro-licentie of een [Power BI Premium-capaciteit (EM of P-SKU)](service-premium-what-is.md) met een licentie voor Power BI.
* Voor het Power BI-webonderdeel voor SharePoint Online is [Moderne pagina's](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b) vereist.

## <a name="embed-your-report"></a>Uw rapport insluiten
Als u wilt uw rapport insluiten in SharePoint Online, moet u de rapport-URL ophalen en deze gebruiken met de SharePoint Online nieuwe Power BI-webonderdeel.

### <a name="get-a-report-url"></a>Een rapport-URL ophalen

1. In Power BI, moet u het rapport weergeven.

2. Selecteer de **bestand** in het vervolgkeuzemenu Selecteer **insluiten in SharePoint Online**.

    ![Menu Bestand](media/service-embed-report-spo/powerbi-file-menu.png)

3. Kopieer de rapport-URL in het dialoogvenster.

    ![Insluitkoppeling](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Het Power BI-rapport toevoegen aan een SharePoint Online-pagina

1. Open de doelpagina in SharePoint Online en selecteer **bewerken**.

    ![Pagina met SP-bewerkingen](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Of selecteert u in Sharepoint Online, **+ nieuw** te maken van een nieuwe moderne sitepagina.

    ![Nieuwe SP-pagina](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selecteer de **+** Vervolgkeuzelijst en selecteer vervolgens de **Power BI**.

    ![Nieuw SP-webonderdeel](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selecteer **Rapport toevoegen**.

    ![Nieuw SP-rapport](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Plak de URL van het rapport eerder hebt gekopieerd in de **Power BI-rapportkoppeling** deelvenster. Het rapport wordt automatisch geladen.

    ![Nieuwe eigenschappen van SP-webonderdelen](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selecteer **Publiceren** om de wijziging zichtbaar te maken voor uw SharePoint Online-gebruikers.

    ![SP-rapport geladen](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Toegang verlenen tot rapporten

Een rapport insluiten in SharePoint Online niet automatisch gebruikers machtigen om het rapport weer te geven: u moet het instellen van machtigingen weergeven in Power BI.

> [!IMPORTANT]
> Controleer wie het rapport kan raadplegen in de Power BI-service en verleen toegang tot personen die niet worden vermeld.

Er zijn twee manieren om aan te bieden van toegang tot de rapporten in Power BI. De eerste manier, als u een Office 365-groep voor het bouwen van uw SharePoint Online-teamsite, is het overzicht van de gebruiker als lid van de **app-werkruimte in Power BI-service** en de **SharePoint-pagina**. Zie [Een app-werkruimte beheren](service-manage-app-workspace-in-power-bi-and-office-365.md) voor meer informatie.

De tweede manier is het insluiten van een rapport in een app en deze delen met gebruikers rechtstreeks:  

1. De auteur (moet een Pro-gebruiker) maakt u een rapport in een app-werkruimte. Om te delen met **gratis Power BI-gebruikers**, de app-werkruimte moet worden ingesteld als een **Premium-werkruimte**.

2. De auteur van het publiceert de app en installeert deze. De auteur nodig heeft om te controleren of de app voor toegang tot de URL van het rapport dat wordt gebruikt voor het insluiten in SharePoint Online te installeren.

3. Nu moeten alle eindgebruikers de app ook installeren. U kunt ook de **app automatisch installeren** functie, die u kunt inschakelen in de [Power BI-beheerportal](service-admin-portal.md), hebben de app is vooraf geïnstalleerd voor eindgebruikers.

   ![App automatisch installeren](media/service-embed-report-spo/install-app-automatically.png)

4. De auteur opent de app en gaat naar het rapport.

5. De auteur van de kopieert het ingesloten rapport-URL van het rapport de app is geïnstalleerd. **Gebruik niet de originele rapport-URL van de app-werkruimte.**

6. Maak een nieuwe teamsite in SharePoint Online.

7. URL van het rapport eerder hebt gekopieerd naar de Power BI-webonderdeel toevoegen.

8. Voeg alle eindgebruikers en/of groepen die gebruik gaan maken van de gegevens toe aan de SharePoint Online-pagina en in de Power BI-app die u hebt gemaakt.

    > [!NOTE]
    > **Gebruikers of groepen hebben toegang nodig tot zowel de SharePoint Online-pagina als het rapport in de Power BI-app om het rapport te kunnen zien op de SharePoint-pagina.**

De eindgebruiker kan nu naar de teamsite in SharePoint Online gaan en de rapporten bekijken op de pagina.

## <a name="multi-factor-authentication"></a>Meervoudige verificatie

Als u zich voor uw Power BI-omgeving moet aanmelden met meervoudige verificatie, krijgt u mogelijk het verzoek om u aan te melden met een beveiligingsapparaat om uw identiteit te verifiëren. Dit gebeurt als u niet hebben aangemeld bij SharePoint Online met meervoudige verificatie, maar uw Power BI-omgeving vereist een beveiligingsapparaat om een account te valideren.

> [!NOTE]
> Azure Active Directory 2.0 biedt geen ondersteuning voor multi-factor authentication - gebruikers zien een foutbericht weergegeven. Als dergelijke gebruikers zich met hun beveiligingsapparaat opnieuw aanmelden bij SharePoint Online, kunnen ze het rapport mogelijk weergeven.

## <a name="web-part-settings"></a>Instellingen van het webonderdeel

Hieronder vindt u de instellingen die u voor de Power BI-webonderdeel voor SharePoint Online kunt aanpassen.

![Eigenschappen van SP-webonderdelen](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Eigenschap | Beschrijving |
| --- | --- |
| Paginanaam |Hiermee stelt u de standaardpagina van het webonderdeel. Selecteer een waarde in de vervolgkeuzelijst. Als er geen pagina's worden weergegeven, zijn er twee mogelijke redenen: uw rapport bestaat uit één pagina of de URL die u hebt geplakt, bevat de naam van een pagina. Verwijder de rapportsectie uit de URL om een specifieke pagina te selecteren. |
| Weergave |Hiermee past u op hoe het rapport in de SharePoint Online-pagina past. |
| Navigatiedeelvenster weergeven |Geeft het navigatiedeelvenster van de pagina weer of verbergt het. |
| Filterdeelvenster weergeven |Geeft het Filterdeelvenster weer of verbergt het. |

## <a name="reports-that-do-not-load"></a>Rapporten die niet worden geladen

Als uw rapport niet binnen de Power BI-webonderdeel wordt geladen, ziet u mogelijk het volgende bericht:

![Deze inhoud is niet beschikbaar-bericht](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Er zijn twee gangbare redenen voor dit bericht.

1. U hebt geen toegang tot rapporten.
2. Het rapport is verwijderd.

Neem contact op met de eigenaar van de SharePoint Online-pagina om u te helpen bij het oplossen van het probleem.

## <a name="licensing"></a>Licentieverlening

Gebruikers die in SharePoint een rapport bekijken, moeten een **Power BI Pro-licentie** hebben of de inhoud moet zich in een werkruimte bevinden in een **[Power BI Premium-capaciteit (EM of P SKU)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Bekende problemen en beperkingen

* Fout: 'Er is een fout opgetreden. Meld u af en meld u opnieuw aan. Ga vervolgens opnieuw naar deze pagina. Correlatie-ID: niet-gedefinieerde HTTP-antwoordstatus: 400, serverfoutcode 10001, bericht: Ontbrekende vernieuwingstoken'
  
  Als u dit foutbericht ontvangt, probeert u een van de onderstaande stappen voor probleemoplossing.
  
  1. Meld u af bij SharePoint en meld u weer aan. Sluit alle browservensters voordat u zich weer aanmeldt.

  2. Als uw gebruikersaccount is vereist voor multi-factor authentication (MFA), klikt u zich aanmelden bij SharePoint met behulp van uw MFA-apparaat (telefoon-app, smartcard, enzovoort).
  
  3. Accounts van Azure B2B-gastgebruikers worden niet ondersteund. Gebruikers zien het Power BI-logo in het onderdeel dat wordt geladen, maar het rapport wordt niet weergegeven.

* Power BI ondersteunt niet dezelfde gelokaliseerde talen als SharePoint Online. U kunt hierdoor mogelijk niet de juiste lokalisatie zien in een ingesloten rapport.

* Er kunnen problemen optreden als u Internet Explorer 10 gebruikt. U kunt de [browserondersteuning voor Power BI](consumer/end-user-browsers.md) en voor [Office 365](https://products.office.com/office-system-requirements#Browsers-section) onderzoeken.

* Het Power BI-webonderdeel is niet beschikbaar voor [nationale clouds](https://powerbi.microsoft.com/clouds/).

* De klassieke SharePoint Server wordt niet ondersteund met dit webonderdeel.

* [URL-filters](service-url-filters.md) worden niet ondersteund met het SPO-webonderdeel.

## <a name="next-steps"></a>Volgende stappen

* [Toestaan of verhinderen dat eindgebruikers moderne sitepagina's maken](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Een app maken en distribueren in Power BI](service-create-distribute-apps.md)  
* [Een dashboard delen met collega's en anderen](service-share-dashboards.md)  
* [Wat is Power BI Premium?](service-premium-what-is.md)
* [Rapport insluiten in een veilige portal of website](service-embed-secure.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)