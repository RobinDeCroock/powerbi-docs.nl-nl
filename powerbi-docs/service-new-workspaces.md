---
title: Werk in de nieuwe werkruimten - Power BI te organiseren
description: Meer informatie over de nieuwe werkruimten die verzamelingen van dashboards en rapporten die is gebouwd zijn voor het leveren van belangrijke metrische gegevens voor uw organisatie.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100689"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Werk in de nieuwe werkruimten in Power BI te organiseren

 *Werkruimten* plaatsen samenwerken met collega's om verzamelingen van dashboards, rapporten en gepagineerde rapporten te maken. De nieuwe werkruimte-ervaring kunt u toegang tot de inhoud beter te beheren. Dit artikel beschrijft de nieuwe werkruimten, en hoe ze verschillen van de klassieke werkruimten.  Als met klassieke werkruimten u nog steeds gebruiken om te maken en distribueren van apps. Meer informatie over hoe u [maken van een nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md).

De nieuwe werkruimte-ervaring, algemene beschikbaarheid (GA) heeft bereikt en is nu de standaardwerkruimte. U kunt nog steeds te maken en gebruiken [klassieke werkruimten](service-create-workspaces.md) op basis van Office 365-groepen. 

> [!NOTE]
> Als u beveiliging op rijniveau (RLS) voor Power BI Pro-gebruikers inhoud in een werkruimte te bladeren, echter ook doorgaan met [klassieke werkruimten](service-create-workspaces.md). Selecteer de **leden kunnen alleen Power BI-inhoud weergeven** optie. U kunt ook een Power BI-app publiceren voor gebruikers of delen gebruiken om inhoud te distribueren. De rol van toekomstige Viewer schakelt u dit scenario in de toekomst in nieuwe werkruimten van de werkruimte-ervaring.

Met de nieuwe werkruimten, kunt u het volgende doen:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Office 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een Office 365-groep te maken.
- Gedetailleerdere werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.

Wanneer u een van de nieuwe werkruimten maakt, maakt u geen onderliggende, gekoppelde Office 365-groep. Alle werkruimtebeheer vindt plaats in Power BI, niet in Office 365. In de nieuwe werkruimte-ervaring, kunt u nu een Office 365-groep in de toegangslijst van de werkruimte om door te gaan met het beheren van de gebruikerstoegang tot inhoud via Office 365-groepen toevoegen.

## <a name="administering-new-workspace-experience-workspaces"></a>Nieuwe werkruimte-ervaring werkruimten beheren
Beheer voor nieuwe werkruimten van de werkruimte-ervaring is nu in Power BI, Power BI-beheerders bepalen wie er binnen een organisatie werkruimten kunt maken. Ze kunnen ook beheren en herstellen van de werkruimte. Ze moeten de Power BI-beheerportal of de PowerShell-CmdLets gebruiken om dit te doen. Voor klassieke werkruimten op basis van Office 365-groepen, beheer zich blijft voordoen in Office 365-beheerportal en Azure Active Directory.

In **werkruimte instellingen** in de beheerportal beheerders de werkruimten maken (met de nieuwe werkruimte-ervaring) instellen waarmee iedereen of niemand in een organisatie kunt gebruiken voor het maken van nieuwe werkruimte-ervaring werkruimten. Ze kunnen het maken van werkruimten ook beperken tot leden van specifieke beveiligingsgroepen.

> [!NOTE]
> De werkruimten maken (met de nieuwe werkruimte-ervaring) standaardinstellingen toe te staan dat gebruikers die Office 365-groepen voor het maken van de nieuwe werkruimten in Power BI kunnen maken. Zorg ervoor dat een waarde instellen in de Power BI-beheerportal om te controleren of de juiste gebruikers kunnen nieuwe werkruimte ervaring werkruimten maken.

