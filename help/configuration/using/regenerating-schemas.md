---
product: campaign
title: Regenerieren von Schemata
description: Erfahren Sie, wie Sie Campaign-Schemata neu generieren
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 2%

---

# Regenerieren von Schemata{#regenerating-schemas}

Wenn Sie ein Schema ändern und die Änderungen speichern, wird das erweiterte Schema automatisch generiert. Möglicherweise müssen Sie die Schemata jedoch manuell neu generieren, um Änderungen vorzunehmen. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Schemas aus, die Sie neu generieren möchten.
1. Klicken Sie mit der rechten Maustaste und wählen **[!UICONTROL Aktionen > Ausgewählte Schemata wiederherstellen…]** .
1. Klicken Sie **[!UICONTROL OK]**, um den Vorgang zu bestätigen und zu starten.

Sie können dann die Struktur des generierten Schemas auf den Registerkarten Vorschau und Dokumentation überprüfen. Weiterführende Informationen hierzu finden Sie im Abschnitt [Grundlagen](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Wenn Sie eine erneute Generierung aller Schemata erzwingen müssen, um z. B. bestimmte Abhängigkeitsprobleme in den Umkehrlinks zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungs-Server aus starten:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Sie müssen dann den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Client-Konsole trennen/wiederherstellen.
