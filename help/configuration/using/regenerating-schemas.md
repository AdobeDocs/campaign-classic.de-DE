---
product: campaign
title: Regenerieren von Schemata
description: Erfahren Sie, wie Sie Campaign-Schemata neu generieren
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
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
