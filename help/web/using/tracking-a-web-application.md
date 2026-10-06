---
product: campaign
title: Nachverfolgen von Besuchen in einem Web-Programm
description: Nachverfolgen von Besuchen in einem Web-Programm
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
TQID: 'https://experienceleague.adobe.com/TtUrQKKVdMc4ZttsgFG9ly8hTCdqCnb3bMm2Tn3E6ww'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
    internal-label: Web Apps
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
    internal-label: Web Forms
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
    internal-label: Landing pages
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 100%
---
# Nachverfolgen von Besuchen in einem Web-Programm{#tracking-a-web-application}



Mit Adobe Campaign können Sie Besuche auf Seiten von Web-Anwendungen verfolgen und messen, indem Sie Tracking-Tags einfügen. Diese Funktion kann für alle Typen von Web-Anwendungen (Formulare, Web-Seiten usw.) verwendet werden.

So können Sie mehrere Navigationspfade definieren und deren Erfolg bewerten. Die gewonnenen Daten stehen dann in den Berichten der einzelnen Anwendungen zur Verfügung.

Die wichtigsten Verbesserungen in dieser Version sind:

* Möglichkeit, mehrere Trackingtags auf derselben Seite einzufügen, um die Definition des Navigationspfads zu vereinfachen (z. B. Kauf, Abonnement, Rückgabe)
* Ansicht der Navigationspfade und Trackingtags auf den unterschiedlichen Seiten im Webanwendungs-Dashboard.

  ![](assets/trackers_1.png)

* Erstellen eines vollständigen Tracking-Berichts

  ![](assets/trackers_5.png)

  Die wichtigsten Indikatoren sind:

  * **Konversionsrate**: Anzahl der Personen, die alle Schritte eines Vorgangs durchlaufen haben.
  * **Bounce-Rate**: Anzahl der Personen, für die nur der erste Schritt angezeigt wurde.
  * **Konversionstrichter**: Verlustrate von einem Schritt zum nächsten.

  Zusätzlich wird in einer **Sektorgrafik** die Population entsprechend ihrer Herkunft dargestellt.

## Traffic-Herkunft identifizieren {#identifying-the-traffic-source}

Es können zwei verschiedene Modi verwendet werden, um festzustellen, woher der Besucher beim Zugriff auf eine Webanwendung kommt:

1. Senden einer speziellen Nachricht, in der Sie ihm Zugriff auf die Webanwendungsseiten gewähren: In diesem Fall ist die Traffic-Herkunft dieser Versand.
1. Verknüpfen der Webanwendung mit einer bestimmten Traffic-Herkunft: In diesem Fall muss es sich um eine externe „Traffic-Herkunft“ handeln. Sie kann aus den Eigenschaften der Webanwendung oder dem Zielgruppen-Mapping ausgewählt werden.

   ![](assets/trackers_6.png)

Um die Traffic-Herkunft in einer Webanwendung festzustellen, sucht Adobe Campaign nach den folgenden Informationen:

1. Die Versandkennung der Quelle, sofern eine vorhanden ist (nlId-Cookie),
1. Die in den Eigenschaften der Webanwendung definierte Kennung des externen Versands, sofern vorhanden,
1. Die im Zielgruppen-Mapping definierte Kennung des externen Versands, sofern vorhanden.

>[!NOTE]
>
>Das anonyme Tracking ist nur verfügbar, wenn die Option bei der Installation von Campaign im Bereitstellungassistenten aktiviert wurde.

## Mit dem Digital Content Editor (DCE) erstellte Web-Anwendungen {#web-applications-designed-with-digital-content-editor--dce-}

Wenn eine Webanwendung mit dem HTML-Contenteditor – dem **Digital Content Editor (DCE)** – erstellt wird, werden Trackingtags über den Tab **[!UICONTROL Eigenschaften]** des Editors eingefügt. Weiterführende Informationen zum Digital Content Editor (DCE) finden Sie in [diesem Abschnitt](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Bei der Verwendung der Webschnittstelle werden Trackingtags über die Seiteneigenschaften eingefügt.

![](assets/trackers_3.png)

Mit dem Symbol **[!UICONTROL Bausteine anzeigen]** können Sie die Anzahl der für die Seite definierten Trackingtags anzeigen.

![](assets/trackers_4.png)
