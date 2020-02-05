---
title: Een Power BI-visual naar AppSource verzenden met Verkoperdashboard
description: Een Power BI-visual naar AppSource verzenden met Verkoperdashboard
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223673"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Een Power BI-visual naar AppSource verzenden met Verkoperdashboard

U moet een e-mailbericht met het **pbiviz**-bestand en het **pbix**-bestand verzenden naar het Power BI-team vóór indiening bij AppSource. Hierdoor kan het Power BI-team de bestanden uploaden naar de openbare shareserver. Anders kunnen de bestanden niet worden opgehaald in de store. U moet de bestanden met nieuwe verzendingen van Power BI-visuals, updates in bestaande Power BI-visuals, en oplossingen voor geweigerde verzendingen verzenden.

>[!NOTE]
>[Verkoperdashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) zal op den duur verdwijnen. Het wordt vervangen door [Partnercentrum](https://docs.microsoft.com/partner-center/). Gebruik Verkoperdashboard alleen als u nog een lopende aanvraag voor een Power BI-visual hebt. Als u een nieuwe Power BI-visual wilt indienen op AppSource, gebruikt u de [methode met Partnercentrum](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Inzendingsproces voor Verkoperdashboard

U hebt een geldig Office-ontwikkelaarsaccount nodig om u te kunnen aanmelden bij het [Office-ontwikkelaarscentrum](https://dev.office.com/). Een Office-ontwikkelaarsaccount moet een Windows Live ID zijn, zoals hotmail.com of outlook.com.

1. Navigeer naar het [ontwikkelaarscentrum](https://sellerdashboard.microsoft.com/Application/Summary).

2. Selecteer **Een nieuwe app toevoegen**.

    ![App toevoegen](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Selecteer **Aangepast visueel Power BI-element** en vervolgens **Volgende**.

4. Selecteer de **+** onder **App-pakket** en selecteer het XML-bestand van het app-pakket dat u hebt ontvangen van het Power BI-team in het dialoogvenster Bestand openen.

    ![App-pakket](media/office-store/powerbi-custom-visual-apppackage.png)

5. Als het goed is, ontvangt u een goedkeuringsbericht dat dit een geldig Power BI-app-pakket is.

    ![Manifest goedgekeurd](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Vul de details van **Algemene informatie** in.

   * *Titel van inzending:* de naam van uw inzending in het ontwikkelaarscentrum.
   * *Versie:* uw versienummer wordt automatisch ingevuld op basis van het app-pakket van uw invoegtoepassing.
   * *Releasedatum (UTC):* selecteer een releasedatum voor uw app in de store. Als u een datum in de toekomst kiest, is uw app pas vanaf die datum beschikbaar in de store.
   * *Categorie:* de eerste categorie wordt automatisch ingevuld als 'Gegevensvisualisatie + BI'. Alle Power BI-visuals worden zo getagd. U mag maximaal twee extra categorieën opgeven zodat uw visual eenvoudig te vinden is voor gebruikers.
   * *Testopmerkingen:* optioneel, voor als u bepaalde instructies voor de testers van Microsoft wilt opgeven
   * *Mijn app bevat of gebruikt versleuteling of cryptografie, of roept versleuteling of cryptografie aan:* laat dit selectievakje uitgeschakeld
   * *Deze invoegtoepassing beschikbaar maken in de catalogus met Office-invoegtoepassingen op de iPad:* laat dit selectievakje uitgeschakeld
7. Upload het logo van uw visuele element door **+** te selecteren onder **App-logo**. Selecteer vervolgens het pictogrambestand in het dialoogvenster Bestand openen. Het bestand moet een PNG-, JPG-, JPEG- of GIF-bestand zijn. Het logo moet exact 300 pixels breed en 300 pixels hoog zijn en het bestand mag niet groter zijn dan 512 kB.

    ![App-logo](media/office-store/powerbi-custom-visual-app-logo.png)

8. Vul de details van **Ondersteuningsdocumenten** in.

   * Koppeling naar ondersteuningsdocument
   * Koppeling naar privacydocument
   * Koppeling naar video
   * Gebruiksrechtovereenkomst

       U moet een bestand met een gebruiksrechtovereenkomst uploaden. U kunt uw eigen gebruiksrechtovereenkomst gebruiken, of de standaardgebruiksrechtovereenkomst voor Power BI-visuals in Office Store. Als u de standaardgebruiksrechtovereenkomst wilt gebruiken, plakt u de volgende URL in het dialoogvenster voor het uploaden van het bestand Gebruiksrechtovereenkomst van het verkoperdashboard: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Selecteer **Volgende** om door te gaan naar de pagina **Details**.

10. Selecteer **Taal** en kies een taal in de lijst.

    ![Taal](media/office-store/powerbi-custom-visual-language.png)

11. Vul de details van Beschrijving in.

    * *App-naam (voor deze taal):* voer de titel van uw app in, zoals die moet worden weergegeven in de webwinkel.
    * *Korte beschrijving:* voer de korte beschrijving van uw app in (maximaal 100 tekens), zoals die moet worden weergegeven in de webwinkel. Deze beschrijving wordt weergegeven op de pagina's van het hoogste niveau, samen met het logo. U kunt de beschrijving van het PBIVIZ-pakket gebruiken.
    * *Lange beschrijving:* geef een gedetailleerde beschrijving van uw app op. Deze beschrijving wordt weergegeven voor klanten op de pagina met detailgegevens van uw app. Als u uw visuele element wilt laten verbeteren door de community door het visuele element open source te maken, geeft u hier de koppeling naar de openbare opslagplaats, zoals GitHub, op.

12. Upload ten minste één schermopname. De ondersteunde bestandsindelingen zijn PNG, JPG, JPEG en GIF. Het moet exact 1366 pixels breed en 768 pixels hoog zijn. Het bestand mag niet groter zijn dan 1024 kB. *Voeg tekstballonnen toe met meer informatie over de toegevoegde waarde van de belangrijkste functies die worden weergegeven in elke schermopname.*

12. Als u meer talen wilt toevoegen, selecteert u **Een taal toevoegen** en herhaalt u stap 10 en 11. Het toevoegen van meer talen helpt uw gebruikers om de details van het aangepaste visuele element weer te geven in hun eigen taal. Als de gebruiker een taal selecteert die u niet hebt toegevoegd, wordt standaard de taal gebruikt die u als eerste hebt toegevoegd.

13. Wanneer u klaar bent met het toevoegen van talen, selecteert u **Volgende** om door te gaan naar de pagina **Toegang blokkeren**.

14. Als u wilt voorkomen dat klanten in specifieke landen of regio's uw app kunnen gebruiken of kopen, schakelt u het selectievakje in en selecteert u de landen in de lijst.

15. Selecteer **Volgende** om door te gaan naar de pagina **Prijzen**.

16. Op dit moment worden alleen *gratis* visuele elementen ondersteund en zijn aanvullende aankopen binnen het visuele element (in-app aankopen) niet toegestaan. Selecteer **Deze app is gratis**.

    > [!NOTE]
    > Als u een andere optie dan gratis selecteert of als het element inhoud bevat voor een in-app aankoop, wordt de inzending geweigerd.

17. U kunt nu **Opslaan als concept** selecteren en de visual later indienen, of **Indienen voor goedkeuring** selecteren om de aangepaste visual in te dienen bij de Office-store.

## <a name="seller-dashboard-certification-submission-process"></a>Inzendingsproces voor certificering in Verkoperdashboard

Volg de instructies in deze sectie om een Power BI-visual in te dienen voor certificering in Verkoperdashboard. Gebruik deze methode als u eerder een Power BI-visual hebt verzonden naar AppSource met behulp van Verkoperdashboard.

1. Verzend een e-mailbericht naar het ondersteuningsteam voor Power BI-visuals (pbicvsupport@microsoft.com). Neem de volgende informatie op in het e-mailbericht:
    * Titel: Aanvraag voor certificering van visual
    * Koppeling naar de GitHub-opslagplaats waar de broncode van de door mensen leesbare broncode wordt gehost
    * [Voldoen aan de vereisten](power-bi-custom-visuals-certified.md#certification-requirements)
    * Voldoen aan de codebeoordeling

2. U krijgt bericht van het Microsoft-team voor Power BI-visuals wanneer uw Power BI-visual is gecertificeerd en toegevoegd aan de lijst met [gecertificeerde Power BI-visuals](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) of wanneer uw visual is geweigerd. In dat geval ontvangt u een rapport van de problemen die moeten worden verholpen. Het is de verantwoordelijkheid van de ontwikkelaar om contact te houden met Microsoft en hun gecertificeerde visuals waar nodig bij te werken.

## <a name="tracking-submission-status-and-usage"></a>Status en gebruik van de inzending bijhouden

U kunt de [validatiebeleidsregels](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals) controleren.

Na het indienen kunt u de status van uw inzending volgen in het [app-dashboard](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Het visuele element certificeren

Nadat de visual is gemaakt, kunt u deze desgewenst laten [certificeren](../developer/power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Volgende stappen

[Een aangepaste visual voor Power BI ontwikkelen](visuals/custom-visual-develop-tutorial.md)  
[Visualisaties in Power BI](../visuals/power-bi-report-visualizations.md)  
[Aangepaste visualisaties in Power BI](../developer/power-bi-custom-visuals.md)  
[Een Power BI-visual laten certificeren](../developer/power-bi-custom-visuals-certified.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
