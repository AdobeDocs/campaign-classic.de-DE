---
solution: Campaign Classic
product: campaign
title: Kohärenzregeln
description: Kohärenzregeln
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 100%

---


# Kohärenzregeln{#consistency-rules}

## Über Kohärenzregeln {#about-consistency-rules}

Adobe Campaign ermöglicht die Sicherstellung der Kohärenz Ihrer Marketingkommunikation mithilfe einer Reihe von in den Kampagnentypologien enthaltenen Regeln. Diese dienen dazu, die an die Empfänger übermittelten Sendungen in Bezug auf ihr Volumen, ihre Art, ihre Relevanz etc. zu kontrollieren.

Mithilfe von **Kapazitätsregeln** kann etwa verhindert werden, dass die Plattform, die den Versand verarbeitet, überlastet wird. Zum Beispiel dürfen Sonderangebote mit einem Download-Link nicht an eine zu große Population gesendet werden, um den Server nicht zu überladen; eine Telefonkampagne darf die Verarbeitungskapazität der Telefonzentrale nicht überschreiten usw. Weitere Informationen hierzu finden Sie unter [Kontrollieren der Kapazitätsauslastung](#controlling-capacity).

## Kontrollieren der Kapazitätsauslastung {#controlling-capacity}

Stellen Sie vor dem Versand von Nachrichten sicher, dass Ihre physische Infrastruktur über ausreichende Kapazitäten verfügt, um sowohl ausgehende als auch eingehende Nachrichten (z. B. Antworten, Bounces, Anrufe im Callcenter etc.) verarbeiten zu können.

Erstellen Sie hierfür Typologieregeln vom Typ **[!UICONTROL Kapazität]**.

Im folgenden Beispiel wird eine Typologieregel für eine telefonische Treuekampagne erstellt. Die Regel soll die Anzahl der Nachrichten auf 20 pro Tag begrenzen, entsprechend der Verarbeitungskapazität eines Callcenters. Nachdem die Regel auf zwei Sendungen angewendet wurde, kann die Auslastung über die Logs abgelesen werden.

Gehen Sie wie folgt vor, um eine neue Kapazitätsregel zu erstellen:

1. Klicken Sie im Verzeichnisknoten **[!UICONTROL Administration > Kampagnenverwaltung > Typologieverwaltung > Typologieregeln]** auf **[!UICONTROL Neu]**.
1. Wählen Sie eine Regel vom Typ **[!UICONTROL Kapazität]** aus.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Erstellen Sie im Tab **[!UICONTROL Kapazität]** die Verfügbarkeitszeilen. In unserem Beispiel wären dies Zeiträume, in denen Anrufe getätigt werden können. Wählen Sie einen Zeitraum von 24 Stunden aus und geben Sie als Ursprungsmenge 150 ein, was bedeutet, dass das Callcenter 150 Anrufe pro Tag verarbeiten kann.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Die Verfügbarkeitszeilen dienen nur als Richtwerte. Sie können bei Bedarf jedoch auch festlegen, dass bei Erreichen der Kapazitätsbegrenzung Nachrichten ausgeschlossen werden. Näheres hierzu finden Sie in [diesem Abschnitt](#exclude-messages-when-capacity-limit-reached).

1. Weisen Sie diese Regel einer Typologie zu und referenzieren Sie die Typologie in Ihrer Sendung, damit die Kapazitätsregel von dieser angewendet wird. Näheres hierzu finden Sie in [diesem Abschnitt](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Über die Tabs **[!UICONTROL Entnahmen]** und **[!UICONTROL Kapazität]** für diese Regel können Sie die Auslastung der Kapazitäten überwachen.

   Wenn eine Regel in einem Versand verwendet wird, zeigen die Spalten **[!UICONTROL Entnommen]** und **[!UICONTROL Verbleibend]** die verbrauchte Menge an, wie im unten stehenden Beispiel:

   ![](assets/campaign_opt_create_capacity_03.png)

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#monitoring-consumption).

## Maximale Auslastung festlegen {#defining-the-maximum-load}

Um die maximale Auslastung zu definieren, müssen Sie Verfügbarkeitszeilen festlegen. Dazu stehen zwei Optionen zur Verfügung: Sie können manuell eine oder mehrere Verfügbarkeitszeilen erstellen (siehe [Verfügbarkeitszeilen einzeln hinzufügen](#adding-availability-lines-one-by-one)) oder Verfügbarkeitsbereiche erstellen. Die Häufigkeit dieser Zeiträume kann automatisiert werden (siehe [Mehrere Verfügbarkeitszeilen hinzufügen](#add-a-set-of-availability-lines)).

### Verfügbarkeitszeilen einzeln hinzufügen {#adding-availability-lines-one-by-one}

Um eine einzelne Verfügbarkeitszeile zu erstellen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Option **[!UICONTROL Eine Verfügbarkeitszeile hinzufügen]** aus. Geben Sie den Verfügbarkeitszeitraum und die verfügbare Menge an.

![](assets/campaign_opt_create_capacity_02.png)

Sie können die Ihrer Verarbeitungskapazität entsprechende Anzahl an Zeilen hinzufügen.

### Mehrere Verfügbarkeitszeilen hinzufügen {#add-a-set-of-availability-lines}

Um Verfügbarkeitszeiträume in einem gegebenen Zeitraum festzulegen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Option **[!UICONTROL Mehrere Verfügbarkeitszeilen hinzufügen]**. Geben Sie die Dauer jedes Zeitraums und die Anzahl der zu erstellenden Zeiträume an.

Um die Zeitraumerstellung zu automatisieren, klicken Sie auf die Schaltfläche **[!UICONTROL Ändern]** und legen Sie die Planung der Zeiträume fest.

![](assets/campaign_opt_create_capacity_07.png)

Zur Erstellung von Verfügbarkeitszeiträumen an Werktagen zwischen 9 und 17 Uhr mit einer Kapazität von 10 Anrufen pro Stunde, folgen Sie den nachstehenden Schritten:

1. Wählen Sie den Häufigkeitstyp und die Gültigkeitszeiträume aus:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Geben Sie die Gültigkeitsdaten an:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Überprüfen Sie die Konfiguration, bevor Sie sie beenden:

   ![](assets/campaign_opt_create_capacity_10.png)

Der Workflow **[!UICONTROL Planungen]** erstellt automatisch alle entsprechenden Zeilen.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Es wird empfohlen, Verfügbarkeitszeilen über einen Dateiimport zu erstellen. Im Kapazität-Tab können die Verfügbarkeitszeilen anschließend eingesehen und überprüft werden.

## Nachrichten bei Erreichen der Kapazitätsbegrenzung ausschließen {#exclude-messages-when-capacity-limit-reached}

Die Verfügbarkeitszeilen dienen nur als Richtwerte. Um überschüssige Nachrichten auszuschließen, kreuzen Sie die Option **[!UICONTROL Die die Kapazität übersteigenden Nachrichten aus der Zielgruppe ausschließen]** an. Die Kapazität kann so nicht überschritten werden. Für die gleiche Population wie im vorhergehenden Beispiel können Verbrauch und verbleibende Kapazität die Ursprungsmenge nicht übersteigen.

![](assets/campaign_opt_create_capacity_04.png)

Die Anzahl der zu verarbeitenden Nachrichten ist gleichmäßig über den gesamten festgelegten Zeitraum verteilt. Dies ist insbesondere für Callcenter von Bedeutung, da die Anzahl der Anrufe, die diese pro Tag verarbeiten können, begrenzt ist. Im Fall von E-Mail-Sendungen können Sie mit der Option **[!UICONTROL Sofortige Versandkapazität nicht begrenzen]** diesen Zeitraum ignorieren und gleichzeitig Ihre E-Mails versenden.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>Bei Überlastung werden die beizubehaltenden Nachrichten nach einer in den Versandeigenschaften bestimmten Formel ausgewählt.

![](assets/campaign_opt_create_capacity_06.png)

## Verbrauch kontrollieren {#monitoring-consumption}

Kapazitätsregeln dienen standardmäßig lediglich Informationszwecken. Wählen Sie die Option **[!UICONTROL Die die Kapazität übersteigenden Nachrichten aus der Zielgruppe ausschließen]**, damit die festgelegte Menge nicht überschritten werden kann. Überschüssige Nachrichten werden dann automatisch von Sendungen ausgeschlossen, die diese Typologieregel anwenden.

Im Tab **[!UICONTROL Kapazität]** der Typologieregel haben Sie die Möglichkeit, in der **[!UICONTROL Verbraucht]**-Spalte die Inanspruchnahme der vorhandenen Ressourcen zu verfolgen.

![](assets/campaign_opt_create_capacity_04.png)

Klicken Sie zur Ansicht der Verbrauchszeilen auf den Tab **[!UICONTROL Verbrauch]** der Regel.
