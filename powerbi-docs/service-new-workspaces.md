---
title: Werk organiseren in de nieuwe werkruimten in Power BI
description: Lees hier alles over de nieuwe werkruimten, die bestaan uit verzamelingen dashboards en rapporten die zijn gemaakt om belangrijke statistieken over uw organisatie te bieden.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/12/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 976d53a5a74bc077d3d4642ccec336b1225344ae
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2020
ms.locfileid: "77426559"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Werk organiseren in de nieuwe werkruimten in Power BI

 *Werkruimten* zijn plekken waar u met collega’s kunt samenwerken om verzamelingen dashboards, rapporten en gepagineerde rapporten te maken. De nieuwe werkruimte-ervaring helpt om de toegang tot inhoud beter te beheren. Dit artikel beschrijft de nieuwe werkruimten, en hoe deze verschillen van de klassieke werkruimten.  Net als de klassieke werkruimten gebruikt u de nieuwe werkruimten ook om apps te maken en distribueren. Lees meer over het [maken van een nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md).

De nieuwe werkruimte-ervaring is algemeen beschikbaar (GA) en is nu dan ook de standaardwerkruimte. U kunt nog steeds [klassieke werkruimten](service-create-workspaces.md) op basis van Office 365-groepen maken en gebruiken. 

> [!NOTE]
> Als u beveiliging op rijniveau (RLS) wilt afdwingen voor gebruikers die inhoud in een werkruimte bekijken, gebruikt u de rol Lezer. Als u beveiliging op rijniveau wilt afdwingen zonder toegang tot de werkruimte te geven, publiceert u een Power BI-app naar die gebruikers of gebruikt u delen om inhoud te distribueren.

Met de nieuwe werkruimten kunt u het volgende doen:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Office 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een Office 365-groep te maken.
- Meer gedetailleerde werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.
- De Power BI-beheerder kan bepalen wie werkruimten kan maken in Power BI.

Wanneer u een van de nieuwe werkruimten maakt, maakt u geen onderliggende, gekoppelde Office 365-groep. Alle werkruimtebeheer vindt plaats in Power BI, niet in Office 365. In de nieuwe werkruimte-ervaring kunt u een Office 365-groep toevoegen aan de lijst met werkruimtetoegang om gebruikerstoegang tot inhoud te blijven beheren via Office 365-groepen.

## <a name="administering-new-workspace-experience-workspaces"></a>Werkruimten beheren in nieuwe werkruimte-ervaring
Het beheer van werkruimten uit de nieuwe werkruimte-ervaring verloopt nu via Power BI. Beheerders van Power BI besluiten wie in een organisatie werkruimten kan maken. Ze kunnen ook werkruimten beheren en herstellen met behulp van de Power BI-beheerportal of PowerShell-cmdlets. Voor klassieke werkruimten die zijn gebaseerd op Office 365-groepen, blijft het beheer geconcentreerd in de Office 365-beheerportal en Azure Active Directory.

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

Wanneer u rollen aan een gebruikersgroep toewijst, hebben de personen in de groep toegang tot de inhoud. Als u gebruikersgroepen nest, zijn alle ingesloten gebruikers gemachtigd.

De functies van de vier rollen zijn: beheerders, leden, inzenders en lezers. Al deze mogelijkheden, met uitzondering van bekijken en ermee werken, vereisen een Power BI Pro-licentie.

|Mogelijkheid   | Beheerder  | Lid  | Inzender  | Lezer |
|---|---|---|---|---|
| De werkruimte bijwerken en verwijderen.  | X  |   |   |   | 
| Personen, met inbegrip van andere beheerders, toevoegen/verwijderen.  | X  |   |   |   |
| Leden of anderen met minder machtigingen toevoegen.  |  X | X  |   |   |
| Apps publiceren en bijwerken. |  X | X  |   |   |
| Items en apps delen.<sup>1</sup> |  X | X  |   |   |
| Anderen toestaan items opnieuw te delen.<sup>1</sup> |  X | X  |   |   |
| Inhoud in de werkruimte maken, bewerken en verwijderen.  |  X | X  | X  |   |
| Rapporten publiceren naar de werkruimte, inhoud verwijderen.  |  X | X  | X  |   |
| Een rapport in een andere werkruimte maken op basis van een gegevensset in deze werkruimte.<sup>1</sup> |  X | X  | X  |   |
| Een rapport kopiëren.<sup>2</sup> | X | X | X |  |
| Een item bekijken en ermee werken.<sup>3</sup> |  X | X  | X  | X  |

