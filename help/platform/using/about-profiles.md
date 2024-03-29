---
product: campaign
title: Erste Schritte mit Profilen
description: Arbeiten mit Profilen in Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 88%

---

# Erste Schritte mit Profilen{#about-profiles}



Alle Profile werden in der Adobe Campaign-Datenbank zentral gespeichert. Die Akquise von Profilen und die Datenbankerstellung können auf verschiedenste Weisen erfolgen: Online-Akquise über Web-Formulare, manueller oder automatisierter Import von Textdateien, Replikation von bereits existierenden Datenbanken oder Informationssystemen des Unternehmens. Mit Adobe Campaign können Sie Marketing-Verlauf, Kaufinformationen, Voreinstellungen, CRM-Daten und alle relevanten PI-Daten in eine konsolidierte Ansicht integrieren, um sie zu analysieren und Maßnahmen zu ergreifen.

**Profil** bezeichnet einen Datensatz, der einen Endkunden, einen Interessenten oder Lead repräsentiert. Bei diesen Daten kann es sich z. B. um einen Datensatz in der nmsRecipient-Tabelle oder einer externen Tabelle handeln, die die Kennung eines Cookies, eines Kunden oder eines Mobiltelefons oder andere für einen bestimmten Kanal relevante Informationen enthält.

In Adobe Campaign sind die Standardprofile für Sendungen (E-Mails, SMS usw.) die Empfänger. Mit den in der Datenbank gespeicherten Empfängerdaten können Sie die Zielgruppe filtern, die einen bestimmten Versand erhalten soll, und Personalisierungsdaten in den Versandinhalt einfügen. In der Datenbank gibt es noch andere Arten von Profilen. Sie sind für unterschiedliche Zwecke gedacht. So werden beispielsweise Testprofile erstellt, um Ihre Sendungen zu testen, bevor sie an die endgültige Zielgruppe gesendet werden.

