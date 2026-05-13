---
product: campaign
title: Über Testadressen
description: Erste Schritte mit Testadressen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
TQID: https://experienceleague.adobe.com/ZFeQSj9pGtKzG-wBsm5Go39ja7jvZ0pVi8h3xKOYR8c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 400
ht-degree: 87%

---

# Über Testadressen{#about-seed-addresses}

Testadressen ermöglichen die Auswahl von Empfängern, die nicht den definierten Zielgruppenkriterien entsprechen. Auf diese Weise können Empfänger, die außerhalb des Versandbereichs liegen, den Versand wie jeder andere Zielgruppenempfänger erhalten.

Einer der Hauptgründe für ihre Verwendung ist **der Schutz der Mailing-Liste**. Wenn Sie Testadressen in Ihre Mailing-Liste einfügen, können Sie feststellen, ob sie von einem Drittanbieter verwendet wird. Die Testadressen, die darin enthalten sind, erhalten die Sendungen an Ihre Mailing-Liste.

Zusätzlich können Sie durch die Durchführung von Testsendungen an Testadressen die **Personalisierung und das Rendering Ihrer Sendungen vor dem Versand in der Vorschau ansehen und testen** (siehe [Testadressen als Zielgruppe verwenden](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Mehr zu dieser Funktion erfahren Sie im Video.](steps-defining-the-target-population.md#seeds-and-proofs-video).

Die Verwendung von Testadressen bietet die folgenden Vorteile:

* Ersetzen fehlender Werte durch Empfängerdaten aus der Zielgruppe (Zufallsauswahl). So ist es beispielsweise möglich, in Testadressen nur die E-Mail-Adresse anzugeben und die anderen Felder automatisch von Campaign aus dem Profil ausfüllen zu lassen (siehe [Anwendungsbeispiel: Konfigurieren der Feldersetzung](use-case-configuring-the-field-substitution.md)).
* Bei Workflows mit Datamanagement-Funktionen können die im Versand genutzten zusätzlichen Daten auf Ebene der Testadressen angegeben werden, um den entsprechenden Wert zu erzwingen. Auf diese Weise umgeht man die zufällige Wertersetzung.
* Testadressen werden in den folgenden Versandstatistikberichten grundsätzlich nicht berücksichtigt: **[!UICONTROL Klicks]**, **[!UICONTROL Öffnungen]**, **[!UICONTROL Abmeldungen]**.

Testadressen werden entweder durch Importieren zur Versandzielgruppe hinzugefügt oder direkt im Versand oder der Kampagne erstellt.

>[!NOTE]
>
>Testadressen gehören nicht zur Empfängertabelle, sondern werden in einer separaten Tabelle erstellt. Wenn Sie die Empfängertabelle um neue Daten erweitern, müssen Sie die Testadressen-Tabelle ebenfalls um die gleichen Daten erweitern. Andernfalls werden erweiterte Felder für Testadressen nicht berücksichtigt.
>
>In diesem Abschnitt wird ein Beispiel für die Erweiterung der Tabelle mit Testadressen dargestellt: [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](use-case-selecting-seed-addresses-on-criteria.md).

Für den Briefpost-Versand werden Testadressen während der Extraktion hinzugefügt und im Ausgabedokument unter die restlichen Informationen gemischt.

>[!IMPORTANT]
>
>Bei Briefpost-Sendungen muss das Format der Extraktionsdatei folgende Bedingungen erfüllen:
>
>* Keine Verwendung der Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]**.
>* Bei der Extraktion von Sammlungselementen bleiben die entsprechenden Felder für Testadressen leer, es sei denn, die Option **[!UICONTROL Nur eine Zeile (Expertenmodus)]** wurde ausgewählt. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
