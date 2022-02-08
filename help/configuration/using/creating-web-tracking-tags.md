---
product: campaign
title: Webtrackingtags erstellen
description: Erfahren Sie, wie Sie Web-Tracking-Tags erstellen
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Webtrackingtags erstellen{#creating-web-tracking-tags}

![](../../assets/v7-only.svg)

Jede Seite der Site, die Sie verfolgen möchten, muss in Ihrer Adobe Campaign-Plattform referenziert werden. Diese Referenzierung kann auf zwei Arten durchgeführt werden:

1. Manuelle Definition der zu verfolgenden URLs,
1. Erstellung von URLs, die direkt verfolgt werden sollen.

## Definieren der URLs, die in der Anwendung verfolgt werden sollen {#defining-the-urls-to-be-tracked-in-the-application}

Mit dieser Methode können Sie die zu verfolgenden Seiten manuell definieren und dann ein Beispiel für das zugehörige Webtrackingtag generieren. Dieser Vorgang wird im **[!UICONTROL Kampagnenausführung > Ressourcen > Webtracking-Tags]** -Knoten der Clientkonsole.

![](assets/d_ncs_integration_webtracking_screen.png)

So generieren Sie den HTML-Code, der in die Seite eingefügt werden soll:

* Geben Sie den Titel des Tags ein: wird es in den Trackinglogs angezeigt,
* Geben Sie die Quell-URL an: Dieses Feld dient zu Informationszwecken und ermöglicht die Angabe der verfolgten Seite (optional).
* Geben Sie bei Bedarf einen Gültigkeitszeitraum an.
* Klicken **[!UICONTROL Erzeugen]** HTML-Code.

Kopieren Sie dann den generierten Code und fügen Sie ihn in die zu verfolgende Seite ein.

## spontane Erstellung von zu verfolgenden URLs {#on-the-fly-creation-of-urls-to-be-tracked}

Sie können die Web-Tracking-URLs direkt erstellen, indem Sie dem Wert der Variablen **tagid** Parameter:

* Typ der verfolgten Seite: &quot;w&quot;für WEB oder &quot;t&quot;für TRANSAKTION,
* Der interne Name des Ordners, in dem die URL erstellt werden muss.

Diese beiden Informationen müssen mit der Kennung der verfolgten Seite durch Hinzufügen des Zeichens &#39;|&#39; verkettet werden:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Denken Sie daran, den Wert der **tagid** -Parameter, wenn er als URL-Parameter verwendet wird.

**Beispiel**: Erstellung einer Webtracking-URL vom Typ Transaktion.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
