---
solution: Campaign Classic
product: campaign
title: Regenerieren von Schemata
description: Regenerieren von Schemata
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 6%

---


# Regenerieren von Schemata{#regenerating-schemas}

Wenn Sie ein Schema ändern und die Änderungen speichern, wird automatisch ein erweitertes Schema generiert. Möglicherweise müssen Sie Schema jedoch manuell neu generieren, um Änderungen anzuwenden. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die zu regenerierenden Schema aus.
1. Klicken Sie mit der rechten Maustaste und wählen Sie &quot; **[!UICONTROL Aktionen&quot;> &quot;Ausgewählte Schema neu generieren&quot;...]** .
1. Klicken Sie auf **[!UICONTROL OK]** , um den Prozess zu bestätigen und zu starten.

Anschließend können Sie die Struktur des generierten Schemas auf den Registerkarten &quot;Vorschau&quot;und &quot;Dokumentation&quot;überprüfen. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Wenn Sie die Wiederherstellung des gesamten Schemas erzwingen müssen, um beispielsweise bestimmte Abhängigkeitsprobleme in den Reverse-Links zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungsserver starten:
>
>**nlserver config -postupgrade -instance:` &lt;instance_name>&#39; -force**
>
>Anschließend müssen Sie den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Client-Konsole trennen/wiederherstellen.
