---
title: 'Voorbeeld van human resources: Rondleiding volgen'
description: 'Voorbeeld van human resources voor Power BI: Rondleiding volgen'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 4b36c02abe0ca0bbd2d117559855a69edff370db
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61233768"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Voorbeeld van human resources voor Power BI: Rondleiding volgen

## <a name="overview-of-the-human-resources-sample"></a>Overzicht van het voorbeeld van Human Resources
De HR-afdeling hanteert hetzelfde rapportagemodel voor verschillende bedrijven, zelfs wanneer deze verschillen qua branche of omvang. In dit voorbeeld kijken we naar nieuwe medewerkers, actieve medewerkers en medewerkers die niet meer in dienst zijn en proberen we trends te ontdekken in de strategie voor het aannemen van personeel. Dit zijn de belangrijkste doelstellingen die we beter willen begrijpen:

* Wie nemen we aan
* Vooroordelen in onze strategie voor het aannemen van personeel
* Trends in het vrijwillig ontslag nemen

![](media/sample-human-resources/hr1.png)

Dit voorbeeld is onderdeel van een serie die laat zien hoe u Power BI kunt gebruiken met bedrijfsgegevens, rapporten en dashboards. Dit zijn echte gegevens die afkomstig zijn van obviEnce ([www.obvience.com)](http://www.obvience.com/) die zijn geanonimiseerd. De gegevens zijn beschikbaar in verschillende indelingen: inhoudspakket/-app, Excel-werkmap of een .pbix-bestand van Power BI Desktop. Bekijk [Voorbeelden van gegevenssets](sample-datasets.md) voor meer informatie.

## <a name="prerequisites"></a>Vereisten

 Voordat u het voorbeeld kunt gebruiken, moet u het eerst downloaden als een [inhoudspakket](https://docs.microsoft.com/power-bi/sample-human-resources#get-the-content-pack-for-this-sample), een [PBIX-bestand](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) of een [Excel-werkmap](http://go.microsoft.com/fwlink/?LinkId=529780).

### <a name="get-the-content-pack-for-this-sample"></a>Het inhoudspakket voor dit voorbeeld ophalen

1. Open Power BI-service (app.powerbi.com) en meld u aan.
2. Selecteer in de linkerbendehoek **Gegevens ophalen**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Selecteer op de pagina Gegevens ophalen het pictogram **Voorbeelden**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Selecteer het **voorbeeld van Human Resources** en kies vervolgens **Verbinding maken**.  
   
   ![Gegevens ophalen](media/sample-human-resources/pbi_hr_sample_connect.png)
5. Het inhoudspakket wordt geïmporteerd in Power BI en er wordt een nieuw dashboard, nieuw rapport en een nieuwe gegevensset toegevoegd aan de huidige werkruimte. De nieuwe inhoud is gemarkeerd met een geel sterretje. 
   
   ![Sterretje](media/sample-human-resources/human-resources-sample-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Het pbix-bestand voor dit voorbeeld ophalen

U kunt ook het voorbeeld downloaden als pbix-bestand, dat bedoeld is voor gebruik met Power BI Desktop. 

 * [PBIX-voorbeeld van Human resources](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>De Excel-werkmap ophalen voor dit voorbeeld
U kunt ook [alleen de gegevensset (Excel-werkmap)](http://go.microsoft.com/fwlink/?LinkId=529780) voor dit voorbeeld downloaden. De werkmap bevat Power View-werkbladen die u kunt bekijken en wijzigen. Als u de onbewerkte gegevens wilt bekijken, selecteert u **Power Pivot > Beheren**.

## <a name="new-hires"></a>Nieuwe medewerkers
Laten we eerst eens kijken naar de gegevens van nieuwe medewerkers.

1. Selecteer in uw werkruimte het tabblad **Dashboards** en open het dashboard Human Resources.
2. Selecteer in het dashboard de tegel **New Hire Count, New Hires SPLY en Actives YoY % Change** **by Month**.  
   ![](media/sample-human-resources/hr2.png)  

   De pagina **New Hires** van het voorbeeldrapport Human Resources wordt geopend.  

   ![](media/sample-human-resources/hr3.png)

Enkele zaken die opvallen:

* De combinatiegrafiek **New Hire Count, New Hires SPLY en Actives YoY % Change per Month** toont aan dat we dit jaar elke maand meer mensen hebben aangenomen dan vorig jaar, waarbij het in sommige maanden om aanzienlijk meer mensen gaat.
* In de combinatiegrafiek **New Hire Count en Active Employee Count per Region en Ethnicity** valt op dat we minder nieuwe mensen aannemen in de regio **East**.
* De watervalgrafiek **New Hires YoY Var per Age Group** laat zien dat we voornamelijk jongere mensen in dienst nemen. De reden hiervoor kan zijn dat het hoofdzakelijk om part-time banen gaat.
* De cirkelgrafiek **New Hire Count per Gender** toont een redelijk gelijkmatige verdeling.

Kunt u nog meer inzichten vinden; bijvoorbeeld een regio waar de verdeling tussen mannen en vrouwen sterk afwijkt? Selecteer verschillende leeftijdsgroepen en geslachten in de grafieken om de relaties tussen leeftijd, geslacht, regio en etniciteit te verkennen.

Selecteer de naam van het dashboard in de bovenste navigatiebalk om terug te keren naar het dashboard.

![](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-current-active-and-former-employees"></a>Actieve en voormalige medewerkers vergelijken
Laten we eens kijken naar gegevens van de huidige medewerkers en medewerkers die niet langer voor het bedrijf werken.

Selecteer op het dashboard de tegel **Active Employee Count by Age Group**.  
![](media/sample-human-resources/pbi_hr_sample_activepie.png)

Het voorbeeldrapport van Human Resources wordt geopend op de pagina **Active Employees vs. Separations**.  
![](media/sample-human-resources/hr5.png)

**Aandachtspunten**:

* De combinatiegrafieken aan de linkerkant tonen de jaar-tot-jaarwijzigingen voor actieve medewerkers en vrijwillig vertrokken medewerkers. We hebben dit jaar meer actieve medewerkers door snelle inhuur, maar ook meer medewerkers die de organisatie hebben verlaten.
* In augustus zijn er meer mensen vertrokken dan in andere maanden. Selecteer de verschillende leeftijdsgroepen, geslachten of regio's om te zien of u uitbijters kunt vinden.
* Als we naar de cirkeldiagrammen kijken, valt op dat de verdeling van actieve medewerkers naar geslacht en leeftijdsgroep tamelijk gelijkmatig is. Selecteer verschillende leeftijdsgroepen om te zien of de verdeling naar geslacht verschillen oplevert in leeftijd. Hebben we binnen elke leeftijdsgroep een evenredige verdeling naar geslacht?

## <a name="reasons-for-separation"></a>Redenen voor ontslag
Laten we het rapport eens bekijken in de bewerkingsweergave. Selecteer **Rapport bewerken** in de linkerbovenhoek.

Wijzig de cirkeldiagrammen zodat deze gegevens van vertrokken medewerkers (Separates) in plaats van actieve medewerkers (Actives) aangeven.

1. Selecteer het cirkeldiagram **Active Employee Count per Age Group**.
2. Selecteer bij **Velden** aan de rechterkant de pijl naast **Employees** om de tabel met medewerkers uit te vouwen. Schakel het selectievakje naast **Active Employee Count** uit om dat veld te verwijderen.
3. Schakel het selectievakje naast **Separation Count** in de tabel Employees in om dat veld toe te voegen aan het vak **Waarden**.
4. Ga terug naar het rapportcanvas en selecteer de staaf **Voluntary** in het staafdiagram **Separation Count per Separation Reason**. In de andere visualisaties in het rapport worden nu de gegevens gemarkeerd voor medewerkers die vrijwillig zijn vertrokken.
5. Klik op het cirkelsegment 50+ van het cirkeldiagram Separation Count per Age Group.

   Kijk naar het lijndiagram Separations per Reason in de rechterbenedenhoek. Dit diagram is gefilterd op alleen vrijwillig vertrokken medewerkers.  
   ![](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Ziet u de trend in de leeftijdsgroep 50+? Tijdens het laatste gedeelte van het jaar vertrekken meer medewerkers ouder dan 50 op vrijwillige basis de organisatie. Dit zou een gebied zijn om met meer gegevens te onderzoeken.
6. U kunt dezelfde stappen ook uitvoeren voor het cirkeldiagram **Active Employee Count per Gender** en hier het aantal vertrokken medewerkers weergeven in plaats van actieve medewerkers. Bekijk de gegevens van vrijwillig vertrokken medewerkers onderverdeeld naar geslacht om te zien of dat andere inzichten oplevert.
7. Klik op **Power BI** in de bovenste navigatiebalk om terug te keren naar het dashboard. U kunt de wijzigingen die u hebt aangebracht in het rapport al dan niet opslaan.

## <a name="bad-hires"></a>Kortstondige medewerkers
Het laatste gebied dat we gaan onderzoeken zijn kortstondige medewerkers. Dit zijn medewerkers die niet meer dan 60 dagen in dienst zijn geweest. We nemen snel mensen aan. Maar nemen we wel de juiste kandidaten in dienst?

1. Selecteer de tegel **Bad Hires as % of Actives by Age Group** in het dashboard. Hiermee opent u het rapport op pagina 3, 'Bad Hires'.

   ![](media/sample-human-resources/hr7.png)  
2. Schakel het selectievakje **Northwest** in de regiokiezer aan de linkerkant in en het segment **Male** in het ringdiagram Bad Hire Count per Gender.  Bekijk de andere grafieken op de pagina 'Bad Hires'. U ziet dat er meer mannen dan vrouwen heel snel zijn vertrokken en dat er veel kortstondige medewerkers uit groep A afkomstig zijn.
   ![](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  
3. Als we naar het ringdiagram **Bad Hire Count by Gender** kijken en de regio's in de slicer **Region** doorlopen, zien we dat East de enige regio is waarin meer vrouwen dan mannen het bedrijf snel hebben verlaten.  
4. Selecteer de naam van het dashboard in de bovenste navigatiebalk om terug te keren naar het dashboard.

## <a name="asking-a-question-in-the-qa-box"></a>Een vraag stellen in het vak Q&A
Het [Q&A-vraagvak](power-bi-tutorial-q-and-a.md) is de plek waar u een vraag kunt stellen in natuurlijke taal, maar alleen in het Engels. Q&A herkent de woorden die u typt, en zoekt uit waar in de gegevensset het antwoord kan worden gevonden.

1. Klik in het Q&A-vraagvak. U ziet dat het vak direct al suggesties bevat, zelfs voordat u begint te typen:

   ![](media/sample-human-resources/pbi_hr_sample_qabox.png)
2. Kies een van deze suggesties of typ: **show age group, gender and bad hires SPLY where region is east**.  

   ![](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   U ziet dat de meeste kortstondige medewerkers vrouwen zijn jonger dan 30.

Dit is een veilige omgeving om wat dingen uit te proberen. U kunt er namelijk altijd voor kiezen de wijzigingen niet op te slaan. Als u ze wel opslaat, kunt u altijd via **Gegevens ophalen** een nieuwe kopie van dit voorbeeld downloaden.

## <a name="next-steps-connect-to-your-data"></a>Volgende stappen: Verbinding maken met uw gegevens
We hopen dat deze rondleiding heeft laten zien hoe Power BI-dashboards, Q&A en rapporten inzicht kunnen geven in gegevens van de HR-afdeling. Nu is het uw beurt om verbinding met uw eigen gegevens te maken. Met Power BI kunt u verbinding maken met een groot aantal gegevensbronnen. Zie [Aan de slag met Power BI](service-get-started.md) voor meer informatie.  
