---
title: Web-Tracking-Tags erstellen
seo-title: Web-Tracking-Tags erstellen
description: Web-Tracking-Tags erstellen
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Web-Tracking-Tags erstellen{#creating-web-tracking-tags}

Jede Seite der Site, die Sie verfolgen möchten, muss in Ihrer Adobe Campaign-Plattform referenziert werden. Diese Referenz kann auf zwei Arten durchgeführt werden:

1. manuelle Definition der zu verfolgenden URLs,
1. Erstellen von URLs, die direkt verfolgt werden sollen.

## Definieren der URLs, die in der Anwendung verfolgt werden sollen {#defining-the-urls-to-be-tracked-in-the-application}

Mit dieser Methode können Sie die zu verfolgenden Seiten manuell definieren und dann ein Beispiel für das zugehörige Web-Verfolgungstag generieren. Dieser Vorgang wird im **[!UICONTROL Campaign execution>Resources>Web tracking tags]** Knoten der Client-Konsole definiert.

![](assets/d_ncs_integration_webtracking_screen.png)

So generieren Sie den HTML-Code, der in die Seite eingefügt werden soll:

* Geben Sie die Bezeichnung des Tags ein: es wird in den Verfolgungsprotokollen angezeigt,
* Quell-URL angeben: dieses Feld dient Informationszwecken und ermöglicht die Angabe der verfolgten Seite (optional),
* Geben Sie bei Bedarf eine Gültigkeitsdauer ein,
* Klicken Sie auf **[!UICONTROL Generate]** HTML-Code.

Kopieren Sie dann den generierten Code und fügen Sie ihn in die zu verfolgende Seite ein.

## Direkte Erstellung von zu verfolgenden URLs {#on-the-fly-creation-of-urls-to-be-tracked}

Sie können die Web-Tracking-URLs spontan erstellen, indem Sie dem Wert des **tagid** -Parameters Informationen hinzufügen:

* Typ der verfolgten Seite: &#39;w&#39; für WEB oder &#39;t&#39; für TRANSACTION,
* Der interne Name des Ordners, in dem die URL erstellt werden muss.

Diese beiden Informationen müssen mit dem Bezeichner der verfolgten Seite verknüpft werden, indem das Zeichen &quot;|&quot; hinzugefügt wird:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Denken Sie daran, den Wert des Parameters **tagid** zu kodieren, wenn er als URL-Parameter verwendet wird.

**Beispiel**: Erstellung einer Transaktionstyp-Web-Tracking-URL.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
