---
product: campaign
title: Regenerieren von Schemata
description: Regenerieren von Schemata
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: e3e2ac09de6a9e846e9f9262d522b9395a725648
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Regenerieren von Schemata{#regenerating-schemas}

Wenn Sie ein Schema ändern und die Änderungen speichern, wird automatisch ein erweitertes Schema generiert. Es kann jedoch erforderlich sein, die Schemata manuell zu regenerieren, um Änderungen vorzunehmen. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Schemas aus, die Sie neu generieren möchten.
1. Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Aktionen > Ausgewählte Schemas regenerieren...]** .
1. Klicken Sie auf **[!UICONTROL OK]** , um den Prozess zu bestätigen und zu starten.

Anschließend können Sie die Struktur des erstellten Schemas in den Registerkarten Vorschau und Dokumentation überprüfen. Weitere Informationen hierzu finden Sie im Abschnitt [Prinzipien](../../configuration/using/data-schemas.md#principles) .

>[!NOTE]
>
>Wenn Sie die Neuerstellung des gesamten Schemas erzwingen müssen, z. B. um bestimmte Abhängigkeitsprobleme in den Rückwärtslinks zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungsserver starten:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Anschließend müssen Sie den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Clientkonsole trennen/wiederherstellen.
