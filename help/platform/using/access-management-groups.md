---
product: campaign
title: Erstellen und Verwalten von Benutzergruppen
description: Erfahren Sie, wie Sie Benutzergruppen Zugriff gewähren.
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
TQID: https://experienceleague.adobe.com/FZhH7zDL3g3tG8Ar40XJQWE-2O9Rs5-KD-NliQ6wH3M
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 620
ht-degree: 88%

---

# Erstellen und Verwalten von Benutzergruppen {#operator-groups}

>[!NOTE]
>
>Diese Verfahren gelten nur für Benutzende, die mit **nativer Authentifizierung der Vorgängerversion** eine Verbindung zu Campaign herstellen. Ab Campaign Classic v7.3.1 sollten alle Benutzenden das [Adobe-Identitäts-Management-System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} verwenden, um eine Verbindung mit Campaign herzustellen. [Weitere Informationen](../../technotes/using/migrate-users-to-ims.md)
>
>Wenn Sie die Verbindung zu Campaign mit Ihrer Adobe ID herstellen, gilt der folgende Abschnitt nicht mehr. In der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=de){target="_blank"} erfahren Sie, wie Sie Berechtigungen mit Adobe IMS einrichten können.

Benutzergruppen werden über den Verzeichnisknoten **[!UICONTROL Administration > Zugriffe > Benutzergruppen]** erstellt.

## Erstellen einer neuen Benutzergruppe {#creating-a-new-operator-group}

Gehen Sie wie folgt vor, um eine neue Benutzergruppe zu erstellen:

1. Klicken Sie oberhalb der Gruppenliste auf die Schaltfläche **[!UICONTROL Neu]** oder klicken Sie mit der rechten Maustaste auf die Liste und wählen Sie **[!UICONTROL Neu]**.
1. Geben Sie im unteren Bereich des Fensters im Tab **[!UICONTROL Allgemein]** den Namen und die Beschreibung der Gruppe in die entsprechenden Felder ein.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klicken Sie auf den Tab **[!UICONTROL Inhalt]**, um der Gruppe Berechtigungen einzuräumen.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um spezifische Berechtigungen oder Benutzer auszuwählen, die der Gruppe hinzugefügt werden sollen.
1. Klicken Sie auf die Dropdown-Liste oder auf das Ordnersymbol rechts neben dem Feld **[!UICONTROL Ordner]**, um die der Gruppe zuzuordnenden spezifischen Berechtigungen oder Benutzer zu lokalisieren und anzuzeigen.
1. Wählen Sie die hinzuzufügenden Berechtigungen oder Benutzer aus und klicken Sie zum Bestätigen auf **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Wiederholen Sie diese Schritte, um weitere Berechtigungen oder Benutzer hinzuzufügen.

1. Klicken Sie abschließend auf die Schaltfläche **[!UICONTROL Speichern]**, um die Gruppe der Liste hinzuzufügen.

## Standardgruppen {#default-groups}

Es existieren folgende Standardgruppen:

1. **[!UICONTROL Administrator]**

   Die Benutzer in dieser Gruppe haben vollen Zugriff auf die Instanz. Administratoren sind Benutzer, die Zugriff auf die meisten technischen Elemente der Benutzeroberfläche haben. Sie haben die **[!UICONTROL Administratorrolle]** inne und stellen sicher, dass die Plattform vollständig eingerichtet ist.

   Die Gruppe beinhaltet die folgende spezifische Berechtigung:

   * **[!UICONTROL ADMINISTRATION]**: Berechtigt zum Ausführen, Erstellen, Bearbeiten und Löschen von Objekten wie Workflows, Sendungen, Skripten usw.

1. **[!UICONTROL Versandverantwortliche Benutzer]**

   Die Benutzer dieser Gruppe sind für die Versandverwaltung verantwortlich. Die Gruppe verleiht Zugriff auf die für die Erstellung und Vorbereitung von Sendungen notwendigen Hauptressourcen (Kampagnentypologien, Versandmappings, Standardvorlagen, Gestaltungsbausteine etc.).

   Die Gruppe beinhaltet folgende spezifische Berechtigungen:

   * **[!UICONTROL SENDUNGEN VORBEREITEN]**: Berechtigt zum Erstellen, Bearbeiten und Starten der Versandanalyse;
   * **[!UICONTROL SENDUNGEN STARTEN]**: Berechtigt zur Validierung von zuvor analysierten Sendungen.

1. **[!UICONTROL Kampagnenverantwortliche Benutzer]**

   Die Benutzer dieser Gruppe können Marketing-Kampagnen verwalten: Über sie können Sie auf die mit Kampagnen verknüpften Objekte zugreifen (Pläne, Programme, Workflows, Budgets usw.) im Rahmen von **[!UICONTROL Campaign]** (optionales Adobe Campaign-Modul).

   Die Gruppe beinhaltet folgende spezifische Berechtigungen:

   * **[!UICONTROL EINFÜGEN VON ORDNERN]**: Berechtigt zum Einfügen von Ordnern in den Adobe Campaign-Navigationsbaum (erfordert Schreibzugriff für betroffene Zweige);
   * **[!UICONTROL WORKFLOW]**: Berechtigt zur Nutzung von Workflows.

   >[!NOTE]
   >
   >Benutzer dieser Gruppe können keine Sendungen starten.

1. **[!UICONTROL Autoren]**

   Die Benutzer dieser Gruppe können auf die Inhaltsordner im Rahmen von **[!UICONTROL Content-Management“ zugreifen]** optionales Adobe Campaign-Modul). Diese Gruppe gewährt keine zusätzlichen Rechte.

1. **[!UICONTROL Berichtzugriff]**

   Diese Gruppe ist externen Benutzenden vorbehalten, um die Symbole für Bericht, Zeitplan und Forum im Kampagnen-Dashboard für bestimmte Benutzende zu aktivieren.

1. **[!UICONTROL Workflow-Ausführung]**

   Diese Gruppe verleiht Benutzern die Berechtigung, die von Kampagnen unabhängigen Workflows zu verwalten.

1. **[!UICONTROL Workflow-Verantwortliche]**

   Die Benutzer dieser Gruppe werden im Falle von Meldungen bezüglich Kampagnen-Workflows per E-Mail benachrichtigt.

1. Lokale/Zentrale Verwaltung

   Diese Gruppen ermöglichen den Einsatz des **[!UICONTROL Dezentralen Marketings]** (optionales Adobe Campaign-Modul).

1. **[!UICONTROL Angebotsverantwortliche Benutzer]**

   Die Benutzer dieser Gruppe können Angebote erstellen und verwalten. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../interaction/using/operator-profiles.md).
Diese Gruppe enthält die folgenden spezifischen Berechtigungen:

   * **[!UICONTROL EINFÜGEN VON ORDNERN]**: Berechtigt zum Einfügen von Ordnern in den Adobe Campaign-Navigationsbaum (erfordert Schreibzugriff für betroffene Zweige);
   * **[!UICONTROL BEARBEITUNG VON ORDNERN]**: Berechtigt zum Ändern von Ordnereigenschaften wie interner Name, Titel, verknüpftes Bild, Reihenfolge der Unterordner usw.
