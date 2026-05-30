---
product: campaign
title: Best Practices bei der Inhaltsbearbeitung
description: Best Practices bei der Inhaltsbearbeitung
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
TQID: https://experienceleague.adobe.com/9ei3-06pNnCbg0airicWrcVLosdZLvuq7RCUrEfHxGc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2: id: f391046b-0cf3-4e76-bd3b-97fe06654506id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 571
ht-degree: 81%

---

# Best Practices bei der Inhaltsbearbeitung{#content-editing-best-practices}



Bitte beachten Sie folgende Hinweise, um eine optimale Funktionsweise des Editors zu gewährleisten:

* Bevor Sie in Adobe Campaign eine **HTML-Vorlage importieren**, ist sicherzustellen, dass die Vorlage korrekt geöffnet und in den verschiedenen Browsern angezeigt werden kann.
* Wenn die HTML-Seite **JavaScript**-Elemente enthält, müssen diese außerhalb des Editors **fehlerfrei** ausführbar sein.
* Bei der Erstellung einer Vorlage wird empfohlen, den Tags ein **&#39;type&#39;**-Attribut beizufügen. `<input>` Beim Konfigurieren von Webanwendungen hilft die Interpretation dieser Information durch den Editor dem Benutzer bei der Zuordnung von einem Feld der Datenbank zu dem Feld des Formulars.

  Beispiel eines HTML-Codes in einer Vorlage:

  ```
  <input id="email" type="email" name="email"/>
  ```

  Das Attribut **type** ist in der Benutzeroberfläche in der folgenden Form sichtbar:

  ![](assets/dce_sidebar_inputtypechanges.png)

  Die offizielle Liste der „type“-Attribute ist [auf dieser Website](https://www.w3schools.com/tags/att_input_type.asp) verfügbar.

* Schritte zur Simulation einer Endseite mit dem DCE:

  ![](assets/dce_enchainement.png)

* Achten Sie darauf, dass `<body> </body>` auf der Seite nur einmal vorkommt.
* Beim Hochladen einer CSS- oder JS-Datei werden die in der ZIP-Datei enthaltenen Bilder nicht hochgeladen. Die Verweise auf diese Bilder im CSS werden daher nicht aktualisiert.

## Vom Content Editor unterstützte Formate {#content-editor-supported-formats}

Der Digital Content Editor unterstützt das HTML-Format: Sie können jederzeit in den **Quellmodus** wechseln.

Die Importfunktion des Digital Content Editors funktioniert mit diesen unterstützten Formaten folgendermaßen:

* CSS: die in der ZIP-Datei vorhandenen Bilder werden nicht importiert. Die Verweise auf diese Bilder im CSS werden nicht aktualisiert.
* JS: die in der ZIP-Datei vorhandenen Bilder werden nicht importiert. Die Verweise auf diese Bilder im JS werden nicht aktualisiert.
* Iframe: Die verknüpften Seiten werden nicht importiert.
* Landingpages und Webanwendungen: Wenn ein **form**-Tag fehlt, wird eine Warnung angezeigt. Im Nachrichtentext muss immer ein `<form> </form>` vorhanden sein.

Der Digital Content Editor unterstützt auch die folgenden Code-Seiten:

* ISO-8859-1
* ISO-8859-2
* UTF-7
* UTF-8 (empfohlen bei der Verwendung eines BOM)
* ISO-8859-15
* US-ASCII
* Shift-JIS
* ISO-2022-JP
* BIG-5
* EUC-KR
* UTF-16

>[!NOTE]
>
>Die HTML-Codeseite muss in einem Meta-Tag (HTML 4 oder HTML 5) oder in der Stückliste definiert werden. Wenn keine Codeseite verfügbar ist, öffnen Sie die Datei in latin1.

## HTML-Inhaltsstatus {#html-content-statuses}

Im oberen Bereich des Editors werden Meldungen angezeigt, die sich auf den Status des Inhalts beziehen. Die Farbcodes für die Nachrichten lauten wie folgt:

* **Graue Nachricht:** Informationsnachricht, keine Aktionen sind im Editor erforderlich.
* **Blaue Nachricht:** Informationsnachricht im Zusammenhang mit dem bearbeiteten Inhalt.
* **Gelbe Nachricht**: Warnhinweis oder Fehlermeldung erfordert eine Aktion vonseiten des Benutzers.

### Liste der Nachrichten beim Bearbeiten einer Web-Anwendung {#list-of-messages-when-editing-a-web-application}

* Der HTML-Inhalt ist funktionsfähig.
* Webanwendung wurde nicht veröffentlicht. Es besteht kein Online-Zugriff.
* Die Webanwendung ist online. Änderungen werden nur durch eine erneute Veröffentlichung übernommen.
* Der Inhalt der Seite ist nicht funktionsfähig. Es muss ein HTML-Formular vorhanden (`<form>`) sein
* Noch n Eingabefelder oder Schaltflächen zu konfigurieren.
* Um das Weiterblättern zu ermöglichen, ist die Verbindung der Aktion &quot;Folgende Seite&quot; mit einer Schaltfläche oder einem Link der aktuellen Seite erforderlich.

### Liste der Nachrichten beim Bearbeiten eines Versands {#list-of-messages-when-editing-a-delivery}

* Versandinhalt ist einsatzbereit.
* Noch n Personalisierungsfelder oder Gestaltungsbausteine zu konfigurieren.
* Versandinhalt wurde vorbereitet. Änderungen erfordern eine erneute Analyse.
* Der Versand ist startbereit.
