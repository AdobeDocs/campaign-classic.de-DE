---
title: Über Profile
seo-title: Über Profile
description: Über Profile
seo-description: null
page-status-flag: never-activated
uuid: 9a3fcb58-a356-4eee-bc26-c64825de5f99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 5addada8-0185-488f-9825-83f60981c139
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Über Profile{#about-profiles}

## Profiltypen {#profile-types}

Die Adobe-Campaign-Plattform ermöglicht die Verwaltung von Profilen über den gesamten Zyklus hinweg, von der Erstellung oder dem Import über Zielgruppenbestimmung und Tracking bis hin zur Aktualisierung und anderen Aktivitäten.

Ein Profil entspricht einem Datensatz in der Datenbank, der alle nötigen Informationen enthält, um einen Kontakt zu qualifizieren, zu verfolgen und in Zielgruppen einzubeziehen.

Profile können verschiedenen Kategorien zugeteilt werden, welche sich im Speicherort widerspiegeln, zum Beispiel: einem Empfänger, einem Besucher, einem Benutzer, einem Abonnenten, einem Interessenten usw.

## Empfängerprofile {#recipient-profiles}

Versandempfänger werden in der Datenbank in Form von Profilen mit den entsprechenden Informationen – Nachname, Vorname, Adressdaten, Abonnements, Sendungen etc. – gespeichert. Sendungen innerhalb von Marketingkampagnen können sich an Empfängergruppen aus der Datenbank richten, die nach bestimmten – einfachen oder komplexen – Kriterien erstellt werden.

Eine weitere Möglichkeit besteht darin, Kampagnen für Profile zu erstellen, die nicht in der Datenbank, sondern in Dateien enthalten sind. In diesem Fall handelt es sich um s. g. externe Sendungen. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Die gängigsten Methoden der Profilerstellung sind:

* direkte Erfassung in der Benutzeroberfläche,
* Import von Profildateien,
* Online-Akquise über Webformulare.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/generic-imports-and-exports.md).

## Profile und Zielgruppen {#profiles-and-targets}

Über den **[!UICONTROL Profiles and targets]** Link können Sie Empfänger anzeigen, die in der Adobe Campaign-Datenbank gespeichert sind. Sie können einen neuen Empfänger erstellen, einen vorhandenen Empfänger bearbeiten und auf sein Profil zugreifen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Außerdem haben Sie an dieser Stelle Zugriff auf:

* Listen; siehe [Erstellen und Verwalten von Listen](../../platform/using/creating-and-managing-lists.md),
* Anmeldedienste; siehe [diese Seite](../../delivery/using/managing-subscriptions.md),
* Webanwendungen; siehe [diese Seite](../../web/using/about-web-applications.md),
* Einfuhren und Ausfuhren (Arbeitsplätze); auf [allgemeine Ein- und Ausfuhren](../../platform/using/generic-imports-and-exports.md),
* Zielgruppen-Workflow; siehe [diese Seite](../../workflow/using/building-a-workflow.md#implementation-steps-),

Über die Empfängerseite sind die gängigsten Aktionen möglich. Sie können Profile bearbeiten, aktualisieren, sortieren, löschen oder neue Profile erstellen.

Für erweiterte Profilmanipulationen müssen Sie die Adobe Campaign-Struktur bearbeiten. Klicken Sie dazu auf den **[!UICONTROL Explorer]** Link auf der Adobe Campaign-Homepage.

Standardmäßig werden Empfänger im **[!UICONTROL Profiles and Targets > Recipients]** Knoten des Baums gespeichert. Sie können Empfänger aus dieser Ansicht erstellen sowie:

* sort and filter the profiles of the database; see [Filtering options](../../platform/using/filtering-options.md),
* move, copy or delete profiles from the database; see [Managing profiles](../../platform/using/managing-profiles.md),
* Aktualisierungsprofile; siehe [Aktualisieren von Daten](../../platform/using/updating-data.md),
* Empfänger; siehe [Profile](../../platform/using/exporting-and-importing-profiles.md)exportieren und importieren,
* Empfängergruppen erstellen; Siehe [Erstellen und Verwalten von Listen](../../platform/using/creating-and-managing-lists.md).

Erweiterte Funktionen und Konfigurationsmöglichkeiten stehen ausschließlich über den **[!UICONTROL Explorer]** zur Verfügung.

![](assets/d_ncs_user_interface01.png)

Das allgemeine Layout des Adobe Campaign-Explorers wird in [Verwenden des Adobe Campaign-Explorers](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)dargestellt.

>[!NOTE]
>
>Sie können eine erweiterte Ansicht dieser Liste auch in der Adobe Campaign-Struktur anzeigen, indem Sie auf den **[!UICONTROL Profiles and targets > Recipients]** Link klicken. Die Listenanzeige kann entsprechend Ihren Anforderungen konfiguriert werden. Sie können Spalten hinzufügen oder löschen, die Spaltenreihenfolge definieren, Daten sortieren usw. Die Konfiguration der Listenanzeige wird unter [Verwenden des Adobe Campaign-Explorers](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)beschrieben.
>
>Sie können auch Empfänger-Ansichten definieren. Weitere Informationen zu dieser Funktion finden Sie unter [Ordner und Ansichten](../../platform/using/access-management.md#folders-and-views).

## Aktive Profile {#active-profiles}

Aktive Profile sind die Profile, die zu Fakturierungszwecken berücksichtigt werden.

**Profil** bezeichnet einen Datensatz, der einen Endkunden, einen Prospect oder Lead repräsentiert. Bei diesen Daten kann es sich z. B. um einen Datensatz in der nmsRecipient-Tabelle oder einer externen Tabelle handeln, die die Kennung eines Cookies, eines Kunden oder eines Mobiltelefons oder andere für einen bestimmten Kanal relevante Informationen enthält.

Für die Fakturierung werden nur **aktive** Profile berücksichtigt. Ein Profil wird als aktiv erachtet, wenn es in den vergangenen zwölf Monaten über einen beliebigen Kanal angesprochen wurde oder mit ihm kommuniziert wurde.

>[!NOTE]
>
>Die Kanäle Facebook und Twitter werden nicht berücksichtigt.

Sie können sich einen Überblick über das **[!UICONTROL Number of active profiles]** Menü **[!UICONTROL Administration > Campaign Management > Customer metrics]** verschaffen.

Die tatsächliche Anzahl wird durch den **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [technischen Arbeitsablauf](../../workflow/using/delivery.md)ausgeführt, der täglich ausgeführt wird und die neuen Daten dem vorhandenen Bericht für den aktuellen Zeitraum im **[!UICONTROL Customer metrics]** Menü hinzufügt. Jeder Zeitraum dauert 12 Monate.

Die Profile, die während der Versandvorbereitung ausgeschlossen wurden (Typologieregeln, Quarantänen), werden nicht berücksichtigt. Ein Profil, das mehrere Sendungen erhalten hat, wird nur einmal gezählt.