![](assets/do-not-localize/how-to-video.png) [Informationen zum Profilkonzept finden Sie in diesem Video](#create-profiles-video)

## Profiltypen {#profile-types}

Die Adobe Campaign-Plattform ermöglicht die Verwaltung von Profilen über den gesamten Zyklus hinweg, von der Erstellung oder dem Import über Zielgruppenbestimmung und Tracking bis hin zur Aktualisierung und anderen Aktivitäten.

Ein Profil entspricht einem Datensatz in der Datenbank, der alle nötigen Informationen enthält, um einen Kontakt zu qualifizieren, zu verfolgen und in Zielgruppen einzubeziehen.

Profile können verschiedenen Kategorien zugeteilt werden, welche sich im Speicherort widerspiegeln, zum Beispiel: einem Empfänger, einem Besucher, einem Benutzer, einem Abonnenten, einem Interessenten usw.

## Empfängerprofile {#recipient-profiles}

Versandempfänger werden in der Datenbank in Form von Profilen mit den entsprechenden Informationen – Nachname, Vorname, Adressdaten, Abonnements, Sendungen etc. – gespeichert. Sendungen innerhalb von Marketingkampagnen können sich an Empfängergruppen aus der Datenbank richten, die nach bestimmten – einfachen oder komplexen – Kriterien erstellt werden.

Sie können auch Kampagnen für Empfänger erstellen, deren Profile nicht in der Datenbank, sondern in Dateien gespeichert sind. Diese werden als &quot;externe&quot; Sendungen bezeichnet. Weitere Informationen zu diesem Versandtyp finden Sie unter [diese Seite](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Die gängigsten Methoden der Profilerstellung sind:

* direkte Erfassung in der Benutzeroberfläche,
* Import von Profildateien,
* Online-Akquise über Webformulare.

>[!NOTE]
>
>Dateiimport und Webformulare werden im Abschnitt [Allgemeine Importe und Exporte](../../platform/using/get-started-data-import-export.md) vorgestellt.

## Profile und Zielgruppen {#profiles-and-targets}

Die **[!UICONTROL Profile und Zielgruppen]** -Link ermöglicht die Anzeige von in der Adobe Campaign-Datenbank gespeicherten Empfängern. Sie können einen neuen Empfänger erstellen, einen vorhandenen Empfänger bearbeiten und auf sein Profil zugreifen. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Außerdem haben Sie an dieser Stelle Zugriff auf:

* Listen – [Mehr dazu](../../platform/using/creating-and-managing-lists.md)
* Anmeldedienste – [Mehr dazu](../../delivery/using/managing-subscriptions.md)
* Web-Programme – [Mehr dazu](../../web/using/about-web-applications.md)
* Importe und Exporte (Vorgänge) – [Mehr dazu](../../platform/using/about-generic-imports-exports.md)
* Zielgruppen-Workflows – [Mehr dazu](../../workflow/using/building-a-workflow.md#implementation-steps-)

Über die Empfängerseite sind die gängigsten Aktionen möglich. Sie können Profile bearbeiten, aktualisieren, sortieren, löschen oder neue Profile erstellen.

Für erweiterte Profilmanipulationen müssen Sie die Adobe Campaign-Struktur bearbeiten. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Explorer]** auf der Adobe Campaign-Startseite.

Standardmäßig werden Empfänger in der Baumstruktur im Knoten **[!UICONTROL Profile und Zielgruppen > Empfänger]** gespeichert. Sie können Empfänger aus dieser Ansicht erstellen sowie:

* Profile der Datenbank zu sortieren und zu filtern – [Mehr dazu](../../platform/using/filtering-options.md)
* Profile der Datenbank zu verschieben, zu duplizieren oder zu löschen – [Mehr dazu](../../platform/using/managing-profiles.md)
* Profile zu aktualisieren – [Mehr dazu](../../platform/using/updating-data.md)
* Empfänger zu exportieren – [Mehr dazu](../../platform/using/exporting-and-importing-profiles.md)
* Empfängergruppen zu erstellen – [Mehr dazu](../../platform/using/creating-and-managing-lists.md)

Erweiterte Funktionen und Konfigurationsmöglichkeiten stehen über den **[!UICONTROL Explorer]** zur Verfügung.

![](assets/d_ncs_user_interface01.png)

Auf [dieser Seite](../../platform/using/adobe-campaign-explorer.md) wird die allgemeine Struktur des Adobe Campaign-Explorers beschrieben.

>[!NOTE]
>
>Durch Klicken im Adobe Campaign-Navigationsbaum auf **[!UICONTROL Profile und Zielgruppen > Empfänger]** haben Sie Zugriff auf eine erweiterte Ansicht der Empfängerliste. Es besteht die Möglichkeit, sie Ihren Bedürfnissen entsprechend anzupassen. Sie können beispielsweise Spalten hinzufügen oder löschen und ihre Reihenfolge festlegen und Daten sortieren. Die Konfiguration der Listenansicht wird auf [dieser Seite](../../platform/using/adobe-campaign-ui-lists.md) beschrieben.
>
>Sie können auch Empfängeransichten definieren. Weiterführende Informationen zu dieser Funktion finden Sie in [diesem Abschnitt](../../platform/using/access-management-folders.md).

## Aktive Profile {#active-profiles}

Aktive Profile sind die Profile, die zu Fakturierungszwecken berücksichtigt werden.

Für die Fakturierung werden nur **aktive** Profile berücksichtigt. Ein Profil wird als aktiv betrachtet, wenn es in den vergangenen zwölf Monaten über einen beliebigen Kanal angesprochen wurde oder mit ihm kommuniziert wurde.

Ein Profil, das für mehrere Sendungen ausgewählt wurde, wird nur einmal gezählt.

>[!NOTE]
>
>Die Kanäle Facebook und X (früher bekannt als Twitter) werden nicht berücksichtigt.

Die Anzahl der aktiven Profile ist nur für **Marketing-Instanzen** verfügbar. Sie ist nicht für Ausführungsinstanzen verfügbar, d. h. MID (Mid-Sourcing)- und RT (Message Center-/Echtzeit-Messaging)-Instanzen.

>[!NOTE]
>
>Sie können auch die Anzahl der aktiven Profile in Ihrer Instanz direkt über das Control Panel von Campaign überwachen. Weitere Informationen hierzu finden Sie in der [Dokumentation zu Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=de).

## Anleitungsvideo {#create-profiles-video}

Erfahren Sie, wie Sie auf Profildaten zugreifen, Profile sortieren und filtern und Profile manuell erstellen und verwalten können.

In diesem Video wird auch die Einhaltung der Datenschutz-Grundverordnung durch Adobe Campaign Classic erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

**Siehe auch**

* [Datenschutzverwaltung in Campaign](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html)

* [Bestimmen der Zielpopulation](../../delivery/using/define-the-right-audience.md)

* [Erstellen von Abfragen und Segmentdaten in Workflows](../../workflow/using/targeting-data.md)

* [Auswählen von Zielgruppen-Mapping](../../delivery/using/selecting-a-target-mapping.md)

* [Bestimmen der Audience – Best Practices](../../delivery/using/define-the-right-audience.md)
