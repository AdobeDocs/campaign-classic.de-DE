---
product: campaign
title: Kohärenzregeln
description: Erfahren Sie, wie in Adobe Campaign mit Kohärenzregeln gearbeitet wird.
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
TQID: https://experienceleague.adobe.com/rkCdxvBXQAvuM0hpIt2nQ35lxDBK2XpS-0tHN7NzQVI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 830
ht-degree: 69%

---

# Kohärenzregeln{#consistency-rules}

## Über Kohärenzregeln {#about-consistency-rules}

Adobe Campaign garantiert konsistente Kommunikation dank einer Reihe von Regeln, die in Kampagnentypologien enthalten sind. Sie dienen der Kontrolle der an Empfängerinnen und Empfänger gesendeten Sendungen, z. B. Menge, Art, Relevanz usw.

**Kapazitätsregeln** können beispielsweise verhindern, dass die vom Nachrichtenversand betroffene Plattform überlastet wird. Beispielsweise dürfen Sonderangebote mit einem Download-Link nicht an zu viele Personen gleichzeitig gesendet werden, um den Server nicht zu überlasten; Telefonkampagnen dürfen die Verarbeitungskapazität von Callcentern usw. nicht überschreiten. Weitere Informationen hierzu finden Sie unter [Kontrollieren der Kapazität](#controlling-capacity).

## Kontrollieren der Kapazität {#controlling-capacity}

Stellen Sie vor dem Versand von Nachrichten sicher, dass Ihre physische Infrastruktur über ausreichende Kapazitäten verfügt, um sowohl ausgehende als auch eingehende Nachrichten (z. B. Antworten, Bounces, Anrufe im Callcenter etc.) verarbeiten zu können.

Erstellen Sie hierfür Typologieregeln vom Typ **[!UICONTROL Kapazität]**.

Im folgenden Beispiel erstellen wir eine Typologieregel für eine Telefonloyalitätskampagne. Wir beschränken die Anzahl der Nachrichten auf 20 pro Tag, was der täglichen Verarbeitungskapazität eines Callcenters entspricht. Nachdem die Regel auf zwei Sendungen angewendet wurde, können wir den Verbrauch über Logs überwachen.

Gehen Sie wie folgt vor, um eine neue Kapazitätsregel zu erstellen:

1. Klicken Sie im Verzeichnisknoten **[!UICONTROL Administration > Kampagnenverwaltung > Typologieverwaltung > Typologieregeln]** auf **[!UICONTROL Neu]**.
1. Wählen Sie eine Regel vom Typ **[!UICONTROL Kapazität]** aus.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Erstellen Sie auf **[!UICONTROL Registerkarte]** Kapazität“ die Verfügbarkeitszeilen: In unserem Beispiel handelt es sich um Zeiträume, in denen Anrufe getätigt werden können. Wählen Sie einen Zeitraum von 24 Stunden aus und geben Sie 150 in die Anfangsmenge ein, was bedeutet, dass das Callcenter 150 Anrufe pro Tag verarbeiten kann.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Die Verfügbarkeitszeilen dienen nur als Richtwerte. Sie können bei Bedarf jedoch auch festlegen, dass bei Erreichen der Kapazitätsbegrenzung Nachrichten ausgeschlossen werden. Näheres hierzu finden Sie in [diesem Abschnitt](#exclude-messages-when-capacity-limit-reached).

1. Weisen Sie diese Regel einer Typologie zu und referenzieren Sie die Typologie in Ihrer Sendung, damit die Kapazitätsregel von dieser angewendet wird. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](applying-rules.md#applying-a-typology-to-a-delivery).
1. Über die Tabs **[!UICONTROL Entnahmen]** und **[!UICONTROL Kapazität]** für diese Regel können Sie die Auslastung der Kapazitäten überwachen.

   Wenn eine Regel in einem Versand verwendet wird, zeigen die Spalten **[!UICONTROL Entnommen]** und **[!UICONTROL Verbleibend]** die verbrauchte Menge an, wie im unten stehenden Beispiel:

   ![](assets/campaign_opt_create_capacity_03.png)

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#monitoring-consumption).

## Festlegen der maximalen Auslastung {#defining-the-maximum-load}

Um die maximale Auslastung zu definieren, müssen Sie Verfügbarkeitszeilen festlegen. Dazu stehen zwei Optionen zur Verfügung: Sie können manuell eine oder mehrere Verfügbarkeitszeilen erstellen (siehe [Verfügbarkeitszeilen einzeln hinzufügen](#adding-availability-lines-one-by-one)) oder Verfügbarkeitsbereiche erstellen. Die Häufigkeit dieser Zeiträume kann automatisiert werden (siehe [Mehrere Verfügbarkeitszeilen hinzufügen](#add-a-set-of-availability-lines)).

### Verfügbarkeitszeilen einzeln hinzufügen {#adding-availability-lines-one-by-one}

Um eine Verfügbarkeitszeile zu erstellen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie **[!UICONTROL Verfügbarkeitszeile hinzufügen]** aus. Geben Sie den Verfügbarkeitszeitraum und die verfügbare Last ein.

![](assets/campaign_opt_create_capacity_02.png)

Sie können die Ihrer Verarbeitungskapazität entsprechende Anzahl an Zeilen hinzufügen.

### Mehrere Verfügbarkeitszeilen hinzufügen {#add-a-set-of-availability-lines}

Um Verfügbarkeitszeiträume für einen bestimmten Zeitraum festzulegen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Option **[!UICONTROL Mehrere Verfügbarkeitszeilen hinzufügen]** aus. Geben Sie eine Dauer für jeden Zeitraum und die Anzahl der zu erstellenden Zeiträume an.

Um die Zeitraumerstellung zu automatisieren, klicken Sie auf die Schaltfläche **[!UICONTROL Ändern]** und legen Sie die Planung der Zeiträume fest.

![](assets/campaign_opt_create_capacity_07.png)

Definieren wir beispielsweise einen Zeitplan, um Verfügbarkeitszeiträume für alle Arbeitstage mit einer Rate von 10 Aufrufen pro Stunde zwischen 9 Uhr und 17 Uhr zu erstellen. Gehen Sie hierzu wie folgt vor:

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
>Wir empfehlen, Verfügbarkeitszeilen über Dateiimporte zu erstellen. Auf dieser Registerkarte können Sie Verbrauchszeilen anzeigen und überprüfen.

## Nachrichten bei Erreichen des Kapazitätslimits ausschließen {#exclude-messages-when-capacity-limit-reached}

Die Verfügbarkeitszeilen dienen nur als Richtwerte. Um überschüssige Nachrichten auszuschließen, aktivieren Sie die Option **[!UICONTROL Die die Kapazität übersteigenden Nachrichten aus der Zielgruppe ausschließen]**. Die Kapazität kann so nicht überschritten werden. Für dieselbe Population wie im vorherigen Beispiel dürfen Verbrauch und verbleibende Kapazität die ursprüngliche Menge nicht übersteigen:

![](assets/campaign_opt_create_capacity_04.png)

Die maximale Anzahl von Nachrichten, die verarbeitet werden können, ist gleichmäßig über den definierten Verfügbarkeitsbereich verteilt. Dies ist besonders für Callcenter von Bedeutung, da die Anzahl der Anrufe pro Tag begrenzt ist. Im Fall von E-Mail-Sendungen können Sie mit der Option **[!UICONTROL Sofortige Versandkapazität nicht begrenzen]** diesen Verfügbarkeitsbereich ignorieren und gleichzeitig Ihre E-Mails senden.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>Bei Überlastung werden die beizubehaltenden Nachrichten nach einer in den Versandeigenschaften bestimmten Formel ausgewählt.

![](assets/campaign_opt_create_capacity_06.png)

## Überwachen des Verbrauchs {#monitoring-consumption}

Kapazitätsregeln dienen standardmäßig lediglich Informationszwecken. Wählen Sie die Option **[!UICONTROL Die die Kapazität übersteigenden Nachrichten aus der Zielgruppe ausschließen]**, damit die festgelegte Menge nicht überschritten werden kann. Überschüssige Nachrichten werden dann automatisch von Sendungen ausgeschlossen, die diese Typologieregel anwenden.

Im Tab **[!UICONTROL Kapazität]** der Typologieregel haben Sie die Möglichkeit, in der **[!UICONTROL Verbraucht]**-Spalte die Inanspruchnahme der vorhandenen Ressourcen zu verfolgen.

![](assets/campaign_opt_create_capacity_04.png)

Klicken Sie zur Ansicht der Verbrauchszeilen auf den Tab **[!UICONTROL Verbrauch]** der Regel.
