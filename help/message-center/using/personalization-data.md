---
solution: Campaign Classic
product: campaign
title: Personalisierungsdaten
description: Personalisierungsdaten
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---


# Personalisierungsdaten{#personalization-data}

Mithilfe der im Testadressen-Tab der Nachrichtenvorlage angegebenen Daten kann die Personalisierung der Transaktionsnachrichten getestet werden, indem Sie eine Vorschau erzeugen oder einen Testversand durchführen. Mit Installation des Moduls **Zustellbarkeits-Monitoring** ermöglichen diese Daten zudem die Überprüfung der Nachrichtendarstellung bei unterschiedlichen E-Mail-Anbietern (**Inbox Rendering**, siehe hierzu [diesen Abschnitt](../../delivery/using/inbox-rendering.md)).

Diese Daten dienen nur dazu, die Nachrichten vor dem eigentlichen Versand zu testen und entsprechen nicht den tatsächlich von Message Center verarbeiteten Daten. Ihre XML-Struktur muss jedoch identisch mit der des in der Ausführungsinstanz gespeicherten Ereignisses sein, wie im folgenden Beispiel:

![](assets/messagecenter_create_custo_006.png)

Diese Informationen erlauben die Personalisierung des Nachrichteninhalts mithilfe von Personalisierungsfeldern (siehe hierzu den Abschnitt [Nachrichteninhalt erstellens](../../message-center/using/creating-message-content.md)).

1. Klicken Sie in der Nachrichtenvorlage auf den Tab **[!UICONTROL Testadressen]**.
1. Geben Sie im Inhalt des Ereignisses die Testinformationen im XML-Format ein.

   ![](assets/messagecenter_create_custo_001.png)
