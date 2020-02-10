---
title: Über Vorlagen
seo-title: Über Vorlagen
description: Über Vorlagen
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Über Vorlagen{#about-templates}

Eine Versandkonfiguration kann in einer Vorlage gespeichert werden, um zu einem späteren Zeitpunkt erneut verwendet zu werden. Dabei kann die Vorlage eine partielle oder komplette Konfiguration aufweisen.

Die Bereitstellungsvorlage kann manuell ausgeführt werden, wie in diesem Kapitel beschrieben, oder nach einem Ereignis (zu einem bestimmten Zeitpunkt, bei Ankunft einer Datei auf einem Server usw.). Bereitstellungsvorlagen können über den **[!UICONTROL Resources > Templates > Delivery templates]** Knoten in der Struktur konfiguriert werden.

![](assets/s_user_template_list.png)

Es gibt zwei Arten von Vorlagen:

1. Native Versandvorlagen, d. h. in Adobe Campaign werksmäßig vorhandene Vorlagen.

   Man spricht von nativen Vorlagen, da sie UNTER KEINEN UMSTÄNDEN aus der Anwendung gelöscht werden dürfen. Sie enthalten für jeden Kanal die notwendige Minimalkonfiguration. Ein Administrator hat jedoch die Möglichkeit, gewisse Funktionen zu beschränken oder den Benutzern Standardwerte vorzugeben (Tracking-Aktivierung, Absender-Adresse usw.). Native Versandvorlagen erscheinen fettgedruckt in der Vorlagenliste. Änderungen können nur an Kopien dieser Vorlagen vorgenommen werden.

1. Vorkonfigurierte Versandvorlagen

   Adobe-Campaign-Administratoren können neue Versandvorlagen erstellen. Diese werden dann von den anderen Benutzern (vorausgesetzt sie verfügen über die entsprechenden Berechtigungen) oder auch von automatischen Adobe-Campaign-Serverprozessen verwendet. So ist es einem Administrator beispielsweise möglich, eine E-Mail-Vorlage vollständig zu parametrieren, sodass ein Benutzer bei Verwendung der Vorlage nur noch den Inhalt des Versand im Text- oder HTML-Format einzugeben hat.

>[!NOTE]
>
>Die verfügbaren Vorlagen hängen von Ihren Zugriffsrechten, Ihrer Instanzkonfiguration und dem Kontext ab. Wenn Sie beispielsweise einen Informationsdienst erstellen, können Sie eine Bereitstellungsvorlage für Bestätigungsmeldungen verknüpfen: Sie können dann nur auf die Vorlagen zugreifen, deren Zielzuordnung die Abonnementzuordnung ist. Weitere Informationen finden Sie unter [Auswählen einer Zielzuordnung](../../delivery/using/selecting-a-target-mapping.md) und [Informationen zu Diensten und Abonnements](../../delivery/using/about-services-and-subscriptions.md).
