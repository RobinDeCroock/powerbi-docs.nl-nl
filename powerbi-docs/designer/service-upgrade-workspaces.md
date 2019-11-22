---
title: Een upgraden uitvoeren van de klassieke werkruimten naar de nieuwe werkruimten
description: Meer informatie over het bijwerken van een klassieke werkruimte naar de nieuwe werkruimte-ervaring. U kunt elke werkruimte bijwerken, zolang u maar rekening houdt met een aantal wijzigingen.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 34b0bd1a59ec66cf7a2e5eb41d2c1ec12a39d1e7
ms.sourcegitcommit: 01de0b01f66f28ca45b8d309d7864f261d6c9a85
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74128124"
---
# <a name="upgrade-classic-workspaces-to-the-new-workspaces-in-power-bi"></a>Een upgraden uitvoeren van de klassieke werkruimten naar de nieuwe werkruimten in Power BI

In dit artikel wordt uitgelegd hoe u een klassieke werkruimte bijwerkt naar de nieuwe werkruimte-ervaring. U kunt elke klassieke werkruimte bijwerken. De nieuwe werkruimten hebben meer gedetailleerde werkruimterollen, zodat u de toegang tot de inhoud ervan beter kunt beheren. U hebt meer flexibiliteit bij het beheren van bijgewerkte werkruimten, omdat deze losser zijn verbonden met de oorspronkelijke Office 365-groep. Informatie over de [nieuwe werkruimte-ervaring](../service-new-workspaces.md). 

>[!NOTE]
>Deze documentatie betreft een voorlopige versie voor een functie die nog niet beschikbaar is. We hebben deze gepubliceerd zodat u zich kunt voorbereiden op de nieuwe functionaliteit en ter opheldering van eventuele vraagstukken met betrekking tot deze versie.  

![Een geslaagde upgrade uitvoeren](media/service-upgrade-workspaces/power-bi-upgrade-success.png)

