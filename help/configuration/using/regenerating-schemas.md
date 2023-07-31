---
product: campaign
title: Regenerieren von Schemata
description: Erfahren Sie, wie Sie Campaign-Schemata neu generieren
feature: Custom Resources
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 2%

---

# Regenerieren von Schemata{#regenerating-schemas}

Wenn Sie ein Schema ändern und die Änderungen speichern, wird automatisch ein erweitertes Schema generiert. Es kann jedoch erforderlich sein, die Schemata manuell zu regenerieren, um Änderungen vorzunehmen. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Schemas aus, die Sie neu generieren möchten.
1. Rechtsklick und Auswahl **[!UICONTROL Aktionen > Ausgewählte Schemata regenerieren...]** .
1. Klicks **[!UICONTROL OK]** , um den Prozess zu bestätigen und zu starten.

Anschließend können Sie die Struktur des erstellten Schemas auf den Registerkarten Vorschau und Dokumentation überprüfen. Weitere Informationen hierzu finden Sie im Abschnitt [Grundsätze](../../configuration/using/data-schemas.md#principles) Abschnitt.

>[!NOTE]
>
>Wenn Sie die Neuerstellung des gesamten Schemas erzwingen müssen, z. B. um bestimmte Abhängigkeitsprobleme in den Rückwärtslinks zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungsserver starten:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Anschließend müssen Sie den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Clientkonsole trennen/wiederherstellen.
