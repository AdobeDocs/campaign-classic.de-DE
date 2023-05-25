---
product: campaign
title: Über Testadressen
description: Erste Schritte mit Testadressen
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '391'
ht-degree: 100%

---

# Über Testadressen{#about-seed-addresses}



Testadressen ermöglichen den Versand an Empfänger, die nicht den vorliegenden Zielgruppenkriterien entsprechen. Auf diese Weise können Empfänger, die außerhalb des Versandperimeters liegen, die Nachricht so wie jeder andere Empfänger innerhalb der Zielgruppe erhalten.

Einer der Hauptgründe für ihre Verwendung ist **der Schutz der Mailing-Liste**. Wenn Sie Testadressen in Ihre Mailing-Liste einfügen, können Sie feststellen, ob sie von einem Drittanbieter verwendet wird. Die Testadressen, die darin enthalten sind, erhalten die Sendungen an Ihre Mailing-Liste.

Zusätzlich können Sie durch die Durchführung von Testsendungen an Testadressen die **Personalisierung und das Rendering Ihrer Sendungen vor dem Versand in der Vorschau ansehen und testen** (siehe [Testadressen als Zielgruppe verwenden](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Mehr zu dieser Funktion erfahren Sie im Video.](steps-defining-the-target-population.md#seeds-and-proofs-video).

Die Verwendung von Testadressen bietet die folgenden Vorteile:

* Ersetzen fehlender Werte durch Empfängerdaten aus der Zielgruppe (Zufallsauswahl). So ist es beispielsweise möglich, in Testadressen nur die E-Mail-Adresse anzugeben und die anderen Felder automatisch von Campaign aus dem Profil ausfüllen zu lassen (siehe [Anwendungsbeispiel: Konfigurieren der Feldersetzung](use-case--configuring-the-field-substitution.md)).
* Bei Workflows mit Datamanagement-Funktionen können die im Versand genutzten zusätzlichen Daten auf Ebene der Testadressen angegeben werden, um den entsprechenden Wert zu erzwingen. Auf diese Weise umgeht man die zufällige Wertersetzung.
* Testadressen werden in den folgenden Versandstatistikberichten grundsätzlich nicht berücksichtigt: **[!UICONTROL Klicks]**, **[!UICONTROL Öffnungen]**, **[!UICONTROL Abmeldungen]**.

Testadressen werden entweder durch Importieren zur Versandzielgruppe hinzugefügt oder direkt im Versand oder der Kampagne erstellt.

>[!NOTE]
>
>Testadressen gehören nicht zur Empfängertabelle, sondern werden in einer separaten Tabelle erstellt. Wenn Sie die Empfängertabelle mit neuen Daten erweitern, muss die Testadressen-Tabelle ebenfalls mit denselben Daten erweitert werden. Andernfalls werden diese Daten nicht für Testadressen berücksichtigt.
>
>In diesem Abschnitt wird ein Beispiel für die Erweiterung der Tabelle mit Testadressen dargestellt: [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](use-case--selecting-seed-addresses-on-criteria.md).

Für den Briefpost-Versand werden Testadressen während der Extraktion hinzugefügt und im Ausgabedokument unter die restlichen Informationen gemischt.

>[!IMPORTANT]
>
>Bei Briefsendungen muss das Format der Extraktionsdatei folgende Bedingungen erfüllen:
>
>* Keine Verwendung der Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]**.
>* Bei Extraktion von Sammlungselementen bleiben die entsprechenden Felder für Testadressen leer, es sei denn, die Option **[!UICONTROL Nur eine Zeile (Expertenmodus)]** wurde ausgewählt. Lesen Sie diesbezüglich auch [diesen Abschnitt](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>

