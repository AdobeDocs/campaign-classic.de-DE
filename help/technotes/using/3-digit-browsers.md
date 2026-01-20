---
product: campaign
title: Campaign-Web-Komponenten und Version 100 in Chrome-, Firefox- und Edge-Browsern
description: Campaign-Web-Komponenten und Version 100 in Chrome-, Firefox- und Edge-Browsern
feature: Technote
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '644'
ht-degree: 100%

---

# Die dreistellige Browser-Version hat Einfluss auf Campaign-Web-Komponenten {#version-100}

Google und Mozilla warnen, dass Chrome und Firefox aufgrund der kommenden dreistelligen Versionen einige Websites beschädigen könnten.

Chrome v100 soll am **29. März 2022** und Firefox v100 soll am **3. Mai 2022** veröffentlicht werden.

Microsoft hat Edge v100 bereits Anfang März 2022 veröffentlicht.

Die Änderung der Versionsnummer von zwei auf drei Stellen kann beim Besuch von Websites, die für diese Änderung nicht ausgelegt sind, zu Problemen führen. Einige Web-Seiten werden in diesen neuen Browser-Versionen möglicherweise nicht mehr korrekt angezeigt.

Die Kompatibilität der wichtigsten Websites wurde im Voraus getestet. Wenn es Probleme mit Sites gibt, die nicht behoben werden können, bevor diese Versionen veröffentlicht werden, haben Unternehmen Backup-Pläne, die sicherstellen, dass die Sites nicht betroffen sind.

Potenzielle Probleme oder Funktionsverluste auf der Website stammen aus der Benutzeragenten-Zeichenfolge, die Browser an besuchte Websites senden: Der Benutzeragent ist eine Zeichenfolge, die vom Browser an die Website gesendet wird, um der Site mitzuteilen, welchen Browser, welche Version und welche zugehörige Technologie Sie verwenden. Wenn Ihr Browser eine Anfrage an eine Website sendet, identifiziert er sich mit der Benutzeragenten-Zeichenfolge, bevor der angeforderte Inhalt abgerufen wird. Die Daten in der Benutzeragenten-Zeichenfolge helfen der Website, den Inhalt in einem Format bereitzustellen, das zu Ihrem Browser passt. Die Version des Benutzeragenten wird inkrementiert, sodass sie der Versionsnummer des Browsers entspricht. Das Wechseln von zwei auf drei Stellen kann zu Problemen führen.

## Sind Sie betroffen?{#version-100-impact}

Adobe empfiehlt, Ihre Campaign-Web-Programme, einschließlich Web-Formularen und Umfragen, zu testen, um sicherzustellen, dass sie mit diesen neuen Browser-Versionen weiterhin problemlos funktionieren.

Diese Empfehlung gilt für alle Web-Programme, insbesondere wenn Sie JavaScript-Code eingebunden haben.

Sie müssen dies in allen Browsern (mobil und Desktop) prüfen.

## Wie testen Sie dies?{#version-100-test}

Sie können Ihre Browser so konfigurieren, dass die Version schon jetzt als 100 angenommen wird. Dann können Sie alle Probleme, auf die Sie stoßen, erfassen und korrigieren.

Mit diesen Einstellungen sendet der Browser die neue Benutzeragenten-Zeichenfolge an Websites und gibt an, dass der Browser v100 hat. Wenn Probleme mit Ihren Web-Formularen auftreten, sollten Sie einen Fehler für den Browser-Editor erstellen. Wir empfehlen, diese Web-Formulare neu zu erstellen, bevor diese Aktualisierungen allgemein verfügbar sind.

### Testen mit Firefox 100{#test-firefox-100}

Um Ihre Web-Seiten mit Mozilla Firefox 100 zu testen, können Sie die bevorstehende Änderung des Benutzeragenten in Ihren Web-Apps simulieren, indem Sie Ihre Benutzeragenten-Zeichenfolge manuell ändern.

1. Öffnen Sie Firefox, geben Sie `about:config` in der Adressleiste ein und drücken Sie die Eingabetaste.
1. Suchen Sie nach `general.useragent.override`.
1. Wählen Sie &quot;Zeichenfolge&quot; aus und klicken Sie auf das Pluszeichen (+).

   ![](assets/force-user-agent-firefox.png)

1. Geben Sie folgenden Text in das Feld ein:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Klicken Sie auf das blaue Häkchen, um die Einstellung zu speichern.
1. Schließen Sie den Browser und starten Sie ihn neu.

Wenn Sie Ihren Benutzeragenten wieder auf die Standardeinstellung zurücksetzen möchten, gehen Sie einfach zurück zu `about:config` und suchen Sie wieder nach der Einstellung `general.useragent.override`.  Wenn sie angezeigt wird, klicken Sie auf das Papierkorbsymbol, um die Einstellung zu löschen, und starten Sie den Browser neu.

### Testen mit Chrome 100{#test-chrome-100}

Um den Google Chrome 100-Benutzeragenten in Ihren eigenen Web-Apps zu testen, können Sie diesen Test mit den folgenden Schritten aktivieren:

1. Öffnen Sie Chrome, geben Sie `chrome://flags` in der Adressleiste ein und drücken Sie die Eingabetaste.
1. Suchen Sie `Force major version to 100 in User-Agent` im Suchfeld und aktivieren Sie die Einstellung wie unten dargestellt.

   ![](assets/force-user-agent-chrome.png)

1. Starten Sie den Browser neu.
1. Schließen Sie die Registerkarte `chrome://flags`.

Um den Benutzeragenten wieder in die Standardeinstellung zu ändern, führen Sie diesen Prozess aus, ändern Sie die Einstellung des Flags in `Default` und starten Sie den Browser neu.


### Testen mit Microsoft Edge 100{#test-ms-edge-100}

Ab Version 97 können Site-Besitzer diese Version emulieren, indem sie die Experiment-Flag `#force-major-version-to-100` in `edge://flags` aktivieren.

1. Öffnen Sie Microsoft Edge, geben Sie `edge://flags` in der Adressleiste ein und drücken Sie die Eingabetaste.
1. Suchen Sie nach `force-major-version-to-100` und aktivieren Sie die Einstellung wie unten dargestellt.

   ![](assets/force-user-agent-edge.png)

1. Starten Sie den Browser neu.
1. Schließen Sie die Registerkarte `edge://flags`.

Um den Benutzeragenten wieder in die Standardeinstellung zu ändern, führen Sie diesen Prozess aus, ändern Sie die Einstellung des Flags in `Default` und starten Sie den Browser neu.
