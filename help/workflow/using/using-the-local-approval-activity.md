---
title: Lokale Validierung verwenden
seo-title: Lokale Validierung verwenden
description: Lokale Validierung verwenden
seo-description: null
page-status-flag: never-activated
uuid: 6003aaed-543d-4e6b-b1f2-ad4e9757bff3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: c143d8c3-c3ce-470c-8812-4b19cdb8afbf
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1432'
ht-degree: 100%

---


# Lokale Validierung verwenden{#using-the-local-approval-activity}

Im Rahmen eines Zielgruppen-Workflows ermöglicht die Aktivität **[!UICONTROL Lokale Validierung]** die Formalisierung eines Validierungsprozesses, der die Überprüfung der ausgewählten Empfänger vor Absendung der Kampagne sicherstellt.

>[!CAUTION]
>
>Zur Verwendung dieser Funktion benötigen Sie das Modul Distributed Marketing (Campaign-Option). Bitte prüfen Sie Ihren Lizenzvertrag.

Der Workflow für dieses Anwendungsbeispiel stellt sich wie folgt dar:

![](assets/local_validation_workflow.png)

Der lokale Validierungsprozess gliedert sich in folgende Schritte:

1. Die aus der Zielgruppenbestimmung resultierende Population wird mithilfe einer **[!UICONTROL Aufspaltung]** mit einer Datenverteilungsvorlage begrenzt.

   ![](assets/local_validation_intro_1.png)

1. Die **[!UICONTROL Lokale Validierung]** sendet im Anschluss daran eine E-Mail-Benachrichtigung an alle lokalen Validierungsverantwortlichen. Die Aktivität bleibt im Wartezustand, bis alle Verantwortlichen die ihnen zugewiesenen Empfänger validiert haben.

   ![](assets/local_validation_intro_4.png)

1. Mit Ablauf der Validierungsfrist nimmt der Workflow die Ausführung wieder auf. Im vorliegenden Beispiel wird die **[!UICONTROL Versandaktivität]** aktiviert und der Versand an die validierten Empfänger gestartet.

   >[!NOTE]
   >
   >Die bis zum Ablauf der Validierungsfrist nicht validierten Empfänger werden in der Versand-Zielgruppe nicht berücksichtigt.

   ![](assets/local_validation_intro_6.png)

1. Einige Tage später sendet die zweite **[!UICONTROL Lokale Validierung]** allen lokalen Verantwortlichen eine E-Mail-Benachrichtigung, die sie über die Empfängerreaktionen (Klicks, Öffnungen usw.) informiert.

   ![](assets/local_validation_intro_5.png)

## 1. Schritt: Erstellung der Datenverteilungsvorlage {#step-1--creating-the-data-distribution-template-}

Eine Verteilungsvorlage ermöglicht die Begrenzung der aus der Zielgruppenbestimmung resultierenden Population mithilfe einer Datengruppierung. Jedem Gruppierungswert kann dann ein lokaler Verantwortlicher zugewiesen werden. Im vorliegenden Beispiel wird die **[!UICONTROL E-Mail-Domain]** als Gruppierungswert verwendet und jedem lokalen Verantwortlichen eine Domain zugewiesen.

Weitere Informationen zum Erstellen einer Datenverteilungsvorlage finden Sie unter [Anzahl an Datensätzen in Teilmengen durch Datenverteilung begrenzen](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution).

1. Gehen Sie in den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Datenverteilung]** und klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/local_validation_data_distribution_1.png)

1. Gehen Sie in den **[!UICONTROL Allgemein]**-Tab.

   ![](assets/local_validation_data_distribution_2.png)

