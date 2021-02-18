---
title: Werk organiseren in de nieuwe werkruimten in Power BI
description: Lees hier alles over de nieuwe werkruimten, die bestaan uit verzamelingen dashboards en rapporten die zijn gemaakt om belangrijke statistieken over uw organisatie te bieden.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
ms.date: 02/17/2021
ms.custom: contperf-fy20q4
LocalizationGroup: Share your work
ms.openlocfilehash: 16533d694bd28fd410686f10fdd36bd9c006afe1
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2021
ms.locfileid: "100655751"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Werk organiseren in de nieuwe werkruimten in Power BI

*Werkruimten* zijn plekken waar u met collega’s kunt samenwerken om verzamelingen dashboards, rapporten, gegevenssets en gepagineerde rapporten te maken. De nieuwe werkruimte-ervaring helpt om de toegang tot inhoud beter te beheren. Dit artikel beschrijft de nieuwe werkruimten, en hoe deze verschillen van de klassieke werkruimten.  Net als de klassieke werkruimten gebruikt u de nieuwe werkruimten ook om apps te maken en distribueren. 

Klaar om een nieuwe werkruimte te maken? Lees [Werkruimten maken (nieuwe werkruimte-ervaring)](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Nieuwe werkruimte-ervaring voor Power BI":::

Nieuwe werkruimten kunnen naast bestaande klassieke werkruimten worden gebruikt. De nieuwe werkruimte-ervaring is het standaardtype werkruimte. Zo nodig kunt u nog steeds [klassieke werkruimten](service-create-workspaces.md) op basis van Microsoft 365-groepen maken en gebruiken. Klaar om uw klassieke werkruimte te migreren? Zie [Een upgrade uitvoeren van de klassieke werkruimten naar de nieuwe werkruimten in Power BI](service-upgrade-workspaces.md) voor meer informatie.

## <a name="new-and-classic-workspace-differences"></a>Verschillen tussen nieuwe en klassieke werkruimten

Voor de nieuwe werkruimten hebben wij enkele functies opnieuw ontworpen. Dit zijn de belangrijkste verschillen.

- **Wanneer u de nieuwe werkruimten maakt, worden er geen Microsoft 365-groepen gemaakt,** zoals bij klassieke werkruimten. Alle nieuwe werkruimtebeheer vindt plaats in Power BI, niet in Office 365. Desgewenst kunt u doorgaan met het beheren van de gebruikerstoegang tot inhoud via Microsoft 365-groepen. Hiertoe hoeft u slechts een Microsoft 365-groep toe te voegen aan de toegangslijst voor de werkruimte.
- **Meer gedetailleerde werkruimterollen gebruiken** voor flexibeler beheer van machtigingen in de nieuwe werkruimtes.  In klassieke werkruimten kunt u alleen individuen toevoegen aan de lijsten met leden en beheerders. 
- **Gebruikersgroepen toewijzen aan werkruimterollen**: In de nieuwe werkruimten kunt u meerdere Active Directory-beveiligingsgroepen, distributielijsten of Microsoft 365-groepen toevoegen aan deze rollen om het beheer van gebruikers eenvoudiger te maken. 
- **Lijst met contactpersonen**: In de nieuwe werkruimten kunt u opgeven wie er meldingen over werkruimteactiviteiten ontvangt.
- **Sjabloon-apps maken**: U kunt in de nieuwe werkruimten alleen *sjabloon-apps* maken. Sjabloon-apps zijn apps die u kunt distribueren naar klanten buiten uw organisatie. Deze klanten kunnen vervolgens uw sjabloon-app gebruiken om verbinding te maken met hun eigen gegevens. Meer informatie over [sjabloon-apps](../connect-data/service-template-apps-overview.md).
- **Gegevenssets delen**: Als u een gegevensset buiten een specifieke werkruimte wilt delen, moet u het rapport met de gegevensset in een van de nieuwe werkruimten opslaan. U kunt geen gegevenssets delen vanuit klassieke werkruimten. Meer informatie over [gedeelde gegevenssets](../connect-data/service-datasets-across-workspaces.md).
- **Organisatie-inhoudspakketten**: U kunt organisatie-inhoudspakketten maken en gebruiken in klassieke werkruimten. U kunt ze niet in de nieuwe werkruimten maken of gebruiken. Apps en sjabloon-apps vervangen organisatie-inhoudspakketten in de nieuwe werkruimten. Organisatie-inhoudspakketten worden afgeschaft. Het is nu een goed moment om uw inhoudspakketten te upgraden naar apps. Raadpleeg de sectie over roadmap voor de werkruimte-upgrade van deze blogpost [Aangekondigd: Power BI-beheerders kunnen klassieke werkruimten upgraden](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) voor de tijdlijn.

In dit artikel vindt u meer informatie over deze functies.

> [!NOTE]
> In Power BI worden nog steeds alle Microsoft 365-groepen weergegeven waarvan u lid bent. Hiermee wordt voorkomen dat bestaande werkstromen moeten worden gewijzigd.

### <a name="features-that-work-differently"></a>Functies die anders werken

In de nieuwe werkruimten werken sommige functies anders. Deze verschillen zijn opzettelijk aangebracht, op basis van de feedback die we van klanten hebben ontvangen. Hierdoor kunnen gebruikers flexibeler samenwerken in werkruimten.

- **Afdwingen van licenties**: Bij het publiceren van rapporten naar een nieuwe werkruimte-ervaring worden bestaande licentieregels afgedwongen. Gebruikers die in nieuwe werkruimten samenwerken of inhoud delen met andere gebruikers in de Power BI-service hebben een Power BI Pro-licentie nodig. Gebruikers zonder een Pro-licentie zien de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.
- **Instelling 'Leden kunnen opnieuw delen'** : De rol Inzender in de nieuwe werkruimten vervangt de instelling 'Leden kunnen opnieuw delen' in de klassieke werkruimten.
- **Alleen-lezen werkruimten**: De rol van kijker in de nieuwe werkruimten vervangt de alleen-lezentoegang tot een klassieke werkruimte die aan gebruikers werd verleend. Met de rol Kijker wordt vergelijkbare alleen-lezentoegang tot de inhoud in de nieuwe werkruimten toegestaan.
- **Gebruikers zonder een Pro-licentie** hebben toegang tot een nieuwe werkruimte als deze over een Power BI Premium-capaciteit beschikt, maar alleen als ze de rol van Kijker hebben.
- **Gebruikers toestaan gegevens te exporteren**: Zelfs gebruikers met de rol Kijker in de nieuwe werkruimte kunnen gegevens exporteren als ze de samenstellingsmachtiging hebben voor de gegevenssets in die werkruimte. Meer informatie over [Samenstellingsmachtiging voor gegevenssets](../connect-data/service-datasets-build-permissions.md).
- Geen knop **Werkruimte verlaten** in de nieuwe werkruimten.

### <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte

De nieuwe functie **Lijst met contactpersonen** maakt het mogelijk om op te geven welke gebruikers meldingen moeten ontvangen over problemen die optreden in de nieuwe werkruimten. De standaardinstelling is dat elke gebruiker of groep die is ingesteld als een beheerder van de nieuwe werkruimte, een melding krijgt. U kunt gebruikers aan die lijst toevoegen. Gebruikers of groepen in de lijsten met contactpersonen worden ook weergegeven in de gebruikersinterface (UI) van de nieuwe werkruimten, zodat eindgebruikers van de werkruimte weten met wie ze contact kunnen opnemen. 

Meer informatie over [het maken van de lijst met contactpersonen in de werkruimte](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>Werkruimte op OneDrive

Zoals gezegd maakt Power BI achter de schermen geen Microsoft 365-groep aan wanneer u een van de nieuwe werkruimten maakt. Het kan echter handig zijn om een OneDrive te koppelen aan de nieuwe werkruimte. Met de functie Werkruimte op OneDrive in de nieuwe werkruimten kunt u een Microsoft 365-groep configureren waarvan de bestandsopslag uit de SharePoint-documentbibliotheek beschikbaar is voor werkruimtegebruikers. U maakt de groep buiten Power BI.
 
Power BI synchroniseert niet tussen Microsoft 365-groepslidmaatschap en -machtigingen voor gebruikers of groepen met toegang tot de nieuwe werkruimte. U kunt ze synchroniseren: Beheer werkruimtetoegang via dezelfde Microsoft 365-groep waarvan u de bestandsopslag configureert in deze instelling. 

Meer informatie over [het instellen van de werkruimte op OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Rollen in de nieuwe werkruimten

U kunt met rollen bepalen wie wat kan doen in de nieuwe werkruimtes, zodat teams kunnen samenwerken. U kunt met nieuwe werkruimten rollen toewijzen aan personen en aan gebruikersgroepen: beveiligingsgroepen, Microsoft 365-groepen en distributielijsten. 

Als u toegang wilt verlenen tot een nieuwe werkruimte, kent u aan gebruikersgroepen of individuele gebruikers een van de werkruimterollen toe: Beheerder, Lid, Inzender of Kijker. Iedereen in een gebruikersgroep krijgt de rol die u hebt toegewezen. Als iemand deel uitmaakt van meerdere gebruikersgroepen, krijgt hij of zij het hoogste machtigingsniveau dat aan de toegewezen rollen is toegekend. Als u gebruikersgroepen nest, zijn alle ingesloten gebruikers gemachtigd. Al deze mogelijkheden, met uitzondering van bekijken en ermee werken, vereisen een Power BI Pro-licentie. Lees in dit artikel meer over [licentieverlening](#licenses).

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - U kunt rollen aan afzonderlijke gebruikers of gebruikersgroepen toekennen, zelfs als de gebruikers de rol niet kunnen gebruiken. U kunt gebruikers zonder Power BI Pro-licenties dus aan rollen toewijzen die licenties vereisen. Zie [Licenties](#licenses) in dit artikel voor meer informatie.
> - Als u [beveiliging op rijniveau (RLS)](../admin/service-admin-rls.md) wilt afdwingen voor gebruikers die inhoud in een werkruimte bekijken, gebruikt u de rol van Kijker. U kunt beveiliging op rijniveau ook afdwingen zonder toegang tot de nieuwe werkruimte te verlenen. [Publiceer een app](service-create-distribute-apps.md) en distribueer deze naar die gebruikers of gebruik [delen om inhoud naar hen te distribueren](service-share-dashboards.md).

## <a name="licensing-and-administering"></a>Licentieverlening en beheren

### <a name="licenses"></a>Licenties
Als een van de nieuwe werkruimten een gedeelde capaciteit heeft, heeft iedereen die u toevoegt een Power BI Pro-licentie nodig. Deze gebruikers kunnen allemaal samenwerken aan de dashboards en rapporten in de nieuwe werkruimte. Als u inhoud naar anderen binnen uw organisatie wilt distribueren, wijst u Power BI Pro-licenties aan die gebruikers toe of geeft u de werkruimte een Power BI Premium-capaciteit.

Wanneer de nieuwe werkruimte een Power BI Premium-capaciteit heeft, hebben gebruikers met de rol Kijker toegang tot de werkruimte, zelfs als ze geen Power BI Pro-licentie hebben. Als u echter een hogere rol toewijst aan deze gebruikers, zoals Beheerder, Lid of Inzender, wordt hen gevraagd om een Pro-proefversie te starten wanneer zij toegang proberen te krijgen tot de werkruimte. Als u wilt dat gebruikers zonder Pro-licenties de rol van Kijker gebruiken, moet u ervoor zorgen dat ze niet ook andere werkruimterollen hebben, hetzij afzonderlijk hetzij als onderdeel van een gebruikersgroep.

Bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring gelden strengere normen voor het afdwingen van bestaande licentieregels. Als u zonder een Pro-licentie iets probeert te publiceren vanuit Power BI Desktop of andere clienthulpprogramma's, krijgt u de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.

> [!NOTE]
> Power BI voor de Amerikaanse overheid is niet beschikbaar als een gratis licentie. Zie [Klanten van Power BI voor de Amerikaanse overheid](../admin/service-govus-overview.md) voor informatie over licenties.

### <a name="guest-users"></a>Gastgebruikers

[Azure AD B2B-gastgebruikers](../admin/service-admin-azure-ad-b2b.md) hebben standaard geen toegang tot werkruimten. Power BI-beheerders kunnen [externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Ingeschakelde gastgebruikers hebben toegang tot werkruimten waarvoor ze zijn gemachtigd.

### <a name="administering-new-workspace-experience-workspaces"></a>Werkruimten beheren in nieuwe werkruimte-ervaring

Werkruimten in de nieuwe werkruimte-ervaring worden beheerd vanuit de beheerportal van Power BI. Power BI-beheerders bepalen wie in een organisatie werkruimten kunnen maken en apps kunnen distribueren. Lees meer over [het beheren van de mogelijkheden van gebruikers om werkruimten te maken](../admin/service-admin-portal.md#create-the-new-workspaces) in het artikel Beheerportal. 

Beheerders kunnen ook de status van alle werkruimten in hun organisatie zien. Ze kunnen werkruimten beheren, herstellen en zelfs verwijderen. Lees meer over [het beheren van de werkruimten zelf](../admin/service-admin-portal.md#workspaces) in het artikel Beheerportal.

### <a name="auditing"></a>Controleren

Power BI controleert de volgende activiteiten voor werkruimten van de nieuwe werkruimte-ervaring.

| Beschrijvende naam | Naam van bewerking |
|---|---|
| Power BI-map gemaakt | CreateFolder |
| Power BI-map verwijderd | DeleteFolder |
| Power BI-map bijgewerkt | UpdateFolder |
| Toegang tot Power BI-map bijgewerkt| UpdateFolderAccess |

Lees meer over de [controle door Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Houd rekening met de volgende beperkingen:

- Werkruimten kunnen maximaal 1000 gegevenssets of 1000 rapporten per gegevensset bevatten. 
- Een gebruiker met een Power BI Pro-licentie kan lid zijn van maximaal 1.000 werkruimten.
- De functie van Power BI om te publiceren naar Excel wordt niet ondersteund.

## <a name="frequently-asked-questions"></a>Veelgestelde vragen

**Heeft de nieuwe werkruimte-ervaring gevolgen voor koppelingen naar bestaande inhoud?**

Nee. Koppelingen naar bestaande items in klassieke werkruimten worden niet beïnvloed door de nieuwe werkruimte-ervaring. De algemene beschikbaarheid (GA) van de nieuwe werkruimte-ervaring heeft gevolgen voor de standaardwerkruimte die u maakt, maar bestaande werkruimten blijven ongewijzigd. 

**Worden bestaande werkruimten bijgewerkt naar de nieuwe werkruimte-ervaring bij algemene beschikbaarheid?**

Nee. De algemene beschikbaarheid zorgt er alleen voor dat het type van de standaardwerkruimte wordt gewijzigd in de nieuwe werkruimte-ervaring. Bestaande klassieke werkruimten die zijn gebaseerd op Microsoft 365-groepen blijven ongewijzigd.

**Worden er nog steeds automatisch werkruimten gemaakt voor Microsoft 365-groepen?**

Ja. Omdat we beide typen werkruimten naast elkaar ondersteunen, blijven we in de lijst met werkruimten alle Microsoft 365-groepen weergeven waartoe u toegang hebt.

## <a name="next-steps"></a>Volgende stappen

* [De nieuwe werkruimten maken in Power BI](service-create-the-new-workspaces.md)
* [De klassieke werkruimten maken](service-create-workspaces.md)
* [Apps in Power BI installeren en gebruiken](service-create-distribute-apps.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

