---
product: campaign
title: Erstellen einer partizipativen Kampagne
description: Erfahren Sie, wie Sie eine partizipative Kampagne erstellen
feature: Distributed Marketing
hide: true
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
TQID: https://experienceleague.adobe.com/No3N7fj-k3CN10p7SgpLolqvpzFTEOk-BQrFmOdcmeE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: a6187aac-0a00-4394-8937-e8d4c1a40aa4
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 995
ht-degree: 67%

---

# Erstellen einer partizipativen Kampagne{#creating-a-collaborative-campaign-intro}



Partizipative Kampagnen werden von der Zentralstelle auf Basis der Kampagnenvorlagen **Verteiltes Marketing** erstellt. Mehr dazu erfahren Sie auf [dieser Seite](about-distributed-marketing.md#collaborative-campaign).

## Erstellen einer partizipativen Kampagne {#creating-a-collaborative-campaign}

Partizipative Kampagnen beruhen jeweils auf einer Referenzkampagne, die von der Zentralstelle zu erstellen ist. Dies geschieht ausgehend vom Knoten **[!UICONTROL Kampagnenverwaltung > Kampagnen]** durch Klick auf das **[!UICONTROL Neu]**-Symbol.

>[!NOTE]
>
>Mit Ausnahme der **[!UICONTROL partizipativen Kampagnen mit Kampagnenzugriff]** können die Kampagnen über eine Webschnittstelle konfiguriert und ausgeführt werden.

Der Konfigurationsprozess für eine partizipative Kampagnendatenbank entspricht dem einer lokalen Kampagnenvorlage. Die Spezifikationen der verschiedenen Arten von partizipativen Kampagnen werden nachfolgend beschrieben.

### Partizipative Kampagne (Formular) {#by-form}

Wählen Sie die Vorlage **[!UICONTROL Partizipative Kampagne (Formular) (opCollaborativeByForm)]** aus, um diese Kampagne zu erstellen.

![](assets/mkg_dist_mutual_op_form2.png)

Gehen Sie in den Tab **[!UICONTROL Bearbeiten]** und klicken Sie auf den Link **[!UICONTROL Erweiterte Kampagnenparameter...]**, um auf den Tab **Dezentrales Marketing** zuzugreifen.

Wählen Sie die Web **Benutzeroberfläche &quot;** Formular“. Auf diese Weise können Sie Personalisierungsfelder erstellen, die von Lokalstellen bei der Kampagnenbestellung verwendet werden. Siehe [Lokale Kampagne erstellen (Standardformular)](examples.md#creating-a-local-campaign--by-form-).

Speichern Sie Ihre Kampagne. Sie steht Ihnen nun in der Ansicht **Kampagnenkits** im Tab **Kampagnen** zur Verfügung, indem Sie auf die Schaltfläche **[!UICONTROL Erstellen]** klicken.

Die **[!UICONTROL Kampagnenkit]**-Liste ermöglicht Ihnen die Verwendung von lokalen Kampagnenvorlagen (native oder duplizierte) sowie Referenzkampagnen für partizipative Kampagnen. So können Sie Kampagnen für unterschiedliche Unternehmenseinheiten erstellen.

![](assets/mkg_dist_mutual_op_form1b.png)

### Partizipative Kampagne (Kampagnenzugriff) {#by-campaign}

Wählen Sie die Vorlage **[!UICONTROL Partizipative Kampagne (Kampagnenzugriff) (opCollaborativeByCampaign)]** aus.

![](assets/mkg_dist_mutual_op_by_op2.png)

Die Lokalstelle kann bei der Kampagnenbestellung die von der Zentralstelle festgelegten Kriterien erfassen und die Kampagne vor der Bestellung auswerten.

Sobald eine Bestellung für eine **Partizipative Kampagne (nach Kampagne)** von der Zentralstelle genehmigt wurde, wird eine untergeordnete Kampagne für die Lokalstelle erstellt. Sobald sie ihnen zur Verfügung stehen, kann die Lokalstelle Folgendes ändern:

* Kampagnenworkflow,
* Typologieregeln,
* Personalisierungsfelder.

Die untergeordnete Kampagne wird von der Lokalstelle ausgeführt. Die übergeordnete Kampagne wird von der Zentralstelle ausgeführt.

Über den Link **Liste der verknüpften Kampagnen...** im Kampagnen-Dashboard kann die Zentralstelle alle untergeordneten Kampagnen der **[!UICONTROL partizipativen Kampagne mit Kampagnenzugriff]** einsehen.

![](assets/mkg_dist_mutual_op_by_op.png)

### Partizipative Kampagne (Zielgruppenvalidierung) {#by-target-approval}

Wählen Sie die Vorlage **[!UICONTROL Partizipative Kampagne (Zielgruppenvalidierung) (opCollaborativeByValidation)]** aus.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In diesem Modus muss die Zentralstelle keine Lokalstellen angeben.

Der Kampagnen-Workflow muss die Aktivität **Lokale Validierung** enthalten. Die Aktivitätsparameter lauten wie folgt:

* **[!UICONTROL Auszuführende Aktion]**: Benachrichtigung zur Zielgruppenvalidierung;
* **[!UICONTROL Verteilungskontext]**: Explizit;
* **[!UICONTROL Datenverteilung]**: Lokalstellen-Datenverteilung.

**Datenverteilung vom** „Lokalstellen-Verteilung“ muss erstellt werden. Mit der Datenverteilungsvorlage können Sie die Anzahl der Datensätze aus einer Liste von Gruppierungswerten begrenzen. Klicken Sie unter **[!UICONTROL Ressourcen > Kampagnen-Management > Datenverteilung]** auf das Symbol **[!UICONTROL Neu]**, um eine neue **[!UICONTROL Datenverteilung]** zu erstellen. Mehr Informationen über Datenverteilungen finden Sie im [Workflows-Handbuch](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-).

![](assets/mkg_dist_data_distribution.png)

Geben Sie die **Zielgruppendimension** sowie das **[!UICONTROL Verteilungsfeld]** an. Wählen Sie als **[!UICONTROL Zuweisungstyp]** die Option **Lokalstelle** aus.

Fügen Sie im Tab **[!UICONTROL Verteilung]** ein Feld für jede Lokalstelle hinzu und geben Sie den jeweiligen Wert an.

![](assets/mkg_dist_data_distribution2.png)

Es besteht die Möglichkeit, der **Versand**-Aktivität eine zweite **Zielgruppenvalidierung**-Aktivität anzuschließen, um einen Bericht über letztere zu konfigurieren.

In der Bestätigungs-E-Mail der Kampagnenerstellung erhält die Lokalstelle eine Liste mit Kontakten, die von den von der Zentralstelle bestimmten Parametern abhängt.

![](assets/mkg_dist_mutual_op_by_valid1.png)

Der Lokalstelle steht es frei, je nach Kampagneninhalt bestimmte Kontakte zu entfernen.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Partizipative Kampagne (ohne Konfiguration) {#simple}

Um eine einfache partizipative Kampagne zu erstellen, wählen Sie die Vorlage **[!UICONTROL Partizipative Kampagne (ohne Konfiguration)]** aus.

## Partizipative Kampagnenkits erstellen {#creating-a-collaborative-campaign-package}

Um die Kampagne den Lokalstellen zur Verfügung zu stellen, muss die Zentralstelle ein Kampagnenkit erstellen.

Gehen Sie wie folgt vor:

1. Klicken Sie im Menü **[!UICONTROL Navigation]** der Rubrik **Kampagnen** auf den Link **[!UICONTROL Kampagnenkits]**.
1. Wählen Sie die **[!UICONTROL Erstellen]**-Schaltfläche aus.
1. Wählen Sie im oberen Bereich des Assistenten die Kampagnenvorlage **[!UICONTROL Neues Kit für eine partizipative Kampagne (mutualizedEmpty)]** aus.
1. Geben Sie die Referenzkampagne an.
1. Bestimmen Sie Titel und Speicherort des Kampagnenkits und legen Sie die Ausführungsplanung fest.

### Datum-Funktionen {#dates}

Beginn- und Enddatum bestimmen die Dauer der Sichtbarkeit der Kampagne in der Kampagnenkit-Liste.

Für **partizipative Kampagnen** muss die Zentralstelle einen Anmeldeschluss und gegebenenfalls eine Übergabe-Deadline angeben.

>[!NOTE]
>
>Mit der Frist **[!UICONTROL Personalization]** kann die Zentralstelle eine Frist festlegen, bis zu der die Lokalstellen die für die Kampagnenkonfiguration zu verwendenden Dokumente (Kalkulationstabellen, Bilder) bereitgestellt haben müssen. Dies ist keine obligatorische Option. Wird dieses Datum ausgelagert, hat dies keine Auswirkungen auf die Kampagnenimplementierung.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Zielgruppe {#audience}

Die Zentralstelle muss für die Teilnahme an der Kampagne vorgesehenen Lokalstellen bei der Erstellung der partizipativen Kampagne angeben, außer bei Kampagnen mit Zielgruppenvalidierung.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Partizipative Kampagnenkits ohne Konfiguration, mit Formular oder mit Kampagnenzugriff]** können nicht validiert werden, sofern die vorgesehenen Lokalstellen nicht angegeben wurden.

### Validierungsmodi {#approval-modes}

In **partizipativen Kampagnen** kann der Validierungsmodus für Bestellungen ausgewählt werden:

![](assets/mkg_dist_edit_kit1.png)

Im manuellen Modus muss sich die Lokalstelle für die Kampagne anmelden, um teilnehmen zu können.

Im automatischen Modus hat die Lokalstelle die Kampagne im Voraus abonniert. Es kann das Kampagnenabonnement kündigen oder seine Parameter ändern, ohne die Genehmigung der Zentralstelle zu benötigen.

![](assets/mkg_dist_edit_kit2.png)

### Benachrichtigungen {#notifications}

Die Konfiguration der Benachrichtigungen entspricht der für lokale Kampagnen. Weitere Informationen finden Sie in [diesem Abschnitt](creating-a-local-campaign.md#notifications).

## Bestellen einer Kampagne {#ordering-a-campaign}

Wenn eine partizipative Kampagne zur Kampagnenkit-Liste hinzugefügt wird, werden die Lokalstellen der von der Zentralstelle definierten Audience benachrichtigt (die **partizipativen Kampagnen (mit Zielgruppenvalidierung)** verfügen über keine vordefinierte Audience). Die gesendete Nachricht enthält einen Link, über den Sie sich für die Kampagne registrieren können, wie unten dargestellt:

![](assets/mkg_dist_mutual_op_notification.png)

Diese Nachricht ermöglicht auch Lokalstellen die Anzeige der vom Zentralbenutzer, der das Package erstellt hat, eingegebenen Beschreibung sowie der mit der Kampagne verknüpften Dokumente. Diese gehören nicht zur Kampagne selbst, stellen jedoch zusätzliche Informationen dazu bereit.

Durch Zugriff auf die Webschnittstelle kann die Lokalstelle Informationen über gewünschte Anpassungen der partizipativen Kampagne geben, die sie bestellen möchte:

![](assets/mkg_dist_mutual_op_command.png)

Nach Speicherung der Bestellung erhält der validierungsverantwortliche Benutzer der Lokalstelle eine Benachrichtigungs-E-Mail zur Validierung der Bestellung.

![](assets/mkg_dist_mutual_op_valid_command.png)

Weitere Informationen hierzu finden Sie im Abschnitt [Validierungsprozess](creating-a-local-campaign.md#approval-process).

## Validieren einer Bestellung {#approving-an-order}

Die Validierung der Bestellung eines partizipativen Kampagnen-Kits entspricht der von lokalen Kampagnen. Weitere Informationen finden Sie in [diesem Abschnitt](creating-a-local-campaign.md#approving-an-order).