![Werkruimte-instellingen in de beheerportal](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

De [lijst met werkruimten is beschikbaar](service-admin-portal.md#workspaces) in de Power BI-beheerportal. 

![Lijst met werkruimten](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nieuwe werkruimten naast elkaar met klassieke werkruimten

Nieuwe, bijgewerkte werkruimten en bestaande klassieke werkruimten naast elkaar bestaan naast elkaar, en u kunt maken. De nieuwe werkruimte-ervaring is het type van de werkruimte standaard. Power BI blijft om alle Office 365-groepen de gebruiker lid van in Power BI is om te voorkomen dat het wijzigen van bestaande werkstromen weer te geven. Als u wilt weten hoe u een nieuwe werkruimte maken, lezen [maken van nieuwe werkruimten](service-create-the-new-workspaces.md). Lees voor meer informatie over het maken van een klassieke werkruimte, [maken van de klassieke werkruimten](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Rollen in de nieuwe werkruimten

Toevoegen om toegang te verlenen aan een nieuwe werkruimte, groepen of personen aan een van de werkruimte-rollen: leden, inzenders of beheerders. Iedereen in een gebruikersgroep krijgt de rol die u hebt gedefinieerd. Als een persoon zich in verschillende gebruikersgroepen, krijgen de hoogste mate van machtiging geleverd door de rollen die zijn toegewezen.

U kunt met rollen bepalen wie wat kan doen in een werkruimte, zodat teams kunnen samenwerken. U kunt met nieuwe werkruimten rollen toewijzen aan personen en aan gebruikersgroepen: beveiligingsgroepen, Office 365-groepen en distributielijsten. 

Wanneer u rollen aan een gebruikersgroep toewijst, hebben de personen in de groep toegang tot de inhoud. Als u gebruikersgroepen nest, zijn alle ingesloten gebruikers gemachtigd. Aan een gebruiker die zich in verschillende gebruikersgroepen met verschillende rollen bevindt, wordt de machtiging met de meeste rechten toegewezen. 

De nieuwe werkruimten bieden drie rollen: beheerders, leden en inzenders.

|Mogelijkheid   | Beheerder  | Lid  | Inzender  | 
|---|---|---|---|
| De werkruimte bijwerken en verwijderen.  | X  |   |   |
| Personen, met inbegrip van andere beheerders, toevoegen/verwijderen.  | X  |   |   |
| Leden of anderen met minder machtigingen toevoegen.  |  X | X  |   |
| Apps publiceren en bijwerken. |  X | X  |   |
| Items en apps delen. |  X | X  |   |
| Anderen toestaan items opnieuw te delen. |  X | X  |   |
| Inhoud in de werkruimte maken, bewerken en verwijderen.  |  X | X  | X  |
| Rapporten publiceren naar de werkruimte, inhoud verwijderen. |  X | X  | X  |
 
 
## <a name="licensing"></a>Licentieverlening
Iedereen die u aan een werkruimte toevoegt, heeft een Power BI Pro-licentie nodig. Deze gebruikers kunnen in de werkruimte samenwerken aan dashboards en rapporten die u wilt publiceren naar een breder publiek of zelfs uw hele organisatie. Als u inhoud naar anderen binnen uw organisatie wilt distribueren, kunt u Power BI Pro-licenties toewijzen aan die gebruikers of de werkruimte in een Power BI Premium-capaciteit plaatsen.

> [!NOTE]
> Rapporten publiceren naar nieuwe werkruimte-ervaring heeft strengere afdwingen die bestaande regels-licentieverlening. Gebruikers die proberen te publiceren vanuit Power BI Desktop of andere clients hulpprogramma's zonder een Pro-licentie ziet de fout "alleen gebruikers met Power BI Pro-licenties kunnen publiceren naar deze werkruimte."

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Hoe verschillen de nieuwe werkruimten van de huidige werkruimten?

Voor de nieuwe werkruimten worden enkele functies anders ontworpen. Hier volgen de wijzigingen die u kunt verwachten permanent. 

* Het maken van deze werkruimten niet Office 365-groepen, zoals klassieke werkruimten kunnen worden gemaakt. U kunt echter nu een Office 365-groep gebruiken zodat gebruikers toegang tot uw werkruimte een rol toe te wijzen. 
* In de klassieke werkruimten kunt u mensen alleen individueel toevoegen aan de leden- en beheerderlijsten. In de nieuwe werkruimten kunt u meerdere AD-beveiligingsgroepen, distributielijsten of Office 365-groepen toevoegen aan deze lijsten om het beheer van gebruikers eenvoudiger te maken. 
- U kunt een organisatie-inhoudspakket maken van een klassieke werkruimte. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten maken.
- U kunt een organisatie-inhoudspakket van een klassieke werkruimte verbruiken. U kunt geen organisatie-inhoudspakket op basis van de nieuwe werkruimten gebruiken.

## <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte
De nieuwe **lijst met contactpersonen** functie kunt u opgeven welke gebruikers geïnformeerd over problemen die optreden in de werkruimte. Standaard opgegeven elke gebruiker of groep die als een werkruimte beheerder op de hoogte is gesteld, maar u kunt de lijst. Gebruikers of groepen die worden vermeld in de lijst met contactpersonen wordt weergegeven in de gebruikersinterface (UI) voor hulp bij gebruikers met betrekking tot de werkruimte. 

Meer informatie over de [instellen van de lijst met contactpersonen werkruimte](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Workspace OneDrive
De werkruimte OneDrive-functie kunt u een Office 365-groep waarvan bestandsopslag SharePoint-documentbibliotheek beschikbaar voor gebruikers van deze werkruimte is configureren. De groep moet buiten Power BI worden gemaakt. 

Power BI biedt geen machtigingen van gebruikers of groepen die zijn geconfigureerd voor werkruimtetoegang met het groepslidmaatschap van Office 365 hebben gesynchroniseerd. De aanbevolen procedure is om werkruimtetoegang tot en met de dezelfde Office 365-groep waarvan u in deze instelling configureren bestandsopslag te beheren. 

Meer informatie over hoe u [instellen en toegang tot de werkruimte OneDrive](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Controle
De volgende activiteiten worden gecontroleerd door Power BI voor nieuwe werkruimten van de werkruimte-ervaring.

| Beschrijvende naam |   Naam van bewerking |
|---|---|
| Power BI-map gemaakt | CreateFolder |
| Power BI-map verwijderd | DeleteFolder |
| Power BI-map bijgewerkt | UpdateFolder |
| Toegang tot Power BI-map bijgewerkt| UpdateFolderAccess |

Meer informatie over [Power BI controle](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Houd rekening met de volgende beperkingen:

- Werkruimten kunnen maximaal 1000 gegevenssets of 1000 rapporten per gegevensset bevatten. 
- Een persoon met een Power BI Pro-licentie kan lid zijn van een maximaal 1000 werkruimten.
- Power BI publisher voor Excel wordt niet ondersteund.

## <a name="workspace-features-that-work-differently"></a>Functies van de werkruimten die anders werken

Sommige functies werken in de nieuwe werkruimten anders dan in de huidige werkruimten. Deze verschillen zijn opzettelijke, op basis van feedback die we van klanten hebt ontvangen, en een flexibelere benadering voor samenwerking met werkruimten inschakelen:

- Handhaving: Rapporten publiceren naar nieuwe werkruimte-ervaring wordt afgedwongen bestaande licenties regels waarvoor een licentie voor Power BI Pro voor gebruikers kunnen samenwerken in werkruimten of delen van inhoud naar anderen in de Power BI-service. Gebruikers zonder een Pro-licentie ziet de fout "alleen gebruikers met Powre BI Pro-licenties kunnen publiceren naar deze werkruimte."
- Leden kunnen wel of niet opnieuw delen: vervangen door de rol Inzender
- Alleen-lezenwerkruimten: in plaats van dat u gebruikers alleen-lezentoegang geeft tot een werkruimte, wijst u aan gebruikers de toekomstig beschikbare rol Lezer toe. Hiermee krijgen ze vergelijkbare alleen-lezentoegang tot de inhoud in een werkruimte.
- Geen knop **Werkruimte verlaten**.

## <a name="frequently-asked-questions"></a>Veelgestelde vragen

**GA voor koppelingen naar bestaande inhoud beïnvloed door de nieuwe werkruimte-ervaring zijn**

Nee. Koppelingen naar bestaande items in de klassieke werkruimten worden niet beïnvloed door de nieuwe werkruimte-ervaring. De algemene beschikbaarheid (GA) van de nieuwe werkruimte-ervaring wijzigt de standaard-werkruimte maken, maar bestaande werkruimten niet wijzigen. 

**Bestaande werkruimten een upgrade uitgevoerd naar de nieuwe werkruimte-ervaring met de algemeen beschikbare**

Nee. Het type van de werkruimte standaard de nieuwe werkruimte-ervaring GA alleen gewijzigd naar de nieuwe werkruimte-ervaring. Bestaande klassieke werkruimten die zijn gebaseerd op Office 365-groepen blijven ongewijzigd.

**Werkruimten nog steeds automatisch worden gemaakt voor Office 365-groepen**

Ja. Omdat we beide soorten werkruimten naast elkaar ondersteunen, blijven we om alle Office 365-groepen de gebruiker toegang tot in de lijst met werkruimten heeft weer te geven.

## <a name="next-steps"></a>Volgende stappen
* [De nieuwe werkruimten maken in Power BI](service-create-the-new-workspaces.md)
* [De klassieke werkruimten maken](service-create-workspaces.md)
* [Apps in Power BI installeren en gebruiken](service-create-distribute-apps.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
