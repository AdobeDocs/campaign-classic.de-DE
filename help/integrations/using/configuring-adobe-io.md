---
product: campaign
title: Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers
description: Erfahren Sie, wie Sie Adobe I/O für Adobe Experience Cloud Triggers konfigurieren.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 100%

---

# Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers {#configuring-adobe-io}



>[!CAUTION]
>
>Wenn Sie eine ältere Version der Triggers-Integration über die OAuth-Authentifizierung verwenden, **müssen Sie wie unten beschrieben zu Adobe I/O wechseln**.
>Beachten Sie, dass während dieser Umstellung auf [!DNL Adobe I/O] einige eingehende Auslöser verloren gehen können.
>
>Die alte OAuth-Authentifizierungsmethode mit Campaign wurde am **20. Oktober 2021** eingestellt. Gehostete Umgebungen profitieren von einer Verlängerung bis zum **25. Mai 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis **Mai 2022** zu verlängern. Dazu müssen Sie Adobe [die AppID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md#step-optional) nennen.

## Voraussetzungen {#adobe-io-prerequisites}

Diese Integration gilt nur ab **Campaign Classic-Version 20.2.4 und höher, 19.1.8 und Gold Standard-Version 11**.

Bevor Sie mit dieser Implementierung beginnen, überprüfen Sie, ob Folgendes vorhanden ist:

* eine gültige **Organisationskennung**: Die Organisations-ID ist die eindeutige Kennung innerhalb der Adobe Experience Cloud, die zum Beispiel für den VisitorID-Dienst und das IMS Single-Sign On (SSO) verwendet wird. [Weitere Informationen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de)
* ein **Entwicklerzugriff** auf Ihr Unternehmen. Der Systemadministrator der Organisation muss das Verfahren zum **Hinzufügen von Entwicklern zu einem einzelnen Produktprofil** befolgen, das [auf dieser Seite](https://helpx.adobe.com/de/enterprise/using/manage-developers.html?lang=de) beschrieben wird. Damit ermöglicht er den Entwicklerzugriff für das `Analytics - {tenantID}` Produktprofil des Adobe Analytics-Produkts, das mit Triggers verbunden ist.

## Schritt 1: Erstellen/Aktualisieren eines Adobe I/O-Projekts {#creating-adobe-io-project}

1. Greifen Sie auf [!DNL Adobe I/O] zu und melden Sie sich mit den Entwicklerzugangsdaten Ihrer Organisation an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen Portal der Organisation angemeldet sind.

1. Entnehmen Sie die vorhandene Integrations-Client-Kennung (Client-ID) aus der Konfigurationsdatei &quot;ims/authIMSTAClientId&quot; der Instanz. Ist das Attribut nicht vorhanden oder leer, bedeutet dies, dass die Client-Kennung nicht konfiguriert ist.

   >[!NOTE]
   >
   >Wenn die Client-Kennung leer ist, können Sie in Adobe I/O direkt ein **[!UICONTROL neues Projekt erstellen]**.

1. Identifizieren Sie das vorhandene Projekt mit der gefundenen Client-ID. Suchen Sie nach bestehenden Projekten, die dieselbe Client-Kennung aufweisen wie die im vorherigen Schritt entnommene.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Zu Projekt hinzufügen]** und dann **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Wählen Sie im Fenster **[!UICONTROL Add an API]** (API hinzufügen) **[!UICONTROL Adobe Analytics]** aus.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Service Account (JWT)]**.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Schlüsselpaar generieren]** aus, um ein Paar aus öffentlichem und privatem Schlüssel zu erstellen.

   Die Schlüssel werden dann automatisch mit einem Standardablaufdatum von 365 Tagen heruntergeladen. Nach dem Ablaufdatum müssen Sie ein neues Schlüsselpaar erstellen und die Integration in der Konfigurationsdatei aktualisieren. Mit Option 2 können Sie Ihren **[!UICONTROL öffentlichen Schlüssel]** manuell mit einem längeren Ablaufdatum erstellen und hochladen.

   Eine Schritt-für-Schritt-Anleitung für das Ersetzen ablaufender Zertifikatschlüsselpaare finden Sie auf [dieser Seite](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >Sie sollten die Datei config.zip speichern, wenn die Download-Eingabeaufforderung angezeigt wird, da Sie sie nicht erneut herunterladen können.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Wählen Sie ein vorhandenes **[!UICONTROL Produktprofil]** aus oder erstellen Sie ggf. ein neues. Für dieses **[!UICONTROL Produktprofil]** ist keine Berechtigung erforderlich. Weitere Informationen zu [!DNL Analytics] **[!UICONTROL Produktprofilen]** finden Sie in der [Adobe Analytics-Dokumentation](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=de#admin-console).

   Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Wählen Sie in Ihrem Projekt **[!UICONTROL Adobe Analytics]** aus und kopieren Sie die folgenden Informationen unter **[!UICONTROL Dienstkonto (JWT)]**:

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Das Adobe I/O-Zertifikat läuft nach 12 Monaten ab. Sie müssen jedes Jahr ein neues Schlüsselpaar generieren.

## Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

>[!NOTE]
>
>Dieser Schritt ist nicht erforderlich, wenn Ihre Client-Kennung in [Schritt 1: Erstellen/aktualisieren eines Adobe I/O-Projekts](#creating-adobe-io-project) nicht leer war.

Der private Schlüssel sollte im Base64-UTF-8-Format kodiert werden. Gehen Sie dabei folgendermaßen vor:

1. Verwenden Sie den privaten Schlüssel, der im Abschnitt [Schritt 1: Erstellen/Aktualisieren eines Adobe I/O-Projekts](#creating-adobe-io-project) generiert wurde. Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten Schlüssel identisch sein.

1. Codieren Sie den privaten Schlüssel mit dem folgenden Befehl: `base64 ./private.key > private.key.base64`. Dadurch wird der base64-Inhalt in einer neuen Datei `private.key.base64` gespeichert.

   >[!NOTE]
   >
   >Manchmal werden beim Kopieren/Einfügen des privaten Schlüssels automatisch zusätzliche Zeilen hinzugefügt. Vergessen Sie nicht, diese zu entfernen, bevor Sie Ihren privaten Schlüssel codieren.

1. Kopieren Sie die Inhalte aus der Datei `private.key.base64`.

1. Melden Sie sich über SSH bei jedem Container an, in dem die Adobe Campaign-Instanz installiert ist, und fügen Sie die Projektanmeldeinformationen in Adobe Campaign hinzu, indem Sie den folgenden Befehl als `neolane`-Benutzer ausführen. Dadurch werden die Anmeldeinformationen für das **[!UICONTROL Technische Konto]** in die Konfigurationsdatei der Instanz eingefügt.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Schritt 3: Aktualisieren des Pipelined-Tags {#update-pipelined-tag}

>[!NOTE]
>
>Dieser Schritt ist nicht erforderlich, wenn Ihre Client-Kennung in [Schritt 1: Erstellen/aktualisieren eines Adobe I/O-Projekts](#creating-adobe-io-project) nicht leer war.

Um das [!DNL pipelined]-Tag zu aktualisieren, müssen Sie den Authentifizierungstyp in der Konfigurationsdatei **config-&lt; Name der Instanz >.xml** wie folgt entsprechend dem Adobe I/O-Projekt aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Führen Sie dann einen `config -reload` und einen Neustart von [!DNL pipelined] aus, damit die Änderungen berücksichtigt werden.