1. Vergeben Sie einen **[!UICONTROL Titel]** und füllen Sie die Felder zum **[!UICONTROL Verteilungskontext]** aus. Im vorliegenden Beispiel wurden die **[!UICONTROL Empfänger]** als Zielgruppendimension und das Feld **[!UICONTROL E-Mail-Domain]** als Verteilungsfeld gewählt. Die Empfängerliste wird somit nach Domain verteilt.
1. Wählen Sie im Feld **[!UICONTROL Verteilungstyp]** die Art aus, in der die Zielgruppenbegrenzung im Tab **[!UICONTROL Verteilung]** ausgedrückt werden soll. Im vorliegenden Beispiel wurde **[!UICONTROL Prozent]** ausgewählt.
1. Geben Sie im Feld **[!UICONTROL Validierungsspeicherung]** das dem verwendeten Zielgruppenschema entsprechende Speicherschema an. Hier handelt es sich um das Standard-Speicherschema: **[!UICONTROL Lokale Validierung der Empfänger]**.
1. Klicken Sie dann auf den Link **[!UICONTROL Erweiterte Parameter...]**

   ![](assets/local_validation_data_distribution_3.png)

1. Damit alle Empfänger in der Liste der zu validierenden Empfänger erscheinen, lassen Sie die Option **[!UICONTROL Nachrichten validieren]** angekreuzt.
1. Behalten Sie im Feld **[!UICONTROL Versandtitel]** den Standardausdruck bei (Compute String des Versands). Auf diese Weise wird in der Versandreaktionen-Benachrichtigung der ursprüngliche Versandtitel verwendet.
1. Geben Sie im **[!UICONTROL Gruppierungsfeld]** das **[!UICONTROL Geschlecht]** als Kriterium für die Gruppierung der Empfänger in den Benachrichtigungen an.
1. Wählen Sie im Bereich **[!UICONTROL Nachrichten bearbeiten]** die Webschnittstelle **[!UICONTROL Empfängerbearbeitung]** aus und fügen Sie den Parameter **[!UICONTROL recipientId]** hinzu. Auf diese Weise werden die Empfänger in den Benachrichtigungen anklickbar und leiten auf die entsprechende Webanwendung weiter. Der zusätzliche Parameter der URL ist **[!UICONTROL recipientId]**.
1. Schließen Sie die erweiterten Parameter und gehen Sie in den Tab **[!UICONTROL Verteilung]**. Füllen Sie für jede Domain die folgenden Felder aus:

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Wert]**: Geben Sie den Domainnamen ein.
   * **[!UICONTROL Prozent/Feste Größe]**: Geben Sie für jede Domain die Begrenzung ein. Im vorliegenden Beispiel wurde der Versand auf 10 % jeder Domain begrenzt.
   * **[!UICONTROL Titel]**: Vergeben Sie für jede Domain einen Titel, der in den Validierungs- und Versandreaktionen-Benachrichtigungen angezeigt wird.
   * **[!UICONTROL Gruppe oder Benutzer]**: Geben Sie den Benutzer oder die Benutzergruppe an, dem die Domain zugewiesen wurde.

      >[!CAUTION]
      >
      >Stellen Sie sicher, dass die Benutzer über die nötigen Berechtigungen verfügen.

## 2. Schritt: Erstellung des Zielgruppen-Workflows {#step-2--creating-the-targeting-workflow}

Der Workflow für dieses Anwendungsbeispiel stellt sich wie folgt dar:

![](assets/local_validation_workflow.png)

Folgende Aktivitäten wurden verwendet:

* **[!UICONTROL Abfragen]**,
* **[!UICONTROL Schnittmenge]**,
* **[!UICONTROL Aufspaltung]**,
* **[!UICONTROL Lokale Validierung]**,
* **[!UICONTROL Versand]**,
* **[!UICONTROL Warten]**,
* **[!UICONTROL Lokale Validierung]**,
* **[!UICONTROL Ende]**.

### Abfragen, Schnittmenge und Aufspaltung {#queries--intersection-and-split}

Die Zielgruppenbestimmung geschieht mithilfe zweier Abfragen und einer Schnittmenge. Die **[!UICONTROL Aufspaltung]** schränkt die resultierende Population über eine Datenverteilungsvorlage ein.

Weitere Informationen zum Konfigurieren einer Aufspaltungsaktivität finden Sie unter [Aufspaltung](../../workflow/using/split.md). Die Erstellung einer Datenverteilungsvorlage wird unter [Anzahl an Datensätzen in Teilmengen durch Datenverteilung begrenzen](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution) ausführlich beschrieben.

