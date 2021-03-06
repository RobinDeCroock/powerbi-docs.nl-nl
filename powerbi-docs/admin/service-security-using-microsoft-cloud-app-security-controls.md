---
title: Microsoft Cloud App Security-besturingselementen gebruiken in Power BI
description: Meer informatie over het gebruik van Microsoft Cloud App Security in combinatie met Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 7907242c3ef71b1b621820cbb66bd93e88ff1c99
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532700"
---
# <a name="using-microsoft-cloud-app-security-controls-in-power-bi"></a>Microsoft Cloud App Security-besturingselementen gebruiken in Power BI

Met behulp van Cloud App Security met Power BI kunt u uw Power BI-rapporten, -gegevens en -services beveiligen tegen onbedoelde lekken of inbreuk. Met Cloud App Security kunt u beleid voor voorwaardelijke toegang maken voor de gegevens van uw organisatie, met behulp van real-time sessie besturings elementen in Azure Active Directory (Azure AD), waarmee u ervoor kunt zorgen dat uw Power BI-analyses veilig zijn. Zodra dit beleid is ingesteld, kunnen beveiligingsbeheerders gebruikerstoegang en -activiteit bijhouden, realtime risicoanalyse uitvoeren en labelspecifieke besturingselementen instellen. 

![Het deelvenster Cloud App Security-besturingselementen gebruiken](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-01.png)

U kunt Cloud App Security configureren voor allerlei apps en services, niet alleen Power BI. U moet Cloud App Security configureren om met Power BI te werken, zodat u kunt profiteren van Cloud App Security-beveiligingen voor uw Power BI-gegevens en -analyses. Zie de documentatie over [Cloud App Security](/cloud-app-security/) voor meer informatie over Cloud App Security, inclusief een overzicht van hoe het werkt, het dashboard en app-risicoscores.

## <a name="cloud-app-security-licensing"></a>Cloud App Security-licenties

Als u Cloud App Security met Power BI wilt gebruiken, moet u relevante Microsoft-beveiligingsservices gebruiken en configureren. Een aantal hiervan worden buiten Power BI ingesteld. U moet over de volgende [licenties](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2NXYO) beschikken om Cloud App Security in uw tenant te kunnen gebruiken:
* Microsoft Cloud App Security: Biedt Cloud App Security-mogelijkheden voor alle ondersteunde apps, onderdeel van de EMS E5-suite en de Microsoft 365 E5-suite.
* Office 365 Cloud App Security: Biedt alleen Cloud App Security-mogelijkheden voor Office 365, onderdeel van de Office 365 E5-suite.


## <a name="configure-real-time-controls-for-power-bi-with-cloud-app-security"></a>Real-time besturings elementen configureren voor Power BI met Cloud App Security

> [!NOTE]
> * Een Azure Active Directory Premium P1-licentie is vereist om te profiteren van Cloud App Security real-time besturings elementen.

In de volgende secties worden de stappen beschreven voor het configureren van real-time besturings elementen voor Power BI met Cloud App Security.

### <a name="set-session-policies-in-azure-ad-required"></a>Sessiebeleidsregels instellen in Azure AD (vereist)
De stappen die moeten worden uitgevoerd om sessiebesturingselementen in te stellen, worden voltooid in de Azure AD- en Cloud App Security-portals. In de Azure AD-portal maakt u een beleid voor voorwaardelijke toegang voor Power BI en leidt u sessies die worden gebruikt in Power BI om via de Cloud App Security-service. 

Cloud App Security werkt met behulp van een reverse-proxy-architectuur en wordt geïntegreerd met voorwaardelijke toegang van Azure AD om gebruikersactiviteit in Power BI in realtime bij te houden. U ziet hier de volgende stappen voor meer informatie over het proces. In de gekoppelde inhoud in elk van de volgende stappen vindt u gedetailleerde stapsgewijze instructies. U kunt ook dit [Cloud App Security-artikel](/cloud-app-security/proxy-deployment-aad) lezen voor een beschrijving van het volledige proces.

