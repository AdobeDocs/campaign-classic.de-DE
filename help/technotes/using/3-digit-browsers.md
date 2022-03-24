---
product: campaign
title: Campaign-Webkomponenten und Version 100 in Chrome Firefox und Edge-Browsern
description: Campaign-Webkomponenten und Version 100 in Chrome-, Firefox- und Edge-Browsern
hide: true
hidefromtoc: true
source-git-commit: 48c9aab4f7e5f1f204a003a4d53f8d975247b867
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Die dreistellige Browserversion wirkt sich auf die Campaign-Webkomponenten aus {#version-100}

Google, Mozilla warnen, dass Chrome und Firefox aufgrund der kommenden 3-stelligen Versionen einige Websites beschädigen könnten.

Chrome v100 ist für die Veröffentlichung auf **29. März 2022** und Firefox v100 on **3. Mai 2022**.

Beachten Sie, dass Microsoft Edge ihre Version 100 Anfang März 2022 veröffentlicht hat.

Die Änderung der Versionsnummer von 2 auf 3 Stellen kann beim Besuch von Websites, die für diese Änderung nicht vorbereitet sind, zu Problemen führen. Einige Webseiten werden in diesen neuen Browserversionen möglicherweise nicht mehr korrekt angezeigt.

Die Kompatibilität der wichtigsten Websites wurde bereits früher getestet. Wenn es Probleme mit Sites gibt, die nicht behoben werden können, bevor diese Versionen veröffentlicht werden, verfügen Unternehmen über Backup-Pläne, die sicherstellen, dass die Sites nicht betroffen sind.

Potenzielle Probleme oder Funktionsverluste auf der Website stammen aus der Benutzeragenten-Zeichenfolge, die Browser an besuchte Websites senden: Der Benutzeragent ist eine Zeichenfolge, die vom Browser an die Website gesendet wird, um der Site mitzuteilen, welcher Browser und welche Version Sie verwenden, und die zugehörige Technologie. Wenn Ihr Browser eine Anforderung an eine Website sendet, identifiziert er sich mit der Benutzeragenten-Zeichenfolge, bevor der angeforderte Inhalt abgerufen wird. Die Daten in der Benutzeragenten-Zeichenfolge helfen der Website, den Inhalt in einem Format bereitzustellen, das Ihrem Browser entspricht. Die Version des Benutzeragenten wird inkrementiert und entspricht der Versionsnummer des Browsers. Das Wechseln von 2 zu 3 Stellen kann zu Problemen führen.

## Sind Sie betroffen?{#version-100-impact}

Adobe empfiehlt, Ihre Campaign-Webanwendungen, einschließlich Webformulare und Umfragen, zu testen, um sicherzustellen, dass sie mit diesen neuen Browserversionen weiterhin problemlos funktionieren.

Diese Empfehlung gilt für alle Webanwendungen, insbesondere wenn Sie JavaScript-Code eingefügt haben.

Sie müssen beide Browser, Mobile und Desktop, verwenden.

## Wie testen Sie?{#version-100-test}

Sie können Ihre Browser so konfigurieren, dass die Version jetzt als 100 gemeldet wird und dann alle Probleme, auf die Sie stoßen, melden und korrigieren.

Mit diesen Einstellungen sendet der Browser die neue Benutzeragenten-Zeichenfolge an Websites und gibt an, dass der Browser v100 ist. Wenn Probleme mit Ihren Webformularen auftreten, sollten Sie einen Fehler für den Browser-Editor erstellen. Erwägen Sie, diese Webformulare neu zu erstellen, bevor diese Aktualisierungen allgemein verfügbar sind.

### Testen mit Firefox 100{#test-firefox-100}

Um Ihre Webseiten mit Mozilla Firefox 100 zu testen, können Sie die bevorstehende Änderung des Benutzeragenten in Ihren Web-Apps simulieren, indem Sie die Zeichenfolge Ihres Benutzeragenten manuell ändern.

1. Öffnen Sie Firefox, geben Sie ein. `about:config` in der Adressleiste und drücken Sie die Eingabetaste.
1. Suchen Sie nach `general.useragent.override`.
1. Wählen Sie &quot;String&quot;und klicken Sie auf das Pluszeichen (+).

   ![](assets/force-user-agent-firefox.png)

1. Geben Sie folgenden Text in das Feld ein:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Klicken Sie auf die blaue Markierungsschaltfläche, um die Einstellung zu speichern.
1. Schließen Sie den Browser und starten Sie ihn neu.

Wenn Sie Ihren Benutzeragenten wieder auf die Standardeinstellung zurücksetzen möchten, gehen Sie einfach zurück zu `about:config` und suchen Sie nach `general.useragent.override` wieder einstellen.  Wenn es angezeigt wird, klicken Sie auf das Papierkorbsymbol, um die Einstellung zu löschen, und starten Sie den Browser neu.

### Test mit Chrome 100{#test-chrome-100}

Um den Google Chrome 100-Benutzeragenten in Ihren eigenen Web-Apps zu testen, können Sie diesen Test mit den folgenden Schritten aktivieren:

1. Chrome öffnen, eingeben `chrome://flags` in der Adressleiste und drücken Sie die Eingabetaste.
1. Suche `Force major version to 100 in User-Agent` in das Suchfeld ein und aktivieren Sie es wie unten dargestellt.

   ![](assets/force-user-agent-chrome.png)

1. Starten Sie den Browser neu.
1. Schließen Sie die `chrome://flags` Registerkarte.

Um den Benutzeragenten wieder auf die Standardeinstellung zu setzen, führen Sie diesen Prozess aus und ändern Sie die Einstellung des Kennzeichens in `Default` und starten Sie den Browser neu.


### Testen mit Microsoft Edge 100{#test-ms-edge-100}

Ab Version 97 können Site-Eigentümer diese Version emulieren, indem sie das Experiment-Flag aktivieren.  `#force-major-version-to-100` in `edge://flags`.

1. Microsoft Edge öffnen, eingeben `edge://flags` in der Adressleiste und drücken Sie die Eingabetaste.
1. Suchen Sie nach `force-major-version-to-100` und aktivieren Sie es wie unten dargestellt.

   ![](assets/force-user-agent-edge.png)

1. Starten Sie den Browser neu.
1. Schließen Sie die `edge://flags` Registerkarte.

Um den Benutzeragenten wieder auf die Standardeinstellung zu setzen, führen Sie diesen Prozess aus und ändern Sie die Einstellung des Kennzeichens in `Default` und starten Sie den Browser neu.
