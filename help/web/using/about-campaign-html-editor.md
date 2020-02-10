---
title: Über den HTML-Editor von Campaign
seo-title: Über den HTML-Editor von Campaign
description: Über den HTML-Editor von Campaign
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Über den HTML-Editor von Campaign{#about-campaign-html-editor}

Der **Digital Content Editor (DCE)** ist ein HTML-Inhaltseditor, mit dem Sie Vorlagen oder Inhalte im HTML-Format in Adobe Campaign einfach erstellen oder ändern können.

Mit dem Digital Content Editor können Sie Seitenelemente einfügen und formatieren sowie Datenbankfelder Elementen einer HTML-Seite zuordnen. Der Digital Content Editor ist standardmäßig verfügbar, wenn eine Seite für eine Webanwendung oder ein Versand mithilfe einer Vorlage erstellt wird, in der der DCE aktiv ist.

>[!NOTE]
>
>Mit dem DCE können Sie ausschließlich die in diesem Abschnitt aufgeführten Aktionen ausführen.
>
>Wenn Sie serverseitigen JavaScript-Code hinzufügen möchten, sollten Sie dafür Gestaltungsbausteine verwenden. Weiterführende Informationen zur Erstellung und Änderung von Gestaltungsbausteinen finden Sie auf [dieser Seite](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Allgemeine Verwendung des Digital Content Editors {#content-editor-general-operation}

Dieser Abschnitt enthält die wichtigsten Schritte zum Bearbeiten und Hochladen von Inhalten, die im Rahmen einer Webanwendung und eines Versands mit dem DCE bearbeitet wurden.

Allgemein gilt:

![](assets/dce_schema.png)

Um eine einfache Webanwendung zu erstellen, gehen Sie wie folgt vor:

* Erstellen Sie eine Webanwendung. Weitere Informationen finden Sie unter [Erstellen einer Einstiegsseite](../../web/using/creating-a-landing-page.md),
* Select existing content or creating content from a standard template, for more on this, refer to [Template management](../../web/using/template-management.md),
* Bearbeiten und Konfigurieren von Inhalten. Weitere Informationen finden Sie unter [Bearbeiten von Inhalten](../../web/using/editing-content.md),
* Publish the Web application, for more on this, refer to [Publishing content](../../web/using/creating-a-landing-page.md#step-3---publishing-content) and [this page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of a Web application, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md).

Gehen Sie zur Erstellung eines E-Mail-Versands wie folgt vor:

* Erstellen Sie eine Auslieferung aus einer E-Mail-Typvorlage, in der das DCE aktiv ist.
* Wählen Sie vorhandenen Inhalt oder erstellen Sie Inhalte aus einer Standardvorlage.
* Bearbeiten und Konfigurieren von Onlineinhalten,
* Senden Sie die Lieferung, für weitere Informationen zu diesem Abschnitt finden Sie [diesen Abschnitt](../../delivery/using/communication-channels.md).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of an email delivery, refer to [this use case](../../web/using/use-case--creating-an-email-delivery.md).