1. Inzenders en kijkers kunnen items in een werkruimte delen als ze machtigingen voor opnieuw delen hebben.
2. Als u een rapport wilt kopiëren en een rapport wilt maken in een andere werkruimte op basis van een gegevensset in deze werkruimte, moet u aan aanvullende criteria voldoen:
    - U hebt een Power BI Pro-licentie nodig. Zie de volgende sectie, [Licenties](#licensing), voor details.
    - U hebt een samenstellingsmachtiging nodig voor de gegevensset. Voor gegevenssets in deze werkruimte hebben de personen met de rollen Beheerder, Lid en Inzender een Samenstellingsmachtiging via hun werkruimterol.
2. Zelfs als u geen Power BI Pro-licentie hebt, kunt u items in de Power BI-service bekijken en ermee werken als de items zich in een werkruimte in een Premium-capaciteit bevinden.

## <a name="licensing"></a>Licentieverlening
Iedereen die u toevoegt aan een werkruimte in de gedeelde capaciteit, heeft een Power BI Pro-licentie nodig. Deze gebruikers kunnen in de werkruimte samenwerken aan dashboards en rapporten die u wilt publiceren naar een breder publiek of zelfs uw hele organisatie. 

Als u inhoud naar anderen binnen uw organisatie wilt distribueren, kunt u Power BI Pro-licenties toewijzen aan die gebruikers of de werkruimte in een Power BI Premium-capaciteit plaatsen.

Wanneer de werkruimte zich in een Power BI Premium-capaciteit bevindt, hebben gebruikers met de rol Lezer toegang tot de werkruimte, zelfs als ze geen Power BI Pro-licentie hebben. Als u echter een hogere rol toewijst aan deze gebruikers, zoals Beheerder, Lid of Inzender, wordt hen gevraagd om een Pro-proefversie te starten wanneer zij toegang proberen te krijgen tot de werkruimte. Als u de mogelijkheden van de rol Lezer wilt benutten voor gebruikers zonder Pro-licentie, zorgt u ervoor dat de gebruikers met de rol Lezer geen andere rol in de werkruimte hebben, niet als individuele gebruiker en niet als onderdeel van een groep. 

> [!NOTE]
> Bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring gelden strengere normen voor het afdwingen van bestaande licentieregels. Gebruikers zonder een Pro-licentie die proberen te publiceren vanuit Power BI Desktop of andere clienthulpprogramma's, krijgen de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.

## <a name="how-the-new-workspaces-are-different"></a>Het verschil tussen de oude en nieuwe werkruimten

Voor de nieuwe werkruimten hebben wij enkele functies opnieuw ontworpen. Dit zijn de wijzigingen die naar alle waarschijnlijkheid definitief zullen worden doorgevoerd. 

* Wanneer u deze werkruimten maakt, worden er geen Office 365-groepen gemaakt, zoals bij klassieke werkruimten. U kunt nu echter een Office 365-groep gebruiken om gebruikers toegang tot uw werkruimte te geven door een rol toe te wijzen. 
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

| Beschrijvende naam | Naam van bewerking |
|---|---|
| Power BI-map gemaakt | CreateFolder |
| Power BI-map verwijderd | DeleteFolder |
| Power BI-map bijgewerkt | UpdateFolder |
| Toegang tot Power BI-map bijgewerkt| UpdateFolderAccess |

Lees meer over de [controle door Power BI](service-admin-auditing.md).

## <a name="guest-users"></a>Gastgebruikers

[Azure AD B2B-gastgebruikers](service-admin-azure-ad-b2b.md) hebben standaard geen toegang tot werkruimten. Power BI-beheerders kunnen [externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). De ingeschakelde gastgebruikers hebben toegang tot werkruimten waarvoor ze zijn gemachtigd.

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
- Als u wilt toestaan dat gebruikers met de rol Lezer gegevens mogen exporteren, zorgt u ervoor dat ze de machtiging Build hebben voor de gegevenssets in de werkruimte. Meer informatie over [Samenstellingsmachtiging voor gegevenssets](service-datasets-build-permissions.md).
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
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