1.  [Een Azure AD-proefbeleid voor voorwaardelijke toegang maken](/cloud-app-security/proxy-deployment-aad#add-azure-ad)
2.  [Aanmelden bij elke app met behulp van een gebruiker die binnen het bereik van het beleid valt](/cloud-app-security/proxy-deployment-aad#sign-in-scoped)
3.  [Controleren of de apps zijn geconfigureerd op het gebruik van toegangs- en sessiebesturingselementen](/cloud-app-security/proxy-deployment-aad#portal)
4.  [De implementatie testen](/cloud-app-security/proxy-deployment-aad#step-4-test-the-deployment)

Het proces voor het instellen van sessiebeleidsregels wordt in detail beschreven in het artikel [Sessiebeleidsregels](/cloud-app-security/session-policy-aad). 

### <a name="set-anomaly-detection-policies-to-monitor-power-bi-activities-recommended"></a>Beleidsregels voor anomaliedetectie instellen om Power BI-activiteiten bij te houden (aanbevolen)
U kunt Power BI-beleidsregels voor anomaliedetectie definiëren waarvoor het bereik onafhankelijk kan worden bepaald, zodat ze alleen van toepassing zijn op de gebruikers en groepen die u in het beleid wilt opnemen of die u van het beleid wilt uitsluiten. [Meer informatie](/cloud-app-security/anomaly-detection-policy#scope-anomaly-detection-policies).

Cloud App Security heeft ook twee toegewezen, ingebouwde detecties voor Power BI. [Zie de sectie later in dit document voor meer informatie](#built-in-cloud-app-security-detections-for-power-bi).

### <a name="use-microsoft-information-protection-sensitivity-labels-recommended"></a>Vertrouwelijkheidslabels voor Microsoft Information Protection gebruiken (aanbevolen)

Met vertrouwelijkheidslabels kunt u gevoelige inhoud classificeren en beveiligen, zodat mensen in uw organisatie kunnen samenwerken met partners buiten uw organisatie, waarbij ze rekening houden met en zich bewust blijven van gevoelige inhoud en gegevens. 

U kunt het artikel over [vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md) lezen voor meer informatie over het proces van het gebruik van vertrouwelijkheidslabels voor Power BI. Zie hieronder voor een [voorbeeld van een Power BI-beleid op basis van vertrouwelijkheidslabels](#example).

## <a name="custom-policies-to-alert-on-suspicious-user-activity-in-power-bi"></a>Aangepaste beleids regels voor het melden van verdachte gebruikers activiteit in Power BI

Met Cloud App Security-activiteiten beleid kunnen beheerders hun eigen aangepaste regels definiëren voor het detecteren van gebruikers gedrag dat afwijkt van de norm, en kan het ook automatisch worden uitgevoerd als het te gevaarlijk lijkt. Bijvoorbeeld:

* **Het verwijderen van een enorm gevoeligheids label.** Bijvoorbeeld: Waarschuw mij wanneer de labels voor de gevoeligheid worden verwijderd door één gebruiker uit 20 verschillende rapporten in een tijd venster van minder dan 5 minuten.

* **De downgrade van het gevoeligheids label wordt versleuteld.** Bijvoorbeeld: Waarschuw mij wanneer een rapport met een ' zeer vertrouwelijke ' gevoeligheids label nu als ' openbaar ' is geclassificeerd.

> [!NOTE]
> * De unieke id's van Power BI artefacten en gevoeligheids labels kunt u vinden met behulp van [Power bi rest-api's](/rest/api/power-bi/). Zie [gegevens sets ophalen](/rest/api/power-bi/datasets/getdatasets) of [rapporten ophalen](/rest/api/power-bi/reports/getreports).


Aangepaste beleids regels voor activiteiten worden geconfigureerd in de Cloud App Security Portal. [Meer informatie](/cloud-app-security/user-activity-policies). 

## <a name="built-in-cloud-app-security-detections-for-power-bi"></a>Ingebouwde Cloud App Security-detecties voor Power BI

Met behulp van Cloud App Security-detecties kunnen beheerders specifieke activiteiten van een bewaakte app bijhouden. Voor Power BI zijn er momenteel twee toegewezen, ingebouwde Cloud App Security-detecties: 

* **Verdachte share**: detecteert wanneer een gebruiker een gevoelig rapport deelt met een onbekend e-mailadres (van buiten de organisatie). Een gevoelig rapport is een rapport waarvan het vertrouwelijkheidslabel is ingesteld op **ALLEEN INTERN** of hoger. 

* **Massaal delen van rapporten**: detecteert wanneer een gebruiker een groot aantal rapporten in één sessie deelt.

Instellingen voor deze detecties worden geconfigureerd in de Cloud App Security-portal. [Meer informatie](/cloud-app-security/anomaly-detection-policy#unusual-activities-by-user). 

## <a name="power-bi-admin-role-in-cloud-app-security"></a>De Power BI-beheerdersrol in Cloud App Security

Er is een nieuwe rol gemaakt voor Power BI-beheerders wanneer ze Cloud App Security met Power BI gebruiken. Wanneer u zich als een Power BI-beheerder bij de [Cloud App Security-portal](https://portal.cloudappsecurity.com/) aanmeldt, hebt u beperkte toegang tot voor Power BI relevante gegevens, waarschuwingen, gebruikers die risico lopen, activiteitenlogboeken en andere informatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen 
Het gebruik van Cloud App Security met Power BI is ontworpen om inhoud en gegevens van uw organisatie te beveiligen, met detecties waarmee gebruikerssessies en hun activiteiten worden bijgehouden. Wanneer u Cloud App Security met Power BI gebruikt, zijn er een aantal overwegingen en beperkingen waarmee u rekening moet houden:

* Cloud App Security werkt alleen voor Excel-, PowerPoint- en PDF-bestanden.
* Als u de mogelijkheden van vertrouwelijkheidslabels in uw sessiebeleidsregels voor Power BI wilt gebruiken, moet u over een Azure Information Protection Premium P1- of Premium P2-licentie beschikken. Microsoft Azure Information Protection kan ofwel als zelfstandig product als via een van de Microsoft-licentiesuites worden aangeschaft. Zie [Prijzen voor Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) voor meer informatie. Daarnaast moeten vertrouwelijkheidslabels zijn toegepast op uw Power BI-assets.
* Sessiebeheer is beschikbaar voor elke browser op een belangrijk platform van elk besturingssysteem. Het wordt aanbevolen om Internet Explorer 11, Microsoft Edge (meest recente versie), Google Chrome (meest recente versie), Mozilla Firefox (meest recente versie) of Apple Safari (meest recente versie) te gebruiken. Openbare API-aanroepen van Power BI en andere sessies zonder browser worden niet ondersteund als onderdeel van het Cloud App Security-sessiebeheer. [Meer details bekijken](/cloud-app-security/proxy-intro-aad#supported-apps-and-clients).

> [!CAUTION]
> * In het sessiebeleid werkt de mogelijkheid 'beveiligen' (in het gedeelte 'actie') alleen als het item niet van labels is voorzien. Als er al een label bestaat, wordt de actie 'beveiligen' niet toegepast; u kunt een bestaand label dat al op een item in Power BI is toegepast, niet overschrijven.

## <a name="example"></a>Voorbeeld

In het volgende voorbeeld ziet u hoe u een nieuw sessiebeleid maakt met behulp van Cloud App Security met Power BI.

Maak eerst een nieuw sessiebeleid. Selecteer **Beleidsregels** in het linkermenu in de **Cloud App Security**-portal.

![Een nieuw sessiebeleid maken](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-02.png)

Selecteer het vervolgkeuzemenu **Beleid maken** in het venster dat wordt weergegeven.

![Beleid maken selecteren](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-03.png)

In de lijst met opties in het vervolgkeuzemenu selecteert u **Sessiebeleid**.

![Sessiebeleid selecteren](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-04.png)

In het venster dat wordt weergegeven, maakt u het sessiebeleid. Met de genummerde stappen worden instellingen voor de volgende afbeelding beschreven.

  1. In het vervolgkeuzemenu **Beleidssjabloon** kiest u *Geen sjabloon*.
  2. Geef in het vak **Beleidsnaam** een relevante naam voor uw sessiebeleid op.
  3. Als **Sessiebeheertype** selecteert u *Beheerbestand gedownload (met DLP)* .

      Voor de sectie **Bron van activiteit** sectie kiest u relevante beleidsregels voor blokkeren. Het wordt aanbevolen onbeheerde en niet-compatibele apparaten te blokkeren. Kies ervoor om downloads te blokkeren wanneer de sessie in Power BI wordt uitgevoerd.

        ![Maak het sessiebeleid: blokkeer downloads.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-05.png)

        Wanneer u omlaag bladert, ziet u meer opties. In de volgende afbeelding ziet u die opties, met extra voorbeelden. 

  4. Kies *Vertrouwelijkheidslabel* als *Zeer vertrouwelijk* of de optie die het beste bij uw organisatie past.
  5. Wijzig de **Inspectiemethode** in *geen*.
  6. Kies de optie voor **Blokkeren** die het beste bij uw behoeften past.
  7. Zorg ervoor dat u een waarschuwing voor zo'n actie maakt.

        ![Selecteer sessiebeleidsinstellingen.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-06.png)

        

  8. Zorg er tot slot voor dat u op de knop **Maken** drukt om het sessiebeleid te maken.

        ![Maak het sessiebeleid.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-07.png)

## <a name="next-steps"></a>Volgende stappen
In dit artikel wordt beschreven hoe Cloud App Security gegevens- en inhoudsbeveiligingen voor Power BI kan bieden. U bent mogelijk ook geïnteresseerd in de volgende artikelen, waarin gegevensbeveiliging voor Power BI en ondersteunende inhoud voor de Azure-services die dat inschakelen, wordt beschreven.

* [Overzicht van vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md)
* [Vertrouwelijkheidslabels inschakelen in Power BI](service-security-enable-data-sensitivity-labels.md)
* [Vertrouwelijkheidslabels toepassen in Power BI](service-security-apply-data-sensitivity-labels.md)

U bent mogelijk ook geïnteresseerd in de volgende artikelen over Azure en beveiliging:

* [Apps beveiligen met App-beheer voor voorwaardelijke toegang van Microsoft Cloud App Security](/cloud-app-security/proxy-intro-aad)
* [App-beheer voor voorwaardelijke toegang implementeren voor aanbevolen apps](/cloud-app-security/proxy-deployment-aad)
* [Sessiebeleidsregels](/cloud-app-security/session-policy-aad)
* [Overzicht van vertrouwelijkheidslabels](/microsoft-365/compliance/sensitivity-labels)
* [Metrisch rapport gegevensbescherming](service-security-data-protection-metrics-report.md)