Mogelijk moet u wel rekening houden met bepaalde wijzigingen in uw werkruimte. Inhoudspakketten worden bijvoorbeeld niet ondersteund in de nieuwe werkruimte-ervaring. Zie de sectie [Overwegingen en beperkingen voor de upgrade](#upgrade-considerations-and-limitations) verderop in dit artikel.

## <a name="things-to-do-after-upgrading"></a>Wat u moet doen na de upgrade

U moet een aantal dingen doen *na* de upgrade. U kunt deze het beste plannen *voordat* u de upgrade uitvoert:
- Bekijk de toegangslijst en zorg ervoor dat u op de hoogte bent van de [machtigingen na de upgrade](#permissions-after-upgrade).
- Bekijk de [lijst met contactpersonen](#modify-the-contact-list) en zorg ervoor dat deze naar wens is ingesteld.
- Lees de informatie over de [nieuwe werkruimte-ervaring](../service-new-workspaces.md) als u dat nog niet hebt gedaan.

## <a name="upgrade-a-classic-workspace"></a>Een klassieke werkruimte upgraden

Elke werkruimtebeheerder kan de werkruimte upgraden. Voor klassieke werkruimten moet u een eigenaar van de onderliggende Office 365-groep zijn om een werkruimtebeheerder te zijn. Voer de volgende stappen uit om een werkruimte te upgraden.

1. Selecteer in de lijst Inhoud van de werkruimte **Meer opties** ( **...** ) > **Deze werkruimte bewerken**.

    ![Deze werkruimte bewerken](media/service-upgrade-workspaces/power-bi-content-list-edit-workspace.png)

1. Vouw **Geavanceerd** uit en selecteer **Nu upgraden**.

    ![Nu upgraden](media/service-upgrade-workspaces/power-bi-upgrade-now.png)

1. Bekijk de informatie in het dialoogvenster. Er worden waarschuwingen weergegeven als u inhoudspakketten in de werkruimte hebt gepubliceerd of geïnstalleerd. Wanneer u klaar bent, schakelt u **Ik ben gereed voor de upgrade van deze werkruimte** in en selecteert u vervolgens **Upgrade uitvoeren**.

    ![Gereed voor de upgrade](media/service-upgrade-workspaces/power-bi-ready-upgrade.png)

2. Tijdens de upgrade ziet u het bericht dat de **upgrade wordt uitgevoerd**. Meestal duurt het nog geen minuut om uw werkruimte bij te werken.

1. Nadat de upgrade is voltooid, wordt een dialoogvenster weergegeven dat de upgrade is **geslaagd**. U wordt aangeraden [Werk organiseren in de nieuwe werkruimten in Power BI](../service-new-workspaces.md) te lezen, zodat u op de hoogte bent van de verschillen tussen nieuwe werkruimten en klassieke werkruimten.

### <a name="impact-on-other-workspace-users"></a>Gevolgen voor andere gebruikers van de werkruimte

We raden u aan de upgrade uit te voeren buiten kantooruren wanneer er weinig gebruikers actief zijn en items in de werkruimte bekijken of bewerken.

Gebruikers die de werkruimte actief gebruiken, wordt gevraagd hun browser te vernieuwen. Gebruikers die een rapport bewerken, krijgen de mogelijkheid om het rapport op te slaan voordat ze hun browser vernieuwen.

## <a name="upgrade-considerations-and-limitations"></a>Overwegingen en beperkingen voor de upgrade

- De URL's en id's van uw werkruimte, de inhoud van de werkruimte en de app die vanuit de werkruimte wordt gepubliceerd, blijven hetzelfde. Inhoud van inhoudspakketten die in uw werkruimte zijn geïnstalleerd, wordt afzonderlijk afgehandeld. Zie [Inhoudspakketten tijdens de upgrade](#content-packs-during-upgrade) in dit artikel voor meer informatie.
- Inhoudspakketten worden niet ondersteund in de nieuwe werkruimte-ervaring. Lees de secties over [gepubliceerde inhoudspakketten](#published-content-packs) of [geïnstalleerde inhoudspakketten](#installed-content-packs) voor meer informatie over hoe deze worden afgehandeld tijdens de upgrade. Het is raadzaam om inhoudspakketten die in uw werkruimte zijn geïnstalleerd of gepubliceerd te verwijderen voordat u de upgrade uitvoert.
- De Office 365-groep voor uw klassieke werkruimte wordt niet beïnvloed door de upgrade van de werkruimte in Power BI. Alle teams, SharePoint-sites, postvakken of andere resources die worden beheerd door Office 365, worden niet gewijzigd. Ze blijven intact wanneer u de upgrade van uw Power BI-werkruimte uitvoert. Ook de Office 365-groep blijft hetzelfde.
- Er zijn wijzigingen in de manier waarop uw werkruimte wordt beveiligd na de upgrade. Zie de sectie [Machtigingen na de upgrade](#permissions-after-upgrade) voor meer informatie.
- Zo nodig kunt u gebruikmaken van de optie voor **terugkeer naar een klassieke werkruimte**. Bepaalde aspecten van de werkruimte kunnen echter niet volledig worden hersteld naar hoe het was vóór de upgrade. Als u eenmaal functies gebruikt die alleen in de nieuwe werkruimte-ervaring werken, is terugkeer naar een klassieke werkruimte niet meer mogelijk. De optie voor terugkeer is tot 30 dagen na de upgrade beschikbaar.

## <a name="permissions-after-upgrade"></a>Machtigingen na de upgrade

Selecteer **Toegang** in de menubalk boven aan de lijst met werkruimte-inhoud om de machtigingen na de upgrade te controleren.

![Toegang in de menubalk](media/service-upgrade-workspaces/power-bi-workspace-access-menu-bar.png)

Elke Office 365-groepseigenaar wordt afzonderlijk toegevoegd aan de beheerdersrol voor de bijgewerkte werkruimte. De Office 365-groep zelf wordt toegevoegd aan een werkruimterol. De rol waaraan de groep wordt toegevoegd, is afhankelijk van het feit of de klassieke werkruimte is geconfigureerd als *alleen-lezen* of *lezen/schrijven*:

- Als de werkruimte is ingesteld op **Leden kunnen Power BI-inhoud bewerken**, wordt de Office 365-groep na de upgrade toegevoegd aan de toegangslijst voor de werkruimte met de rol **Lid**.
- Als de werkruimte is ingesteld op **Leden kunnen Power BI-inhoud alleen lezen**, wordt de Office 365-groep na de upgrade toegevoegd aan de toegangslijst voor de werkruimte met de rol **Kijker**.

Omdat de Office 365-groep een rol krijgt in de werkruimte, heeft elke gebruiker die aan de Office 365-groep is toegevoegd, die rol in de werkruimte na de upgrade. Als u na de upgrade echter nieuwe eigenaren aan de Office 365-groep toevoegt, hebben ze geen beheerdersrol voor de werkruimte.


### <a name="differences-in-roles-before-and-after-upgrade"></a>Verschillen in rollen voor en na de upgrade

Werkruimterollen in de klassieke werkruimten zijn anders dan die in de nieuwe werkruimten. Met de nieuwe werkruimte-ervaring kunt u werkruimterollen toekennen aan Office 365-groepen,-beveiligingsgroepen of distributielijsten.

- **Leden** kunnen afzonderlijke items delen en toegang tot de hele werkruimte verlenen via de rollen Lid, Inzender of Kijker
- **Kijkers** kunnen alleen inhoud bekijken. Ze kunnen geen onderliggende gegevens exporteren of analyseren in Excel voor werkruimtegegevenssets, tenzij ze de machtiging Build hebben.

Alle gebruikers met toegang tot items in de werkruimte via een machtiging voor delen of een app-machtiging hebben nog steeds toegang tot die items. Iedereen met toegang tot de werkruimte heeft ook toegang tot de app die is gepubliceerd vanuit de werkruimte. Deze gebruikers worden niet vermeld in de toegangslijst voor de app.

U wordt aangeraden te evalueren of u de nieuwe rol Inzender wilt gebruiken. Na de upgrade kunt u de rol van de Office 365-groep in Inzender wijzigen in het deelvenster Toegang.

Na de upgrade kunt u overwegen om een beveiligingsgroep, Office 365-groep of een distributielijst voor werkruimtebeheerders te maken, in plaats van de toegang te beheren via roltoewijzingen aan individuele gebruikers.

Lees hier meer over [rollen in de nieuwe werkruimten](../service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="licensing-after-upgrade"></a>Licentieverlening na de upgrade

Gebruikers met de werkruimterollen Beheerder, Lid of Inzender hebben een Power BI Pro-licentie nodig voor toegang tot de werkruimte.

Als de werkruimte zich in de gedeelde capaciteit bevindt, hebben gebruikers met de werkruimterol Kijker ook een Power BI Pro-licentie nodig voor toegang tot de werkruimte. Als de werkruimte zich in een Premium-capaciteit bevindt, hebben gebruikers met de rol Kijker geen Power BI Pro-licentie nodig voor toegang tot de werkruimte.

## <a name="other-new-workspace-features"></a>Overige nieuwe werkruimtefuncties

De nieuwe werkruimte-ervaring bevat functies die niet beschikbaar zijn in de klassieke werkruimten. Een verschil is de mogelijkheid om een lijst met contactpersonen in te stellen die afwijkt van de lijst met werkruimtebeheerders of -eigenaren. Een overeenkomst is dat deze nog steeds verbonden is met de Share Point-documentbibliotheek van de Office 365-groep. 

### <a name="modify-the-contact-list"></a>De lijst met contactpersonen wijzigen

1. Selecteer **Instellingen** in de menubalk boven aan de lijst met werkruimte-inhoud om de instellingen voor de werkruimte weer te geven.

    ![Instellingen voor werkruimte](media/service-upgrade-workspaces/power-bi-new-workspace-settings.png)

2. Onder **Geavanceerd**, bij **Lijst met contactpersonen**, is de Office 365-groep geconfigureerd waarmee de upgrade van de werkruimte is uitgevoerd. U kunt meer gebruikers of groepen toevoegen aan de lijst met contactpersonen of overschakelen naar werkruimtebeheerders.

    ![Lijst met contactpersonen](media/service-upgrade-workspaces/power-bi-contact-list-workspace.png)

### <a name="the-workspace-onedrive"></a>De werkruimte OneDrive 

Na de upgrade is de werkruimte **OneDrive-** verbonden met de SharePoint-documentbibliotheek van de Office 365-groep. Deze documentbibliotheek wordt weergegeven als de optie **OneDrive** onder **> Gegevens ophalen > Bestanden**. Houd er rekening mee dat gebruikers van de werkruimte alleen zijn gemachtigd voor deze documentbibliotheek als ze lid zijn van de Office 365-groep.

## <a name="content-packs-during-upgrade"></a>Inhoudspakketten tijdens de upgrade

De nieuwe werkruimte-ervaring biedt geen ondersteuning voor inhoudspakketten. Gebruik in plaats daarvan apps en gedeelde gegevenssets voor het distribueren van inhoud in de werkruimte. U kunt het beste gepubliceerde of geïnstalleerde inhoudspakketten uit de werkruimte verwijderen voordat u de upgrade uitvoert. Als er echter inhoudspakketten zijn gepubliceerd of geïnstalleerd wanneer u een upgrade uitvoert, wordt geprobeerd de inhoud te behouden, zoals hieronder wordt beschreven.  Er is geen manier om het inhoudspakket of de koppeling van inhoud aan het inhoudspakket te herstellen na de upgrade.

### <a name="published-content-packs"></a>Gepubliceerde inhoudspakketten

Inhoudspakketten die zijn gepubliceerd vanuit de werkruimte, worden tijdens de upgrade verwijderd. U kunt ze na de upgrade niet publiceren of bijwerken, zelfs niet als u terugkeert naar de klassieke werkruimte. Als anderen uw inhoudspakket hebben geïnstalleerd in hun eigen werkruimten, zien ze na de upgrade een kopie van de inhoud van het inhoudspakket in hun werkruimten. Zie de sectie **Geïnstalleerde inhoudspakketten** voor meer informatie.

### <a name="installed-content-packs"></a>Geïnstalleerde inhoudspakketten

Wanneer u een upgrade van uw werkruimte uitvoert, of een upgrade wordt uitgevoerd van de werkruimte van waaruit het inhoudspakket wordt gepubliceerd, worden er belangrijke wijzigingen aangebracht in geïnstalleerde inhoudspakketten. Na de upgrade bevat uw werkruimte een kopie van de inhoud van het inhoudspakket. Deze is verbonden met de oorspronkelijke gegevensset in de oorspronkelijke werkruimte.

Er zijn echter belangrijke verschillen:

- De inhoud wordt niet meer bijgewerkt als het inhoudspakket wordt bijgewerkt.
- De URL's en item-id's worden gewijzigd en alle bladwijzers of koppelingen die u hebt gedeeld met anderen moeten worden bijgewerkt.
- Alle aanpassingen van gebruikers in het oorspronkelijke inhoudspakket van uw werkruimte gaan verloren. Aanpassingen zijn onder andere abonnementen, waarschuwingen, persoonlijke bladwijzers, permanente filters en favorieten.
- Nieuwe gebruikers hebben mogelijk geen toegang tot de gegevenssets die zich in het inhoudspakket bevonden. U moet er samen met de eigenaar van de gegevensset voor zorgen dat gebruikers van de werkruimte toegang hebben tot de gegevens.

## <a name="go-back-to-a-classic-workspace"></a>Terugkeren naar een klassieke werkruimte

Als onderdeel van de upgrade-ervaring hebt u de mogelijkheid om binnen 30 dagen na de upgrade terug te keren naar een klassieke werkruimte. Met deze functie wordt de koppeling van de werkruimte-inhoud teruggezet met de oorspronkelijke Office 365-groep. Deze optie is beschikbaar voor het geval dat uw organisatie grote problemen ondervindt met het gebruik van de nieuwe werkruimte-ervaring. Er zijn echter beperkingen. Lees eerst [Overwegingen voor terugkeer naar klassiek](#considerations-for-switching-back-to-classic) in dit artikel.

Om te kunnen terugkeren, moet u een eigenaar zijn van de Office 365-groep waaraan de werkruimte was gekoppeld vóór de upgrade. Volg deze stappen.

1. Selecteer in de lijst Inhoud van de werkruimte **Meer opties** ( **...** ) > **Instellingen voor werkruimte**.

    ![Instellingen voor werkruimte](media/service-upgrade-workspaces/power-bi-workspace-settings-more-options.png)

1. Vouw **Geavanceerd** uit en selecteer **Terugkeren naar klassiek**. Als deze optie niet beschikbaar is, raadpleegt u [Overwegingen voor terugkeer naar klassiek](#considerations-for-switching-back-to-classic) in dit artikel.

    ![Terugkeren naar klassiek](media/service-upgrade-workspaces/power-bi-switch-back-classic.png)

1. Wanneer u zover bent, schakelt u het selectie vakje **Ik ben klaar om terug te keren naar klassiek** in en selecteert u de optie voor **terugkeer naar een klassieke werkruimte**. Mogelijk ziet u waarschuwingen of blokkeringen in dit dialoogvenster. Lees de [overwegingen voor terugkeer](#considerations-for-switching-back-to-classic) in dit artikel als u deze problemen ondervindt.

    ![Gereed om terug te keren](media/service-upgrade-workspaces/power-bi-ready-switch-back.png)

1. Wanneer de terugkeer is voltooid, wordt een bevestigingsvenster weergegeven.

    ![Terugkeer geslaagd](media/service-upgrade-workspaces/power-bi-switch-success.png)

### <a name="considerations-for-switching-back-to-classic"></a>Overwegingen voor terugkeer naar klassiek

U kunt niet terugkeren als een of meer van de volgende beweringen over uw werkruimte waar zijn:

- De Office 365-groep is verwijderd.
- Het is meer dan 30 dagen geleden dat u de upgrade hebt uitgevoerd.
- Gegevenssets in de werkruimte worden gebruikt door rapporten of dashboards in andere werkruimten. Hoe gebeurt dit? Stel, u hebt vóór de upgrade een inhoudspakket gepubliceerd vanuit de werkruimte en iemand heeft dat inhoudspakket geïnstalleerd in een andere werkruimte. Onmiddellijk na de upgrade worden de gegevenssets gebruikt door de rapporten en dashboards in dat inhoudspakket.
- De werkruimte maakt deel uit van een beheerpijplijn voor de levenscyclus van toepassingen.
- De werkruimte wordt gebruikt voor sjabloon-apps.
- De werkruimte maakt gebruik van de functie voor grote modellen.
- De werkruimte maakt gebruik van de nieuwe functie voor metrische gegevens over gebruik.

Bij terugkeer naar een klassieke werkruimte wordt er geen exacte kopie van de oorspronkelijke werkruimte teruggezet. De volgende wijzigingen worden aangebracht:

- Machtigingen voor de werkruimte worden ingesteld door de Office 365-groep waarmee de werkruimte oorspronkelijk was verbonden vóór de upgrade.
  - Alle beheerders van de Office 365-groep worden beheerders van de klassieke werkruimte.
  - Alle leden van de Office 365-groep worden leden van de klassieke werkruimte. Als de klassieke werkruimte was ingesteld op **Leden kunnen Power BI-inhoud alleen lezen**, wordt deze instelling hersteld.
  - Gebruikers of gebruikersgroepen die aan de werkruimte zijn toegevoegd nadat de upgrade is voltooid (buiten de Office 365-groep), hebben geen toegang meer tot de werkruimte. Voeg ze toe aan de Office 365-groep om ze toegang te geven. Houd er rekening mee dat Office 365-groepen geen nestbeveiliging of distributiegroepen in het lidmaatschap toestaan.
  - Gebruikers die toegang tot de app voor de werkruimte hebben gekregen, hebben nog steeds toegang tot de app.
  - Gebruikers die toegang tot items in de werkruimte hebben gekregen via delen, hebben nog steeds toegang tot de items.
- Inhoudspakketten die zijn gepubliceerd vanuit de klassieke werkruimte vóór de upgrade, worden niet hersteld.
- Inhoudspakketten die zijn geïnstalleerd in de klassieke werkruimte vóór de upgrade, worden niet hersteld.
- Abonnementen die zijn gemaakt door gebruikers in de werkruimte na de upgrade, worden verwijderd. Abonnementen die al bestonden vóór de upgrade, blijven werken zoals verwacht.
- Gegevensmeldingen blijven niet behouden. Deze worden verwijderd.
- Als u de naam van de werkruimte na de upgrade hebt gewijzigd, wordt de naam van de werkruimte teruggezet zodat deze overeenkomt met de naam van de Office 365-groep.
- Lopende bewerkingen, zoals vernieuwbewerkingen, worden niet beïnvloed door de upgrade van de werkruimte.


## <a name="manage-migration-to-the-new-workspaces-for-your-tenant"></a>Migratie naar de nieuwe werkruimten voor uw tenant beheren 

Sommige organisaties willen een groot aantal of alle werkruimten upgraden naar de nieuwe werkruimte-ervaring. De hulpprogramma's voor het upgraden van werkruimten zijn ontworpen om werkruimtebeheerders in staat te stellen de upgrade uit voeren. Organisaties die een dergelijk proces willen beheren, kunnen de volgende stappen uitvoeren.

1. De lijst met werkruimten in de Power BI-beheerportal en de bijbehorende API bevat alle werkruimten in Power BI. Klassieke werkruimten worden weergegeven met het type Groep in de lijst.
2. Werk met afzonderlijke eigenaren van Office 365-groepen of met uw Office 365-beheerder om de werkruimten te upgraden. Als u de werkruimte wilt upgraden, moet u een eigenaar van de groep worden.

De werkruimte-upgradefunctie biedt geen hulpprogramma's voor bulksgewijze of programmatische upgrades. Daarnaast worden nieuwe Office 365-groepen die zijn gemaakt in uw organisatie, nog steeds weergegeven in Power BI. 
    


## <a name="next-steps"></a>Volgende stappen
* [De nieuwe werkruimten maken in Power BI](../service-create-the-new-workspaces.md)
* [De klassieke werkruimten maken](../service-create-workspaces.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
