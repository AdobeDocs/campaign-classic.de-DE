---
product: campaign
title: Erstellen von Webtracking-Tags
description: Erfahren Sie, wie Sie Webtracking-Tags erstellen
feature: Application Settings
role: Data Engineer, Developer
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Erstellen von Webtracking-Tags{#creating-web-tracking-tags}

Jede Seite der Site, die Sie verfolgen möchten, muss in Ihrer Adobe Campaign-Plattform referenziert werden. Diese Referenzierung kann auf zwei Arten durchgeführt werden:

1. Manuelle Definition der zu verfolgenden URLs,
1. Sofortige Erstellung der zu verfolgenden URLs

## URLs definieren, die in der Anwendung verfolgt werden sollen {#defining-the-urls-to-be-tracked-in-the-application}

Mit dieser Methode können Sie die zu verfolgenden Seiten manuell definieren und dann ein Beispiel für das zugehörige Webtracking-Tag generieren. Dieser Vorgang wird im Knoten **[!UICONTROL Kampagnenausführung>Ressourcen>Webtracking]** der Client-Konsole definiert.

![](assets/d_ncs_integration_webtracking_screen.png)

So generieren Sie den HTML-Code, der auf der Seite eingefügt werden soll:

* Geben Sie den Titel des Tags ein: es wird in den Trackinglogs angezeigt.
* Quell-URL angeben: Dieses Feld dient zu Informationszwecken und ermöglicht die Angabe der verfolgten Seite (optional).
* Geben Sie bei Bedarf einen Gültigkeitszeitraum ein,
* Klicken Sie auf **[!UICONTROL Generieren]** HTML-Code.

Kopieren Sie dann den generierten Code und fügen Sie ihn in die nachzuverfolgende Seite ein.

## Sofortige Erstellung der zu verfolgenden URLs {#on-the-fly-creation-of-urls-to-be-tracked}

Sie können die Webtracking-URLs direkt erstellen, indem Sie Informationen zum Wert des Parameters **tagid** hinzufügen:

* Art der verfolgten Seite: „w“ für WEB oder „t“ für TRANSAKTION,
* Der interne Name des Ordners, in dem die URL erstellt werden muss.

Diese beiden Informationen müssen mit der Kennung der verfolgten Seite verkettet werden, indem das Zeichen &#39;|&#39; hinzugefügt wird:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Denken Sie daran, den Wert des **tagid**-Parameters zu kodieren, wenn er als URL-Parameter verwendet wird.

**Beispiel**: Erstellung einer Webtracking-URL vom Typ Transaktion.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
