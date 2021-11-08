---
product: campaign
title: Spezifische Konfigurationen in v6.02
description: Spezifische Konfigurationen in v6.02
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 7e8f8488-f3ef-4b64-9981-335d67caf372
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# Spezifische Konfigurationen in v6.02{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

Im folgenden Abschnitt wird die zusätzliche Konfiguration beschrieben, die für die Migration von v6.02 erforderlich ist. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

## Web-Anwendungen {#web-applications}

Wenn Sie von v6.02 migrieren, werden möglicherweise Fehlerprotokolle zu Webanwendungen vom Typ &quot;Übersicht&quot;angezeigt. Beispiele für Fehlermeldungen:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Diese Webanwendungen verwendeten SQLData und sind aufgrund erhöhter Sicherheit nicht mit v7 kompatibel. Diese Fehler führen zu einem Migrationsfehler.

Wenn Sie diese Webanwendungen nicht verwendet haben, führen Sie das folgende Bereinigungsskript aus und führen Sie das Postupgrade erneut aus:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Wenn Sie diese Webanwendungen geändert haben und sie weiterhin in v7 verwenden möchten, müssen Sie die **allowSQLInjection** in Ihren verschiedenen Sicherheitszonen und starten Sie das Postupgrade neu. Siehe Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) finden Sie weitere Informationen dazu.

## Benutzerfreundlichkeit: Startseite und Navigation {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Wenn Sie Webanwendungen vom Typ &quot;Übersicht&quot;von v6.02 weiterhin verwenden möchten, müssen Sie die **allowSQLInjection** in den verschiedenen Sicherheitszonen vor dem Postupgrade. Siehe [Webanwendungen](#web-applications).

Nach der Migration von Version 6.02 wird die Adobe Campaign v6.02-Homepage nicht mehr angezeigt, ist aber weiterhin mit Adobe Campaign v7 verfügbar und kompatibel.

Um die Homepage v6.02 weiterhin zu verwenden, müssen Sie nach der Migration ein Kompatibilitätspaket installieren.

Importieren Sie dazu das Kompatibilitätspaket:

Klicken **[!UICONTROL Tools > Erweitert > Package importieren]** und wählen Sie die **campaignMigration.xml** -Paket im **`\nl\datakit\nms\[Your language]\package\optional`**.

Um den Zugriff auf die Schnittstellen vom Typ Web Application (v6.02) zu ermöglichen, muss die **sessionTokenOnly** Die Server-Konfigurationsoption muss in der **serverConf.xml** Datei:

```
sessionTokenOnly="true"
```

Diese Option ändert die Sicherheitsstufen, um die Kompatibilität der Benutzeroberfläche sicherzustellen.

Nachdem das Paket installiert wurde, wird die Adobe Campaign v7-Startseite durch Ihre alte v6.02-Homepage ersetzt, die mit den allgemeinen Konfigurationen von v7 (blaues Startseitenbanner) ergänzt wird.

![](assets/dashboards.png)

Alle Links auf dieser Homepage verlinken zu v7-Bildschirmen mit Ausnahme der Listen (**[!UICONTROL Vorgangsliste]**, **[!UICONTROL Versand-Tracking in Vorgängen]** usw.) , der auf die v6.02-Übersicht (Webanwendungen) verweist.

![](assets/dashboards2.png)

Wenn Sie eine weitere Übersicht hinzufügen möchten, die in v6.02 konfiguriert wurde, müssen Sie diese auf der Startseite im Dashboard hinzufügen. (**[!UICONTROL Administration > Zugriffe > Dashboard]**).

>[!NOTE]
>
>Denken Sie daran, die Verbindung zu trennen und dann die Konsole erneut zu verbinden, um die Änderungen zu registrieren.

## Message Center {#message-center}

Nach der Migration der Kontrollinstanz von Message Center müssen Sie die Transaktionsnachrichten-Vorlagen erneut veröffentlichen, damit sie funktionieren.

In v7 haben sich die Namen der Transaktionsnachrichten-Vorlagen auf Ausführungsinstanzen geändert. Sie erhalten derzeit das Präfix des Operatornamens, der der Kontrollinstanz entspricht, auf der sie erstellt werden, z. B. **control1_template1_rt** , **control1** der Name des Benutzers). Wenn Sie eine große Menge an Vorlagen haben, empfehlen wir, alte Vorlagen in Kontrollinstanzen zu löschen.
