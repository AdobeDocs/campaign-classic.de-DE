---
product: campaign
title: Campaign-Webkomponenten und Version 100 in Chrome- und Firefox-Browsern
description: Campaign-Webkomponenten und Version 100 in Chrome- und Firefox-Browsern
hide: true
hidefromtoc: true
source-git-commit: 88148b70de408de7571166e1869c088e10e87bae
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Auswirkungen von Chrome und Firefox 100 auf Campaign-Webkomponenten {#version-100}

Google und Mozilla warnen, dass Chrome und Firefox aufgrund der kommenden 3-stelligen Versionen einige Websites beschädigen könnten.

Die Änderung der Versionsnummer von 2 auf 3 Stellen kann beim Besuch von Websites, die für diese Änderung nicht vorbereitet sind, zu Problemen führen. Einige Webseiten werden in diesen neuen Browserversionen möglicherweise nicht mehr korrekt angezeigt.

Chrome v100 ist für die Veröffentlichung auf **29. März 2022** und Firefox v100 on **3. Mai 2022**.

Mozilla und Google testen bereits im Vorfeld die Kompatibilität der wichtigsten Websites. Wenn es Probleme mit Sites gibt, die vor der Veröffentlichung dieser Versionen nicht behoben werden können, verfügen beide über Backup-Pläne, um sicherzustellen, dass die Sites nicht betroffen sind.

Potenzielle Probleme oder Funktionsverluste auf der Website stammen aus der Benutzeragenten-Zeichenfolge, die Browser an besuchte Websites senden: Der Benutzeragent ist eine Zeichenfolge, die vom Browser an die Website gesendet wird, um der Site mitzuteilen, welcher Browser und welche Version Sie verwenden, und die zugehörige Technologie. Wenn Ihr Browser eine Anforderung an eine Website sendet, identifiziert er sich mit der Benutzeragenten-Zeichenfolge, bevor der angeforderte Inhalt abgerufen wird. Die Daten in der Benutzeragenten-Zeichenfolge helfen der Website, den Inhalt in einem Format bereitzustellen, das Ihrem Browser entspricht. Die Version des Benutzeragenten wird inkrementiert und entspricht der Versionsnummer des Browsers. Das Wechseln von 2 zu 3 Stellen kann zu Problemen führen.

## Sind Sie betroffen?{#version-100-impact}

Adobe empfiehlt, Ihre Campaign-Webanwendungen, einschließlich Webformularen und Umfragen, sowie E-Mail-Mirrorseiten zu testen, um sicherzustellen, dass sie mit diesen neuen Browserversionen weiterhin problemlos funktionieren.

Diese Empfehlung gilt für alle Webanwendungen, insbesondere wenn Sie JavaScript-Code eingefügt haben.

Sie müssen sowohl mit Firefox als auch Chrome, Mobile und Desktop überprüfen.

## Wie testen Sie?{#version-100-test}

In Chrome und Firefox können Sie den Browser so konfigurieren, dass die Version jetzt als 100 gemeldet und dann alle Probleme, auf die Sie stoßen, gemeldet und korrigiert werden.

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

Mit diesen Einstellungen sendet der Browser die neue Benutzeragenten-Zeichenfolge an Websites und gibt an, dass der Browser Firefox 100 ist. Wenn Probleme mit Ihren Webformularen auftreten, sollten Sie einen neuen Fehlerbericht für Mozilla erstellen. Erwägen Sie, diese Webformulare neu zu erstellen, bevor diese Änderung allgemein verfügbar ist.

Wenn Sie Ihren Benutzeragenten wieder auf die Standardeinstellung zurücksetzen möchten, gehen Sie einfach zurück zu `about:config` und suchen Sie nach `general.useragent.override` wieder einstellen.  Wenn es angezeigt wird, klicken Sie auf das Papierkorbsymbol, um die Einstellung zu löschen, und starten Sie den Browser neu.

### Test mit Chrome 100{#test-chrome-100}

Um den Google Chrome 100-Benutzeragenten in Ihren eigenen Web-Apps zu testen, können Sie diesen Test mit den folgenden Schritten aktivieren:

1. Chrome öffnen, eingeben `chrome://flags` in der Adressleiste und drücken Sie die Eingabetaste.
1. Suche `Force major version to 100 in User-Agent` in das Suchfeld ein und aktivieren Sie es wie unten dargestellt.

   ![](assets/force-user-agent-chrome.png)

1. Schließen Sie den Browser und starten Sie ihn neu.
1. Schließen Sie die `chrome://flags` angezeigt.

Mit diesen Einstellungen sendet der Browser die neue Benutzeragenten-Zeichenfolge an Websites und gibt an, dass der Browser Chrome 100 ist. Wenn Probleme mit den Websites auftreten, die Sie besuchen, sollten Sie einen neuen Fehlerbericht für Google erstellen. Erwägen Sie, diese Webformulare neu zu erstellen, bevor diese Änderung allgemein verfügbar ist.

Um den Benutzeragenten wieder auf die Standardeinstellung zu setzen, führen Sie diesen Prozess aus und ändern Sie die Einstellung des Kennzeichens in `Default` und starten Sie den Browser neu.
