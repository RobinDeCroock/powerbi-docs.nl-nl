---
title: Verbinding maken met Microsoft Dynamics met Power BI
description: Microsoft Dynamics CRM voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 465e54c811691a7149dfff03d48bec797474ca66
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61190447"
---
# <a name="connect-to-microsoft-dynamics-crm-with-power-bi"></a>Verbinding maken met Microsoft Dynamics CRM met Power BI
Met Microsoft Dynamics CRM Online voor Power BI kunt u eenvoudig toegang krijgen tot uw gegevens en deze analyseren. Power BI maakt gebruik van de OData-feed voor het maken van een beschrijvend model, met alle benodigde entiteiten en metrische gegevens zoals Accounts, Activities, Opportunities, Product, Leads, Users en meer. Nadat u de app hebt geïnstalleerd, kunt u het dashboard en de rapporten bekijken in de Power BI-service ([https://powerbi.com](https://powerbi.com)) en in de mobiele Power BI-apps. 

Maak verbinding met Dynamics CRM Online [Sales Manager](https://msit.powerbi.com/groups/me/getdata/services/dynamics-crm-sales-manager) of [Service Manager](https://msit.powerbi.com/groups/me/getdata/services/dynamics-crm-customer-service). Lees meer over [de integratie van Dynamics CRM Online](https://powerbi.microsoft.com/integrations/microsoft-dynamicscrm) met Power BI.

Deze verbinding vereist **Microsoft Dynamics CRM Online 2016 of hoger**. Meer informatie over de [vereisten](#Requirements) leest u hieronder.

## <a name="how-to-connect"></a>Verbinding maken
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
3. Selecteer **Microsoft Dynamics CRM Sales Manager** of **Microsoft Dynamics CRM Service Manager** en klik op **Ophalen**.
   
   ![](media/service-connect-to-microsoft-dynamics-crm/connect.png)
4. Geef de service-URL op die is gekoppeld aan uw account.  De URL moet deze notatie hebben: `https://company.crm.dynamics.com`. Zie [hieronder](#FindingParams) voor meer details.
   
   ![](media/service-connect-to-microsoft-dynamics-crm/params.png)
5. Geef indien gewenst uw referenties op (deze stap kan worden overgeslagen als u al bent aangemeld in uw browser). Selecteer **oAuth2** voor de verificatiemethode en klik op **Aanmelden**:
   
   ![](media/service-connect-to-microsoft-dynamics-crm/creds.png)
6. Als de verbinding tot stand is gekomen, ziet u een dashboard dat is aangepast voor een verkoopmanager of servicemanager, gevuld met uw eigen gegevens:
   
   ![](media/service-connect-to-microsoft-dynamics-crm/dashboard.png)

## <a name="view-the-microsoft-dynamics-crm-dashboard-and-reports"></a>Dashboard en rapporten van Microsoft Dynamics CRM weergeven
[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-open-app.md)]

[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-what-now.md)]

## <a name="whats-included"></a>Wat is inbegrepen
De onderstaande secties bevatten informatie over welke gegevens worden opgenomen voor de rollen [Verkoopmanager](#Sales) en [Servicemanager](#Service).

Gegevens worden beperkt op basis van de beveiligingsrol die is toegewezen aan de Dynamics CRM Online-gebruiker.

Het dashboard en de rapporten zijn bedoeld om operationele rapportages te bieden voor kortetermijngegevens met de focus op een team of groep. Elke query wordt beperkt tot het ophalen van maximaal 100.000 records uit Dynamics CRM Online. Als deze limiet wordt overschreden vanwege de grote hoeveelheid gegevens in uw organisatie, mislukt het inrichten van het dashboard omdat het vernieuwen van gegevens van Dynamics CRM Online wordt beëindigd. Als uw account te groot is, kunt u verbinding maken via Power BI Desktop om een aangepaste oplossing te bouwen.

<a name="Sales"></a>

### <a name="sales-manager"></a>Verkoopmanager
Het dashboard en de rapporten bevatten de belangrijkste metrische gegevens zoals:  

* Won Revenue   
* Win Rate   
* Open Revenue   
* Lost revenue   
* Expected Revenue  
* Average Deal Size en meer.  

Ze bevatten ook belangrijke diagrammen, zoals:  

* Won and Lost Revenue Trend, Won Revenue Vs Estimated Revenue Trend  
* Won Revenue voor verschillende dimensies zoals Industry, Region, Territory   
* Sales Leaders By Revenue, Activities,   
* Top Accounts, Top Won/Lost Deals,    
* New Leads Trend, Sales Pipeline en meer.   

Deze metrische gegevens en diagrammen helpen om inzicht te krijgen in de prestaties van uw verkooporganisatie en maken het mogelijk om de verkooppijplijn binnen het verkoopteam te analyseren.

De volgende tabel bevat de CRM-entiteiten die beschikbaar zijn voor deze service en geeft ook informatie over de filters die zijn toegepast op elk van de entiteitsrecords.

| CRM-entiteit | Toegepaste filters |
| --- | --- |
| Account |Alle accounts met gerelateerde verkoopkansen die mogelijk zijn gewijzigd in de afgelopen 365 dagen. |
| Activiteit |Alle activiteiten die zijn gewijzigd in de afgelopen 90 dagen <br> [modifiedon] > today - 90 days |
| Business Unit |Alle business units die niet zijn uitgeschakeld <br> [isdisabled] = false |
| Lead |Alle leads die zijn gewijzigd in de afgelopen 180 dagen <br> [modifiedon] > today - 180 days |
| Opportunity |Alle verkoopkansen die zijn gewijzigd in de afgelopen 365 dagen <br> [modifiedon] > today - 365 days |
| Opportunity Product |Alle verkoopkansproducten die zijn gewijzigd in de afgelopen 365 dagen <br> [modifiedon] > today - 365 days |
| Product |Alle actieve producten <br> [statecode] <> 1 |
| Territory |Alle gebieden |
| User |Alle actieve gebruikers en niet-gedelegeerde beheerders <br>  [isdisabled] = false and [accessmode] <> 4 |

<a name="Service"></a>

### <a name="service-manager"></a>Servicemanager
Dit dashboard en deze rapporten bevatten belangrijke metrische gegevens zoals:  

* CSAT Percentage   
* SLA Met percentage   
* Escalated Cases Percentage   
* Average Handling Time   
* Total Resolved Cases  
* Total Active Cases  
* Number of Times KB Article Used in cases en meer.    

Ze bevatten ook belangrijke diagrammen, zoals:   

* Case Volume Trends voor Incoming Cases, Resolved Cases, Escalated Cases   
* Case Volume voor verschillende dimensies zoals Origin, Location, Priority, Type  
* Leaders by CSAT percentage, SLA met percentage, Activities, Resolved cases  
* Most Used en Most viewed KB Articles en meer.  
    Deze metrische gegevens en grafieken kunnen inzicht geven in de prestaties van uw ondersteuningsorganisatie en helpen bij het analyseren van actieve dossiers binnen het serviceteam en in de servicewachtrijen.

De volgende tabel bevat de CRM-entiteiten die beschikbaar zijn voor deze service en geeft ook informatie over de filters die zijn toegepast op elk van de entiteitsrecords.

| CRM-entiteit | Toegepaste filters |
| --- | --- |
| Account |Alle accounts met gerelateerde dossiers die mogelijk zijn gewijzigd in de afgelopen 90 dagen |
| Activity |Alle activiteiten die zijn gewijzigd in de afgelopen 90 dagen <br> [modifiedon] > today - 90 days |
| Case |Alle dossiers die zijn gewijzigd in de afgelopen 90 dagen <br> [modifiedon] > today - 90 days |
| Case Resolution Activity |Alle activiteiten voor dossieroplossing die zijn gewijzigd in de afgelopen 90 dagen <br> [modifiedon] > today - 90 days |
| Contact |Alle contactpersonen met gerelateerde dossiers die mogelijk zijn gewijzigd in de afgelopen 90 dagen. |
| Knowledge Article |Alle nieuwste versies van Knowledge Base-artikelen  <br> [islatestversion] = true |
| Knowledge Article Incident |Alle incidenten in Knowledge Base-artikelen die zijn gewijzigd in de afgelopen 90 dagen <br> [modifiedon] > today - 90 days |
| Queue |Alle actieve wachtrijen  <br> [statecode] = 0 |
| Queue Item |Alle dossiergerelateerde wachtrij-items die zijn gemaakt in de afgelopen 365 dagen  <br> [createdon] > today - 365 days and <br> [objecttypecode] = 112 |
| User |Alle actieve gebruikers <br>  [isdisabled] = false |

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systeemvereisten
* Een geldige versie van Dynamics CRM Online 2016 of hoger (Power BI werkt niet met een on-premises CRM-versie). Als u niet beschikt over 2016 of hoger:
* Een beheerder moet het OData-eindpunt in de site-instellingen inschakelen.
* Een account met minder dan 100.000 records in een van de tabellen. Als het account toegang heeft tot meer dan 100.000 records, mislukt het importeren.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
Het adres van het exemplaar kunt u vinden in de URL-balk van uw browser. Het adres heeft meestal deze indeling: `https://[instance_name].crm.dynamics.com`.

Power BI ondersteunt alleen eindpunten van Dynamics CRM 2016. De verbinding werkt niet met eerdere versies van CRM Online. Gebruik Power BI Desktop om rechtstreeks verbinding te maken met uw account.

## <a name="troubleshooting"></a>Problemen oplossen
Controleer het volgende als er problemen zijn met de verbinding:  

* u gebruikt de juiste URL (neem contact op met de beheerder)  
* het exemplaar is CRM Online 2016  
* het OData-eindpunt is ingeschakeld  

Probeer ook rechtstreeks in Power BI Desktop verbinding te maken, met behulp van de URL voor OData: `https://[instance_name].crm.dynamics.com/api/data/v8.0/`.

Als u inderdaad Dynamics CRM Online 2016 hebt, maar het nog steeds niet lukt om verbinding te maken, neemt u contact op met uw CRM-beheerder om te controleren of alle beschikbare updates zijn geïnstalleerd.

Als u niet beschikt over CRM Online 2016 of hoger, gebruikt u Power BI Desktop om rechtstreeks verbinding te maken met uw account.

Als u een fout ziet met de melding dat het vernieuwen van gegevens is mislukt omdat de query de maximumlimiet van 100000 records heeft overschreden, kunt u overwegen om rechtstreeks vanuit Power BI Desktop verbinding te maken of om de oplossingssjabloon voor CRM te gebruiken.

## <a name="next-steps"></a>Volgende stappen
* [Wat zijn apps in Power BI?](service-create-distribute-apps.md)
* [Gegevens ophalen in Power BI](service-get-data.md)
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

