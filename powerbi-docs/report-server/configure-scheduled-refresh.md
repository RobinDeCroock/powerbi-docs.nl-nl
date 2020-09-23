---
title: Een geplande vernieuwing van uw Power BI-rapport configureren
description: Om de gegevens in uw Power BI-rapport te vernieuwen, moet u een gepland vernieuwingsschema maken.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
ms.openlocfilehash: 7bc3b77a8badafe1c9660af347a74214176690ac
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859032"
---
# <a name="how-to-configure-power-bi-report-scheduled-refresh"></a>Een geplande vernieuwing van uw Power BI-rapport configureren
Om de gegevens in uw Power BI-rapport in de Power BI Report Server te vernieuwen, moet u een gepland vernieuwingsschema maken. U maakt dit plan in het gedeelte *Beheren* van een Power BI-rapport op de rapportserver.

![Geslaagde geplande vernieuwing van een Power BI-rapport](media/configure-scheduled-refresh/scheduled-refresh-success.png)

## <a name="configure-data-source-credentials"></a>Referenties voor gegevensbron configureren
U hebt de benodigde machtigingen nodig voor het maken van een gepland vernieuwingsschema. Machtigingen worden gedefinieerd in de roldefinities voor de rapportserver. Zie [Roldefinities: vooraf gedefinieerde rollen](/sql/reporting-services/security/role-definitions-predefined-roles) in de SQL Server Reporting Services-documentatie voor meer informatie.

Voordat u een vernieuwingsschema inplant, moet u de referenties instellen voor **elke gegevensbron** die wordt gebruikt in uw Power BI-rapport.

1. Klik in de webportal met de rechtermuisknop op het Power BI-rapport en selecteer **Beheren**.
   
    ![Selecteer Beheren in het contextmenu van het Power BI-rapport](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Selecteer in het menu links het tabblad **Gegevensbronnen**.
3. Voor elke gegevensbron die wordt weergegeven, kiest u het type verificatie dat u wilt gebruiken bij het verbinden met deze gegevensbron. Geef de juiste referenties op.
   
    ![Referenties van de gegevensbron in het scherm Rapport beheren](media/configure-scheduled-refresh/data-source-credentials.png)

## <a name="creating-a-schedule-refresh-plan"></a>Een gepland vernieuwingsschema maken
Volg deze stappen om een gepland vernieuwingsschema te maken.

1. Klik in de webportal met de rechtermuisknop op het Power BI-rapport en selecteer **Beheren**.
   
    ![Selecteer Beheren in het contextmenu van het Power BI-rapport](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Selecteer in het menu links het tabblad **Geplande vernieuwing**.
3. Selecteer op de pagina **Geplande vernieuwing** de optie **Nieuw gepland vernieuwingsschema**.
   
    ![Nieuw gepland vernieuwingsschema](media/configure-scheduled-refresh/new-scheduled-refresh-plan.png)
4. Op de pagina **Nieuw gepland vernieuwingsschema** voert u een beschrijving in en stelt u een planning in om aan te geven wanneer uw gegevensmodel moet worden vernieuwd.
5. Selecteer **Gepland vernieuwingsschema maken** wanneer u klaar bent.
   
    ![Gepland vernieuwingsschema maken](media/configure-scheduled-refresh/create-scheduled-refresh-plan.png)

## <a name="modifying-a-schedule-refresh-plan"></a>Een gepland vernieuwingsschema wijzigen
Het wijzigen van een gepland vernieuwingsschema lijkt op het maken ervan.

1. Klik in de webportal met de rechtermuisknop op het Power BI-rapport en selecteer **Beheren**.
   
    ![Selecteer Beheren in het contextmenu van het Power BI-rapport](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Selecteer in het menu links het tabblad **Geplande vernieuwing**.
3. Op de pagina **Geplande vernieuwing** selecteert u **Bewerken** naast het vernieuwingsschema dat u wilt beheren.
   
    ![Selecteer Bewerken naast het schema dat u wilt bewerken](media/configure-scheduled-refresh/edit-scheduled-refresh-plan.png)
4. Op de pagina **Gepland vernieuwingsschema bewerken** voert u een beschrijving in en stelt u een planning in om aan te geven wanneer uw gegevensmodel moet worden vernieuwd.
5. Selecteer **Toepassen** wanneer u klaar bent.
   
    ![De pagina Gepland vernieuwingsschema bewerken is vergelijkbaar met het scherm voor het maken ervan](media/configure-scheduled-refresh/edit-scheduled-refresh-plan-page.png)

## <a name="viewing-the-status-of-schedule-refresh-plan"></a>De statuscontrole van een gepland vernieuwingsschema bekijken
U bekijkt de status van een gepland vernieuwingsschema in de webportal.

1. Klik in de webportal met de rechtermuisknop op het Power BI-rapport en selecteer **Beheren**.
   
    ![Selecteer Beheren in het contextmenu van het Power BI-rapport](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Selecteer in het menu links het tabblad **Geplande vernieuwing**.
3. Op de pagina **Geplande vernieuwing** kunt u in de rechterkolom de status van een schema zien.
   
   | **Status** | **Beschrijving** |
   | --- | --- |
   | Nieuw gepland vernieuwingsschema |Het schema is gemaakt, maar is niet uitgevoerd. |
   | Vernieuwen |Het vernieuwingsproces is gestart. |
   | Model streamen naar Analysis Server |Het model wordt gekopieerd van de catalogusdatabase van de rapportserver naar het gehoste Analysis Services-exemplaar. |
   | Gegevens vernieuwen |De gegevens in het model worden vernieuwd. |
   | Referenties verwijderen uit het model |De referenties waarmee verbinding wordt gemaakt met de gegevensbron worden uit het model verwijderd. |
   | Model opslaan in de catalogus |Het vernieuwen van gegevens is voltooid en het vernieuwde model wordt in de catalogusdatabase van de rapportserverdatabase opgeslagen. |
   | Voltooid: Gegevens vernieuwen |Het vernieuwen is voltooid. |
   | Fout: |Er is een fout opgetreden tijdens het vernieuwen. Deze wordt weergegeven. |

De webpagina moet worden vernieuwd om de huidige status te bekijken. De status verandert niet automatisch.

## <a name="next-steps"></a>Volgende stappen
Zie [Schema’s maken, wijzigen en verwijderen](/sql/reporting-services/subscriptions/create-modify-and-delete-schedules) voor meer informatie over het maken en wijzigen van schema's.

Zie [Problemen oplossen met geplande vernieuwing in Power BI Report Server](scheduled-refresh-troubleshoot.md) voor meer informatie over het oplossen van problemen met de geplande vernieuwing.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)