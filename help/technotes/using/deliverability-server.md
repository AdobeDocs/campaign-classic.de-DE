---
product: campaign
title: Migration zum neuen Zustellbarkeits-Server
description: Erfahren Sie, wie Sie den Zustellbarkeits-Server von Campaign implementieren.
hide: true
hidefromtoc: true
source-git-commit: 65ab862ec568647dd06c1f7b7b83e5b921353cc7
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 38%

---

# Campaign Deliverability Server {#acc-deliverability}

Ab Campaign Classic-Version 21.1 bietet Adobe Campaign einen neuen Zustellbarkeits-Server, der hohe Verfügbarkeit bietet und Probleme mit der Einhaltung von Sicherheitsanforderungen behebt. Campaign Classic synchronisiert nun die Zustellbarkeitsregeln, Broadlogs und Unterdrückungsadressen vom und auf den neuen Zustellbarkeits-Server.

Als Campaign Classic-Kunde müssen Sie den neuen Zustellbarkeits-Server implementieren

>[!NOTE]
>
>Fragen zu diesen Änderungen finden Sie in den [Häufig gestellten Fragen](#faq-aa). Weitere Informationen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Was hat sich geändert?{#acc-deliverability-changes}

Adobe beendet ältere Rechenzentren aus Gründen der Sicherheitskonformität. Adobe Campaign Classic-Clients müssen zum neuen Zustellbarkeitsdienst migrieren, der auf Amazon Web Service (AWS) gehostet wird.

Dieser neue Server garantiert eine hohe Verfügbarkeit (99.9) &#x200B; und bietet sichere und authentifizierte Endpunkte, damit Kampagnenserver die erforderlichen Daten abrufen können: Anstatt für jede Anfrage eine Verbindung zur Datenbank herzustellen, speichert der neue Zustellbarkeits-Server die Daten zwischen, um die Anforderungen zu erfüllen. Dieser Mechanismus verbessert die Reaktionszeit. &#x200B;


## Sind Sie betroffen?{#acc-deliverability-impacts}

Wenn Sie den alten Adobe Campaign-Zustellbarkeits-Server verwenden und Ihre Umgebung auf einem niedrigeren Build als Campaign 21.1.1 implementiert wurde, sind Sie betroffen. Sie müssen auf Campaign 21.1 (oder höher) aktualisieren.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

## Wie wird die Aktualisierung durchgeführt?{#acc-deliverability-update}

Wenn Sie ein gehosteter Kunde sind, wird Adobe in Kürze auf Sie zukommen, um für Ihre Instanz(en) das Upgrade auf die neuere Version vorzunehmen.

Als On-Premise-/Hybrid-Kunde müssen Sie auf eine der neueren Versionen aktualisieren, um von dem neuen Zustellbarkeits-Server profitieren zu können.
Sobald alle Instanzen aktualisiert wurden, können Sie [die neue Integration implementieren](#implementation-steps) auf den Zustellbarkeitsserver der Adobe zu gelangen und einen nahtlosen Übergang zu gewährleisten.

## Implementierungsschritte (Hybrid- und On-Premise-Kunden) {#implementation-steps}

>[!IMPORTANT]
>
>Diese Schritte sollten nur von Hybrid- und On-Premise-Implementierungen durchgeführt werden.
>
>Bei gehosteten Implementierungen wenden Sie sich an [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

### Voraussetzungen{#prerequisites}

Im Rahmen der neuen Integration des Zustellbarkeitsservers muss Campaign über eine IMS-basierte Authentifizierung (Identity Management Service) mit Adobe Shared Services kommunizieren. Die bevorzugte Methode ist die Verwendung des Adobe Developer-basierten Gateway-Tokens (auch als Token für technische Konten oder Adobe IO JWT bezeichnet).

### Schritt 1: Erstellen/Aktualisieren Ihres Adobe Developer-Projekts {#adobe-io-project}

1. Zugriff [Adobe Developer-Konsole](https://developer.adobe.com/console/home) und melden Sie sich mit dem Entwicklerzugriff Ihrer Organisation an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen Portal der Organisation angemeldet sind.

1. Wählen Sie **[!UICONTROL + Zu Projekt hinzufügen]** und dann **[!UICONTROL API]**.
1. Im **[!UICONTROL API hinzufügen]** auswählen **[!UICONTROL Adobe Campaign]**.
1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Service Account (JWT)]** (Dienstkonto (JWT)).
1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Generate a key pair]** (Schlüsselpaar generieren) aus, um ein Paar aus öffentlichem und privatem Schlüssel zu erstellen.

   Die Schlüssel werden dann automatisch mit einem Standardablaufdatum von 365 Tagen heruntergeladen. Nach dem Ablaufdatum müssen Sie ein neues Schlüsselpaar erstellen und die Integration in der Konfigurationsdatei aktualisieren. Mit Option 2 können Sie Ihren **[!UICONTROL öffentlichen Schlüssel]** manuell mit einem längeren Ablaufdatum erstellen und hochladen.

   >[!CAUTION]
   >
   >Sie sollten die Datei config.zip speichern, wenn die Download-Eingabeaufforderung angezeigt wird, da Sie sie nicht erneut herunterladen können.

1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie ein vorhandenes **[!UICONTROL Produktprofil]** aus oder erstellen Sie ggf. ein neues. Für dieses **[!UICONTROL Produktprofil]** ist keine Berechtigung erforderlich. Weitere Informationen finden Sie unter [!DNL Analytics] **[!UICONTROL Produktprofile]**, siehe [diese Seite](https://helpx.adobe.com/de/enterprise/using/manage-developers.html?lang=de).

   Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

1. Wählen Sie in Ihrem Projekt **[!UICONTROL Adobe Campaign]** und kopieren Sie die folgenden Informationen unter **[!UICONTROL Dienstkonto (JWT)]**:

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

>[!CAUTION]
>
>Das Adobe Developer-Zertifikat läuft nach 12 Monaten ab. Sie müssen jedes Jahr ein neues Schlüsselpaar generieren.

### Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

Der private Schlüssel sollte im Base64-UTF-8-Format kodiert werden.

Gehen Sie dabei folgendermaßen vor:

1. Verwenden Sie den in den obigen Schritten generierten privaten Schlüssel.
1. Codieren Sie den privaten Schlüssel mit dem folgenden Befehl: `base64 ./private.key > private.key.base64`. Dadurch wird der base64-Inhalt in einer neuen Datei `private.key.base64` gespeichert.

   >[!NOTE]
   >
   >Manchmal werden beim Kopieren/Einfügen des privaten Schlüssels automatisch zusätzliche Zeilen hinzugefügt. Vergessen Sie nicht, diese zu entfernen, bevor Sie Ihren privaten Schlüssel codieren.

1. Kopieren Sie die Inhalte aus der Datei `private.key.base64`.
1. Melden Sie sich über SSH bei jedem Container an, in dem die Adobe Campaign-Instanz installiert ist, und fügen Sie die Projektanmeldeinformationen in Adobe Campaign hinzu, indem Sie den folgenden Befehl als `neolane`-Benutzer ausführen. Dadurch werden die Anmeldeinformationen für das **[!UICONTROL Technische Konto]** in die Konfigurationsdatei der Instanz eingefügt.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Sie müssen den Server stoppen und dann neu starten, damit die Änderung berücksichtigt wird. Sie können auch eine `config -reload` Befehl.

### Schritt 3: Überprüfen der Konfiguration

Nach Abschluss der Einstellungen können Sie die Konfiguration Ihrer Instanz überprüfen. Gehen Sie wie folgt vor:

1. Öffnen Sie die Clientkonsole und melden Sie sich als Administrator bei Adobe Campaign an.
1. Navigieren Sie zu **Administration > Plattform > Optionen**.
1. Überprüfen Sie die `DmRendering_cuid` Optionswert ausgefüllt. Sie sollte in allen Ihren Campaign-Instanzen (MKT, MID, RT, EXEC) ausgefüllt werden. Wenn der Wert nicht ausgefüllt ist, müssen Sie ihn ausfüllen. Wenn kein Wert ausgefüllt ist, kontaktieren Sie [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) um Ihre CUID zu erhalten.

### Schritt 4: Aktivieren des neuen Zustellbarkeits-Servers

Jetzt können Sie den neuen Zustellbarkeits-Server aktivieren. Gehen Sie dazu folgendermaßen vor:

1. Öffnen Sie die Clientkonsole und melden Sie sich als Administrator bei Adobe Campaign an.
1. Navigieren Sie zu **Administration > Plattform > Optionen**.
1. Zugriff auf `NewDeliverabilityServer_FeatureFlag` und setzen Sie den Wert auf `1`. Diese Konfiguration sollte für alle Campaign-Instanzen durchgeführt werden (MKT, MID, RT, EXEC).


### Schritt 5: Überprüfen der Konfiguration

Gehen Sie wie folgt vor, um zu überprüfen, ob die Integration erfolgreich ist:


1. Öffnen Sie die Clientkonsole und melden Sie sich bei Adobe Campaign an.
1. Navigieren Sie zu **Administration > Betreibung > Technische Workflows**.
1. Starten Sie den **Zustellbarkeit aktualisieren** Workflow (deliverabilityUpdate). Dies sollte für alle Campaign-Instanzen (MKT, MID, RT, EXEC) durchgeführt werden.
1. Protokolle überprüfen: Der Workflow sollte fehlerfrei ausgeführt werden.

## Häufig gestellte Fragen{#faq-aa}

F: A:

F: A:



Weitere Informationen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
