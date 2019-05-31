---
ms.openlocfilehash: b05b5b0b5212f39b9b47cb63e2fc8522fff2f8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193810"
---
## <a name="faq"></a>Veelgestelde vragen
**Vraag:** Wat gebeurt er als was ik eerder rollen en regels voor een gegevensset gemaakt in de Power BI-service? Blijven ze gewoon werken als ik niets doe?  
**Antwoord**: Nee. Visuele elementen worden niet goed weergegeven. U moet de rollen en regels opnieuw maken binnen Power BI Desktop en deze publiceren naar de Power BI-service.

**Vraag:** Kan ik deze rollen voor Analysis Services-gegevensbronnen maken?  
**Antwoord**: Dat kan als u de gegevens hebt geïmporteerd in Power BI Desktop. Als u een live verbinding gebruikt, kunt u RLS niet configureren binnen de Power BI-service. Dit wordt gedefinieerd in het Analysis Services-model on-premises.

**Vraag:** Kan ik RLS gebruiken om de kolommen of metingen te beperken die toegankelijk zijn voor mijn gebruikers?  
**Antwoord**: Nee. Als een gebruiker toegang heeft tot een bepaalde gegevensrij, kan deze alle gegevenskolommen voor die rij zien.

**Vraag:** Kan ik met RLS gedetailleerde gegevens verbergen maar toegang geven tot samengevatte gegevens in visuele elementen?  
**Antwoord**: Nee, u beveiligt individuele rijen met gegevens maar gebruikers kunnen altijd de details of de samengevatte gegevens zien.

