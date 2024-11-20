---
product: campaign
title: Erste Schritte mit Profilen
description: Arbeiten mit Profilen in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: ht
source-wordcount: '909'
ht-degree: 100%

---

# Erste Schritte mit Profilen{#about-profiles}



Alle Profile werden in der Adobe Campaign-Datenbank zentral gespeichert. Die Akquise von Profilen und die Datenbankerstellung können auf verschiedenste Weisen erfolgen: Online-Akquise über Web-Formulare, manueller oder automatisierter Import von Textdateien, Replikation von bereits existierenden Datenbanken oder Informationssystemen des Unternehmens. Mit Adobe Campaign können Sie Marketing-Verlauf, Kaufinformationen, Voreinstellungen, CRM-Daten und alle relevanten PI-Daten in eine konsolidierte Ansicht integrieren, um sie zu analysieren und Maßnahmen zu ergreifen.

**Profil** bezeichnet einen Eintrag, der eine Endkundin bzw. einen Endkunden, eine Interessentin bzw. einen Interessenten oder einen Lead repräsentiert. Bei diesen Daten kann es sich z. B. um einen Eintrag in der nmsRecipient-Tabelle oder einer externen Tabelle handeln, die die Kennung eines Cookies, einer Kundin bzw. eines Kunden oder eines Mobiltelefons oder andere für einen bestimmten Kanal relevante Informationen enthält.

In Adobe Campaign sind die Standardprofile für Sendungen (E-Mails, SMS usw.) die Empfänger. Mit den in der Datenbank gespeicherten Empfängerdaten können Sie die Zielgruppe filtern, die einen bestimmten Versand erhalten soll, und Personalisierungsdaten in den Versandinhalt einfügen. In der Datenbank gibt es noch andere Arten von Profilen. Sie sind für unterschiedliche Zwecke gedacht. So werden beispielsweise Testprofile erstellt, um Ihre Sendungen zu testen, bevor sie an die endgültige Zielgruppe gesendet werden.

![](assets/do-not-localize/how-to-video.png) [Informationen zum Profilkonzept finden Sie in diesem Video](#create-profiles-video)

## Profiltypen {#profile-types}

Die Adobe Campaign-Plattform ermöglicht die Verwaltung von Profilen über den gesamten Zyklus hinweg, von der Erstellung oder dem Import über Zielgruppenbestimmung und Tracking bis hin zur Aktualisierung und anderen Aktivitäten.

Ein Profil entspricht einem Datensatz in der Datenbank, der alle nötigen Informationen enthält, um einen Kontakt zu qualifizieren, zu verfolgen und in Zielgruppen einzubeziehen.

Profile können verschiedenen Kategorien zugeteilt werden, welche sich im Speicherort widerspiegeln, zum Beispiel: einem Empfänger, einem Besucher, einem Benutzer, einem Abonnenten, einem Interessenten usw.

## Empfängerprofile {#recipient-profiles}

Versandempfänger werden in der Datenbank in Form von Profilen mit den entsprechenden Informationen – Nachname, Vorname, Adressdaten, Abonnements, Sendungen etc. – gespeichert. Sendungen innerhalb von Marketingkampagnen können sich an Empfängergruppen aus der Datenbank richten, die nach bestimmten – einfachen oder komplexen – Kriterien erstellt werden.

Sie können auch Kampagnen für Empfangende erstellen, deren Profile nicht in der Datenbank, sondern in Dateien gespeichert sind. Diese werden als „externe“ Sendungen bezeichnet. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Die gängigsten Methoden der Profilerstellung sind:

* direkte Erfassung in der Benutzeroberfläche,
* Import von Profildateien,
* Online-Akquise über Webformulare.

>[!NOTE]
>
>Dateiimport und Webformulare werden im Abschnitt [Allgemeine Importe und Exporte](../../platform/using/get-started-data-import-export.md) vorgestellt.

## Profile und Zielgruppen {#profiles-and-targets}

Über den Link **[!UICONTROL Profile und Zielgruppen]** können Sie in der Adobe Campaign-Datenbank enthaltene Empfängerprofile anzeigen. Sie können neue Empfängerprofile erstellen, bestehende bearbeiten und auf Profile zugreifen. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Außerdem haben Sie an dieser Stelle Zugriff auf:

* Listen – [Mehr dazu](../../platform/using/creating-and-managing-lists.md)
* Anmeldedienste – [Mehr dazu](../../delivery/using/managing-subscriptions.md)
* Web-Programme – [Mehr dazu](../../web/using/about-web-applications.md)
* Importe und Exporte (Vorgänge) – [Mehr dazu](../../platform/using/about-generic-imports-exports.md)
* Zielgruppen-Workflows – [Mehr dazu](../../workflow/using/building-a-workflow.md#implementation-steps-)

Über die Empfängerseite sind die gängigsten Aktionen möglich. Sie können Profile bearbeiten, aktualisieren, sortieren, löschen oder neue Profile erstellen.

Erweiterte Funktionalitäten stehen über den Navigationsbaum zur Verfügung. Klicken Sie hierfür auf die **[!UICONTROL Explorer]**-Schaltfläche in der Symbolleiste der Adobe Campaign-Startseite.

Standardmäßig werden Empfänger in der Baumstruktur im Knoten **[!UICONTROL Profile und Zielgruppen > Empfänger]** gespeichert. Sie können Empfangende aus dieser Ansicht erstellen sowie:

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

Ein aktives Profil ist ein Profil, mit dem die Kundin oder der Kunde in den letzten 12 Monaten über einen beliebigen Kanal versucht hat, zu kommunizieren.

Gemäß Ihrem Vertrag erhalten alle Ihre Campaign-Instanzen eine bestimmte Anzahl aktiver Profile, die zu Abrechnungszwecken gezählt werden. Informationen zur Anzahl der gekauften aktiven Profile finden Sie in Ihrem aktuellen Vertrag. Weitere Informationen finden Sie in der [Adobe Campaign-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Sie können die Anzahl der aktiven Profile in Ihrer Instanz direkt über das Control Panel von Campaign überwachen. Weitere Informationen hierzu finden Sie in der [Dokumentation zu Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=de){target="_blank"}.

Es gelten die folgenden Schutzmechanismen und Einschränkungen:

* Ein Profil, das durch mehrere Sendungen angesprochen wurde, wird nur einmal gezählt.
* Profile, die im Rahmen von Social-Media-Marketing auf X (Twitter) oder Facebook angesprochen werden, werden nicht als aktive Profile berücksichtigt.
* Die Zählung aktiver Profile ist nur für **Marketing-Instanzen** verfügbar. Sie ist nicht für Ausführungsinstanzen verfügbar, d. h. MID (Mid-Sourcing)- und RT (Message Center-/Echtzeit-Messaging)-Instanzen.
* Die Anzahl basiert auf dem Primärschlüssel der Empfängerin bzw. des Empfängers. Wenn also ein Profil in zwei verschiedenen Empfängertabellen vorhanden ist, kann es zweimal als aktives Profil gezählt werden.


## Anleitungsvideo {#create-profiles-video}

Erfahren Sie, wie Sie auf Profildaten zugreifen, Profile sortieren und filtern und Profile manuell erstellen und verwalten können.

In diesem Video wird auch die Einhaltung der Datenschutz-Grundverordnung durch Adobe Campaign Classic erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

**Siehe auch**

* [Datenschutzverwaltung in Campaign](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html)

* [Erstellen von Abfragen und Segmentdaten in Workflows](../../workflow/using/targeting-data.md)

* [Auswählen von Zielgruppen-Mapping](../../delivery/using/selecting-a-target-mapping.md)
