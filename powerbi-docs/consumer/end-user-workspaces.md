---
title: Hoe inhoud is georganiseerd in werkruimten
description: Meer informatie over werkruimten en werkruimterollen
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120149"
---
# <a name="collaborate-in-workspaces"></a>Samenwerken in werkruimten

 *Werkruimten* worden geplaatst om met collega's samen te werken aan specifieke inhoud. Werkruimten worden door Power BI-*ontwerpers* gemaakt om verzamelingen dashboards en rapporten te bundelen. Vervolgens kan de ontwerper die verzameling bundelen in een *app* en die verspreiden in de gehele organisatie, of bij specifieke mensen of groepen. 

 Iedereen die de Power BI-service gebruikt, heeft ook een **Mijn werkruimte**.  Mijn werkruimte is uw persoonlijke sandbox waarin u inhoud voor uzelf kunt maken.

 U kunt uw werkruimten bekijken via **Start** in Power BI of door **Werkruimte** of **Mijn werkruimte** te selecteren in het navigatiedeelvenster links.

 ![navigatiedeelvenster met twee typen werkruimten](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Soorten werkruimten
Alle inhoud waarvan u de eigenaar bent en die u maakt, wordt opgeslagen in **Mijn werkruimte**. Deze werkruimte kunt u beschouwen als een persoonlijke sandbox of persoonlijk werkgebied voor uw eigen inhoud. Bij veel Power BI-*consumenten* blijft **Mijn werkruimte** leeg omdat het maken van nieuwe inhoud niet een van de taken is. Zoals de naam al zegt, verbruiken *consumenten* gegevens die door anderen zijn gemaakt, en gebruiken ze deze gegevens om zakelijke beslissingen te nemen. Als u wel inhoud maakt, kunt u [de Power BI-artikelen voorontwerpers](../create-reports/index.yml) raadplegen.

**App-werkruimten** bevatten alle inhoud voor een specifieke app. Wanneer *ontwerpers* een app maken, bundelen ze alle inhoud die voor het gebruik van de app nodig is. De inhoud kan onder andere bestaan uit dashboards, rapporten en gegevenssets. Niet alle apps bevatten deze drie elementen. Het is mogelijk dat een app slechts één dashboard of drie van elk inhoudselement bevat, of zelfs twintig rapporten. Dit is geheel afhankelijk van wat de *ontwerper* in de app wil opnemen. Meestal maken de gegevenssets geen deel uit van app-werkruimten voor *consumenten*.

De onderstaande werkruimte voor het maken van de Vijgenverkoop-app bevat drie rapporten en één dashboard. 

![navigatiedeelvenster met twee typen werkruimten](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Rollen in de werkruimten

Rollen bepalen wat u kunt doen in een werkruimte, zodat teams kunnen samenwerken.  Bij het verlenen van toegang tot een nieuwe werkruimte, voegen *ontwerpers* personen of groepen aan een van de volgende werkruimterollen toe: **Viewer**, **Lid**, **Inzender** of **Beheerder**. 


Als Power BI-*consument* communiceert u in werkruimten doorgaans met behulp van de rol **Kijker**. Een *ontwerper* kan aan u echter ook de rol **Lid** of **Inzender** toewijzen. Met de rol Kijker kunt u inhoud (dashboards, rapporten en apps) bekijken en gebruiken die door anderen zijn gemaakt en met u zijn gedeeld. En omdat iemand met de rol Kijker geen toegang kan krijgen tot de onderliggende gegevensset, is het een veilige manier om te communiceren met inhoud en hoeft u zich geen zorgen te maken dat de onderliggende gegevens worden gewijzigd.


Zie [Power BI-functies voor consumenten](end-user-features.md) voor een gedetailleerde lijst wat u als *consument* met de rol Kijker kunt doen.


### <a name="workspace-roles"></a>Werkruimterollen
De functies van de vier rollen zijn: beheerders, leden, inzenders en lezers. Al deze mogelijkheden, met uitzondering van bekijken en ermee werken, vereisen een Power BI Pro-licentie.

|Mogelijkheid   | Beheerder  | Lid  | Inzender  | Lezer |
|---|---|---|---|---|
| De werkruimte bijwerken en verwijderen.  | X  |   |   |   | 
| Personen, met inbegrip van andere beheerders, toevoegen/verwijderen.  | X  |   |   |   |
| Leden of anderen met minder machtigingen toevoegen.  |  X | X  |   |   |
| Apps publiceren en bijwerken. |  X | X  |   |   |
| Items en apps delen.<sup>1</sup> |  X | X  |   |   |
| Anderen toestaan items opnieuw te delen.<sup>1</sup> |  X | X  |   |   |
| Apps op de startpagina van collega's weergeven |  X | X  |   |   |
| Dashboards en rapporten weergeven op de startpagina van collega's |  X | X  | X |   |
| Inhoud in de werkruimte maken, bewerken en verwijderen.  |  X | X  | X  |   |
| Rapporten publiceren naar de werkruimte, inhoud verwijderen.  |  X | X  | X  |   |
| Een rapport in een andere werkruimte maken op basis van een gegevensset in deze werkruimte.<sup>1</sup> |  X | X  | X  |   |
| Kopieer een rapport. | X | X | X |  |
| Een item bekijken en ermee werken.<sup>2</sup> |  X | X  | X  | X  |
| Gegevens lezen die zijn opgeslagen in gegevensstromen in de werkruimte | X | X | X | X |

1. Inzenders en Leden kunnen items in een werkruimte delen als ze machtigingen voor opnieuw delen hebben.

2. Zelfs als u geen Power BI Pro-licentie hebt, kunt u items in de Power BI-service bekijken en ermee werken als de items zich in een werkruimte met Premium-capaciteit bevinden.

## <a name="licensing-workspaces-and-capacity"></a>Licenties, werkruimten en capaciteit
Licenties spelen ook een rol bij het bepalen wat u wel en niet kunt doen in een werkruimte. Voor veel functies moet de gebruiker beschikken over een Power BI *Pro*-licentie. De meeste *consumenten* werken met een *gratis* licentie. 

Als u een gratis licentie hebt en de werkruimte is opgeslagen in *Premium-capaciteit*, kunt u de inhoud in die werkruimte bekijken en ermee werken. Met een ruitvormig pictogram worden werkruimten en apps aangeduid die zijn opgeslagen in Premium-capaciteit.

![Geselecteerde werkruimten](media/end-user-workspaces/power-bi-diamond.png) Zie [Welke licentie heb ik?](end-user-license.md) voor meer informatie.



## <a name="next-steps"></a>Volgende stappen
* [Apps in Power BI](end-user-apps.md)    

* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

