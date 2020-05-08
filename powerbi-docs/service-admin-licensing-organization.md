---
title: Power BI-licenties in uw organisatie
description: Overzicht van de verschillende licentietypen die beschikbaar zijn in Power BI en hoe beheerders licenties voor hun organisatie aankopen en beheren.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a41e9453158c38a208fe7f4ac937b4e86a515f4b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "81436317"
---
# <a name="power-bi-licensing-in-your-organization"></a>Power BI-licenties in uw organisatie

Wat een gebruiker in de Power BI-service kan doen, hangt af van het type gebruikerslicentie dat ze hebben en of de inhoud waarmee ze werken zich in een werkruimte bevindt die aan een Power BI Premium-capaciteit is toegewezen. Alle gebruikers van de Power BI-service moeten over een licentie beschikken.

Er zijn twee manieren waarop gebruikers een licentie kunnen krijgen. Met behulp van mogelijkheden voor aanmelden via een self-service en hun werk- of schoolaccount kunnen gebruikers hun eigen gratis licentie of Pro-licentie aanvragen. Een andere mogelijkheid is dat beheerders een Power BI-abonnement aanschaffen en licenties aan gebruikers toewijzen.

In dit artikel besteden we aandacht aan de aankoopservice en licenties per gebruiker gezien vanuit het perspectief van een beheerder. Zie [Aanmelden voor Power BI als afzonderlijke gebruiker](service-self-service-signup-for-power-bi.md) voor meer informatie over de manier waarop gebruikers hun eigen licentie kunnen verkrijgen.

## <a name="who-can-purchase-and-assign-licenses"></a>Wie kan licenties kopen en toewijzen?

De rol van beheerder moet aan u zijn toegewezen om licenties voor uw organisatie aan te schaffen of toe te wijzen. Beheerdersrollen worden toegewezen met behulp van het Azure Active Directory-beheercentrum of het Microsoft 365-beheercentrum. In de volgende tabel ziet u welke rol is vereist om taken met betrekking tot aanschaffen en licenties uit te voeren. Zie [Beheerdersrollen weergeven en toewijzen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal) voor meer informatie over beheerdersrollen in Azure Active Directory. Zie [Informatie over beheerdersrollen](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide) voor meer informatie over beheerdersrollen in Microsoft 365, inclusief best practices.

| Wie kan services en licenties aanschaffen? | Wie kan gebruikerslicenties beheren? |
| --------------- | --------------- |
| Factureringsbeheerder | Licentiebeheerder |
| Globale beheerder | Gebruikersbeheerder |
|  | Globale beheerder |

Met deze rollen wordt de organisatie beheerd. Zie [Beheerdersrollen in de Power BI-service](service-admin-role.md) voor informatie over beheerdersrollen in de Power BI-service.

## <a name="get-power-bi-for-your-organization"></a>Power BI voor uw organisatie kopen

Een globale beheerder of een factureringsbeheerder kan zich aanmelden voor de Power BI-service en licenties aanschaffen voor de gebruikers in hun organisatie. Als u nog niet klaar bent om licenties aan te schaffen, selecteert u de proefversie van Power BI Pro. U krijgt 25 licenties die u gedurende één maand mag gebruiken. Zie [Een Power BI-abonnement voor uw organisatie verkrijgen](admin/service-admin-org-subscription.md) voor stapsgewijze instructies over aanmelden.

## <a name="about-self-service-sign-up"></a>Aanmelden via de self-service

Afzonderlijke gebruikers kunnen hun eigen Power BI-licentie verkrijgen door zich aan te melden met hun werk- of schoolaccount. Met een gratis licentie kunnen gebruikers Power BI verkennen voor het analyseren en visualiseren van persoonlijke gegevens met behulp van Mijn werkruimte, maar ze kunnen geen samenwerking met andere gebruikers starten. Een Power BI Pro-licentie is vereist om inhoud te delen. Gebruikers kunnen hun licentietype upgraden naar Pro of zich rechtstreeks aanmelden voor Pro, als de organisatie de commerciële cloud gebruikt. Rechtstreekse aanschaf van of een upgrade naar Pro is niet beschikbaar voor onderwijsinstellingen of organisaties die zijn geïmplementeerd naar overheids- of onafhankelijke cloudexemplaren.

