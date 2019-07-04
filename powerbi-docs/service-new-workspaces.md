---
title: Werk organiseren in de nieuwe werkruimten - Power BI
description: Lees hier alles over de nieuwe werkruimten, die bestaan uit verzamelingen dashboards en rapporten die zijn gemaakt om belangrijke statistieken over uw organisatie te bieden.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 419cd2137b8924f153009843d6f60db594219059
ms.sourcegitcommit: a42c6758aa255c21ece6366a3257b0dd82f3606b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67345548"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Werk organiseren in de nieuwe werkruimten in Power BI

 *Werkruimten* zijn plekken waar u met collega’s kunt samenwerken om verzamelingen dashboards, rapporten en gepagineerde rapporten te maken. De nieuwe werkruimte-ervaring helpt om de toegang tot inhoud beter te beheren. Dit artikel beschrijft de nieuwe werkruimten, en hoe deze verschillen van de klassieke werkruimten.  Net als de klassieke werkruimten gebruikt u de nieuwe werkruimten ook om apps te maken en distribueren. Lees meer over het [maken van een nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md).

De nieuwe werkruimte-ervaring is algemeen beschikbaar (GA) en is nu dan ook de standaardwerkruimte. U kunt nog steeds [klassieke werkruimten](service-create-workspaces.md) op basis van Office 365-groepen maken en gebruiken. 

> [!NOTE]
> Als u beveiliging op rijniveau (RLS) wilt afdwingen voor gebruikers die inhoud in een werkruimte bekijken, gebruikt u de rol Lezer. Als de rol Lezer nog niet beschikbaar is in uw tenant, blijft u de [klassieke werkruimten](service-create-workspaces.md) gebruiken en selecteert u de optie **Leden kunnen alleen Power BI-inhoud weergeven** optie. U kunt een Power BI-app ook publiceren naar die gebruikers of delen gebruiken om inhoud te distribueren.

Met de nieuwe werkruimten kunt u het volgende doen:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Office 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een Office 365-groep te maken.
- Gedetailleerdere werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.
- De Power BI-beheerder kan bepalen wie werkruimten kan maken in Power BI.

Wanneer u een van de nieuwe werkruimten maakt, maakt u geen onderliggende, gekoppelde Office 365-groep. Alle werkruimtebeheer vindt plaats in Power BI, niet in Office 365. In de nieuwe werkruimte-ervaring kunt u een Office 365-groep toevoegen aan de lijst met werkruimtetoegang om gebruikerstoegang tot inhoud te blijven beheren via Office 365-groepen.

## <a name="administering-new-workspace-experience-workspaces"></a>Werkruimten beheren in nieuwe werkruimte-ervaring
Het beheer van werkruimten uit de nieuwe werkruimte-ervaring verloopt nu via Power BI. Beheerders van Power BI besluiten wie in een organisatie werkruimten kan maken. Ze kunnen ook werkruimten beheren en herstellen. Hiervoor moeten ze de Power BI-beheerportal of de PowerShell-cmdlets gebruiken. Voor klassieke werkruimten die zijn gebaseerd op Office 365-groepen, blijft het beheer geconcentreerd in de Office 365-beheerportal en Azure Active Directory.

In **Instellingen voor werkruimte** in de beheerportal kunnen beheerders met de instelling Werkruimten maken (nieuwe werkruimte-ervaring) iedereen of niemand in een organisatie toestaan om werkruimten in de nieuwe werkruimte-ervaring te maken. Ze kunnen het maken van werkruimten ook beperken tot leden van specifieke beveiligingsgroepen.

> [!NOTE]
> Met de instelling Werkruimten maken (nieuwe werkruimte-ervaring) kunnen alleen gebruikers die Office 365-groepen kunnen maken, nieuwe werkruimten maken in Power BI. Zorg ervoor dat u in de Power BI-beheerportal een waarde instelt om ervoor te zorgen dat de juiste gebruikers nieuwe werkruimten kunnen maken in de nieuwe werkruimte-ervaring.

