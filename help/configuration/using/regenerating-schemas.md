---
product: campaign
title: Regenerieren von Schemata
description: Regenerieren von Schemata
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Regenerieren von Schemata{#regenerating-schemas}

![](../../assets/v7-only.svg)

Wenn Sie ein Schema ändern und die Änderungen speichern, wird automatisch ein erweitertes Schema generiert. Es kann jedoch erforderlich sein, die Schemata manuell zu regenerieren, um Änderungen vorzunehmen. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Schemas aus, die Sie neu generieren möchten.
1. Rechtsklick und Auswahl **[!UICONTROL Aktionen > Ausgewählte Schemata regenerieren...]** .
1. Klicken **[!UICONTROL OK]** , um den Prozess zu bestätigen und zu starten.

Anschließend können Sie die Struktur des erstellten Schemas auf den Registerkarten Vorschau und Dokumentation überprüfen. Weitere Informationen hierzu finden Sie im Abschnitt [Grundsätze](../../configuration/using/data-schemas.md#principles) Abschnitt.

>[!NOTE]
>
>Wenn Sie die Neuerstellung des gesamten Schemas erzwingen müssen, z. B. um bestimmte Abhängigkeitsprobleme in den Rückwärtslinks zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungsserver starten:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Anschließend müssen Sie den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Clientkonsole trennen/wiederherstellen.
