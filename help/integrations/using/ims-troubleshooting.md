---
product: campaign
title: Fehlerbehebung bei IMS
description: Fehlerbehebung bei IMS
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Fehlerbehebung bei IMS{#ims-troubleshooting}



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

**[!UICONTROL IMS-Server-URL]**

Prüfen Sie im externen Konto von Campaign für **Adobe Marketing Cloud**, ob die **[!UICONTROL IMS-Server-URL]** `adobeid-na1.services.adobe.com` oder `ims-na1.adobelogin.com` ist. Stellen Sie sicher, dass sowohl Staging- als auch Produktionsinstanzen auf denselben IMS-Produktionsendpunkt verweisen.

**Zuordnungsmaske**

* Überprüfen Sie, ob der Benutzer, der sich anzumelden versucht, zu einer Benutzergruppe im Enterprise Dashboard gehört.
* Überprüfen Sie, ob die **[!UICONTROL Zuordnungsmaske]** ein Präfix des Benutzergruppennamens des Benutzers im Enterprise Dashboard ist.
* Achten Sie darauf, dass keine Leerzeichen und Rechtschreibfehler vorhanden sind.
* Stellen Sie sicher, dass die Namen der Benutzergruppen in Campaign nicht geändert wurden, und befolgen Sie folgende Syntax:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Perimeter**

Im externen Campaign-Konto definierte Perimeter müssen eine Teilmenge der von IMS bereitgestellten Perimeter sein.

**Callback-URL**

Die **Callback-URL** sollte der Zulassungsliste hinzugefügt werden und mit &quot;https://&quot; beginnen. Vergewissern Sie sich, dass die **Callback-URL** mit der entsprechenden Instanz verknüpft ist. Beispielsweise sollte die Produktionsinstanz zur Produktions-URL umgeleitet werden.

**Clientkennung und Client-Geheimnis**

Die Clientkennung stimmt bei externem Campaign-Konto und dem von IMS bereitgestellten Konto überein.

Überprüfen Sie, ob das eingegebene Client-Geheimnis korrekt ist.

**Server neu starten**

Führen Sie einen Neustart des Servers durch, falls Änderungen an den obigen Einstellungen im externen Campaign-Konto vorgenommen werden.

**Gängige Fehlertypen und mögliche Lösungen**

* Der Benutzer wird an die Seite &quot;adobe.com&quot; weitergeleitet:

   Es gibt ein Problem mit der **[!UICONTROL Callback-URL]**. Überprüfen Sie anhand der vorherigen Schritte die Konfiguration der **[!UICONTROL Callback-URL]**.

* Meldung &quot;Der Login besitzt keine Berechtigung, die dem Ausdruck in Adobe Campaign entspricht&quot;:

   Überprüfen Sie anhand der vorherigen Schritte die Konfiguration von **[!UICONTROL Zuordnungsmaske]** und Benutzergruppen.

* Der Benutzer kann nicht auf die Seite für die Anmeldung mit der Adobe ID zugreifen:

   Überprüfen Sie anhand der vorherigen Schritte die Perimeterkonfiguration.
