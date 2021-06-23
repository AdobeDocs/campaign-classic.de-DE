---
product: campaign
title: Aktualisieren Ihrer Umgebung zur Verbindung mit Adobe Campaign mit IMS
description: Campaign - IMS-Aktualisierungen
hide: true
hidefromtoc: true
source-git-commit: b8f3ba60e34f6c5429c63ed934083ebae180cf43
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 21%

---

# Aktualisieren Ihrer Umgebung für die Verbindung mit Adobe Campaign mit IMS {#acc-ims-faq}

Am 30. Juni 2021 werden Änderungen an den Anmeldefunktionen von [Adobe Identity Management System](https://helpx.adobe.com/de/enterprise/using/identity.html) (IMS) vorgenommen, die sich auf Ihre Fähigkeit auswirken könnten, Adobe Campaign weiterhin zu verwenden. Erfahren Sie, wie Sie sicherstellen, dass Sie Adobe Campaign Classic v7 ohne Unterbrechung weiterhin verwenden.

## Was hat sich geändert?

Adobe Identity Management Service (IMS) unterstützt keine alten Internet Explorer-Versionen mehr ab **30. Juni 2021**. [Weitere Informationen](https://helpx.adobe.com/de/x-productkb/global/update-operating-system-and-browser.html).

Adobe möchte die IMS-Funktionalität für alle Kunden ab dem 30. Juni 2021 beibehalten. IMS ist Teil des Sicherheits-Frameworks, das es Benutzern ermöglicht, sich bei der Client Console anzumelden, also bei Adobe Campaign.

Um diese Funktion beizubehalten, müssen Kunden die Client Console auf jedem Benutzercomputer aktualisieren und sicherstellen, dass die neueste Aktualisierung Ihrer [Windows-Version](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems) mit **Internet Explorer 11** auf dem Computer jedes Benutzers installiert ist.

## Sind Sie betroffen?

Wenn Sie eine Verbindung zu Campaign [über einen Adobe ID](../integrations/using/about-adobe-id.md) über den Adobe Identity Management Service (IMS) herstellen und eine ältere Campaign-Version als die unten aufgeführten ausführen, sind Sie betroffen.

Wenn Sie bereits ein Upgrade durchgeführt haben, aber eine alte Version von Microsoft Internet Explorer verwenden, müssen Sie auf Internet Explorer 11 aktualisieren.

## Wie wird die Aktualisierung durchgeführt?

* Als gehosteter Kunde hat Adobe Ihre Instanz(en) bereits auf die neuere Version aktualisiert.

* Als On-Premise-/Hybrid-Kunde müssen Sie auf eine der oben aufgeführten neueren Versionen aktualisieren, um von der neuen Client Console zu profitieren und eine nahtlose Umstellung **vor dem 30. Juni 2021** sicherzustellen.

   Das Upgrade auf eine der folgenden neuen Versionen ist obligatorisch:

   * Gold Standard 11. [Mehr dazu](../rn/using/gold-standard.md)
   * Campaign-Version 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
   * Campaign-Version 20.2.4. [Mehr dazu](../rn/using/release--20-2.md)
   * Campaign-Version 20.1.4. [Mehr dazu](../rn/using/release--20-1.md)
   * Campaign-Version 19.2.4. [Mehr dazu](../rn/using/release--19-2.md)
   * Campaign-Version 19.1.8. [Mehr dazu](../rn/using/release--19-1.md)

Diese Versionen enthalten ein neues Verbindungsprotokoll. Aktualisierung ist sowohl für den Campaign-Server als auch für die Client Console erforderlich: Nachdem alle Instanzen aktualisiert wurden, muss die Client Console auf diese Version aktualisiert werden, damit nach dem 30. Juni 2021 **eine Verbindung zu Campaign hergestellt werden kann.**

Stellen Sie außerdem sicher, dass die neueste Aktualisierung Ihrer [Windows-Version](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems) mit **Internet Explorer 11** auf dem Computer jedes Benutzers installiert ist.

## Häufig gestellte Fragen

**Wie kann ich meine Campaign-Version überprüfen?**

Erfahren Sie [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen.


**Wie kann ich überprüfen, ob ich IMS verwende?**

Um Ihren Verbindungsmodus zu überprüfen, können Sie:

* Starten Sie die Campaign Client Console und greifen Sie auf die Verbindungsparameter Ihrer Instanz zu. Wenn die Option **Verbindung mit einer Adobe ID** ausgewählt ist, verwenden Sie die Adobe IMS.

   ![](../integrations/using/assets/ims_1.png)

or

* Starten Sie die Campaign Client Console und überprüfen Sie Ihr Verbindungsfenster. Wenn Sie eine Verbindung mit einer Adobe ID herstellen (wie im folgenden Bildschirm dargestellt), verwenden Sie IMS.

   ![](../integrations/using/assets/adobeID.png)

**Verbindungswarnungsmeldung**

Die folgende Warnmeldung wird Benutzern angezeigt, wenn sie ihre Client-Konsole aktualisieren oder eine alte Version von Microsoft Internet Explorer verwenden müssen: **Sie müssen die neueste Aktualisierung auf Windows und/oder Ihre Adobe Apps installieren.**

![](../integrations/using/assets/do-not-localize/errorMsg.png)

Wenn eine solche Warnung angezeigt wird, stellen Sie sicher, dass Sie die neuesten Updates des verwendeten Betriebssystems installieren. [Weitere Informationen](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

**Ab dem 30. Juni 2021** wird die folgende Meldung angezeigt und Sie können keine Verbindung mehr zu Adobe Campaign herstellen:

![](../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Nützliche Links

* [Upgrade Ihrer Umgebung](../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../platform/using/faq-build-upgrade.md)
* [Neue Client-Konsole für Benutzer verfügbar machen](../installation/using/client-console-availability-for-windows.md)
* [Campaign-Client-Konsole installieren](../installation/using/installing-the-client-console.md)
* [Zugriff auf Adobe Softwareverteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)