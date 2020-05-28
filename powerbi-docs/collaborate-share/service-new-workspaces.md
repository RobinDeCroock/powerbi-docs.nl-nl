---
title: Werk organiseren in de nieuwe werkruimten in Power BI
description: Lees hier alles over de nieuwe werkruimten, die bestaan uit verzamelingen dashboards en rapporten die zijn gemaakt om belangrijke statistieken over uw organisatie te bieden.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 701f478ce4dd59d77c1722b1386cd79ad3fbf2a0
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83693774"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Werk organiseren in de nieuwe werkruimten in Power BI

*Werkruimten* zijn plekken waar u met collega’s kunt samenwerken om verzamelingen dashboards, rapporten, gegevenssets en gepagineerde rapporten te maken. De nieuwe werkruimte-ervaring helpt om de toegang tot inhoud beter te beheren. Dit artikel beschrijft de nieuwe werkruimten, en hoe deze verschillen van de klassieke werkruimten.  Net als de klassieke werkruimten gebruikt u de nieuwe werkruimten ook om apps te maken en distribueren. Klaar om een nieuwe werkruimte te maken? Lees [Werkruimten maken (nieuwe werkruimte-ervaring)](service-create-the-new-workspaces.md).

Nieuwe werkruimten kunnen naast bestaande klassieke werkruimten worden gebruikt. De nieuwe werkruimte-ervaring is het standaardtype werkruimte. Zo nodig kunt u nog steeds [klassieke werkruimten](service-create-workspaces.md) op basis van Microsoft 365-groepen maken en gebruiken. Klaar om uw klassieke werkruimte te migreren? Zie [Een upgrade uitvoeren van de klassieke werkruimten naar de nieuwe werkruimten in Power BI](service-upgrade-workspaces.md) voor meer informatie.

Met de nieuwe werkruimten kunt u het volgende doen:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Microsoft 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een onderliggende, gekoppelde Microsoft 365-groep te maken. Alle werkruimtebeheer vindt plaats in Power BI, niet in Microsoft 365.
- Desgewenst kunt u doorgaan met het beheren van de gebruikerstoegang tot inhoud via Microsoft 365-groepen. Hiertoe hoeft u slechts een Microsoft 365-groep toe te voegen aan de toegangslijst voor de werkruimte.
- Meer gedetailleerde werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.

In Power BI worden nog steeds alle Microsoft 365-groepen weergegeven waarvan u lid bent. Hiermee wordt voorkomen dat bestaande werkstromen moeten worden gewijzigd.

## <a name="new-and-classic-workspace-differences"></a>Verschillen tussen nieuwe en klassieke werkruimten

Voor de nieuwe werkruimten hebben wij enkele functies opnieuw ontworpen. Dit zijn de belangrijkste verschillen.

- Wanneer u deze werkruimten maakt, worden er geen Microsoft 365-groepen gemaakt, zoals bij klassieke werkruimten. U kunt nu echter een Microsoft 365-groep gebruiken om gebruikers toegang tot uw werkruimte te geven door een rol toe te wijzen.
- In klassieke werkruimten kunt u alleen individuen toevoegen aan de lijsten met leden en beheerders. In de nieuwe werkruimten kunt u meerdere Active Directory-beveiligingsgroepen, distributielijsten of Microsoft 365-groepen toevoegen aan deze lijsten om het beheer van gebruikers eenvoudiger te maken.
- U kunt een organisatie-inhoudspakket maken op basis van een klassieke werkruimte. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten maken.
- U kunt een organisatie-inhoudspakket uit een klassieke werkruimte gebruiken. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten gebruiken.

### <a name="workspace-features-that-work-differently"></a>Functies van de werkruimten die anders werken

Sommige functies werken in de nieuwe werkruimten anders dan in de huidige werkruimten. Deze verschillen zijn opzettelijk aangebracht, op basis van de feedback die we van klanten hebben ontvangen. Hierdoor kunnen gebruikers flexibeler samenwerken in werkruimten.

- **Afdwingen van licenties**: Bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring worden bestaande licentieregels afgedwongen. Gebruikers die in werkruimten samenwerken of inhoud delen met andere gebruikers in de Power BI-service hebben een Power BI Pro-licentie nodig. Gebruikers zonder een Pro-licentie zien de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.
- **Leden kunnen inhoud al dan niet opnieuw delen**: De rol Inzender vervangt deze instelling.
- **Alleen-lezen werkruimten**: In plaats van gebruikers alleen-lezen toegang te geven tot een werkruimte, wijst u gebruikers de rol Lezer toe. Hiermee wordt vergelijkbare alleen-lezen toegang tot de inhoud in een werkruimte toegestaan.
- **Gebruikers zonder een Pro-licentie** hebben toegang tot de werkruimte als deze zich in een Power BI Premium-capaciteit bevindt, maar alleen als zij beschikken over de rol Kijker.
- **Gebruikers toestaan gegevens te exporteren**: Gebruikers met de rol Lezer kunnen gegevens exporteren als ze de samenstellingsmachtiging hebben voor de gegevenssets in de werkruimte. Meer informatie over [Samenstellingsmachtiging voor gegevenssets](../connect-data/service-datasets-build-permissions.md).
- Geen knop **Werkruimte verlaten**.

### <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte

De nieuwe functie **Lijst met contactpersonen** maakt het mogelijk om op te geven welke gebruikers meldingen moeten ontvangen over problemen die optreden in de werkruimte. De standaardinstelling is dat elke gebruiker of groep die is ingesteld als een beheerder van de werkruimte een melding krijgt, maar u kunt de lijst aanpassen. Gebruikers of groepen die in de lijst met contactpersonen staan, worden weergegeven in de gebruikersinterface (UI) zodat gebruikers hulp kunnen krijgen met betrekking tot de werkruimte. 

Lees hier meer over het [instellen van de lijst met contactpersonen voor een werkruimte](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>Werkruimte op OneDrive

Met de functie Werkruimte op OneDrive kunt u een Microsoft 365-groep configureren waarvan de bestandsopslag uit de SharePoint-documentbibliotheek beschikbaar is voor werkruimtegebruikers. U maakt de groep buiten Power BI.

Power BI biedt geen synchronisatie voor machtigingen van gebruikers of groepen die zijn geconfigureerd voor werkruimtetoegang met behulp van het lidmaatschap van een Microsoft 365-groep. De aanbevolen procedure is om werkruimtetoegang te beheren via dezelfde Microsoft 365-groep waarvan u de bestandsopslag configureert in deze instelling.

Lees meer over hoe u [Werkruimte op OneDrive](service-create-the-new-workspaces.md#workspace-onedrive) instelt en gebruikt.  

## <a name="roles-in-the-new-workspaces"></a>Rollen in de nieuwe werkruimten

Als u toegang wilt verlenen tot een nieuwe werkruimte, voegt u groepen met gebruikers of individuele gebruikers toe aan een van de werkruimterollen: beheerders, leden, inzenders of lezers. Iedereen in een gebruikersgroep krijgt de rol die u hebt gedefinieerd. Als iemand deel uitmaakt van verschillende gebruikersgroepen, krijgt hij of zij het hoogste machtigingsniveau dat aan de toegewezen rollen is toegewezen.

U kunt met rollen bepalen wie wat kan doen in een werkruimte, zodat teams kunnen samenwerken. U kunt met nieuwe werkruimten rollen toewijzen aan personen en aan gebruikersgroepen: beveiligingsgroepen, Microsoft 365-groepen en distributielijsten.

Wanneer u rollen aan een gebruikersgroep toewijst, hebben de personen in de groep toegang tot de inhoud. Als u gebruikersgroepen nest, zijn alle ingesloten gebruikers gemachtigd.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Als u beveiliging op rijniveau (RLS) wilt afdwingen voor gebruikers die inhoud in een werkruimte bekijken, gebruikt u de rol Lezer. Als u beveiliging op rijniveau wilt afdwingen zonder toegang tot de werkruimte te geven, publiceert u een Power BI-app naar die gebruikers of gebruikt u delen om inhoud te distribueren.

## <a name="licensing"></a>Licentieverlening
Iedereen die u toevoegt aan een werkruimte in de gedeelde capaciteit, heeft een Power BI Pro-licentie nodig. Deze gebruikers kunnen in de werkruimte samenwerken aan dashboards en rapporten die u wilt publiceren naar een breder publiek of zelfs uw hele organisatie. 

Als u inhoud naar anderen binnen uw organisatie wilt distribueren, kunt u Power BI Pro-licenties toewijzen aan die gebruikers of de werkruimte in een Power BI Premium-capaciteit plaatsen.

Wanneer de werkruimte zich in een Power BI Premium-capaciteit bevindt, hebben gebruikers met de rol Lezer toegang tot de werkruimte, zelfs als ze geen Power BI Pro-licentie hebben. Als u echter een hogere rol toewijst aan deze gebruikers, zoals Beheerder, Lid of Inzender, wordt hen gevraagd om een Pro-proefversie te starten wanneer zij toegang proberen te krijgen tot de werkruimte. Als u gebruik wilt maken van de rol Lezer voor gebruikers zonder Pro-licenties, moet u ervoor zorgen dat ze geen andere werkruimterollen hebben, individueel of via een gebruikersgroep.

> [!NOTE]
> Bij het publiceren van rapporten naar de nieuwe werkruimte-ervaring gelden strengere normen voor het afdwingen van bestaande licentieregels. Als u zonder een Pro-licentie iets probeert te publiceren vanuit Power BI Desktop of andere clienthulpprogramma's, krijgt u de fout 'Alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte'.

## <a name="administering-new-workspace-experience-workspaces"></a>Werkruimten beheren in nieuwe werkruimte-ervaring

Werkruimten in de nieuwe werkruimte-ervaring worden nu beheerd vanuit de beheerportal van Power BI. Power BI-beheerders bepalen wie in een organisatie werkruimten kunnen maken en apps kunnen distribueren. Beheerders kunnen de status van alle werkruimten in hun organisatie zien. Ze kunnen ook werkruimten beheren en herstellen. Meer informatie over het [maken van de nieuwe werkruimten](../admin/service-admin-portal.md#create-the-new-workspaces) vindt u in het artikel over de beheerportal.

## <a name="guest-users"></a>Gastgebruikers

[Azure AD B2B-gastgebruikers](../admin/service-admin-azure-ad-b2b.md) hebben standaard geen toegang tot werkruimten. Power BI-beheerders kunnen [externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Ingeschakelde gastgebruikers hebben toegang tot werkruimten waarvoor ze zijn gemachtigd.

## <a name="auditing"></a>Controleren

De volgende activiteiten worden gecontroleerd door Power BI voor werkruimten van de nieuwe werkruimte-ervaring.

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

