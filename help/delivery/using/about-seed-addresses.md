---
solution: Campaign Classic
product: campaign
title: Über Testadressen
description: Über Testadressen
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 76%

---


# Über Testadressen{#about-seed-addresses}

Testadressen ermöglichen den Versand an Empfänger, die nicht den vorliegenden Zielgruppenkriterien entsprechen. Auf diese Weise können Empfänger, die außerhalb des Versandperimeters liegen, die Nachricht so wie jeder andere Empfänger innerhalb der Zielgruppe erhalten.

Einer der Hauptgründe für die Verwendung von Testadressen ist **der Schutz Ihrer Mailingliste**. Wenn Sie Testadressen in Ihre Mailingliste einfügen, erfahren Sie, wenn diese von einer Drittpartei verwendet wird, da auch die Testadressen die Sendungen an Ihre Mailingliste erhalten.

Darüber hinaus können Sie **Vorschau und die Personalisierung und Wiedergabe der Versand vor dem Versenden durch Testadressen testen, indem Sie ihnen Testversand senden (siehe [Testadressen als Testversand](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof) verwenden.**

![](assets/do-not-localize/how-to-video.png) [Mehr zu dieser Funktion erfahren Sie im Video.](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video).

Die Verwendung von Testadressen bietet die folgenden Vorteile:

* Zufällige Ersetzung von Feldern durch Daten aus Empfänger-Profilen: Auf diese Weise können Sie nur die E-Mail-Adresse eingeben, z. B. im Bereich &quot;Seed-Adresse&quot;, und die Kampagne kann die anderen Felder des Profils automatisch ausfüllen (siehe [Anwendungsfall: konfigurieren Sie das Feld Ersetzen](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Bei Workflows mit Datamanagement-Funktionen können die im Versand genutzten zusätzlichen Daten auf Ebene der Testadressen angegeben werden, um den entsprechenden Wert zu erzwingen. Auf diese Weise umgeht man die zufällige Wertersetzung.
* Testadressen werden in den folgenden Versandstatistikberichten grundsätzlich nicht berücksichtigt: **[!UICONTROL Klicks]**, **[!UICONTROL Öffnungen]**, **[!UICONTROL Abmeldungen]**.

Testadressen werden entweder durch Importieren zur Versandzielgruppe hinzugefügt oder direkt im Versand oder der Kampagne erstellt.

>[!NOTE]
>
>Testadressen gehören nicht zur Empfängertabelle, sondern werden in einer separaten Tabelle erstellt. Wenn Sie die Empfängertabelle mit neuen Daten erweitern, muss die Testadressen-Tabelle ebenfalls mit denselben Daten erweitert werden. Andernfalls werden diese Daten nicht für Testadressen berücksichtigt.
>
>Ein Beispiel zum Erweitern der Tabelle &quot;Testadressen&quot;finden Sie in diesem Abschnitt: [Anwendungsfall: Testadressen für Kriterien auswählen](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Für den Briefpost-Versand werden Testadressen während der Extraktion hinzugefügt und im Ausgabedokument unter die restlichen Informationen gemischt.

>[!IMPORTANT]
>
>Bei Briefsendungen muss das Format der Extraktionsdatei folgende Bedingungen erfüllen:
>
>* Keine Verwendung der Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]**.
>* Bei Extraktion von Kollektionselementen bleiben die entsprechenden Felder für Testadressen leer, es sei denn, die Option **[!UICONTROL Nur eine Zeile (Expertenmodus)]** wurde ausgewählt. Lesen Sie diesbezüglich auch [diesen Abschnitt](../../platform/using/executing-export-jobs.md#step-7---data-formatting).

>