Zie [Aanmelden via een self-service in- of uitschakelen](admin/service-admin-disable-self-service.md) als u niet wilt dat aanmelden via een self-service beschikbaar is voor gebruikers in uw organisatie, zodat u kunt leren hoe u dit uitschakelt.

Zie [Gebruikerslicenties weergeven en beheren](admin/service-admin-manage-licenses.md) als u wilt zien welke gebruikers in uw organisatie mogelijk al over een licentie beschikken.

## <a name="license-types-and-capabilities"></a>Licentietypen en mogelijkheden

Er zijn twee soorten Power BI-licenties per gebruiker: gratis en Pro. Welk type licentie een gebruiker nodig heeft, wordt bepaald door de locatie waar inhoud is opgeslagen en hoe de gebruiker die inhoud gebruikt. De locatie waar inhoud kan worden opgeslagen, wordt bepaald door het [abonnementstype](#subscription-types) van uw organisatie.

Met een van de abonnementstypen, [Power BI Premium](service-admin-premium-purchase.md), kunnen gebruikers met een gratis licentie inhoud gebruiken in werkruimten die aan Premium-capaciteit zijn toegewezen. Buiten de Premium-capaciteit kan een gebruiker met een gratis licentie de Power BI-service alleen gebruiken om verbinding te maken met gegevens en om rapporten en dashboards in een persoonlijke werkruimte te maken. Ze kunnen geen inhoud met anderen delen of inhoud naar app-werkruimten publiceren.

Voor een Power BI-standaardabonnement wordt gedeelde capaciteit gebruikt. Wanneer inhoud wordt opgeslagen in een gedeelde capaciteit, kunnen gebruikers aan wie een Power BI Pro-licentie is toegewezen, alleen samenwerken met andere Power BI Pro-gebruikers. Ze kunnen inhoud gebruiken die door andere gebruikers is gedeeld, inhoud publiceren naar app-werkruimten, dashboards delen en zich abonneren op dashboards en rapporten.  Wanneer werkruimten zich in de Premium-capaciteit bevinden, kunnen Pro-gebruikers inhoud distribueren naar gebruikers die geen Power BI Pro-licentie hebben.

In de onderstaande tabel worden de basismogelijkheden van elk licentietype samengevat. Zie [Functies per licentietype](service-features-license-type.md) voor een gedetailleerd overzicht van de beschikbare functies per licentietype.

| Licentietype | Mogelijkheden wanneer werkruimte zich in gedeelde capaciteit bevindt | Aanvullende mogelijkheden wanneer werkruimte zich in Premium-capaciteit bevindt |
| --------- | ----------- | ----------- |
| Power BI (gratis) | Toegang tot inhoud in Mijn werkruimte | Inhoud gebruiken die met hun is gedeeld |
| Power BI Pro | Inhoud naar app-werkruimten publiceren, dashboards delen, abonneren op dashboards en rapporten, delen met gebruikers die over een Pro-licentie beschikken | Inhoud distribueren naar gebruikers met gratis licenties |

## <a name="subscription-types"></a>Abonnementstypen

Alle op gebruikers gebaseerde, commerciële licentieabonnementen van Microsoft zijn gebaseerd op Azure Active Directory-identiteiten. Dit betekent dat u zich moet aanmelden met een identiteit die door Azure Active Directory wordt ondersteund voor commerciële licenties. U kunt een Power BI-abonnement toevoegen aan elk Microsoft-abonnement waarvoor Azure Active Directory wordt gebruikt voor identiteitsservices. Sommige abonnementen, zoals Office 365 E5, omvatten al een Power BI Pro-licentie, dus hiervoor hoeft u zich niet apart aan te melden voor Power BI.

Er zijn twee soorten Power BI-abonnementen voor organisaties: self-service BI met Power BI Pro en geavanceerde analyse met Power BI Premium.

Met een standaard, self-service Power BI Pro-abonnement kunnen beheerders licenties per gebruiker toewijzen. Er zijn maandelijkse kosten per gebruiker voor Power BI Pro-licenties, waardoor samenwerking, publicaties, delen en ad-hocanalyse mogelijk zijn. Inhoud wordt opgeslagen naar gedeelde opslagcapaciteit die volledig door Microsoft wordt beheerd.

Een Power BI Premium-abonnement wijst toegewezen capaciteit toe aan een organisatie. Premium is geschikt voor zakelijke BI, big data-analyse en cloud- en on-premises rapporten, en biedt geavanceerde besturingselementen voor beheer en implementatie. Toegewezen reken- en opslagresources worden beheerd door capaciteitsbeheerders in uw organisatie. Er worden maandelijkse kosten in rekening gebracht voor deze toegewezen omgeving. Naast andere Premium-voordelen kan inhoud die in Premium-capaciteit is opgeslagen ook worden geopend door en gedistribueerd naar gebruikers die geen Power BI Pro-licentie hebben. Aan ten minste één gebruiker moet een Power BI Pro-licentie zijn toegewezen om Premium te kunnen gebruiken, en inhoudsmakers en ontwikkelaars hebben nog steeds een Power BI Pro-licentie nodig.

De twee typen abonnementen sluiten elkaar niet uit. U kunt zowel Power BI Premium als Power BI Pro gebruiken. In deze configuratie kan inhoud die in Premium-capaciteit is opgeslagen, worden gedeeld met alle gebruikers en is gedeelde capaciteit ook beschikbaar. Zie [Gegevensopslag beheren in Power BI-werkruimten](service-admin-manage-your-data-storage-in-power-bi.md) voor informatie over capaciteitslimieten.

Zie [Power BI-prijzen](https://powerbi.microsoft.com/pricing) om productfuncties en prijzen te vergelijken.

## <a name="guest-user-access"></a>Toegang voor gastgebruikers

U kunt inhoud distribueren naar gebruikers buiten uw organisatie. Het is mogelijk om inhoud te delen met externe gebruikers door hen uit te nodigen de inhoud als gast weer te geven. Met Azure Active Directory Business-to-Business (Azure AD B2B) kunt u inhoud delen met externe gastgebruikers. Aan de volgende voorwaarden moet worden voldaan om te delen met externe gebruikers:

- De mogelijkheid om inhoud met externe gebruikers te delen moet zijn ingeschakeld

- De gastgebruiker moet over de juiste licenties beschikken om de gedeelde inhoud te kunnen weergeven

Zie [Power BI-inhoud distribueren naar externe gastgebruikers met Azure AD B2B](service-admin-azure-ad-b2b.md) voor meer informatie over toegang voor gastgebruikers.

## <a name="purchase-power-bi-pro-licenses"></a>Power BI Pro-licenties kopen

Als beheerder kunt u Power BI Pro-licenties kopen via Microsoft 365 of via een Microsoft-partner. Nadat u de licenties hebt gekocht, wijst u ze toe aan individuele gebruikers. Zie [Power BI Pro-licenties kopen en toewijzen](service-admin-purchasing-power-bi-pro.md) voor meer informatie.

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro-licentie verloopt

Er is een respijtperiode na het verstrijken van een Power BI Pro-licentie. Voor licenties die deel uitmaken van een volumelicentie-aankoop, is de respijtperiode 90 dagen. Als u de licentie rechtstreeks hebt aangeschaft, bedraagt de respijtperiode 30 dagen.

Power BI Pro heeft dezelfde levenscyclus van abonnementen als Office 365. Raadpleeg [Wat gebeurt er met mijn gegevens en toegang wanneer mijn abonnement op Office 365 voor bedrijven eindigt?](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3) voor meer informatie.


## <a name="next-steps"></a>Volgende stappen

- [Power BI Pro-licenties kopen en toewijzen](service-admin-purchasing-power-bi-pro.md)
- [Documentatie over Microsoft 365 Business-abonnementen en facturering](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [Power Bi-gebruikers zoeken die zich hebben aangemeld](service-admin-access-usage.md)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
