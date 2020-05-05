---
title: Über Testadressen
seo-title: Über Testadressen
description: Über Testadressen
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# Über Testadressen{#about-seed-addresses}

Testadressen ermöglichen den Versand an Empfänger, die nicht den vorliegenden Zielgruppenkriterien entsprechen. Auf diese Weise können Empfänger, die außerhalb des Versandperimeters liegen, die Nachricht so wie jeder andere Empfänger innerhalb der Zielgruppe erhalten.

Einer der Hauptgründe für die Verwendung von Testadressen ist **der Schutz Ihrer Mailingliste**. Wenn Sie Testadressen in Ihre Mailingliste einfügen, erfahren Sie, wenn diese von einer Drittpartei verwendet wird, da auch die Testadressen die Sendungen an Ihre Mailingliste erhalten.

Zusätzlich können Sie durch die Durchführung von Testsendungen an Testadressen die **Personalisierung und das Rendering Ihrer Sendungen vor dem Versand in der Vorschau ansehen und testen** (siehe [Testadressen als Zielgruppe verwenden](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

Die Verwendung von Testadressen bietet die folgenden Vorteile:

* Ersetzen fehlender Werte durch Empfängerdaten aus der Zielgruppe (Zufallsauswahl). So ist es beispielsweise möglich, in Testadressen nur die E-Mail-Adresse anzugeben und die anderen Felder automatisch von Campaign aus dem Profil ausfüllen zu lassen (siehe [Anwendungsbeispiel: Wertersetzung konfigurieren](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Bei Workflows mit Datamanagement-Funktionen können die im Versand genutzten zusätzlichen Daten auf Ebene der Testadressen angegeben werden, um den entsprechenden Wert zu erzwingen. Auf diese Weise umgeht man die zufällige Wertersetzung.
* Testadressen werden in den folgenden Versandstatistikberichten grundsätzlich nicht berücksichtigt: **[!UICONTROL Klicks]**, **[!UICONTROL Öffnungen]**, **[!UICONTROL Abmeldungen]**.

Testadressen werden entweder durch Importieren zur Versandzielgruppe hinzugefügt oder direkt im Versand oder der Kampagne erstellt.

>[!NOTE]
>
>Testadressen gehören nicht zur Empfängertabelle, sondern werden in einer separaten Tabelle erstellt. Wenn Sie die Empfängertabelle mit neuen Daten erweitern, muss die Testadressen-Tabelle ebenfalls mit denselben Daten erweitert werden. Andernfalls werden diese Daten nicht für Testadressen berücksichtigt.
>
>In diesem Abschnitt wird ein Beispiel für die Erweiterung der Tabelle mit Testadressen dargestellt: [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

Für den Briefpost-Versand werden Testadressen während der Extraktion hinzugefügt und im Ausgabedokument unter die restlichen Informationen gemischt.

>[!CAUTION]
>
>Bei Briefsendungen muss das Format der Extraktionsdatei folgende Bedingungen erfüllen:
>
>* Keine Verwendung der Option **[!UICONTROL Gruppierungen verwalten (GROUP BY + HAVING)]**.
>* Bei Extraktion von Kollektionselementen bleiben die entsprechenden Felder für Testadressen leer, es sei denn, die Option **[!UICONTROL Nur eine Zeile (Expertenmodus)]** wurde ausgewählt. Lesen Sie diesbezüglich auch [diesen Abschnitt](../../platform/using/exporting-data.md#step-7---data-formatting).
>


