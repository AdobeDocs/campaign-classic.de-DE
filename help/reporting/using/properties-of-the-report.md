---
product: campaign
title: Berichteigenschaften
description: Weiterführende Informationen zu den Einstellungen der Berichteigenschaften
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
TQID: https://experienceleague.adobe.com/NAcXKBNoDJRopQf-QpqnFhwxFRvvScp7xShJotE0s1A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: cc72dcf1-72e1-48cc-b434-e7c27d62d67c
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 462
ht-degree: 100%

---

# Berichteigenschaften{#properties-of-the-report}



Sie können Ihren Bericht ganz nach Bedarf personalisieren und konfigurieren. Bearbeiten Sie dazu seine Eigenschaften. Auf Berichteigenschaften können Sie mit der Schaltfläche **[!UICONTROL Eigenschaften]** über dem Diagramm für Aktivitätsabfolgen zugreifen.

![](assets/s_ncs_advuser_report_properties_01.png)

Allgemeine Eigenschaften werden nachfolgend beschrieben. Erweiterte Funktionen, die sich auf den Tabs **[!UICONTROL Parameter]**, **[!UICONTROL Variablen]** und **[!UICONTROL Scripts]** konfigurieren lassen, werden [in diesem Abschnitt](../../reporting/using/advanced-functionalities.md) beschrieben.

## Allgemeine Eigenschaften {#overall-properties}

Auf dem Tab **[!UICONTROL Allgemein]** der Berichteigenschaften können Sie die folgenden Einstellungen bearbeiten:

* Titel und interner Berichtsname. Der **[!UICONTROL interne Name]** wird in der endgültigen URL des Berichts verwendet. Er sollte nach der Berichterstellung nicht mehr geändert werden.

* Der **Ordner** des Berichts wird bei der Berichterstellung ausgewählt. Es empfiehlt sich, für benutzerspezifische Berichte einen eigenen Ordner zu erstellen, damit diese nicht mit [integrierten Berichten](../../reporting/using/about-campaign-built-in-reports.md) vermischt werden.

* Die **Speicherung** wird beim Erstellen des Berichts ausgewählt. Um die Datentabelle des Berichts zu ändern, klicken Sie auf das Symbol **[!UICONTROL Verknüpftes Element auswählen]** rechts neben dem Feld **[!UICONTROL Dokumenttyp]**.

  ![](assets/s_ncs_advuser_report_properties_02.png)

* Die Parameter der **Zugriffskontrolle**. Diese Einstellungen werden nachfolgend beschrieben.

## Kontrollieren des Zugriffs auf den Bericht {#report-accessibility}

Auf einen Bericht kann über die Adobe Campaign-Konsole oder einen Webbrowser zugegriffen werden. In dem Fall kann es erforderlich sein, wie unten dargestellt die Zugriffskontrolle für den Bericht zu konfigurieren.

![](assets/s_ncs_advuser_report_properties_02b.png)

Mögliche Optionen sind:

* **[!UICONTROL Anonymer Zugriff]**: Diese Option bietet uneingeschränkten Zugriff auf den Bericht. Eine Bearbeitung ist jedoch nicht möglich.

  Die Anzeige der Berichtelemente hängt von den Berechtigungen des technischen &quot;webapp&quot;-Benutzers ab. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../platform/using/access-management-operators.md).

* **[!UICONTROL Zugriffskontrolle]**: Diese Option bietet Adobe Campaign-Benutzern nach der Anmeldung Zugriff auf den Bericht.
* **[!UICONTROL Spezifisches Konto nutzen]**: Diese Option ermöglicht die Ausführung des Berichts mit den Berechtigungen des im Feld **[!UICONTROL Benutzer]** ausgewählten Benutzers.

## Übersetzen des Berichts {#report-localization}

Die Sprachen, in die der Bericht übersetzt werden soll, können konfiguriert werden. Klicken Sie hierzu auf den Tab **[!UICONTROL Lokalisierung]**.

![](assets/s_ncs_advuser_report_properties_06.png)

Die Bearbeitungssprache ist die Sprache, in der Sie schreiben. Beim Hinzufügen einer Sprache erscheint eine Unterregisterkarte in der Bearbeitungsseite des Berichts.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Weiterführende Informationen zur Lokalisierung von Web-Seiten in Campaign finden Sie in [diesem Abschnitt](../../web/using/translating-a-web-form.md).

## Personalisieren des HTML-Renderings {#personalizing-html-rendering}

In der Registerkarte **[!UICONTROL Rendering]** können Sie den Anzeigemodus der Daten auf der Seite anpassen. Sie können Folgendes auswählen:

* Die Navigation im Bericht: über Schaltflächen oder Links.
* Die Standardposition der Titel der Berichtelemente. Die Position kann für jedes Element überschrieben werden.
* Die Vorlage oder das Thema, das zur Erzeugung der Berichtseiten verwendet wird.

![](assets/s_ncs_advuser_report_properties_08.png)

## Fehlerseite anpassen {#personalizing-the-error-page}

Im Tab **[!UICONTROL Fehlerseite]** können Sie die Nachricht anpassen, die im Falle eines Fehlers bei der Berichtanzeige erscheint.

Sie können Texte verfassen und diesen Kennungen zuordnen, die für die Berichtlokalisierung erforderlich sind. Weitere Informationen hierzu finden Sie unter [Header und Footer hinzufügen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
