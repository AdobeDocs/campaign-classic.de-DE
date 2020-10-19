---
title: Berichteigenschaften
description: Weitere Informationen zu den Berichtseigenschaften
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: b0b9a0714075474bf52c3eed78d45bcef25b44fc
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 41%

---


# Berichteigenschaften{#properties-of-the-report}

Sie können Ihren Bericht ganz nach Ihren Bedürfnissen personalisieren und konfigurieren. Bearbeiten Sie dazu die Eigenschaften. Auf Berichteigenschaften wird über die Schaltfläche **[!UICONTROL Eigenschaften]** über dem Diagramm für die Aktivität zugegriffen.

![](assets/s_ncs_advuser_report_properties_01.png)

Allgemeine Eigenschaften werden nachfolgend beschrieben. Die erweiterten Funktionen, die auf den Registerkarten **[!UICONTROL Parameter]**, **[!UICONTROL Variablen]** und **[!UICONTROL Skripten]** konfiguriert wurden, werden [in diesem Abschnitt](../../reporting/using/advanced-functionalities.md)beschrieben.

## Allgemeine Eigenschaften {#overall-properties}

Auf der Registerkarte &quot; **[!UICONTROL Allgemein]** &quot;der Berichtseigenschaften können Sie die unten aufgeführten Einstellungen bearbeiten:

* Die Bezeichnung und der interne Name des Berichts. Der **[!UICONTROL interne Name]** wird in der endgültigen URL des Berichts verwendet. Sie sollte nach der Berichterstellung nicht mehr geändert werden.

* Der **Berichtsordner** wird bei der Berichterstellung ausgewählt. Es empfiehlt sich, einen eigenen Ordner für benutzerspezifische Berichte zu erstellen, damit diese nicht mit [integrierten Berichten](../../reporting/using/about-campaign-built-in-reports.md)gemischt werden.

* Die **Datenspeicherung** wird beim Erstellen des Berichts ausgewählt. Um die Datentabelle des Berichts zu ändern, klicken Sie auf das Symbol Link **** auswählen rechts neben dem Feld **[!UICONTROL Dokument]** .

   ![](assets/s_ncs_advuser_report_properties_02.png)

* Die **Zugriffskontrolle** -Parameter. Diese Einstellungen werden nachfolgend beschrieben.

## Controlling access to the report {#report-accessibility}

Auf einen Bericht kann über die Adobe Campaign-Konsole oder einen Webbrowser zugegriffen werden. In diesem Fall kann es erforderlich sein, die Zugriffskontrolle des Berichts wie unten dargestellt zu konfigurieren.

![](assets/s_ncs_advuser_report_properties_02b.png)

Mögliche Optionen sind:

* **[!UICONTROL Anonymer Zugriff]**: Diese Option ermöglicht uneingeschränkten Zugriff auf den Bericht. Manipulation ist jedoch nicht möglich.

   Die Rechte des technischen Betreibers &quot;webapp&quot;werden zur Anzeige von Berichtselementen verwendet. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../platform/using/access-management.md#default-operators).

* **[!UICONTROL Zugriffskontrolle]**: Diese Option ermöglicht es Adobe Campaign-Operatoren, darauf zuzugreifen, sobald sie angemeldet sind.
* **[!UICONTROL Spezifisches Konto]**: Mit dieser Option können Sie den Bericht mit den Rechten des Operators ausführen, die im Feld **[!UICONTROL Operator]** ausgewählt sind.

## Berichtlokalisierung verwalten {#managing-report-localization}

Die Sprachen, in die der Bericht übersetzt werden soll, können konfiguriert werden. Klicken Sie hierzu auf den Tab **[!UICONTROL Lokalisierung]**.

![](assets/s_ncs_advuser_report_properties_06.png)

Die Arbeitssprache entspricht der Sprache, in der Sie den Bericht verfassen. Beim Hinzufügen einer Sprache erscheint ein Untertab der Bearbeitungsseite des Berichts.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Weitere Informationen zur lokale Anpassung von Webseiten in der Kampagne finden Sie in [diesem Abschnitt](../../web/using/translating-a-web-form.md).

## HTML-Rendering anpassen {#personalizing-html-rendering}

Im Tab **[!UICONTROL Rendering]** haben Sie die Möglichkeit, den Anzeigemodus der Daten auf der Seite anzupassen. Folgende Elemente können ausgewählt werden:

* Die Rendering-Engine für Grafiken: Adobe Campaign bietet zwei verschiedene Modi zur Erzeugung des Grafik-Renderings. Die Standard-Rendering-Engine ist HTML 5. Bei Bedarf kann ein Flash-Rendering gewählt werden.
* Die Navigation im Bericht: über Schaltflächen oder Links.
* Die Standardposition der Titel der Berichtelemente. Die Position kann auf Ebene jedes Elements überschrieben werden.
* Die Vorlage oder das Thema, das zur Erzeugung der Berichtseiten verwendet wird.

![](assets/s_ncs_advuser_report_properties_08.png)

## Fehlerseite anpassen {#personalizing-the-error-page}

Im Tab **[!UICONTROL Fehlerseite]** können Sie die Nachricht anpassen, die im Falle eines Fehlers bei der Berichtanzeige erscheint.

Sie können Texte verfassen und diesen Kennungen zuordnen, die für die Berichtlokalisierung erforderlich sind. Weitere Informationen hierzu finden Sie unter [Header und Footer hinzufügen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