Wenn Sie die aus der Abfrage resultierende Population nicht einschränken möchten, ist die Verwendung der **[!UICONTROL Abfragen]**, **[!UICONTROL Schnittmenge]** und **[!UICONTROL Aufspaltung]** nicht erforderlich. Konfigurieren Sie in diesem Fall die Verteilungsvorlage in der ersten Aktivität vom Typ **[!UICONTROL Lokale Validierung]**.

1. Öffnen Sie die Aufspaltung und kreuzen Sie im Bereich **[!UICONTROL Begrenzung der Anzahl von Datensätzen]** die Option **[!UICONTROL Anzahl von Datensätzen begrenzen]** an. Klicken Sie anschließend auf den Link **[!UICONTROL Bearbeiten...]**.

   ![](assets/local_validation_split_1.png)

1. Aktivieren Sie die Option **[!UICONTROL Die ersten, aus einer Sortierung hervorgehenden Elemente beibehalten]** und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/local_validation_split_1bis.png)

1. Fügen Sie im Bereich **[!UICONTROL Sortierungsspalten]** das Feld hinzu, nach dem die Liste sortiert werden soll. Im vorliegenden Beispiel ist dies **[!UICONTROL E-Mail]**. Klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![](assets/local_validation_split_2.png)

1. Wählen Sie die Option **[!UICONTROL Durch Datenverteilung]**, wählen Sie die zuvor erstellte Verteilungsvorlage aus (siehe [Schritt 1: Erstellung der Datenverteilungsvorlage](#step-1--creating-the-data-distribution-template-)) und klicken Sie auf **[!UICONTROL Beenden]**.

   ![](assets/local_validation_split_3.png)

In der Verteilungsvorlage wurde die Population auf 10 % je Gruppierungswert begrenzt. Dies spiegelt sich im Workflow wieder (340 Empfänger in der eingehenden Transition, 34 in der ausgehenden).

![](assets/local_validation_intro_1.png)

### Validierungsbenachrichtigung {#approval-notification}

Die **[!UICONTROL Lokale Validierung]** erlaubt den Versand einer Benachrichtigung an jeden lokalen Verantwortlichen.

Weiterführende Informationen zur Konfiguration der **[!UICONTROL lokalen Validierung]** finden Sie im Abschnitt [Lokale Validierung](../../workflow/using/local-approval.md).

![](assets/local_validation_workflow_2.png)

Folgende Angaben sind erforderlich:

1. Im Bereich **[!UICONTROL Auszuführende Aktion]**: Wählen Sie die Option **[!UICONTROL Benachrichtigung zur Zielgruppenvalidierung]** aus.
1. Im Bereich **[!UICONTROL Verteilungskontext]**: Wählen Sie die Option **[!UICONTROL Wird durch die Transition angegeben]** aus.

   Wenn die resultierende Population nicht begrenzt werden soll, ist die Option **[!UICONTROL Explizit]** anzukreuzen und im Feld **[!UICONTROL Datenverteilung]** die zuvor erstellte Verteilungsvorlage anzugeben.

1. Im Bereich **[!UICONTROL Validierungsverwaltung]**: Wählen Sie die Versandvorlage aus und geben Sie den Betreff für die Benachrichtigungs-E-Mail an. Im vorliegenden Beispiel wurde die Standardvorlage beibehalten, d. h. **[!UICONTROL Benachrichtigung bezüglich der Zielgruppenvalidierung]**.
1. Definieren Sie außerdem den **[!UICONTROL Validierungstyp]**. Im vorliegenden Beispiel wurde die Standardoption beibehalten, d. h. die Validierung muss spätestens 3 Tage nach dem Unterbreitungsdatum erfolgen, andernfalls werden die nicht validierten Empfänger beim Versand nicht berücksichtigt.

Die von der Aktivität **[!UICONTROL Lokale Validierung]** gesendete Benachrichtigung stellt sich wie folgt dar:

![](assets/local_validation_intro_2.png)

### Warten {#wait}

Die Warteaktivität verzögert den Start der zweiten Validierungsaktivität, welche die Versandreaktionen-Benachrichtigungen versendet. Im Feld **[!UICONTROL Wartezeit]** wurde hier **[!UICONTROL 5T]**, also 5 Tage, angegeben. Auf diese Weise werden die Empfängerreaktionen der nächsten fünf Tage in der Versandreaktionen-Benachrichtigung berücksichtigt.

![](assets/local_validation_workflow_3.png)

### Versandreaktionen-Benachrichtigung {#feedback-notification}

Die zweite Aktivität vom Typ **[!UICONTROL Lokale Validierung]** sendet an jeden lokalen Verantwortlichen einen Versandreaktionen-Bericht.

![](assets/local_validation_workflow_4.png)

Folgende Angaben sind erforderlich:

1. Im Bereich **[!UICONTROL Auszuführende Aktion]**: Wählen Sie die Option **[!UICONTROL Versandreaktionen-Bericht]** aus.
1. Im Bereich **[!UICONTROL Versand]**: Wählen Sie die Option **[!UICONTROL Wird durch die Transition angegeben]** aus.
1. Im Bereich **[!UICONTROL Validierungsverwaltung]**: Wählen Sie die Versandvorlage aus und geben Sie den Betreff für die Benachrichtigungs-E-Mail an.

Nach Ablauf der in der Warteaktivität definierten Wartezeit sendet die zweite **[!UICONTROL Lokale Validierung]** an jeden lokalen Verantwortlichen folgende Benachrichtigung:

![](assets/local_validation_intro_3.png)

### Validierungsverfolgung durch den Administrator {#approval-tracking-by-the-administrator}

Bei jedem Start der lokalen Validierungsaktivität wird eine Validierungsaufgabe erstellt. Der Administrator hat die Möglichkeit, jede dieser Validierungsaufgaben zu prüfen.

Klicken Sie im Zielgruppen-Workflow Ihrer Kampagne auf den Tab **[!UICONTROL Lokale Validierungsaufgaben]**.

![](assets/local_validation_admin_1.png)

Eine weitere Zugriffsmöglichkeit besteht über den Tab **[!UICONTROL Validierungsaufgaben]** in der Datenverteilungsvorlage.

![](assets/local_validation_admin_2.png)

Markieren Sie die zu prüfende Aufgabe und klicken Sie auf die Schaltfläche **[!UICONTROL Detail]**. Im **[!UICONTROL Allgemein]**-Tab der Aufgabe werden die wichtigsten Informationen zur Aufgabe angezeigt. Es besteht des Weiteren die Möglichkeit, die Validierungs-Deadline und das Erinnerungsdatum zu ändern.

![](assets/local_validation_admin_3.png)

Folgende Informationen stehen zur Verfügung:

* Titel und Kennung der Aufgabe,
* verwendete Verteilung,
* Anzahl potenziell zu sendender Nachrichten,
* zugrundeliegender Workflow und Kampagne,
* Planung der Aufgabe.

Im Tab **[!UICONTROL Verteilung]** der Aufgabe werden die Validierungslogs und -status, die Anzahl potenziell zu sendender Nachrichten, das Validierungsdatum und die validierenden Benutzer angezeigt.

![](assets/local_validation_admin_4.png)

Markieren Sie ein Validierungslog und klicken Sie auf die Schaltfläche **[!UICONTROL Details...]** für genauere Informationen. Im **[!UICONTROL Allgemein]**-Tab des Validierungslogs kann darüber hinaus der Validierungsstatus geändert werden.

![](assets/local_validation_admin_5.png)

Folgende Informationen stehen zur Verfügung:

* Zugrunde liegende Validierungsaufgabe,
* Validierungsstatus (**[!UICONTROL Validiert]** oder **[!UICONTROL Ausstehend]**),
* verwendete Verteilung,
* lokaler Verantwortlicher, der validiert hat, und Validierungsdatum,
* Anzahl potenziell zu sendender Nachrichten und Anzahl validierter Nachrichten.

Im Tab **[!UICONTROL Zielkontakte]** des Validierungslogs wird die Liste der potenziellen Empfänger und ihr Validierungsstatus angezeigt. Der Status kann an dieser Stelle geändert werden.

![](assets/local_validation_admin_6.png)

