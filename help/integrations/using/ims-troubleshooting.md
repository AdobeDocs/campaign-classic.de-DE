---
title: Problembehebung bei IMS
seo-title: Problembehebung bei IMS
description: Problembehebung bei IMS
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Problembehebung bei IMS{#ims-troubleshooting}

Mithilfe der folgenden Problembehebungstipps können **On-Premise**-Kunden die gängigsten Probleme bei Verwendung der IMS-Integration beheben. **Gehostete** Kunden sollten sich an Adobe wenden.

**Externes Konto**

Es sollte nur **ein** externes Konto mit folgenden Einstellungen vorhanden sein:

* **Interner Name**: Adobe_Marketing_Cloud
* **Typ**: Adobe Marketing Cloud

Löschen Sie etwaige doppelte externe Konten, die dieselben Einstellungen aufweisen.

**Produktkontext**

Wenn das externe Konto das Feld **Produktkontext** aufweist, überprüfen Sie, ob dafür der Wert **dma_campaign_classic** festgelegt ist.

Stellen Sie sicher, dass der Produktkontext für Campaign und Experience Cloud identisch ist.

Wenn beispielsweise das Feld **Produktkontext** nicht angezeigt wird, sollte der Standardproduktkontext sowohl für Campaign als auch Experience Cloud **dma_campaign** lauten. Wenn das Feld **Produktkontext** angezeigt wird, sollte der Standardproduktkontext sowohl für Campaign als auch Experience Cloud **dma_campaign_classic** lauten.

**[!UICONTROL IMS Server URL]**

Überprüfen Sie im externen Kampagnen- **Adobe Marketing Cloud** -Konto, ob es sich um **[!UICONTROL IMS Server URL]** adobeid-na1.services.adobe.com[ oder ](https://adobeid-na1.services.adobe.com/)ims-na1.adobelogin.com[](http://ims-na1.adobelogin.com/) handelt. Stellen Sie sicher, dass sowohl die Stage- als auch die Produktionsinstanzen auf denselben IMS-Produktionsendpunkt verweisen.

**Zuordnungsmaske**

* Überprüfen Sie, ob der Benutzer, der sich anzumelden versucht, zu einer Benutzergruppe im Enterprise Dashboard gehört.
* Check that the **[!UICONTROL Association Mask]** is a prefix of the user&#39;s operator group name in the Enterprise Dashboard.
* Achten Sie darauf, dass keine Leerzeichen und Rechtschreibfehler vorhanden sind.
* Stellen Sie sicher, dass die Namen der Benutzergruppen in Campaign nicht geändert wurden, und befolgen Sie folgende Syntax:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Perimeter**

Im externen Campaign-Konto definierte Perimeter müssen eine Teilmenge der von IMS bereitgestellten Perimeter sein.

**Callback-URL**

Die **Callback-URL** sollte sich auf der Whitelist befinden und mit &quot;https://&quot; beginnen. Überprüfen Sie, ob die **Callback-URL** mit der entsprechenden Instanz verknüpft ist. Beispielsweise sollte die Produktionsinstanz an die Produktions-URL weiterleiten.

**Clientkennung und Client-Geheimnis**

Die Clientkennung stimmt bei externem Campaign-Konto und dem von IMS bereitgestellten Konto überein.

Überprüfen Sie, ob das eingegebene Client-Geheimnis korrekt ist.

**Server neu starten**

Führen Sie einen Neustart des Servers durch, falls Änderungen an den obigen Einstellungen im externen Campaign-Konto vorgenommen werden.

**Gängige Fehlertypen und mögliche Lösungen**

* Der Benutzer wird an die Seite &quot;adobe.com&quot; weitergeleitet:

   Es gibt ein Problem mit dem **[!UICONTROL Callback URL]**. Refer to the previous steps to check the **[!UICONTROL Callback URL]** configuration.

* Meldung &quot;Der Login besitzt keine Berechtigung, die dem Ausdruck in Adobe Campaign entspricht&quot;:

   Refer to the previous steps to check the **[!UICONTROL Association Mask]** and operator groups configuration.

* Der Benutzer kann nicht auf die Seite für die Anmeldung mit der Adobe ID zugreifen:

   Überprüfen Sie anhand der vorherigen Schritte die Perimeterkonfiguration.

