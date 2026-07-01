---
product: campaign
title: Anwenden von Typologieregeln
description: Hier erfahren Sie, wie Sie Typologieregeln anwenden
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
TQID: https://experienceleague.adobe.com/BmGFu9rC1n6on2Nc4N55KYX9EQuvWDUZrFwBGwXHEI0
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
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1063
ht-degree: 100%

---

# Anwenden von Typologieregeln{#applying-rules}

## Anwenden von Typologien auf Sendungen {#applying-a-typology-to-a-delivery}

Um die von Ihnen erstellten Typologieregeln anzuwenden, müssen Sie sie mit einer Typologie verknüpfen und diese in Ihrem Versand referenzieren. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Kampagnentypologie.

   Die Typologien befinden sich im Verzeichnisknoten **[!UICONTROL Administration > Kampagnenverwaltung > Typologieverwaltung]** > **[!UICONTROL Typologien]**.

1. Klicken Sie im Tab **[!UICONTROL Regeln]** auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Regeln aus, die im Rahmen dieser Typologie angewendet werden sollen.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Speichern Sie die Typologie, um sie der Liste der bereits vorhandenen Typologien hinzuzufügen.
1. Öffnen Sie die Sendung, auf die Sie die Regeln anwenden möchten.
1. Öffnen Sie die Versandeigenschaften und rufen Sie den Tab **[!UICONTROL Typologie]** auf.
1. Wählen Sie die Typologie in der Dropdown-Liste aus.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >Die Typologie kann auf Ebene der Versandvorlage festgelegt werden, um sie automatisch auf alle mit der jeweiligen Vorlage erstellten Sendungen anzuwenden.

## Definieren der Anwendungsbedingungen {#defining-application-conditions}

Es besteht die Möglichkeit, das Anwendungsfeld einer Regel Ihren Bedürfnissen entsprechend einzuschränken (mit Ausnahme von Kontrollregeln).

Typologieregeln können demnach so konfiguriert werden, dass sie nur bestimmte Sendungen, in denen sie referenziert sind, oder nur bestimmte Empfänger einer Sendung betreffen.

Um die Anwendungskriterien einer Regel zu bestimmen, klicken Sie auf den Link **[!UICONTROL Anwendungskriterien der Regel bearbeiten]** im Tab **[!UICONTROL Allgemein]**.

