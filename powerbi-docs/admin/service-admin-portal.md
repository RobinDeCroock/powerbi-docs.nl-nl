---
title: Power BI-beheerportal
description: Met de beheerportal kunt u instellingen voor de hele organisatie configureren voor Power BI. U kunt metrische gebruiksgegevens bekijken, tenantinstellingen configureren, werken met capaciteit, en werkruimten, organisatievisuals en aanbevolen inhoud weergeven.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/05/2020
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 554cce8c0313ad6624a2991aa09f60c98ff454be
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969587"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Power BI beheren in de beheerportal

De beheerportal stelt u in staat om de Power BI-instellingen voor uw organisatie te beheren. De portal bevat onder andere metrische gegevens over gebruik, toegang tot het Microsoft 365-beheercentrum en instellingen voor Power BI voor alle gebruikers.

De volledige beheerportal is toegankelijk voor globale beheerders en gebruikers met de rol Power BI-servicebeheerder. Als u niet een van deze rollen heeft, ziet u in de portal alleen de optie **Capaciteitsinstellingen**. Zie [Understanding the Power BI admin role](service-admin-role.md) (Power BI-beheerdersrol) voor meer informatie over de beheerdersrol voor de Power BI-service.

## <a name="how-to-get-to-the-admin-portal"></a>Toegang krijgen tot de beheerportal

U moet een globale beheerder of Power BI-servicebeheerder zijn om toegang te krijgen tot de Power BI-beheerportal. Zie [Understanding the Power BI admin role](service-admin-role.md) (Power BI-beheerdersrol) voor meer informatie over de beheerdersrol voor de Power BI-service. Volg deze stappen om naar de Power BI-beheerportal te gaan:

