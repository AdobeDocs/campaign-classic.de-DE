---
product: campaign
title: Fehlerbehebung bei IMS
description: Fehlerbehebung bei IMS
feature: Configuration
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
TQID: https://experienceleague.adobe.com/cUoMAlp8ExhammApiilFqRyrOkyyqxk1om0AifZVxb0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 521
ht-degree: 100%

---

# Fehlerbehebung bei IMS{#ims-troubleshooting}


Mithilfe folgender Tipps können **On-Premise** und **Hybrid**-Kundinnen und -Kunden die gängigsten Probleme mit der IMS-Integretion beheben. **Gehostete** Kundinnen und Kunden wenden sich bitte an Adobe.

**Externes Konto**

Es sollte nur **ein** externes Konto mit folgenden Einstellungen vorhanden sein:

* **Interner Name**: Adobe_Marketing_Cloud
* **Typ**: Adobe Marketing Cloud

Löschen Sie etwaige doppelte externe Konten, die dieselben Einstellungen aufweisen.

**Produktkontext**

Wenn das externe Konto das Feld **Produktkontext** aufweist, überprüfen Sie, ob dafür der Wert **dma_campaign_classic** festgelegt ist.

Stellen Sie sicher, dass der Produktkontext für Campaign und Experience Cloud identisch ist.

Wenn beispielsweise der **Produktkontext** nicht angezeigt wird, sollte der standardmäßige Produktkontext in Campaign sowie in Experience Cloud **dma_campaign** lauten. Wenn das Feld **Produktkontext** angezeigt wird, sollte der standardmäßige Produktkontext in Campaign sowie in Experience Cloud **dma_campaign_classic** lauten.

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

**Probleme mit WebView2-Cache**

Wenn bei der Anmeldung mit Ihrer Adobe ID bei der **[!UICONTROL Client-Konsole]** Probleme auftreten, versuchen Sie, den lokalen WebView2-Cache zu löschen. In den meisten Fällen löst dies das Problem. Gehen Sie wie folgt vor:

1. Schließen Sie die **[!UICONTROL Client-Konsole]** und stoppen Sie alle laufenden `nlclient`-Prozesse.

1. Löschen Sie alle `webview2`- und `webview2Cache`-Ordner an den folgenden Speicherorten:

   * `C:\ProgramData\Neolane\NL_5\nlclient\`
   * `C:\Users\<username>\AppData\Roaming\Neolane\NL_5\nlclient\`

1. Starten Sie die **[!UICONTROL Client-Konsole]** neu und melden Sie sich mit Ihrer Adobe ID an. Die Cache-Ordner werden beim nächsten Launch automatisch neu erstellt.
