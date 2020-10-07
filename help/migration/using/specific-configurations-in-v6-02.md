---
title: Spezifische Konfigurationen in v6.02
seo-title: Spezifische Konfigurationen in v6.02
description: Spezifische Konfigurationen in v6.02
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 4%

---


# Spezifische Konfigurationen in v6.02{#specific-configurations-in-v6-02}

Im folgenden Abschnitt wird die zusätzliche Konfiguration beschrieben, die bei der Migration von Version 6.02 erforderlich ist. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) beschrieben sind.

## Webanwendungen {#web-applications}

Wenn Sie von Version 6.02 migrieren, werden möglicherweise Fehlerprotokolle zu Webanwendungen vom Übersichtstyp angezeigt. Beispiele für Fehlermeldungen:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Diese Webanwendungen verwendeten SQLData und sind aufgrund erhöhter Sicherheit nicht mit v7 kompatibel. Diese Fehler führen zu einem Migrationsfehler.

Wenn Sie diese Webanwendungen nicht verwendet haben, führen Sie das folgende Bereinigungsskript aus und führen Sie das Post-Upgrade erneut aus:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Wenn Sie diese Webanwendungen geändert haben und weiterhin in v7 verwenden möchten, müssen Sie die Option **allowSQLInject** in den verschiedenen Sicherheitszonen aktivieren und die Nachrüstung erneut Beginn ausführen. Weitere Informationen finden Sie im Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) .

## Benutzerfreundlichkeit: Startseite und Navigation {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Wenn Sie weiterhin Übersichtswebanwendungen vom Typ v6.02 verwenden möchten, müssen Sie die Option **allowSQLInject** vor der Aktualisierung in den verschiedenen Sicherheitszonen aktivieren. Refer to [Web applications](#web-applications).

Nach der Migration von Version 6.02 wird die Homepage des Adobe Campaigns v6.02 nicht mehr angezeigt, aber sie ist noch immer verfügbar und mit Adobe Campaign v7 kompatibel.

Um weiterhin die Homepage v6.02 zu verwenden, müssen Sie nach der Migration ein &quot;Kompatibilitätspaket&quot;installieren.

Importieren Sie dazu das Kompatibilitätspaket:

Klicken Sie auf **[!UICONTROL Extras > Erweitert > Paket]** importieren und wählen Sie das Paket **campaignMigration.xml** im **`\nl\datakit\nms\[Your language]\package\optional`**.

Um Zugriff auf die Schnittstellen des Typs v6.02 Webanwendung zuzulassen, muss die **Option für die Serverkonfiguration sessionTokenOnly** in der Datei **serverConf.xml** aktiviert werden:

```
sessionTokenOnly="true"
```

Diese Option ändert die Sicherheitsstufen, um die Kompatibilität der Benutzeroberfläche sicherzustellen.

Nachdem das Paket installiert wurde, wird die Adobe Campaign v7-Startseite durch Ihre alte v6.02-Homepage ersetzt, die mit den allgemeinen Konfigurationen von v7 (blaues Startseite-Banner) versehen ist.

![](assets/dashboards.png)

Alle Links auf dieser Homepage verlinken mit Ausnahme der Listen (**[!UICONTROL Liste]** der Vorgänge, Verfolgung von **[!UICONTROL Versänden in Vorgängen]** usw.) , der auf die v6.02-Übersicht verweist (Webanwendungen).

![](assets/dashboards2.png)

Wenn Sie eine weitere in Version 6.02 konfigurierte Übersicht hinzufügen möchten, müssen Sie diese der Startseite aus dem Dashboard hinzufügen. (**[!UICONTROL Administration > Zugriffsverwaltung > Dashboard]**).

>[!NOTE]
>
>Denken Sie daran, die Verbindung zu trennen und dann die Konsole erneut zu verbinden, um die Änderungen zu registrieren.

## Message Center {#message-center}

Nach der Migration einer Message Center-Kontrollinstanz müssen Sie die Transaktionsnachrichtenvorlagen erneut veröffentlichen, damit sie funktionieren.

In v7 haben sich die Namen der Transaktionsnachrichtenvorlagen auf Ausführungsinstanzen geändert. Sie werden derzeit vom Operatornamen vorangestellt, der der Kontrollinstanz entspricht, auf der sie erstellt wurden, z. B. **control1_template1_rt** (wobei **control1** der Name des Operators ist). Wenn Sie über eine beträchtliche Menge an Vorlagen verfügen, empfehlen wir das Löschen alter Vorlagen auf Kontrollinstanzen.