1. Meld u aan bij [Power BI](https://app.powerbi.com) met behulp van de referenties van uw beheerdersaccount.

1. Selecteer in de paginakoptekst **Instellingen** > **Beheerportal**.

   :::image type="content" source="media/service-admin-portal/settings-portal.png" alt-text="Menu Instellingen met beheerportal geselecteerd.":::

De beheerportal bevat verschillende secties. De rest van dit artikel biedt informatie over elk van deze secties.

   :::image type="content" source="media/service-admin-portal/portal-menu.png" alt-text="Menu Beheerportal":::

* [Metrische gegevens over gebruik](#usage-metrics)
* [Gebruikers](#users)
* [Premium per gebruiker (preview)](#premium-per-user-preview)
* [Auditlogboeken](#audit-logs)
* [Tenantinstellingen](#tenant-settings)
* [Capaciteitsinstellingen](#capacity-settings)
* [Codes insluiten](#embed-codes)
* [Organisatievisuals](organizational-visuals.md#organizational-visuals)
* [Azure-verbindingen (preview)](#azure-connections-preview)
* [Werkruimten](#workspaces)
* [Aangepaste huisstijl](#custom-branding)
* [Metrische gegevens voor beveiliging](#protection-metrics)
* [Aanbevolen inhoud](#featured-content)

## <a name="usage-metrics"></a>Metrische gegevens over gebruik

Met de **Metrische gegevens over gebruik** kunt u het Power BI-gebruik voor uw organisatie bewaken. Ook wordt weergegeven welke gebruikers en groepen in uw organisatie het meest actief zijn in Power BI.

> [!NOTE]
> De eerste keer dat u het dashboard opent, of als u het dashboard weergeeft nadat u het lange tijd niet hebt gebruikt, ziet u waarschijnlijk een melding dat het dashboard wordt geladen.

Nadat het dashboard is geladen, ziet u twee secties met tegels. De eerste sectie bevat gebruiksgegevens voor individuele gebruikers, en de tweede sectie bevat vergelijkbare informatie voor groepen.

Hier volgt een overzicht van wat u in elke tegel kunt zien:

* Unieke telling van alle dashboards, rapporten en gegevenssets in de gebruikerswerkruimte.
  
    ![Unieke telling van dashboards, rapporten, gegevenssets](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)


* Het meest gebruikte dashboard qua het aantal gebruikers dat er toegang tot heeft. Bijvoorbeeld: U hebt een dashboard dat u deelt met drie gebruikers. U hebt het dashboard ook toegevoegd aan een inhoudspakket waarmee twee verschillende gebruikers zijn verbonden. Het aantal dashboards is dan 6 (1 + 3 + 2).
  
    ![Meest gebruikte dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* De meest populaire inhoud waarmee gebruikers verbinding hebben gemaakt. Dit is alle inhoud die de gebruikers kunnen bereiken via het proces Gegevens ophalen, zoals SaaS-inhoudspakketten, organisatie-inhoudspakketten, bestanden of databases.

  
    ![Meest gebruikte pakketten](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Een weergave van de actiefste gebruikers op basis van hoeveel dashboards ze hebben, zowel dashboards die ze zelf hebben gemaakt en dashboards die met ze zijn gedeeld.
  
    ![Actiefste gebruikers - dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Een weergave van de actiefste gebruikers op basis van de hoeveelheid rapporten die ze hebben.
  
    ![Actiefste gebruikers - rapporten](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

De tweede sectie bevat hetzelfde type informatie, maar dan op basis van groepen. In deze sectie ziet u welke groepen in uw organisatie het actiefst zijn en wat voor soort inhoud ze gebruiken.

Deze informatie biedt nuttige inzichten in hoe personen Power BI gebruiken in uw organisatie.

## <a name="control-usage-metrics"></a>Metrische gegevens over gebruik beheren

Rapporten met metrische gegevens over gebruik zijn een functie die de Power BI- of globale beheerder kan in- of uitschakelen. Beheerders hebben gedetailleerde controle over welke gebruikers toegang hebben tot metrische gegevens over gebruik. Ze zijn standaard ingeschakeld (**Aan**) voor alle gebruikers in de organisatie.

Beheerders kunnen ook bepalen of makers van inhoud gegevens per gebruiker kunnen bekijken in metrische gegevens over gebruik. 

Zie [Metrische gegevens over het gebruik van Power BI-dashboards en -rapporten bewaken](../collaborate-share/service-usage-metrics.md) voor meer informatie over de rapporten zelf.

### <a name="usage-metrics-for-content-creators"></a>Metrische gegevens over het gebruik voor makers van inhoud

1. Selecteer in de beheerportal **Tenantinstellingen** > **Instellingen voor controle en gebruik** > **Metrische gegevens over het gebruik voor makers van inhoud**.

    ![Metrische gegevens over het gebruik in Tenantinstellingen in de beheerportal](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Schakel metrische gegevens over gebruik in (of uit) > **Toepassen**.

    ![Metrische gegevens over gebruik ingeschakeld](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Gegevens per gebruiker in metrische gegevens over gebruik voor makers van inhoud

Gegevens per gebruiker zijn standaard ingeschakeld voor metrische gebruiksgegevens, en accountgegevens worden opgenomen in het metrische rapport. Als u geen accountgegevens wilt opnemen voor een bepaalde gebruiker of voor alle gebruikers, schakelt u de functie voor bepaalde beveiligingsgroepen of voor een hele organisatie uit. Accountgegevens worden dan in het rapport weergegeven als *Naamloos*.

![Gebruiksgegevens per gebruiker](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Alle bestaande inhoud voor metrische gegevens over gebruik verwijderen

Bij het uitschakelen van metrische gegevens over gebruik voor de gehele organisatie kunnen beheerders ook een of beide van deze opties kiezen:

- **Alle bestaande inhoud voor metrische gegevens over gebruik verwijderen** om alle bestaande rapporten en dashboardtegels te verwijderen die zijn gemaakt met behulp van de rapporten en gegevenssets voor metrische gegevens over gebruik. Deze optie verwijdert alle toegang tot metrische gegevens voor alle gebruikers in de organisatie die deze mogelijk al gebruiken.
- **Verwijder alle bestaande gegevens per gebruiker uit de huidige inhoud van metrische gegevens over gebruik** om alle toegang tot gegevens per gebruiker te verwijderen voor alle gebruikers in de organisatie die deze mogelijk al gebruiken.

Let op, want het verwijderen van bestaande metrische gegevens over gebruik en gegevens per gebruiker kan niet ongedaan worden gemaakt.

## <a name="users"></a>Gebruikers

U beheert Power BI-gebruikers, -groepen en -beheerders in het Microsoft 365-beheercentrum. Het tabblad **Gebruikers** bevat een link naar het beheercentrum.

![Naar het Microsoft 365-beheercentrum gaan](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="premium-per-user-preview"></a>Premium per gebruiker (preview)

Premium per gebruiker is een nieuwe manier om premium-functies per gebruiker te licentiëren. Deze functie is momenteel beschikbaar als preview-product. Nadat aan ten minste één gebruiker een Premium per gebruiker-licentie is toegewezen, kunnen de bijbehorende functies in elke werkruimte worden ingeschakeld. Beheerders kunnen de instellingen voor automatisch vernieuwen en gegevenssetworkload beheren die worden weergegeven voor gebruikers, evenals de bijbehorende standaardwaarden. Bijvoorbeeld: toegang tot het XMLA-eindpunt kan worden uitgeschakeld, ingesteld op alleen-lezen of ingesteld op lezen/schrijven.

   :::image type="content" source="media/service-admin-portal/premium-per-user-options.png" alt-text="Instellingen voor Premium per gebruiker":::.

Zoek in [Power BI Premium per gebruiker: veelgestelde vragen (preview)](service-premium-per-user-faq.md) voor meer informatie over dit licentiemodel.

## <a name="audit-logs"></a>Auditlogboeken

U beheert Power BI-auditlogboeken in het Office 365-centrum voor beveiliging en naleving. Het tabblad **Auditlogboeken** bevat een link naar het centrum voor beveiliging en naleving. Zie [Activiteiten van gebruikers bijhouden in Power BI](service-admin-auditing.md) voor meer informatie.

Als u auditlogboeken wilt gebruiken, zorg dan dat de instelling [**Auditlogboeken maken voor het controleren van interne activiteiten en naleving**](#create-audit-logs-for-internal-activity-auditing-and-compliance) is ingeschakeld.

## <a name="tenant-settings"></a>Tenantinstellingen

Met **Tenantinstellingen** kunt u nauwkeurig bepalen welke functies aan uw organisatie ter beschikking worden gesteld. Als u zich zorgen maakt over gevoelige gegevens, zijn sommige van onze functies mogelijk niet geschikt voor uw organisatie, of misschien wilt u alleen een bepaalde functie beschikbaar stellen aan een specifieke groep.

> [!NOTE]
> Tenantinstellingen waarmee u de beschikbaarheid van functies in de Power BI-gebruikersinterface bepaalt, kunnen helpen bij het vaststellen van beheerbeleid, maar zijn geen beveiligingsmaatregel. De instelling **Gegevens exporteren** beperkt bijvoorbeeld niet de machtigingen van een Power BI-gebruiker voor een gegevensset. Power BI-gebruikers met leestoegang tot een gegevensset hebben de toestemming om deze gegevensset op te vragen en kunnen mogelijk de resultaten behouden zonder de functie **Gegevens exporteren** in de Power BI-gebruikersinterface te gebruiken.

In de volgende secties vindt u meer informatie over de instellingen op het tabblad **Tenantinstellingen**.

> [!NOTE]
> Het duurt maximaal 15 minuten voordat een instelling voor iedereen in uw organisatie is gewijzigd.

Veel instellingen hebben een van deze drie statussen:

* **Uitgeschakeld voor de hele organisatie**: niemand in uw organisatie kan deze functie gebruiken.

    ![Instelling 'Uitgeschakeld voor iedereen'](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Ingeschakeld voor de hele organisatie**: iedereen in uw organisatie kan deze functie gebruiken.

    ![Instelling 'Ingeschakeld voor iedereen'](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Ingeschakeld voor een subset van de organisatie**: Specifieke beveiligingsgroepen in uw organisatie mogen deze functie gebruiken.

    U kunt een functie ook inschakelen voor de hele organisatie **Met uitzondering van beveiligingsgroepen**.

    ![Instelling 'Ingeschakeld voor subset'](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    U kunt instellingen ook combineren om de functie alleen in te schakelen voor een specifieke groep gebruikers en uit te schakelen voor een andere groep gebruikers. Op deze manier kunt u ervoor zorgen dat bepaalde gebruikers geen toegang hebben tot de functie, zelfs niet als ze deel uitmaken van de groep die wel toegang heeft. De meest beperkende instelling voor een gebruiker is van toepassing.

    ![Instelling 'Ingeschakeld met uitzonderingen'](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

In de volgende secties ziet u een overzicht van de verschillende typen tenantinstellingen.

## <a name="tenant-wide-new-look-settings"></a>Instellingen voor het nieuwe uiterlijk voor de hele tenant

Wanneer de optie **Nieuw uiterlijk** is uitgeschakeld, kunnen gebruikers in deze organisatie het nieuwe uiterlijk van Power BI in- of uitschakelen. Wanneer u de optie **Nieuw uiterlijk** inschakelt, zien *alle* gebruikers in deze organisatie de hele tijd de moderne besturingselementen van het nieuwe uiterlijk van Power BI. Ze kunnen het nieuwe uiterlijk niet meer uitschakelen. De optie Nieuw uiterlijk is standaard ingeschakeld.

:::image type="content" source="media/service-admin-portal/admin-portal-new-look-disable.png" alt-text="Schermopname van de optie Nieuw uiterlijk uitschakelen in de beheerportal.":::

## <a name="help-and-support-settings"></a>Instellingen voor Help en ondersteuning

### <a name="publish-get-help-information"></a>Help-informatie publiceren

![Help-informatie publiceren](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

Beheerders kunnen interne URL's opgeven om de bestemming van koppelingen in het Help-menu van Power BI te overschrijven, en voor licentie-upgrades. Als aangepaste URL's zijn ingesteld, worden gebruikers in de organisatie naar interne Help- en ondersteuningsresources geleid, in plaats van naar de standaardbestemmingen. De bestemmingen van de volgende resources kunnen worden aangepast:

* **Learn**. Deze koppeling uit het Help-menu leidt standaard naar een [lijst met al uw Power BI-leertrajecten en -modules](/learn/browse/?products=power-bi). Als u deze koppeling wilt omleiden naar interne trainingsresources, stelt u een aangepaste URL in voor **Trainingsdocumentatie**.

* **Community**. Als u gebruikers vanuit het Help-menu naar een intern forum wilt leiden, in plaats van naar de [Power BI-community](https://community.powerbi.com/), stelt u een aangepaste URL in voor **Discussieforum**.

* **Licentie-upgrades**. Gebruikers met een (gratis) Power BI-licentie kunnen de kans krijgen om hun account bij te werken naar Power BI Pro tijdens het gebruik van de service. Als u een interne URL opgeeft voor **Licentieaanvragen**, leidt u gebruikers om naar een interne aanvraag- en aankoopstroom, en voorkomt u selfservice-aankopen. Raadpleeg [Gebruikers toestaan Power BI Pro uit te proberen](#allow-users-to-try-power-bi-paid-features) als u wilt voorkomen dat gebruikers licenties kopen, maar het wel goed vindt dat gebruikers een proefversie van Power BI Pro starten.

* **Hulp vragen**. Als u gebruikers vanuit het Help-menu naar een interne helpdesk wilt leiden, in plaats van naar [Power BI-ondersteuning](https://powerbi.microsoft.com/support/), stelt u een aangepaste URL in voor **Helpdesk**.

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>E-mailmeldingen ontvangen voor serviceonderbrekingen of incidenten

Voor e-mail ingeschakelde beveiligingsgroepen ontvangen e-mailmeldingen als deze tenant wordt beïnvloed door een serviceonderbreking of incident. Meer informatie over [Meldingen over onderbrekingen van de service](service-interruption-notifications.md).

### <a name="allow-users-to-try-power-bi-paid-features"></a>Gebruikers toestaan betaalde Power BI-functies uit te proberen

![Gebruikersinterface-instellingen: Gebruikers toestaan Power BI Pro uit te proberen](media/service-admin-portal/allow-pro-trial.png)

De instelling om **Gebruikers toestaan betaalde Power BI-functies uit te proberen** is standaard ingeschakeld. Met deze instelling wordt de controle vergroot over hoe gebruikers Power BI Pro-licenties kunnen verkrijgen. In scenario's waarin u selfservice-aankopen hebt geblokkeerd, stelt deze instelling gebruikers in staat om een proefversie van Power BI Pro te starten. De ervaring van eindgebruikers is afhankelijk van hoe u licentie-instellingen samenvoegt. In de onderstaande tabel ziet u hoe upgraden van (gratis) Power BI naar Power BI Pro wordt beïnvloed door verschillende instellingencombinaties:

| Instelling voor selfservice-aankopen | Gebruiker toestaan Power BI Pro uit te proberen | Ervaring voor de eindgebruiker |
| ------ | ------ | ----- |
| Ingeschakeld | Uitgeschakeld | Gebruiker kan een Pro-licentie kopen, maar geen proefversie starten |
| Ingeschakeld | Ingeschakeld | Gebruiker kan een gratis proefversie van Pro starten, en kan upgraden naar een betaalde licentie |
| Uitgeschakeld | Uitgeschakeld | Gebruiker wordt in een bericht gevraagd contact op te nemen met de IT-beheerder om een licentie aan te vragen |
| Uitgeschakeld | Ingeschakeld | Gebruiker kan een proefversie van Pro starten, maar moet contact opnemen met de IT-beheerder om een betaalde licentie te krijgen |

> [!NOTE]
> U kunt een interne URL voor licentieaanvragen toevoegen in [Instellingen voor Help en ondersteuning](#help-and-support-settings). Als u de URL instelt, wordt de standaard-selfserviceaankoopervaring overschreven. De aanmelding wordt niet omgeleid voor proefversie van een Power BI Pro-licentie. Gebruikers die een licentie kunnen kopen in de scenario's die in de bovenstaande tabel zijn beschreven, worden omgeleid naar uw interne URL.

Zie [Selfservice-registratie en -aankopen in- of uitschakelen](service-admin-disable-self-service.md) voor meer informatie.

### <a name="show-a-custom-message-before-publishing-reports"></a>Een aangepast bericht weergeven voordat u rapporten publiceert  

Beheerders kunnen een aangepast bericht opgeven dat wordt weergegeven voordat een gebruiker een rapport publiceert vanuit Power BI Desktop. Nadat u de instelling hebt ingeschakeld, moet u een **aangepast bericht** opgeven. Het aangepaste bericht kan tekst zonder opmaak zijn of de syntaxis voor markdown volgen, zoals in het volgende voorbeeldbericht:

```markdown
#### Important Disclaimer 

Before publishing the report to a workspace, be sure to validate that the appropriate users or groups have access to the destination workspace. If some users or groups should *not* have access to the content and underlying artifacts, remove or modify their access to the workspace, or publish the report to a different workspace. [Learn more](https://docs.microsoft.com/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace). 
```

Het tekstgebied **Aangepast bericht** ondersteunt scrollen, zodat u een bericht kunt maken van maximaal 5.000 tekens.

:::image type="content" source="media/service-admin-portal/admin-show-custom-message.png" alt-text="Schermafbeelding van het aangepaste berichtvenster.":::

Wanneer uw gebruikers rapporten publiceren naar werkruimten in Power BI, zien ze het bericht dat u hebt geschreven.

:::image type="content" source="media/service-admin-portal/admin-user-show-custom-message.png" alt-text="Het dialoogvenster dat uw gebruikers zien wanneer ze rapporten publiceren naar een werkruimte.":::

Net als bij andere tenantinstellingen kunt u kiezen op wie het **aangepaste bericht** van toepassing is:

- **De hele organisatie**.
- **Specifieke beveiligingsgroepen**.
- Of **Specifieke beveiligingsgroepen uitsluiten**.

## <a name="workspace-settings"></a>Instellingen voor werkruimte

In **Tenantinstellingen** in de beheerportal zijn drie secties voor het beheren van werkruimten:

- [De nieuwe werkruimte-ervaringen maken](#create-the-new-workspaces).
- [Gegevenssets in werkruimten gebruiken](#use-datasets-across-workspaces).
- [Het maken van een klassieke werkruimte blokkeren](#block-classic-workspace-creation).

### <a name="create-the-new-workspaces"></a>Nieuwe werkruimten maken

Werkruimten zijn plaatsen waar gebruikers samenwerken aan dashboards, rapporten en andere inhoud. Beheerders gebruiken de instelling **Werkruimten maken (nieuwe werkruimte-ervaring)** om aan te geven welke gebruikers in de organisatie werkruimten mogen maken. Beheerders kunnen iedereen of niemand binnen de organisatie toestemming geven om werkruimten te maken. Ze kunnen het maken van werkruimten ook beperken tot leden van specifieke beveiligingsgroepen. Meer informatie over [werkruimten](../collaborate-share/service-new-workspaces.md).

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="Werkruimten maken (nieuwe werkruimte-ervaring)":::

Voor klassieke werkruimten die zijn gebaseerd op Microsoft 365-groepen, blijft het beheer geconcentreerd in de beheerportal en Azure Active Directory.

> [!NOTE]
> Met de instelling **Werkruimten maken (nieuwe werkruimte-ervaring)** kunnen alleen gebruikers die Microsoft 365-groepen kunnen maken, nieuwe werkruimten maken in Power BI. Zorg ervoor dat u in de Power BI-beheerportal een waarde instelt om ervoor te zorgen dat de juiste gebruikers nieuwe werkruimten kunnen maken.

**Lijst met werkruimten**

De beheerportal heeft nog een sectie met instellingen over de werkruimten in uw tenant. In die sectie kunt u de lijst werkruimten sorteren en filteren, en de details van elke werkruimte weergeven. Zie [Werkruimten](#workspaces) in dit artikel voor meer informatie.

**Inhoudspakketten en apps publiceren**

In de beheerportal bepaalt u ook welke gebruikers machtigingen krijgen om apps naar de organisatie te distribueren. Zie [Inhoudspakketten en apps naar de volledige organisatie publiceren](#publish-content-packs-and-apps-to-the-entire-organization) in dit artikel voor meer informatie.

### <a name="use-datasets-across-workspaces"></a>Gegevenssets in werkruimten gebruiken

Beheerders kunnen bepalen welke gebruikers in de organisatie gegevenssets kunnen gebruiken in verschillende werkruimten. Als deze instelling is ingeschakeld, hebben gebruikers nog steeds de vereiste machtiging voor het maken van een specifieke gegevensset nodig.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="Gegevenssets in werkruimten gebruiken":::

Zie [Inleiding tot gegevenssets in werkruimten](../connect-data/service-datasets-across-workspaces.md) voor meer informatie.

### <a name="block-classic-workspace-creation"></a>Het maken van een klassieke werkruimte blokkeren

Beheerders kunnen bepalen of de organisatie klassieke werkruimten kan maken. Als deze instelling is ingeschakeld, kunnen gebruikers die alleen werkruimten maken deze alleen maken in de nieuwe werkruimte-ervaring. 

![Het maken van een klassieke werkruimte blokkeren](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

Als deze functie is ingeschakeld, worden nieuw gemaakte Office 365-groepen niet weergegeven in de lijst Power BI-werkruimten. Bestaande klassieke werkruimten worden nog steeds weergegeven in de lijst. Als de instelling is uitgeschakeld, worden alle Office 365-groepen waarvan de gebruiker lid is, weergegeven in de lijst met werkruimten. Meer informatie over [werkruimten in de nieuwe werkruimte-ervaring](../collaborate-share/service-new-workspaces.md).

## <a name="export-and-sharing-settings"></a>Instellingen voor exporteren en delen

### <a name="allow-azure-active-directory-guest-users-to-access-power-bi"></a>Gastgebruikers van Azure Active Directory toegang tot Power BI geven

Als u deze instelling inschakelt, hebben gastgebruikers van Azure Active Directory Business-to-Business (Azure AD B2B) toegang tot Power BI. Als u deze instelling uitschakelt, ontvangen gastgebruikers een foutmelding als ze Power BI willen openen. Als u deze instelling voor de hele organisatie uitschakelt, kunnen gebruikers ook geen gasten voor uw organisatie uitnodigen. Gebruik de optie specifieke beveiligingsgroepen om te bepalen welke gastgebruikers toegang hebben tot Power BI.

![Gastgebruikers van Azure Active Directory toegang tot Power BI geven](media/service-admin-portal/powerbi-admin-allow-aad-b2b-guests.png)

### <a name="invite-external-users-to-your-organization"></a>Externe gebruikers uitnodigen voor uw organisatie 

De instelling **Externe gebruikers uitnodigen voor uw organisatie** helpt organisaties om te kiezen of nieuwe externe gebruikers voor de organisatie kunnen worden uitgenodigd via delen en het verlenen van machtigingen in Power BI. Als deze instelling is uitgeschakeld, kan een externe gebruiker die nog geen gastgebruiker in de organisatie is, niet via Power BI aan de organisatie worden toegevoegd.

![Externe gebruikers uitnodigen voor uw organisatie](media/service-admin-portal/powerbi-admin-allow-invite-aad-b2b-guests.png)

> [!IMPORTANT]
> Deze instelling heette vroeger 'Inhoud delen met externe gebruikers'. De gewijzigde naam weerspiegelt nauwkeuriger wat de instelling doet.

Als een gebruiker externe gebruikers wil uitnodigen tot een organisatie, moet deze ook de rol van gastuitnodiger in Azure Active Directory hebben. Met deze instelling kan alleen de mogelijkheid worden beheerd om iemand via Power BI uit te nodigen. 

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren

Azure AD B2B-gastgebruikers kunnen inhoud in de organisatie bewerken en beheren. [Meer informatie](service-admin-azure-ad-b2b.md)

In de volgende afbeelding ziet u de optie Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren.

![Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

In de beheerportal bepaalt u ook welke gebruikers machtigingen krijgen om externe gebruikers uit te nodigen voor de organisatie. Raadpleeg [Inhoud delen met externe gebruikers](#export-and-sharing-settings) in dit artikel voor details.

### <a name="publish-to-web"></a>Publiceren op internet

Als Power BI-beheerder krijgt u met de instelling **Publiceren op internet** opties waarmee gebruikers invoegcodes kunnen maken voor het publiceren van rapporten op internet. Met deze functionaliteit wordt het rapport en de gegevens die het bevat, beschikbaar voor iedereen op internet. Meer informatie over [publiceren op internet](../collaborate-share/service-publish-to-web.md).

> [!NOTE]
> Alleen Power BI-beheerders kunnen iemand machtigen verlenen voor het maken van nieuwe invoegcodes voor publiceren op internet. Organisaties kunnen bestaande invoegcodes hebben. Zie de sectie [Invoegcodes](service-admin-portal.md#embed-codes) van de beheerportal om momenteel gepubliceerde rapporten te bekijken.

De volgende afbeelding toont het menu **Meer options (...)** voor een rapport wanneer de instelling **Publiceren op internet** is ingeschakeld.

![Publiceren op internet via het menu Meer opties](media/service-admin-portal/power-bi-more-options-publish-web.png)

De instelling **Publiceren op internet** in de beheerportal bevat opties waarvoor gebruikers invoegcodes kunnen maken.

![Instelling 'Publiceren op internet'](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Beheerders kunnen **Publiceren op internet** instellen op **Ingeschakeld** en de optie **Kiezen hoe invoegcodes werken** op **Alleen bestaande invoegcodes toestaan**. In dat geval kunnen gebruikers invoegcodes maken, maar moeten ze contact opnemen met de Power BI-beheerder om hiervoor toestemming te krijgen.

![Prompt voor publiceren op internet](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

Gebruikers zien verschillende opties in de gebruikersinterface, afhankelijk van de instelling **Publiceren op internet**.

|Functie |Ingeschakeld voor de hele organisatie |Uitgeschakeld voor de hele organisatie |Specifieke beveiligingsgroepen   |
|---------|---------|---------|---------|
|**Publiceren op internet** onder het menu **Meer opties (...)** van het rapport|Ingeschakeld voor iedereen|Niet voor iedereen zichtbaar|Alleen zichtbaar voor gemachtigde gebruikers of groepen.|
|**Invoegcodes beheren** onder **Instellingen**|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen|Ingeschakeld voor iedereen<br><br>Optie * **Verwijderen** alleen voor gemachtigde gebruikers of groepen.<br>* **Ophalen van codes** ingeschakeld voor iedereen.|
|**Codes invoegen** binnen de beheerportal|De status heeft een van de volgende waarden:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd|De status geeft **Uitgeschakeld** weer|De status heeft een van de volgende waarden:<br>* Actief<br>* Niet ondersteund<br>* Geblokkeerd<br><br>Als een gebruiker niet is geautoriseerd op basis van de tenantinstelling, wordt de status weergegeven als **geschonden**.|
|Bestaande gepubliceerde rapporten|Iedereen ingeschakeld|Iedereen uitgeschakeld|Rapporten blijven weergeven voor iedereen.|

### <a name="copy-and-paste-visuals"></a>Visuals kopiëren en plakken

Gebruikers in de organisatie kunnen visuals kopiëren van een tegel, of visuals rapporteren en plakken in externe toepassingen.

![Schermopname van schaeklaar voor het inschakelen van kopiëren en plakken van visuals.](media/service-admin-portal/powerbi-admin-portal-copy-paste-visuals-setting.png)

### <a name="export-to-excel"></a>Exporteren naar Excel

Gebruikers in de organisatie kunnen de gegevens van een visualisatie exporteren naar een Excel-bestand.

![Schermopname van de instelling Exporteren naar Excel](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

### <a name="export-to-csv"></a>Exporteren naar CSV

Gebruikers in de organisatie kunnen gegevens van een tegel, een visualisatie of een gepagineerd rapport exporteren naar een CSV-bestand.

![Schermopname van de instelling Exporteren naar CSV](media/service-admin-portal/powerbi-admin-portal-export-to-csv-setting.png)

### <a name="download-reports"></a>Rapporten downloaden

Gebruikers in de organisatie kunnen PBIX-bestanden en gepagineerde rapporten downloaden.

![Schermopname van de instelling Rapporten downloaden.](media/service-admin-portal/powerbi-admin-portal-download-reports-setting.png)

### <a name="allow-live-connections"></a>Live-verbindingen toestaan

Gebruikers in de organisatie kunnen de Power BI-service Live Connect gebruiken. Als u live-verbindingen toestaat, kunnen gebruikers ook analyseren in Excel.

![Schermopname van de instelling Live-verbindingen toestaan.](media/service-admin-portal/powerbi-admin-portal-allow-live-connections-setting.png)

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Rapporten als PowerPoint-presentaties of PDF-documenten exporteren

Gebruikers binnen de organisatie kunnen rapporten als PowerPoint-bestanden of PDF-documenten exporteren.

![Schermopnamen van rapporten als PowerPoint- of PDF-documenten exporteren.](media/service-admin-portal/powerbi-admin-portal-export-pptx-pdf-setting.png)

### <a name="export-reports-as-mhtml-documents"></a>Rapporten exporteren als MHTML-document

Gebruikers in de organisatie kunnen gepagineerde rapporten als MHTML-document exporteren.

![Schermopname van de instelling Exporteren naar MHTML.](media/service-admin-portal/powerbi-admin-portal-export-mhtml-setting.png)

### <a name="export-reports-as-word-documents"></a>Rapporten exporteren als Word-document

Gebruikers in de organisatie kunnen gepagineerde rapporten als Word-document exporteren.

![Schermopname van de instelling Exporteren naar Word.](media/service-admin-portal/powerbi-admin-portal-export-word-setting.png)

### <a name="export-reports-as-xml-documents"></a>Rapporten exporteren als XML-document

Gebruikers in de organisatie kunnen gepagineerde rapporten als XML-document exporteren.

![Schermopname van de instelling Exporteren naar XML.](media/service-admin-portal/powerbi-admin-portal-export-xml-setting.png)

### <a name="export-reports-as-image-files-preview"></a>Rapporten exporteren als afbeeldingsbestanden (preview-versie)

Gebruikers in de organisatie kunnen de API voor het exporteren van rapporten naar bestanden gebruiken om rapporten te exporteren als afbeeldingsbestanden.

![Schermopname van de instelling Exporteren als afbeelding.](media/service-admin-portal/powerbi-admin-portal-export-as-image-setting.png)

### <a name="print-dashboards-and-reports"></a>Dashboards en rapporten afdrukken


![Schermopname van de instelling Dashboards en rapporten afdrukken.](media/service-admin-portal/powerbi-admin-portal-print-dashboards-reports-setting.png)

### <a name="certification"></a>Certificering
Gebruikers in deze organisatie toestaan om gegevenssets, gegevensstromen, rapporten en apps te certificeren. Raadpleeg [Inhoudscertificering inschakelen](service-admin-setup-certification.md) voor meer informatie.

### <a name="email-subscriptions"></a>E-mailabonnementen
Gebruikers in de organisatie kunnen e-mailabonnementen maken. Meer informatie over [abonnementen](../collaborate-share/service-report-subscribe.md).

![E-mailabonnementen inschakelen](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Aanbevolen inhoud

Toestaan dat sommige of alle auteurs van rapporten in uw organisatie hun inhoud in de sectie Aanbevolen van de Power BI-startpagina kunnen aanbevelen. Nieuwe gebruikers krijgen bovenaan hun Power BI-startpagina de aanbevolen inhoud te zien. De aanbevolen inhoud schuift omlaag op de startpagina wanneer gebruikers **Favorieten**, **Vaak gebruikte items** en **Recente items** toevoegen. 

We raden u aan eerst te beginnen met een klein aantal promotors. Wanneer de hele organisatie inhoud mag aanbevelen op de startpagina, kan het lastig zijn om alle gepromoveerde inhoud bij te houden. 

Wanneer u aanbevolen inhoud hebt ingeschakeld, kunt u deze ook beheren in de Beheerportal. Zie [Aanbevolen inhoud beheren](#manage-featured-content) in dit artikel voor meer informatie over het beheren van aanbevolen inhoud in uw domein.

### <a name="allow-connections-to-featured-tables"></a>Verbindingen met aanbevolen tabellen toestaan

Met deze instelling kunnen Power BI-beheerders bepalen wie in de organisatie aanbevolen tabellen kan gebruiken in de galerie Gegevenstypen van Excel. 

![Schermopname van de instelling Verbindingen met aanbevolen tabellen toestaan.](media/service-admin-portal/powerbi-admin-portal-allow-connections-featured-tables-setting.png)

>[!NOTE]
>Verbindingen met aanbevolen tabellen worden ook uitgeschakeld als de instelling [Live-verbindingen toestaan](#allow-live-connections) is ingesteld op Uitgeschakeld.

Meer informatie over [Uitgelichte Power BI-tabellen in Excel](../collaborate-share/service-excel-featured-tables.md).

### <a name="share-to-teams"></a>Delen in Teams

Met deze instelling kunnen organisaties de knoppen voor **Delen in Teams** verbergen in de Power BI-service. Indien de instelling is uitgeschakeld, zien gebruikers de knoppen **Delen in Teams** niet op de actiebalk of in de contextmenu's bij het bekijken van rapporten en dashboards in de Power BI-service.

![Schermopname van de tenantinstelling Delen in Teams in de Power BI-beheerportal.](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

Meer informatie over [het delen van Power BI-inhoud in Teams](../collaborate-share/service-share-report-teams.md).

## <a name="content-pack-and-app-settings"></a>Instellingen voor inhoudspakket en app

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Inhoudspakketten en apps naar de volledige organisatie publiceren

Beheerders gebruiken deze instelling om te bepalen welke gebruikers inhoudspakketten en apps naar de volledige organisatie mogen publiceren, in plaats van naar specifieke groepen. Meer informatie over [het publiceren van apps](../collaborate-share/service-create-distribute-apps.md).

De volgende afbeelding toont de optie **Mijn hele organisatie** bij het maken van een inhoudspakket.

![Inhoudspakket publiceren naar organisatie](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Sjabloon-apps en organisatie-inhoudspakketten maken

Gebruikers in de organisatie kunnen sjabloon-apps en organisatie-inhoudspakketten maken die gegevenssets gebruiken die zijn gebaseerd op één gegevensbron in Power BI Desktop. Meer informatie over [sjabloon-apps](../connect-data/service-template-apps-create.md).

### <a name="push-apps-to-end-users"></a>Apps pushen naar eindgebruikers

Makers van rapporten kunnen apps rechtstreeks met eindgebruikers delen zonder dat er installatie vanuit [AppSource](https://appsource.microsoft.com) is vereist. Meer informatie over [het automatisch installeren van apps voor eindgebruikers](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Instellingen voor integratie

### <a name="allow-xmla-endpoints-and-analyze-in-excel-with-on-premises-datasets"></a>XMLA-eindpunten en Analyseren in Excel toestaan met on-premises gegevenssets

Gebruikers in de organisatie kunnen Excel gebruiken voor het weergeven van on-premises Power BI-gegevenssets en het werken met deze sets. Hierdoor worden ook verbindingen met XMLA-eindpunten toegestaan. [Meer informatie](../collaborate-share/service-analyze-in-excel.md)

### <a name="use-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI gebruiken

Gebruikers in de organisatie kunnen de visualisatie ArcGIS Maps for Power BI, die is geleverd door Esri, gebruiken. [Meer informatie](../visuals/power-bi-visualizations-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Algemene zoekopdrachten voor Power BI gebruiken (preview-versie)

Gebruikers in de organisatie kunnen externe-zoekopdrachtfuncties gebruiken waarbij gebruik wordt gemaakt van Azure Search.

## <a name="r-visuals-settings"></a>Instellingen voor R-visuals

### <a name="interact-with-and-share-r-visuals"></a>Interactie met visuele R-elementen en visuele R-elementen delen

Gebruikers in de organisatie kunnen interactie hebben met visuele elementen die zijn gemaakt met R scripts en deze elementen delen. [Meer informatie](../visuals/service-r-visuals.md)

> [!NOTE]
> Deze instelling geldt voor de hele organisatie en kan niet worden beperkt tot specifieke groepen.

## <a name="audit-and-usage-settings"></a>Instellingen voor controle en gebruik

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Auditlogboeken maken voor het controleren van interne activiteiten en naleving

Gebruikers in de organisatie kunnen de auditfunctie gebruiken voor het controleren van acties die door andere gebruikers in de organisatie worden uitgevoerd in Power BI. [Meer informatie](service-admin-auditing.md)

Deze instelling moet worden ingeschakeld om vermeldingen te kunnen vastleggen in het auditlogboek. Er kan een vertraging tot 48 uur optreden tussen het inschakelen van de controlefunctie en het kunnen weergeven van controlegegevens. Als u niet direct gegevens ziet, controleert u de controlelogboeken op een later tijdstip. Er kan een vergelijkbare vertraging optreden tussen het ophalen van machtiging voor het weergeven van controlelogboeken en het kunnen openen van de logboeken.

> [!NOTE]
> Deze instelling geldt voor de hele organisatie en kan niet worden beperkt tot specifieke groepen.

### <a name="usage-metrics-for-content-creators"></a>Metrische gegevens over het gebruik voor makers van inhoud

Gebruikers in de organisatie kunnen metrische gegevens weergeven over het gebruik van de dashboards en rapporten die ze hebben gemaakt. [Meer informatie](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Gegevens per gebruiker in metrische gegevens over gebruik voor makers van inhoud

In metrische gegevens over het gebruik voor makers van inhoud zijn namen en e-mailadressen zichtbaar van gebruikers die inhoud openen. [Meer informatie](../collaborate-share/service-usage-metrics.md)

Standaard wordt Gegevens per gebruiker ingeschakeld voor metrische gegevens over gebruik. Accountgegevens van makers van inhoud worden in het metrische rapport opgenomen. Als u deze informatie niet voor alle gebruikers wilt verzamelen, schakelt u de functie voor bepaalde beveiligingsgroepen of voor een hele organisatie uit. Accountgegevens voor de uitgesloten gebruikers worden dan in het rapport weergegeven als *Naamloos*.

## <a name="dashboard-settings"></a>Instellingen voor dashboard

### <a name="data-classification-for-dashboards"></a>Gegevensclassificatie voor dashboards

Gebruikers in de organisatie kunnen dashboards taggen met classificaties die het beveiligingsniveau van het dashboard aangeven. [Meer informatie](../create-reports/service-data-classification.md)

> [!NOTE]
> Deze instelling geldt voor de hele organisatie en kan niet worden beperkt tot specifieke groepen.

### <a name="web-content-on-dashboard-tiles"></a>Webinhoud op dashboardtegels

Gebruikers in de organisatie kunnen tegels voor webinhoud toevoegen en weergeven op Power BI-dashboards. [Meer informatie](../create-reports/service-dashboard-add-widget.md)

> [!NOTE]
> Dit kan uw organisatie blootstellen aan beveiligingsrisico's via schadelijke webinhoud.

## <a name="developer-settings"></a>Instellingen voor ontwikkelaars

### <a name="embed-content-in-apps"></a>Inhoud in apps insluiten

Gebruikers in de organisatie kunnen Power BI-dashboards en rapporten insluiten in SaaS-toepassingen (Software as a Service). Als u deze instelling uitschakelt, kunnen gebruikers de REST API's niet gebruiken om inhoud van Power BI in hun toepassing in te sluiten. [Meer informatie](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Toestaan dat service-principals gebruikmaken van API's van Power BI

Web-apps die in Azure AD (Active Directory) zijn geregistreerd, maken gebruik van een toegewezen service-principal voor toegang tot API's van Power BI zonder een aangemelde gebruiker. Als u wilt toestaan dat een app verificatie via een service-principal gebruikt, moet de betreffende service-principal worden opgenomen in een beveiligingsgroep die toegang heeft. [Meer informatie](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> Service-principals nemen de machtigingen voor alle instellingen van de Power BI-tenant over van hun beveiligingsgroep. Als u deze machtigingen wilt beperken, maakt u een specifieke beveiligingsgroep voor service-principals en voegt u deze toe aan de lijst Behalve specifieke beveiligingsgroepen voor de desbetreffende, ingeschakelde Power BI-instellingen.

## <a name="dataflow-settings"></a>Gegevensstroominstellingen

### <a name="create-and-use-dataflows"></a>Gegevensstromen maken en gebruiken

Gebruikers in de organisatie kunnen gegevensstromen maken en gebruiken. Zie [Selfservice voor gegevensvoorbereiding in Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md) voor een overzicht van gegevensstromen. Zie [Workloads configureren](service-admin-premium-workloads.md) als u gegevensstromen wilt inschakelen in een Premium-capaciteit.

> [!NOTE]
> Deze instelling geldt voor de hele organisatie en kan niet worden beperkt tot specifieke groepen.

## <a name="template-apps-settings"></a>Instellingen voor sjabloon-apps

Drie instellingen bepalen wie de mogelijkheid heeft om sjabloon-apps te publiceren of te installeren.

![Instellingen voor sjabloon-apps in de Power BI-beheerportal](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Sjabloon-apps publiceren

Gebruikers in de organisatie kunnen werkruimten voor sjabloon-apps maken. U bepaalt welke gebruikers sjabloon-apps mogen publiceren of distribueren aan clients buiten uw organisatie via [AppSource](https://appsource.microsoft.com) of andere distributiemethoden.

![Instelling voor de publicatiesjabloon-apps zijn ingeschakeld voor de hele organisatie](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Sjabloon-apps installeren die in AppSource worden vermeld

Gebruikers in de organisatie kunnen **alleen** vanuit [AppSource](https://appsource.microsoft.com) sjabloon-apps downloaden en installeren. U bepaalt welke specifieke gebruikers of beveiligingsgroepen sjabloon-apps mogen installeren vanuit AppSource.

![Instelling voor het installeren van sjabloon-apps](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Sjabloon-apps installeren die niet in AppSource worden vermeld

U bepaalt welke gebruikers in de organisatie sjabloon-apps mogen downloaden en installeren die **niet in [ AppSource](https://appsource.microsoft.com) worden vermeld**.

![Sjabloon-apps installeren die niet in de AppSource-instelling worden vermeld](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Capaciteitsinstellingen

### <a name="power-bi-premium"></a>Power BI Premium

Via het tabblad **Power BI Premium-instellingen** kunt u capaciteiten van Power BI Premium (Em of P SKU) beheren die voor uw organisatie zijn gekocht. Alle gebruikers binnen uw organisatie kunnen het tabblad **Power BI Premium-instellingen** zien, maar ze zien alleen inhoud op het tabblad als ze zijn aangewezen als *Capaciteitsbeheerder* of als ze beschikken over toewijzingsmachtigingen. Als een gebruiker geen machtigingen heeft, verschijnt het volgende bericht.

![Geen toegang tot Premium-instellingen](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

Via het tabblad **Power BI Embedded-instellingen** kunt u de capaciteiten van Power BI Embedded (A SKU) bekijken die u voor uw klant hebt aangeschaft. Aangezien u alleen A SKU's vanuit Azure kunt aanschaffen, kunt u [ingesloten capaciteiten in Azure beheren](../developer/embedded/azure-pbie-create-capacity.md) vanuit de **Azure-portal**.

Zie [Wat is Power BI Embedded?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md) voor meer informatie over het beheren van Power BI Embedded (A SKU)-instellingen.

## <a name="embed-codes"></a>Codes insluiten

Als beheerder kunt u de invoegcodes weergeven die worden gegenereerd voor uw tenant om rapporten openbaar te delen. U kunt ook codes intrekken of verwijderen. [Meer informatie](../collaborate-share/service-publish-to-web.md)

![Codes invoegen binnen de Power Bi-beheerportal](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals"></a>Organisatievisuals

Alle beheerinstellingen voor Power BI-visuals, inclusief tenantinstellingen voor Power BI-visuals, worden beschreven in [Beheerinstellingen voor Power BI-visuals beheren](organizational-visuals.md).

## <a name="azure-connections-preview"></a>Azure-verbindingen (preview)

### <a name="tenant-level-storage-preview"></a>Opslag op tenantniveau (preview)

Gegevens die worden gebruikt met Power BI worden standaard opgeslagen in de interne opslag die wordt geleverd door Power BI. Met de integratie van gegevensstromen en Azure Data Lake Storage Gen2 (ADLS Gen2) kunt u uw gegevensstromen opslaan in het Azure Data Lake Storage Gen2-account van uw organisatie. Ga naar [Integratie van gegevensstromen en Azure Data Lake (preview)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md) voor meer informatie.

### <a name="workspace-level-storage-permissions-preview"></a>Opslagmachtigingen op werkruimteniveau (preview)

Werkruimtebeheerders mogen standaard niet hun eigen opslagaccount verbinden. Met deze preview-functie kunt u een instelling inschakelen op basis waarvan is toegestaan dat werkruimtebeheerders hun eigen opslagaccount verbinden.

## <a name="workspaces"></a>Werkruimten

Als beheerder kunt u op het tabblad **Werkruimten** alle werkruimten bekijken die aanwezig zijn in uw tenant. Op dit tabblad kunt u deze acties uitvoeren:

- De lijst met werkruimten en de bijbehorende gegevens vernieuwen.
- De gegevens over de werkruimten exporteren in een CSV-bestand. 
- Details van een werkruimte bekijken, inclusief de id, de bijbehorende gebruikers en hun rollen, en de dashboards, rapporten en gegevenssets.
- De lijst met personen die toegang hebben bewerken. Dit betekent dat u de werkruimte kunt verwijderen. U kunt uzelf als beheerder toevoegen aan een werkruimte, en vervolgens de werkruimte openen en verwijderen.
- De velden Naam en Beschrijving bewerken.
- Klassieke werkruimten upgraden naar de toepassing met nieuwe werkruimten

![Lijst met werkruimten](media/service-admin-portal/workspaces-list.png)

Beheerders kunnen ook bepalen of gebruikers een werkruimte in de nieuwe werkruimte-ervaring, of een klassieke werkruimte kunnen maken. Zie [Instellingen voor werkruimte](#workspace-settings) in dit artikel voor meer informatie.

De tabelkolommen op het tabblad **Werkruimten** komen overeen met de eigenschappen die worden geretourneerd met de [REST API voor Power BI-beheer](/rest/api/power-bi/admin) voor werkruimten. Persoonlijke werkruimten zijn van het type **PersonalGroup**, klassieke werkruimten zijn van het type **Group** en werkruimten met de nieuwe werkruimte-ervaring zijn van het type **Workspace**. Zie [Werk organiseren in de nieuwe werkruimten](../collaborate-share/service-new-workspaces.md) voor meer informatie.

Op het tabblad **Werkruimten** wordt de *status* voor elke werkruimte weergegeven. De volgende tabel bevat meer informatie over de betekenis van deze statussen.

|Staat  |Beschrijving  |
|---------|---------|
| **Actief** | Een normale werkruimte. Er wordt geen informatie gegeven over het gebruik of de inhoud ervan, alleen dat de werkruimte zelf 'normaal' is. |
| **Zwevend** | Een werkruimte zonder gebruiker met beheerdersrechten. |
| **Verwijderd** | Een verwijderde werkruimte. We bewaren gedurende 90 dagen voldoende metagegevens om de werkruimte te herstellen indien gewenst. |
| **Verwijderen** | Een werkruimte die wordt verwijderd, maar nog niet is verdwenen. Gebruikers kunnen hun eigen werkruimten verwijderen door items in Verwijderen en uiteindelijk Verwijderd te plaatsen. |

Beheerders kunnen ook werkruimten beheren en herstellen met behulp van de beheerportal of PowerShell-cmdlets. 

![Lijst met werkruimten](media/service-admin-portal/workspaces-list.png)

Beheerders kunnen klassieke werkruimten upgraden naar de toepassing met nieuwe werkruimten. Beheerders kunnen een of meer werkruimten van het type **Groep** selecteren om deze te upgraden. Upgrades worden asynchroon in de wachtrij geplaatst en uitgevoerd. Het kan enkele minuten tot enkele dagen duren voordat alle upgrades met de status **In behandeling** zijn voltooid, omdat het totale aantal upgrades dat door beheerders wordt gestart beperkt wordt, zodat de service probleemloos kan worden uitgevoerd. Met de kolom **Status van upgrade voor werkruimte** kunnen beheerders de voortgang bijhouden van upgrades die worden gestart door beheerders. Beheerders kunnen upgrades die worden gestart door beheerders annuleren wanneer deze de status **In behandeling** hebben. Als u een werkruimte onmiddellijk wilt upgraden, neemt u contact op met de werkruimtebeheerder en laat u deze de upgrade starten via het deelvenster met de instellingen voor de werkruimte. [Lees meer over de upgrade van werkruimten voordat u begint met het upgraden van de werkruimte die door de Power BI-beheerder wordt gestart.](../collaborate-share/service-upgrade-workspaces.md).

De volgende tabel bevat meer informatie over de status van de upgrade.

|Status  |Beschrijving  |
|---------|---------|
| **(Leeg)** | De werkruimte wordt niet geüpgraded door een Power BI-beheerder. |
| **In behandeling** | De werkruimte is in de wachtrij geplaatst om te worden geüpgraded. De upgrade kan worden geannuleerd. |
| **Wordt uitgevoerd** | De werkruimte wordt momenteel geüpgraded. De upgrade kan niet worden geannuleerd. |
| **Voltooid** | De werkruimte is in de afgelopen 30 dagen geüpgraded door een Power BI-beheerder. Een werkruimtebeheerder kan desgewenst terugkeren naar de klassieke optie tijdens de periode van 30 dagen na de upgrade van de werkruimte. |


## <a name="custom-branding"></a>Aangepaste huisstijl

Als beheerder kunt u het uiterlijk van Power BI aanpassen voor uw hele organisatie. Op dit moment zijn er drie hoofdopties:

![Opties voor aangepaste huisstijl](media/service-admin-portal/power-bi-custom-branding.png)

* **Logo uploaden**: het beste resultaat krijgt u als u een logo uploadt dat is opgeslagen als een PNG-bestand van maximaal 10 kB en ten minste 200 x 30 pixels.

* **Voorbladafbeelding uploaden**: het beste resultaat krijgt u als u een voorbladafbeelding uploadt die is opgeslagen als een JPG- of PNG-bestand van maximaal 1 MB en ten minste 1920 x 160 pixels.

* **Themakleur selecteren**: U kunt een thema selecteren op basis van een hexadecimale waarde, een RGB-waarde of uit het beschikbare palet.


Zie [Aangepaste huisstijl voor uw organisatie](https://aka.ms/orgBranding) voor meer informatie.

## <a name="protection-metrics"></a>Metrische gegevens voor beveiliging

Nadat u gegevensbeveiliging voor Power BI hebt ingeschakeld, zijn metrische gegevens voor gegevensbeveiliging zichtbaar in de beheerportal. In dit rapport wordt weergegeven hoe vertrouwelijkheidslabels u helpen uw inhoud te beveiligen.

## <a name="manage-featured-content"></a>Aanbevolen inhoud beheren

Als Power BI-beheerder kunt u alle rapporten, dashboards en apps beheren die nu worden weergegeven in de sectie Aanbevolen op de Power BI-startpagina in uw organisatie.

- Selecteer **Aanbevolen inhoud** in de Beheerportal.

Hier ziet u een overzicht van de personen die de inhoud hebben aanbevolen, wanneer de inhoud is aanbevolen en alle bijbehorende relevante metagegevens. Als iets er verdacht uitziet of als u de sectie Aanbevolen wilt opschonen, kunt u indien nodig gepromoveerde inhoud verwijderen.

Zie [Aanbevolen inhoud](#featured-content) in dit artikel voor meer informatie over het inschakelen van aanbevolen inhoud.

## <a name="next-steps"></a>Volgende stappen

[Power BI in uw organisatie beheren](service-admin-administering-power-bi-in-your-organization.md)  
[Understanding the Power BI admin role](service-admin-role.md) (Power BI-beheerdersrol)  
[Power BI controleren in uw organisatie](service-admin-auditing.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