Definieren Sie dann Filterbedingungen mit dem Abfrage-Editor. Im folgenden Beispiel betrifft die Kapazitätsregel nur Sendungen, die den Begriff „Angebot“ im Titel enthalten, und solche, die vor dem 1. April 2013 erstellt wurden.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>Für Filterregeln kann der Anwendungskontext der Filterkriterien ausgewählt werden: Sie können versandabhängig oder entwurfsabhängig sein. Weitere Informationen finden Sie unter [Bedingungen für Filterregeln erstellen](filtering-rules.md#conditioning-a-filtering-rule).

## Anpassen der Berechnungsfrequenz {#adjusting-calculation-frequency}

Schlichtungen werden jede Nacht automatisch durch den Datenbankbereinigungs-Workflow neu ausgeführt. Werte können jedoch über diesen Zeitraum hinaus gespeichert werden.

Einige Berechnungen verwenden nämlich Werte, die sich nicht täglich ändern. Es wäre daher überflüssig, die Daten täglich neu zu berechnen und die Datenbank unnötig zu überlasten. Wenn beispielsweise ein Prozess die Marketing-Datenbank wöchentlich mit der Tendenzauswertung und Kaufinformationen der Kundschaft anreichert, müssen die auf diesen Werten basierenden Daten nicht täglich neu berechnet werden.

Geben Sie hierzu im Feld **[!UICONTROL Frequenz]** der Registerkarte **[!UICONTROL Allgemein]** an, wie lange die Berechnungen höchstens beibehalten werden sollen. Der Standardwert **0s** veranlasst, dass die Berechnungen bis zur nächsten Ausführung der täglichen Neuschlichtung gültig bleiben.

Um die Ergebnisse über diese Begrenzung hinaus beizubehalten, geben Sie einen Wert von über 12h im Feld **[!UICONTROL Frequenz]** an: Wenn diese Frist abgelaufen ist, werden alle Regeln erneut angewandt.

Die Option **[!UICONTROL Zur Beginn der Personalisierung Regel erneut anwenden]** ermöglicht es, die Regel systematisch bei der Personalisierungsphase anzuwenden, auch wenn die im Feld **[!UICONTROL Frequenz]** angegebene Frist nicht abgelaufen ist.

## Phase der Regelanwendung auswählen {#selecting-the-rule-application-phase}

Typologieregeln werden in einer spezifischen Reihenfolge je nach Konfiguration zum Zeitpunkt der Zielgruppenbestimmung, Analyse bzw. Personalisierung des Versands angewendet.

### Anwendungsreihenfolge {#execution-order}

Im Standard-Ausführungsmodus werden die Regeln in der folgenden Reihenfolge ausgeführt:

1. Kontrollregeln, wenn sie zu Beginn der Zielgruppenbestimmung angewendet werden
1. Filterregeln:

   * Native Anwendungsregeln für die Adressqualifizierung: definierte Adresse / nicht verifizierte Adresse / Adresse auf der Blockierungsliste / Adresse in Quarantäne / Qualität der Adresse.
   * Vom Benutzer definierte Filterregeln
   * Regeln zur Adress- oder Kennungsdeduplizierung (bei Bedarf angewandt);

1. Druckregeln;
1. Kapazitätsregeln;
1. Kontrollregeln, wenn sie am Ende der Zielgruppenbestimmung angewendet werden
1. Kontrollregeln, wenn sie zu Beginn der Personalisierung angewendet werden Wenn Benutzerregeln (Filter/Druck/Kapazität) abgelaufen sind und neu berechnet werden müssen, werden sie in diesem Schritt angewendet.
1. Kontrollregeln, wenn sie sich auf das Ende der Personalisierung beziehen.

>[!NOTE]
>
>Wenn Sie das Modul &quot;Interaction&quot; nutzen, werden die Eignungsregeln gleichzeitig mit den Filterregeln (für Angebote in Versandentwürfen) oder während der Personalisierungsphase beim Aufruf des Angebotsmoduls angewendet.

Sie können die Anwendungsreihenfolge von Regeln mit demselben Typ mithilfe des entsprechenden Felds auf der Registerkarte **[!UICONTROL Allgemein]** der Regel anpassen. Dies ist insbesondere interessant, wenn in der gleichen Verarbeitungsphase der Nachrichten mehrere Regeln zur Anwendung kommen.****

Beispielsweise wird eine Druckregel mit einer Anwendungsreihenfolge von 20 vor einer Druckregel mit einem Wert von 30 ausgeführt.

### Kontrollregeln {#control-rules}

**[!UICONTROL Kontrollregeln]** können zu verschiedenen Zeitpunkten eines Versands zum Tragen kommen. Wählen Sie den gewünschten Wert in der Dropdown-Liste des Felds **[!UICONTROL Phase]** auf der Registerkarte **[!UICONTROL Allgemein]** der Typologieregel aus.

![](assets/campaign_opt_define_control_phase.png)

Mögliche Werte:

* **[!UICONTROL Zu Beginn der Zielgruppenbestimmung]**

  Die Kontrollregel kann in dieser Phase angewandt werden, um im Falle eines Fehlers die Personalisierungsetappe nicht auszuführen.

* **[!UICONTROL Nach der Zielgruppenbestimmung]**

  Wenn Sie die Größe der Zielgruppe kennen müssen, um die Kontrollregel anzuwenden, wählen Sie diese Phase aus.

  Die Kontrollregel **[!UICONTROL Prüfung der Testversandgröße]** beispielsweise wird zwingend nach der Zielgruppenbestimmungsphase angewandt: Diese Regel verhindert eine Nachrichtenpersonalisierung, wenn die Zielgruppe des Testversands zu groß ist.

* **[!UICONTROL Zu Beginn der Personalisierung]**

  Diese Phase muss ausgewählt werden, wenn die Kontrolle die Validierung der Nachrichtenpersonalisierung betrifft. Die Nachrichtenpersonalisierung erfolgt während der Analysephase.

* **[!UICONTROL Am Ende der Analyse]**

  Wenn für eine Überprüfung die Nachrichtenpersonalisierung abgeschlossen sein muss, wählen Sie diese Phase aus.

## Ergänzende Konfigurationen {#additional-configurations}

### Ausgehenden SMTP-Traffic steuern {#control-outgoing-smtp-traffic}

Optional können Sie mit dem Feld **[!UICONTROL Verwaltung der IP-Adressen-Affinitäten]** Sendungen mit dem Versand-Server (MTA) verknüpfen, der die betreffende Affinität verwaltet. Damit können Sie die Zustellung von E-Mails auf bestimmte Geräte oder IP-Adressen begrenzen.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>Die Affinitätenverwaltung gilt nicht für **[!UICONTROL Filter]**-Typologien.\
>Affinitäten werden direkt in der Konfigurationsdatei der Instanz auf dem Adobe-Campaign-Server bestimmt. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/about-initial-configuration.md).

### Kampagnenoptimierung und dezentrales Marketing {#campaign-optimization-and-distributed-marketing}

In der Registerkarte **[!UICONTROL Dezentrales Marketing]** können Sie die Neuzuordnung von Typologien und/oder Regeln definieren, die bei der Bestellung und/oder Reservierung einer freigegebenen Kampagne angewendet werden. Typologien/Regeln, die für eine Lokalstelle definiert wurden (und mit denen verknüpft sind, die für die Zentralstelle definiert wurden), ersetzen Regeln/Typologien, die mit der Zentralstelle verknüpft sind. Durch die Neuzuordnung können Sie die Regeln der Zentralstelle an die Lokalstellen anpassen, die die Kampagne bestellen.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>Im Zusammenhang mit den Typologien und Typologieregeln wird der Tab **[!UICONTROL Dezentrales Marketing]** angeboten, sofern Ihre Lizenz die Option Distributed Marketing beinhaltet. Überprüfen Sie Ihren Lizenzvertrag.\
>Weitere Informationen zu dezentralem Marketing finden Sie im Abschnitt [Über dezentrales Marketing](../../distributed/using/about-distributed-marketing.md).
