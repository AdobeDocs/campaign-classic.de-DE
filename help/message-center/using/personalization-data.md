---
title: Personalisierungsdaten
seo-title: Personalisierungsdaten
description: Personalisierungsdaten
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '155'
ht-degree: 100%

---


# Personalisierungsdaten{#personalization-data}

Mithilfe der im Testadressen-Tab der Nachrichtenvorlage angegebenen Daten kann die Personalisierung der Transaktionsnachrichten getestet werden, indem Sie eine Vorschau erzeugen oder einen Testversand durchführen. Mit Installation des Moduls **Zustellbarkeits-Monitoring** ermöglichen diese Daten zudem die Überprüfung der Nachrichtendarstellung bei unterschiedlichen E-Mail-Anbietern (**Inbox Rendering**, siehe hierzu [diesen Abschnitt](../../delivery/using/about-deliverability.md)).

Diese Daten dienen nur dazu, die Nachrichten vor dem eigentlichen Versand zu testen und entsprechen nicht den tatsächlich von Message Center verarbeiteten Daten. Ihre XML-Struktur muss jedoch identisch mit der des in der Ausführungsinstanz gespeicherten Ereignisses sein, wie im folgenden Beispiel:

![](assets/messagecenter_create_custo_006.png)

Diese Informationen erlauben die Personalisierung des Nachrichteninhalts mithilfe von Personalisierungsfeldern (siehe hierzu den Abschnitt [Nachrichteninhalt erstellens](../../message-center/using/creating-message-content.md)).

1. Klicken Sie in der Nachrichtenvorlage auf den Tab **[!UICONTROL Testadressen]**.
1. Geben Sie im Inhalt des Ereignisses die Testinformationen im XML-Format ein.

   ![](assets/messagecenter_create_custo_001.png)