![Werkruimte-instellingen in de beheerportal](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

De [lijst met werkruimten is beschikbaar](service-admin-portal.md#workspaces) in de Power BI-beheerportal. 

![Lijst met werkruimten](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nieuwe werkruimten naast klassieke werkruimten

Nieuwe, bijgewerkte werkruimten en bestaande, klassieke werkruimten kunnen naast elkaar worden gebruikt en u kunt beide typen werkruimten maken. De nieuwe werkruimte-ervaring is het standaardtype werkruimte. In Power BI worden alle Office 365-groepen waarvan de gebruiker lid is in Power BI nog steeds vermeld om te voorkomen dat bestaande werkstromen worden gewijzigd. Als u wilt weten hoe u een nieuwe werkruimte maken, leest u [Nieuwe werkruimten maken](service-create-the-new-workspaces.md). Als u wilt weten hoe u een klassieke werkruimte kunt maken, leest u [Klassieke maken](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Rollen in de nieuwe werkruimten

Als u toegang wilt te verlenen tot een nieuwe werkruimte, voegt u groepen met gebruikers of individuele gebruikers toe aan een van de werkruimterollen: lezers, leden, inzenders of beheerders. Iedereen in een gebruikersgroep krijgt de rol die u hebt gedefinieerd. Als iemand deel uitmaakt van verschillende gebruikersgroepen, krijgt hij of zij het hoogste machtigingsniveau dat aan de toegewezen rollen is toegewezen.

U kunt met rollen bepalen wie wat kan doen in een werkruimte, zodat teams kunnen samenwerken. U kunt met nieuwe werkruimten rollen toewijzen aan personen en aan gebruikersgroepen: beveiligingsgroepen, Office 365-groepen en distributielijsten. 

Wanneer u rollen aan een gebruikersgroep toewijst, hebben de personen in de groep toegang tot de inhoud. Als u gebruikersgroepen nest, zijn alle ingesloten gebruikers gemachtigd. Aan een gebruiker die zich in verschillende gebruikersgroepen met verschillende rollen bevindt, wordt de machtiging met de meeste rechten toegewezen. 

De nieuwe werkruimte-ervaring biedt vier rollen: beheerders, leden, inzenders en lezers.

|Mogelijkheid   | Beheerder  | Lid  | Inzender  | Lezer |
|---|---|---|---|---|
| De werkruimte bijwerken en verwijderen.  | X  |   |   |   | 
| Personen, met inbegrip van andere beheerders, toevoegen/verwijderen.  | X  |   |   |   |
| Leden of anderen met minder machtigingen toevoegen.  |  X | X  |   |   |
| Apps publiceren en bijwerken. |  X | X  |   |   |
| Items en apps delen. |  X | X  |   |   |
| Anderen toestaan items opnieuw te delen. |  X | X  |   |   |
| Inhoud in de werkruimte maken, bewerken en verwijderen.  |  X | X  | X  |   |
| Rapporten publiceren naar de werkruimte, inhoud verwijderen.  |  X | X  | X  |   |
| Een item weergeven. |  X | X  | X  | X  |
 
 
## <a name="licensing"></a>Licentieverlening
Iedereen die u toevoegt aan een werkruimte in de gedeelde capaciteit, heeft een Power BI Pro-licentie nodig. Deze gebruikers kunnen in de werkruimte samenwerken aan dashboards en rapporten die u wilt publiceren naar een breder publiek of zelfs uw hele organisatie. 

Als u inhoud naar anderen binnen uw organisatie wilt distribueren, kunt u Power BI Pro-licenties toewijzen aan die gebruikers of de werkruimte in een Power BI Premium-capaciteit plaatsen.

Wanneer de werkruimte zich in een Power BI Premium-capaciteit bevindt, hebben gebruikers met de rol Lezer toegang tot de werkruimte, zelfs als ze geen Power BI Pro-licentie hebben. Als u echter een hogere rol toewijst aan deze gebruikers, zoals Beheerder, Lid of Inzender, hebben ze geen toegang tot de werkruimte. Ze worden dan gevraagd om een proefversie van Power BI Pro te starten wanneer ze proberen toegang te krijgen tot de werkruimte. Als u de mogelijkheden van de rol Lezer wilt benutten voor gebruikers zonder Pro-licentie, zorgt u ervoor dat de gebruikers met de rol Lezer geen andere rol in de werkruimte hebben, niet als individuele gebruiker en niet als onderdeel van een groep. 

> [!NOTE]
> Bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring gelden strengere normen voor het afdwingen van bestaande licentieregels. Gebruikers zonder een Pro-licentie die proberen te publiceren vanuit Power BI Desktop of andere clienthulpprogramma's, krijgen de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Hoe verschillen de nieuwe werkruimten van de huidige werkruimten?

Voor de nieuwe werkruimten worden enkele functies anders ontworpen. Dit zijn de wijzigingen die naar alle waarschijnlijkheid definitief zullen worden doorgevoerd. 

* Door het maken van deze werkruimten worden er niet automatisch ook Office 365-groepen gemaakt, zoals bij klassieke werkruimten. U kunt nu echter een Office 365-groep gebruiken om gebruikers toegang tot uw werkruimte te geven door een rol toe te wijzen. 
* In klassieke werkruimten kunt u alleen individuen toevoegen aan de lijsten met leden en beheerders. In de nieuwe werkruimten kunt u meerdere AD-beveiligingsgroepen, distributielijsten of Office 365-groepen toevoegen aan deze lijsten om het beheer van gebruikers eenvoudiger te maken. 
- U kunt een organisatie-inhoudspakket maken op basis van een klassieke werkruimte. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten maken.
- U kunt een organisatie-inhoudspakket uit een klassieke werkruimte gebruiken. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten gebruiken.

## <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte
De nieuwe functie **Lijst met contactpersonen** maakt het mogelijk om op te geven welke gebruikers meldingen moeten ontvangen over problemen die optreden in de werkruimte. De standaardinstelling is dat elke gebruiker of groep die is ingesteld als een beheerder van de werkruimte een melding krijgt, maar u kunt de lijst aanpassen. Gebruikers of groepen die in de lijst met contactpersonen staan, worden weergegeven in de gebruikersinterface (UI) zodat gebruikers hulp kunnen krijgen met betrekking tot de werkruimte. 

Lees hier meer over het [instellen van de lijst met contactpersonen voor een werkruimte](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Werkruimte op OneDrive
Met de functie Werkruimte op OneDrive kunt u een Office 365-groep configureren waarvan de bestandsopslag uit de SharePoint-documentbibliotheek beschikbaar voor werkruimtegebruikers. De groep moet buiten Power BI worden gemaakt. 

Power BI biedt geen synchronisatie voor machtigingen van gebruikers of groepen die zijn geconfigureerd voor werkruimtetoegang met behulp van het lidmaatschap van een Office 365-groep. De aanbevolen procedure is om werkruimtetoegang te beheren via dezelfde Office 365-groep waarvan u de bestandsopslag configureert in deze instelling. 

Lees meer over hoe u [Werkruimte op OneDrive](service-create-the-new-workspaces.md#workspace-onedrive) instelt en gebruikt.  
   
## <a name="auditing"></a>Controle
De volgende activiteiten worden gecontroleerd door Power BI voor werkruimten van de nieuwe werkruimte-ervaring.

| Beschrijvende naam |   Naam van bewerking |
|---|---|
| Power BI-map gemaakt | CreateFolder |
| Power BI-map verwijderd | DeleteFolder |
| Power BI-map bijgewerkt | UpdateFolder |
| Toegang tot Power BI-map bijgewerkt| UpdateFolderAccess |

Lees meer over de [controle door Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Houd rekening met de volgende beperkingen:

- Werkruimten kunnen maximaal 1000 gegevenssets of 1000 rapporten per gegevensset bevatten. 
- Een gebruiker met een Power BI Pro-licentie kan lid zijn van maximaal 1.000 werkruimten.
- De functie van Power BI om te publiceren naar Excel wordt niet ondersteund.

## <a name="workspace-features-that-work-differently"></a>Functies van de werkruimten die anders werken

Sommige functies werken in de nieuwe werkruimten anders dan in de huidige werkruimten. Deze verschillen zijn doorgevoerd op basis van feedback die we van klanten hebben ontvangen en maken een flexibelere benadering voor de samenwerking met werkruimten mogelijk:

- Afdwingen van licenties: bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring worden regels van bestaande licenties afgedwongen die een licentie voor Power BI Pro vereisen voor gebruikers die samenwerken in werkruimten of die inhoud met anderen delen in de Power BI-service. Gebruikers zonder een Pro-licentie zien de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.
- Leden kunnen wel of niet opnieuw delen: vervangen door de rol Inzender
- Alleen-lezenwerkruimten: in plaats van dat u gebruikers alleen-lezentoegang geeft tot een werkruimte, wijst u de rol Lezer toe aan gebruikers. Hiermee krijgen ze vergelijkbare alleen-lezentoegang tot de inhoud in een werkruimte.
- Gebruikers zonder een Pro-licentie hebben toegang tot de werkruimte als deze zich in een Power BI Premium-capaciteit bevindt, zelfs als gebruikers alleen de rol Lezer hebben.
- Als u wilt toestaan dat gebruikers met de rol Lezer gegevens mogen exporteren, zorgt u ervoor dat ze de machtiging Build hebben voor de gegevenssets in de werkruimte.
- Geen knop **Werkruimte verlaten**.

## <a name="frequently-asked-questions"></a>Veelgestelde vragen

**Heeft de algemene beschikbaarheid van de nieuwe werkruimte-ervaring gevolgen voor koppelingen naar bestaande inhoud?**

Nee. Koppelingen naar bestaande items in klassieke werkruimten worden niet beïnvloed door de nieuwe werkruimte-ervaring. De algemene beschikbaarheid (GA) van de nieuwe werkruimte-ervaring heeft gevolgen voor de standaardwerkruimte die u maakt, maar bestaande werkruimten blijven ongewijzigd. 

**Worden bestaande werkruimten bijgewerkt naar de nieuwe werkruimte-ervaring bij algemene beschikbaarheid?**

Nee. De algemene beschikbaarheid zorgt er alleen voor dat het type van de standaardwerkruimte wordt gewijzigd in de nieuwe werkruimte-ervaring. Bestaande klassieke werkruimten die zijn gebaseerd op Office 365-groepen blijven ongewijzigd.

**Worden er nog steeds automatisch werkruimten gemaakt voor Office 365-groepen?**

Ja. Aangezien we beide typen werkruimten naast elkaar ondersteunen, blijven we in de lijst met werkruimten alle Office 365-groepen weergeven waartoe de gebruiker toegang heeft.

## <a name="next-steps"></a>Volgende stappen
* [De nieuwe werkruimten maken in Power BI](service-create-the-new-workspaces.md)
* [De klassieke werkruimten maken](service-create-workspaces.md)
* [Apps in Power BI installeren en gebruiken](service-create-distribute-apps.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
