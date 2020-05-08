---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409357"
---
## <a name="faq"></a>Veelgestelde vragen
**Vraag:** Wat als ik eerder rollen en regels hebt gemaakt voor een gegevensset in de Power BI-service? Blijven ze gewoon werken als ik niets doe?  
**Antwoord**: Nee, visuals worden niet goed weergegeven. U moet de rollen en regels opnieuw maken binnen Power BI Desktop en deze publiceren naar de Power BI-service.

**Vraag:** Kan ik deze rollen voor Analysis Services-gegevensbronnen maken?  
**Antwoord**: Dat kan als u de gegevens hebt geïmporteerd in Power BI Desktop. Als u een live verbinding gebruikt, kunt u RLS niet configureren binnen de Power BI-service. Dit wordt gedefinieerd in het Analysis Services-model on-premises.

**Vraag:** Kan ik RLS gebruiken om de kolommen of metingen te beperken die toegankelijk zijn voor mijn gebruikers?  
**Antwoord**: Nee. Als een gebruiker toegang heeft tot een bepaalde gegevensrij, kan deze gebruiker alle gegevenskolommen voor die rij zien.

**Vraag:** Kan ik met RLS gedetailleerde gegevens verbergen maar toegang geven tot samengevatte gegevens in visuele elementen?  
**Antwoord**: Nee, u beveiligt individuele rijen met gegevens maar gebruikers kunnen altijd de details of de samengevatte gegevens zien.

**Vraag:** Er zijn al beveiligingsrollen gedefinieerd voor mijn gegevensbron (bijvoorbeeld SQL Server-rollen of SAP BW-rollen). Wat is de relatie tussen de beveiligingsrollen en beveiliging op rijniveau?  
**Antwoord**: Het antwoord hangt af van het feit of u gegevens importeert of DirectQuery gebruikt. Als u gegevens importeert in uw Power BI-gegevensset, worden de beveiligingsrollen in uw gegevensbron niet gebruikt. In dat geval moet u beveiliging op rijniveau instellen om beveiligingsregels af te dwingen voor gebruikers die verbinding maken in Power BI. Als u DirectQuery gebruikt, worden de beveiligingsrollen in uw gegevensbron gebruikt. Wanneer een gebruiker een rapport opent, verzendt Power BI een query naar de onderliggende gegevensbron waarmee beveiligingsregels worden toegepast op de gegevens op basis van de inloggegevens van de gebruiker.
