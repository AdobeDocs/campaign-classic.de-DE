---
product: campaign
title: Verwalten von Datenschutzanfragen
description: Erfahren Sie mehr über Datenschutzanfragen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '530'
ht-degree: 100%

---

# Datenschutzanfragen {#privacy-requests}



Allgemeine Informationen zum Thema Datenschutzverwaltung finden Sie in [diesem Abschnitt](privacy-management.md).

Diese Informationen gelten für DSGVO, CCPA, PDPA und LGPD. Weitere Informationen zu diesen Verordnungen finden Sie in [diesem Abschnitt](privacy-management.md#privacy-management-regulations).

>[!NOTE]
>
>Die Möglichkeit zum Opt-out aus dem Verkauf von personenbezogenen Daten, die sich speziell auf den CCPA bezieht, wird in [diesem Abschnitt](#sale-of-personal-information-ccpa) erläutert.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Um Sie bei der Einhaltung der Datenschutzverordnungen zu unterstützen, ermöglicht Ihnen Adobe Campaign die Durchführung von Zugriffs- und Löschanfragen. Das **Recht auf Zugriff** und das **Recht auf Vergessenwerden** (Löschanfrage) werden in [diesem Abschnitt](privacy-management.md#right-access-forgotten) beschrieben.

Adobe Campaign bietet Datenverantwortlichen zwei Möglichkeiten zur Durchführung von Zugriffs- und Löschanfragen:

* Über die **Adobe Campaign-Benutzeroberfläche**: Für jede Datenschutzanfrage erstellt der Datenverantwortliche eine neue Datenschutzanfrage in Adobe Campaign. Siehe [diesen Abschnitt](privacy-requests-ui.md).
* Über die **API**: Adobe Campaign verfügt über eine API, mit der Datenschutzanfragen automatisch per SOAP verarbeitet werden können. Siehe [diesen Abschnitt](privacy-requests-api.md).

>[!NOTE]
>
>Weitere Informationen zu personenbezogenen Daten und zu den verschiedenen Entitäten, die Daten verwalten (Datenverantwortlicher, Auftragsverarbeiter und betroffene Person), finden Sie unter [Personenbezogene Daten und Personas](privacy-and-recommendations.md#personal-data).

## Voraussetzungen {#prerequesites}

Adobe Campaign bietet Datenverantwortlichen Tools zum Erstellen und Verarbeiten von Datenschutzanfragen für in Adobe Campaign gespeicherte Daten. Für den Kontakt mit den betroffenen Personen ist jedoch der Datenverantwortliche allein zuständig (über E-Mail, Kundenunterstützung oder ein Web-Portal).

Als Datenverantwortlicher sind Sie daher außerdem verpflichtet, die Identität der betroffenen Person zu überprüfen, die die Anfrage stellt, und sicherzustellen, dass die dem Anfragenden übermittelten Daten zur betroffenen Person gehören.

## Installieren des Datenschutz-Package {#install-privacy-package}

Um diese Funktion nutzen zu können, müssen Sie das Package **[!UICONTROL Datenschutzbestimmung]** über das Menü **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]** > **[!UICONTROL Adobe-Campaign-Package]** installieren. Weitere Informationen zum Installieren von Packages finden Sie im [entsprechenden Handbuch](../../installation/using/installing-campaign-standard-packages.md).

Zwei neue speziell für den Datenschutz vorgesehene Ordner werden unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** erstellt:

* **[!UICONTROL Datenschutzanfragen]**: In diesem Ordner erstellen Sie Ihre Datenschutzanfragen und verfolgen ihren Verlauf.
* **[!UICONTROL Namespaces]**: Hier definieren Sie das Feld, das zur Identifikation der betroffenen Person in der Adobe Campaign-Datenbank herangezogen wird.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]** werden täglich drei technische Workflows ausgeführt, um Datenschutzanfragen zu verarbeiten.

![](assets/privacy-workflows.png)

* **[!UICONTROL Datenschutzanfragen erfassen]**: Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten abgerufen und im Datenschutzanfrage-Fenster für den Download bereitgestellt.
* **[!UICONTROL Datenschutz-Anfragedaten löschen]**: Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten gelöscht.
* **[!UICONTROL Bereinigung der Datenschutzanfrage]**: Mit diesem Workflow werden Zugriffsanfragedateien gelöscht, die älter als 90 Tage sind.

Unter **[!UICONTROL Administration]** > **[!UICONTROL Zugriffe]** > **[!UICONTROL Spezifische Berechtigungen]** wurde die Berechtigung **[!UICONTROL Datenschutzrecht]** hinzugefügt. Datenverantwortliche benötigen diese spezifische Berechtigung, um Datenschutz-Tools verwenden zu können. Damit können Sie neue Anfragen erstellen, ihren Verlauf verfolgen, die API verwenden etc.

![](assets/privacy-right.png)

## Namespaces {#namesspaces}

Bevor Sie Datenschutzanfragen erstellen können, müssen Sie den Namespace definieren, den Sie verwenden möchten. Dies ist der Schlüssel, der zur Identifikation der betroffenen Person in der Adobe Campaign-Datenbank herangezogen wird.

Standardmäßig sind drei Namespaces verfügbar: E-Mail, Telefon und Mobiltelefon. Wenn Sie einen anderen Namespace benötigen (z. B. ein benutzerdefiniertes Empfängerfeld), können Sie unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Namespaces]** einen neuen erstellen.

>[!NOTE]
>
>Für optimale Leistung wird empfohlen, vordefinierte Namespaces zu verwenden.
