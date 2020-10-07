---
title: Een rapport maken op een SharePoint-lijst
description: Deze zelfstudie laat zien hoe u uw SharePoint-lijstgegevens kunt transformeren naar een Power BI-rapport.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: f6bcd67d41f2c04cedd7c66eb5989f2a6919b030
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91598656"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Een rapport maken op een SharePoint-lijst

Veel teams en organisaties gebruiken lijsten in SharePoint Online om gegevens op te slaan, omdat deze eenvoudig kunnen worden ingesteld en gemakkelijk kunnen worden bijgewerkt.  Soms kunnen gebruikers veel eenvoudiger snel inzicht krijgen in de gegevens via een grafiek dan door de lijst zelf te bekijken. In deze zelfstudie laten we u zien hoe u uw SharePoint-lijstgegevens kunt transformeren naar een Power BI-rapport.

Bekijk deze zelfstudievideo van vijf minuten of schuif omlaag voor stapsgewijze instructies.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Deel 1: Verbinding maken met uw SharePoint-lijst

1. Als u er nog niet over beschikt, kunt u [Power BI Desktop](https://powerbi.microsoft.com/desktop/) downloaden en installeren.
2. Open Power BI Desktop en selecteer op het tabblad Start van het lint de optie **Gegevens ophalen** > **Meer**.
3. Selecteer **Online Services** en selecteer vervolgens **SharePoint Online-lijst**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="Screenshot shows the Get Data dialog box with Online Services selected." width="350"/>

4. Selecteer **Verbinding maken**.
4. Zoek het adres (ook wel een URL genoemd) van de SharePoint Online-site die uw lijst bevat.  U kunt vanaf een pagina in SharePoint Online het adres van de site doorgaans ophalen door **Start** te selecteren in het navigatiedeelvenster of het pictogram voor de site bovenaan. Vervolgens kopieert u het adres uit de adresbalk van uw webbrowser.

   Bekijk een video van deze stap:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. Plak in Power BI Desktop het adres in het veld **Site-URL** in het geopende dialoogvenster.

6. Het is mogelijk dat er geen SharePoint-toegangsscherm wordt weergegeven als in de volgende afbeelding.  Als het niet wordt weergegeven, gaat u verder met stap 10.  Als het wel wordt weergegeven, selecteert u **Microsoft-account** aan de linkerkant van de pagina.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Selecteer **Aanmelden** en voer de gebruikersnaam en het wachtwoord in die u gebruikt om u aan te melden bij Microsoft 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Wanneer u zich hebt aangemeld, selecteert u **Verbinding maken**.

9. Schakel aan de linkerkant van de Navigator het selectievakje in naast de SharePoint-lijst waarmee u verbinding wilt maken.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="Screenshot shows the Navigator page with BudgetRequests selected." width="450"/>

10. Selecteer **Laden**.  Power BI laadt uw lijstgegevens in een nieuw rapport.

## <a name="part-2-create-a-report"></a>Deel 2: Een rapport maken

1. Selecteer aan de linkerkant het pictogram **Gegevens** om te zien of uw SharePoint-lijstgegevens zijn geladen.

2. Zorg ervoor dat in de lijstkolommen met getallen het Som-of Sigma-pictogram wordt weergegeven in het deelvenster **Velden** aan de rechterkant.  Selecteer voor kolommen zonder pictogram de kolomkop in de tabelweergave, selecteer het tabblad **Model maken** en wijzig vervolgens het **gegevenstype** in **Decimaal getal** of **Geheel getal**, afhankelijk van de gegevens.  Als u wordt gevraagd om de wijziging te bevestigen, selecteert u **Ja**.  Als uw getal een speciale indeling heeft, zoals valuta, kunt u deze ook kiezen door de **notatie**in te stellen.

   Bekijk een video van deze stap:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. Selecteer aan de linkerkant het pictogram **Rapport**.
4. Selecteer de kolommen die u wilt visualiseren door in het deelvenster **Velden** aan de rechterkant het selectievakje ernaast in te schakelen.

   Bekijk een video van deze stap:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Wijzig zo nodig het visualtype.
6. U kunt meerdere visuals in hetzelfde rapport maken door de selectie van de bestaande visual op te heffen en vervolgens selectievakjes voor andere kolommen in te schakelen in het deelvenster **Velden**.
7. Selecteer **Opslaan** om uw rapport op te slaan.
