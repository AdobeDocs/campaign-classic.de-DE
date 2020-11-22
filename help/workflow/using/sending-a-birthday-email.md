---
solution: Campaign Classic
product: campaign
title: Geburtstags-E-Mail senden
description: Erfahren Sie, wie Sie eine Geburtstagsemail mit einem Workflow senden
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 98%

---


# Geburtstags-E-Mail senden{#sending-a-birthday-email}

## Einleitung {#introduction}

Im folgenden Anwendungsbeispiel wird aufgezeigt, wie sich der wiederkehrende Versand einer E-Mail an Empfänger zu deren Geburtstag planen lässt.

Der Workflow für dieses Anwendungsbeispiel stellt sich wie folgt dar:

![](assets/birthday-workflow_usecase_1.png)

In diesem täglich ausgeführten Workflow werden alle Empfänger ausgewählt, deren Geburtstag dem aktuellen Datum entspricht.

Dieses Anwendungsbeispiel ist auch als Video unter [Creating a workflow](https://docs.adobe.com/content/help/de-DE/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) verfügbar.

Erstellen Sie eine Kampagne und klicken Sie auf den Tab **[!UICONTROL Zielbestimmungen und Workflows]**. Lesen Sie diesbezüglich auch den Abschnitt [Erstellen einer Hauptzielgruppe im Workflow](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

Gehen Sie dann wie folgt vor:

## Planung des Versands {#configuring-the-scheduler}

1. Fügen Sie zunächst eine **Planung** hinzu, um den täglichen Versand auszulösen. Im Beispiel unten wird der Versand jeden Tag um 6 Uhr erstellt.

   ![](assets/recur_delivery2.png)


## Identifizieren von Empfängern, die Geburtstag haben {#identifying-recipients-whose-birthday-it-is}

Konfigurieren Sie zunächst die **[!UICONTROL Planung]** für eine tägliche Ausführung des Workflows. Identifizieren Sie dann alle Empfänger, deren Geburtstag dem aktuellen Datum entspricht.

Gehen Sie hierzu wie folgt vor:

1. Ziehen Sie eine **[!UICONTROL Abfrage]** in den Workflow-Arbeitsbereich und öffnen Sie sie per Doppelklick.
1. Klicken Sie auf den Link **Abfrage bearbeiten** und wählen Sie **[!UICONTROL Filterbedingungen]** aus.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Klicken Sie in die erste Zelle der Spalte **[!UICONTROL Ausdruck]** und anschließend auf die Schaltfläche **[!UICONTROL Ausdruck bearbeiten]**, um den Ausdruckseditor zu öffnen.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Erweiterte Auswahl]**, um den Filtermodus auszuwählen.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Wählen Sie die Option **[!UICONTROL Formel von einem Ausdruck ausgehend erstellen]** und klicken Sie auf die Schaltfläche **[!UICONTROL Weiter]**.
1. Wählen Sie aus der Funktionsliste über den Knoten **[!UICONTROL Datum]** mit einem Doppelklick die Funktion **[!UICONTROL Day]** aus. Diese Funktion gibt die Zahl aus, die dem Tag des als Parameter übergebenen Datums entspricht.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Wählen Sie in der Liste der verfügbaren Felder mit einem Doppelklick das **[!UICONTROL Geburtsdatum]** aus. Im oberen Abschnitt des Editors wird nun die folgende Formel angezeigt:

   ```
   Day(@birthDate)
   ```

   Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

1. Wählen Sie nun aus der Dropdown-Liste den **[!UICONTROL Operator]****[!UICONTROL gleich aus]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Klicken Sie anschließend in die erste Zelle der Spalte **[!UICONTROL Werte]** und auf die Schaltfläche **[!UICONTROL Ausdruck bearbeiten]**, um den Ausdruckseditor zu öffnen.
1. Wählen Sie aus der Funktionsliste über den Knoten **[!UICONTROL Datum]** mit einem Doppelklick die Funktion **[!UICONTROL Day]** aus.
1. Wählen Sie anschließend mit einem Doppelklick die Funktion **[!UICONTROL GetDate]** aus, um das aktuelle Datum abzurufen.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   Im oberen Abschnitt des Ausdruckseditors wird nun folgende Formel angezeigt:

   ```
   Day(GetDate())
   ```

   Klicken Sie zur Bestätigung auf **[!UICONTROL Beenden]**.

1. Wiederholen Sie diesen Vorgang, um den dem aktuellen Monat entsprechenden Geburtsmonat abzurufen. Klicken Sie hierzu auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wiederholen Sie die Schritte 3 bis 10 unter Ersetzung der Funktion **[!UICONTROL Day]** durch die Funktion **[!UICONTROL Month]**.

   Die vollständige Formel lautet wie folgt:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Schließen Sie nun am Ergebnis der **[!UICONTROL Abfrage]**-Aktivität einen **[!UICONTROL E-Mail-Versand]** an, damit alle in Ihrer Liste enthaltenen Empfänger eine E-Mail zum Geburtstag erhalten.

## Einschluss von Abonnenten, die am 29. Februar Geburtstag haben (optional) {#including-recipients-born-on-february-29th--optional-}

Wenn Sie alle Abonnenten einschließen möchten, die am 29. Februar Geburtstag haben, sehen Sie in diesem Anwendungsbeispiel, wie Sie den Versand einer wiederkehrenden Geburtstags-E-Mail an eine Liste von Empfängern planen können – unabhängig davon ob es sich um ein Schaltjahr handelt oder nicht.

Die Umsetzung des Anwendungsbeispiels gliedert sich in folgende Schritte:

* Auswahl der Empfänger, die am aktuellen Datum Geburtstag haben.
* Test, ob ein Schaltjahr vorliegt.
* Auswahl der Empfänger, die am 29. Februar Geburtstag haben.

Der Workflow für dieses Anwendungsbeispiel stellt sich wie folgt dar:



Sollte es sich bei dem laufenden Jahr **nicht um ein Schaltjahr handeln**, müssen bei der Workflow-Ausführung am 1. März auch die Empfänger ausgewählt und zu der Empfängerliste hinzugefügt werden, deren Geburtstag am 29. Februar ist. In allen anderen Fällen ist keinerlei zusätzliche Maßnahme notwendig.

### 1. Schritt: Auswahl der Empfänger, die am aktuellen Datum Geburtstag haben {#step-1--selecting-the-recipients}

Konfigurieren Sie zunächst die **[!UICONTROL Planung]** für eine tägliche Ausführung des Workflows. Identifizieren Sie dann alle Empfänger, deren Geburtstag dem aktuellen Datum entspricht.

>[!NOTE]
>
>Sollte es sich bei dem laufenden Jahr um ein Schaltjahr handeln, werden alle Empfänger, deren Geburtstag auf den 29. Februar fällt, automatisch mit eingeschlossen.

![](assets/birthday-workflow_usecase_2.png)

Die Auswahl der Empfänger, deren Geburtstag dem aktuellen Datum entspricht, wird im Abschnitt [Identifizieren von Empfängern, die Geburtstag haben](#identifying-recipients-whose-birthday-it-is) beschrieben.

### 2. Schritt: Test, ob ein Schaltjahr vorliegt {#step-2--select-whether-or-not-it-is-a-leap-year}

Prüfen Sie mithilfe einer **[!UICONTROL Test]**-Aktivität, ob das aktuelle Jahr ein Schaljahr und ob das aktuelle Datum der 1. März ist.

Wenn der Test wahr ist (d. h. es ist kein Schaltjahr – es gibt keinen 29. Februar – und das aktuelle Datum ist der 1. März), wird die **[!UICONTROL Wahr]**-Transition aktiviert und die Empfänger, die am 29. Februar Geburtstag haben, werden zum Versand des 1. März hinzugefügt. Andernfalls wird die **[!UICONTROL Falsch]**-Transition aktiviert und nur die Empfänger, die am aktuellen Datum Geburtstag haben, erhalten den Versand.

Kopieren Sie den unten stehenden Code und fügen Sie ihn im Bereich **[!UICONTROL Initialisierungsscript]** des **[!UICONTROL Erweitert]**-Tabs ein.

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

Fügen Sie im Bereich **[!UICONTROL Bedingte Verzweigung]** die folgende Bedingung hinzu:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 3. Schritt: Auswahl der Empfänger, die am 29. Februar Geburtstag haben {#step-3--select-any-recipients-born-on-february-29th}

Ziehen Sie eine **[!UICONTROL Verzweigung]** in das Diagramm und schließen Sie an eine der ausgehenden Transitionen eine **[!UICONTROL Abfrage]**-Aktivität an.

Wählen Sie in dieser Abfrage alle Empfänger aus, die am 29. Februar Geburtstag haben.

![](assets/birthday-workflow_usecase_5.png)

Kombinieren Sie die Ergebnisse mithilfe einer **[!UICONTROL Vereinigung]**.

Schließen Sie nun an beide Zweige der **[!UICONTROL Test]**-Aktivität einen **[!UICONTROL E-Mail-Versand]** an, damit alle in Ihrer Liste enthaltenen Empfänger eine E-Mail zum Geburtstag erhalten – selbst diejenigen, die am 29. Februar Geburtstag haben, und das auch, wenn gerade kein Schaltjahr vorliegt.

## Wiederkehrenden Versand erstellen {#creating-a-recurring-delivery-in-a-targeting-workflow}

Fügen Sie für die gewünschte Geburtstags-E-Mail-Vorlage einen **wiederkehrenden Versand** hinzu.

>[!CAUTION]
>
>Damit die Workflows ausgeführt werden, müssen die mit dem Kampagnenprozess verbundenen technischen Workflows gestartet werden. Lesen Sie diesbezüglich den Abschnitt [Liste der Kampagnenprozess-Workflows](../../workflow/using/campaign.md).
>
>Wenn die Validierungsschritte für die Kampagne aktiviert sind, werden die Sendungen erst ausgeführt, nachdem diese Schritte bestätigt wurden. Weitere Informationen hierzu finden Sie im Abschnitt [Zu verifizierende Prozesse auswählen](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved).

![](assets/birthday-workflow_usecase_1.png)
