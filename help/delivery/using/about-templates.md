---
product: campaign
title: Über Vorlagen
description: Erste Schritte mit Versandvorlagen
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---

# Über Vorlagen{#about-templates}



Eine Versandkonfiguration kann in einer Vorlage gespeichert werden, um zu einem späteren Zeitpunkt erneut verwendet zu werden. Dabei kann die Vorlage eine partielle oder komplette Konfiguration aufweisen.

Die Ausführung von Versandvorlagen geschieht entweder manuell - wie nachfolgend beschrieben - oder wird durch ein Ereignis ausgelöst (Start zu einer festen Uhrzeit, bei Eingang einer bestimmten Datei auf dem Server usw.). Der Zugriff auf Versandvorlagen geschieht im Navigationsbaum über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Versandvorlagen]**.

![](assets/s_user_template_list.png)

Es gibt zwei Arten von Vorlagen:

1. Native Versandvorlagen, d. h. in Adobe Campaign werksmäßig vorhandene Vorlagen.

   Man spricht von nativen Vorlagen, da sie UNTER KEINEN UMSTÄNDEN aus der Anwendung gelöscht werden dürfen. Sie enthalten für jeden Kanal die notwendige Minimalkonfiguration. Ein Administrator hat jedoch die Möglichkeit, gewisse Funktionen zu beschränken oder den Benutzern Standardwerte vorzugeben (Tracking-Aktivierung, Absender-Adresse usw.). Native Versandvorlagen erscheinen fettgedruckt in der Vorlagenliste. Änderungen können nur an Kopien dieser Vorlagen vorgenommen werden.

1. Vorkonfigurierte Versandvorlagen

   Der Adobe Campaign-Administrator kann neue Versandvorlagen erstellen. Sie können von Benutzern (mit entsprechenden Zugriffsrechten) oder automatisch von Server-Prozessen wiederverwendet werden. Sie können beispielsweise eine E-Mail-Versandvorlage konfigurieren. Wenn Benutzer einen Versand mithilfe dieser Vorlage erstellen, müssen sie lediglich den Text oder den HTML-Inhalt eingeben und ihn dann versenden. Die anderen Optionen wurden bereits vom Administrator definiert.

>[!NOTE]
>
>Welche Vorlagen Ihnen zur Verfügung stehen, hängt von Ihren Benutzerrechten, der Konfiguration Ihrer Instanz und dem jeweiligen Anwendungskontext ab. Wenn Sie beispielsweise einen Informationsdienst erstellen, können Sie eine Vorlage zum Versand von Bestätigungsnachrichten verwenden. In diesem Kontext werden nur Vorlagen mit dem Zielgruppen-Mapping &quot;Abonnements&quot; angezeigt. Mehr dazu finden Sie unter [Auswählen eines Zielgruppen-Mappings](selecting-a-target-mapping.md) und [Services und Abonnements](about-services-and-subscriptions.md).
