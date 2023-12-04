---
product: campaign
title: Aktualisierung auf den neuen Zustellbarkeits-Server
description: Erfahren Sie, wie Sie eine Aktualisierung auf den neuen Zustellbarkeits-Server von Campaign durchführen
feature: Technote, Deliverability
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: eea3657f1cffa215e1fc1cb1eb8782b83321aae4
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 100%

---

# Aktualisierung auf den neuen Zustellbarkeits-Server {#acc-deliverability}

Mit der [Veröffentlichung von Version 7.2.2](../../rn/using/latest-release.md#release-7-2-2) stellt Adobe Campaign einen neuen Zustellbarkeits-Server bereit, der hohe Verfügbarkeit bietet und Probleme mit der Einhaltung von Sicherheitsvorschriften behebt. Campaign Classic synchronisiert nun die Zustellbarkeitsregeln, Broadlogs und Unterdrückungsadressen mit dem neuen Zustellbarkeits-Server. Der alte Zustellbarkeits-Server wird am 31. August 2022 eingestellt.

Als Kundin oder Kunde von Campaign Classic müssen Sie den neuen Zustellbarkeits-Server **vor dem 31. August 2022** implementieren.

>[!NOTE]
>
>Weitere Informationen zu diesen Änderungen finden Sie in den [häufig gestellten Fragen](#faq) oder bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## Was hat sich geändert?{#acc-deliverability-changes}

Aus Sicherheitsgründen nimmt Adobe ältere Rechenzentren außer Betrieb. Adobe Campaign Classic-Kunden müssen zum neuen Zustellbarkeits-Service migrieren, der auf Amazon Web Service (AWS) gehostet wird.

Dieser neue Server garantiert hohe Verfügbarkeit (99,9) und bietet sichere, authentifizierte Endpunkte, damit Campaign-Server die erforderlichen Daten abrufen können. Anstatt für jede Anfrage eine Verbindung zur Datenbank herzustellen, bewahrt der neue Zustellbarkeits-Server die Daten in einem Zwischenspeicher auf, um die Anfragen nach Möglichkeit zu beantworten. Dieser Mechanismus verbessert die Reaktionszeit.

## Sind Sie betroffen?{#acc-deliverability-impacts}

Alle Kundinnen und Kunden sind betroffen und müssen ein Upgrade auf [Campaign Version 7.2.2](../../rn/using/latest-release.md#release-7-2-2) (oder höher) vornehmen und es in ihrer Umgebung implementieren, um von dem neuen Zustellbarkeits-Server zu profitieren.

## Wie wird die Aktualisierung durchgeführt?{#acc-deliverability-update}

Wenn Sie **gehosteter Kunde** sind, arbeitet Adobe mit Ihnen zusammen, um Ihre Instanz(en) auf die neuere Version zu aktualisieren und ein Projekt in der Adobe Developer Console zu erstellen.

Als **On-Premise-/Hybrid-Kunde** müssen Sie ein Upgrade auf [Campaign Version 7.2.2](../../rn/using/latest-release.md#release-7-2-2) (oder höher) vornehmen, um den neuen Zustellbarkeits-Server nutzen zu können. Sobald alle Instanzen das Upgrade erhalten haben, müssen Sie die neue Integration mit dem Adobe Zustellbarkeits-Server [implementieren](#implementation-steps) und so einen nahtlosen Übergang sicherstellen.

## Implementierungsschritte {#implementation-steps}

>[!WARNING]
>
>Diese Schritte sollten nur bei Hybrid- und On-Premise-Implementierungen durchgeführt werden.

Zur Integration des neuen Zustellbarkeits-Servers muss Campaign mit Adobe Shared Services über eine auf dem Identity Management Service (IMS) basierende Authentifizierung kommunizieren. Die bevorzugte Methode dazu ist die Verwendung des auf Adobe Developer basierenden Gateway-Tokens (auch Technical Account Token oder Adobe IO JWT genannt).

>[!AVAILABILITY]
>
> JWT (JSON Web Tokens) wird gerade eingestellt und durch OAuth ersetzt. Die Umstellung erfolgt schrittweise mit den anstehenden Campaign-Versionen. Die Dokumentation wird entsprechend diesen Aktualisierungen aktualisiert.

### Voraussetzungen{#prerequisites}

Überprüfen Sie vor Beginn der Implementierung Ihre Instanzkonfiguration.

1. Öffnen Sie die Client-Konsole von Campaign und melden Sie sich bei Adobe Campaign als Administrator an.
1. Gehen Sie zu **Administration > Plattform > Optionen**.
1. Prüfen Sie, ob der Optionswert `DmRendering_cuid` ausgefüllt ist.

   * Wenn die Option ausgefüllt ist, können Sie die Implementierung starten.
   * Wenn kein Wert eingetragen ist, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}, um Ihre CUID zu erhalten.

   In dieser Option muss für alle Campaign-Instanzen (MKT, MID, RT, EXEC) der richtige Wert angegeben werden. Wenden Sie sich als Hybrid-Kunde an Adobe, damit diese Option in Ihren MID-, RT- und EXEC-Instanzen konfiguriert wird.

Als On-Premise-Kunde müssen Sie auch überprüfen, ob für Ihre Organisation ein Campaign-**[!UICONTROL Produktprofil]** vorhanden ist. Gehen Sie dazu wie folgt vor:

1. Verbinden Sie sich als Administrator mit der [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Rufen Sie den Bereich **Produkte und Services** auf und überprüfen Sie, ob **Adobe Campaign** aufgeführt ist.
Wenn Sie **Adobe Campaign** nicht sehen können, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}, damit dieses Produkt hinzugefügt wird.
1. Klicken Sie auf **Adobe Campaign** und wählen Sie Ihre Organisation aus.
   **Achtung**: Wenn Sie mehrere Organisationen haben, achten Sie darauf, dass die richtige ausgewählt ist. Weitere Informationen zu Organisationen finden Sie [auf dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=de#ims-org-id){_blank}.

1. Überprüfen Sie, ob ein **[!UICONTROL Produktprofil]** vorhanden ist. Wenn nicht, erstellen Sie eines. Für dieses **[!UICONTROL Produktprofil]** ist keine Berechtigung erforderlich.


>[!CAUTION]
>
>Wenn Sie On-Premise-Kunde sind und auf Ihrer Seite eine Firewall implementiert ist, müssen Sie die URL `https://deliverability-service.adobe.io` zu Ihrer Zulassungsliste hinzufügen. [Weitere Informationen](../../installation/using/url-permissions.md).


### Schritt 1: Erstellen/Aktualisieren Sie Ihr Adobe Developer-Projekt {#adobe-io-project}

1. Rufen Sie die [Adobe Developer Console](https://developer.adobe.com/console/home) auf und melden Sie sich mit den Entwicklerzugriffsdaten Ihrer Organisation an. Stellen Sie sicher, dass Sie beim richtigen Portal der Organisation angemeldet sind.
   **Achtung**: Wenn Sie mehrere Organisationen haben, achten Sie darauf, dass die richtige ausgewählt ist. Weitere Informationen zu Organisationen finden Sie [auf dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=de#ims-org-id){_blank}.
1. Wählen Sie **[!UICONTROL Neues Projekt erstellen]** aus.
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >Wenn Sie bereits die JWT-Authentifizierungsfunktion von Adobe IO für eine andere Integration verwenden, z. B. für den Analytics-Connector oder Adobe Triggers, müssen Sie Ihr Projekt aktualisieren, indem Sie zu diesem Projekt die **Campaign-API** hinzufügen.

1. Wählen Sie **[!UICONTROL API hinzufügen]**.
   ![](assets/Add-API.png)
1. Wählen Sie im Fenster **[!UICONTROL API hinzufügen]** die Option **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Schlüsselpaar generieren]** aus, um ein Paar aus öffentlichem und privatem Schlüssel zu erstellen.
   ![](assets/Generate-a-key-pair.png)

   Die Schlüssel werden dann automatisch mit einem Standardablaufdatum von 365 Tagen heruntergeladen. Nach dem Ablaufdatum müssen Sie ein neues Schlüsselpaar erstellen und die Integration in der Konfigurationsdatei aktualisieren. Mit Option 2 können Sie Ihren **[!UICONTROL öffentlichen Schlüssel]** manuell mit einem längeren Ablaufdatum erstellen und hochladen.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Sie sollten die Datei `config.zip` speichern, wenn die Aufforderung zum Herunterladen angezeigt wird, da Sie sie nicht erneut herunterladen können.

1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie ein vorhandenes **[!UICONTROL Produktprofil]** aus oder erstellen Sie ggf. ein neues. Für dieses **[!UICONTROL Produktprofil]** ist keine Berechtigung erforderlich. Weitere Informationen zu **[!UICONTROL Produktprofilen]** finden Sie auf [dieser Seite](https://helpx.adobe.com/de/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

1. Wählen Sie in Ihrem Projekt **[!UICONTROL Adobe Campaign]** und kopieren Sie die folgenden Informationen unter **[!UICONTROL Service Account (JWT)]**.

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

>[!CAUTION]
>
>Das Adobe Developer-Zertifikat läuft nach 12 Monaten ab. Sie müssen jedes Jahr ein neues Schlüsselpaar generieren.

### Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

Der private Schlüssel sollte im Base64-UTF-8-Format kodiert sein.

Gehen Sie dabei folgendermaßen vor:

1. Verwenden Sie den in den obigen Schritten generierten privaten Schlüssel.
1. Codieren Sie den privaten Schlüssel mit dem folgenden Befehl: `base64 ./private.key > private.key.base64`. Dadurch wird der base64-Inhalt in einer neuen Datei `private.key.base64` gespeichert.

   >[!NOTE]
   >
   >Manchmal werden beim Kopieren/Einfügen des privaten Schlüssels automatisch zusätzliche Zeilen hinzugefügt. Vergessen Sie nicht, diese zu entfernen, bevor Sie Ihren privaten Schlüssel codieren.

1. Kopieren Sie die Inhalte aus der Datei `private.key.base64`.
1. Melden Sie sich über SSH bei jedem Container an, in dem die Adobe Campaign-Instanz installiert ist, und fügen Sie die Projektanmeldeinformationen in Adobe Campaign hinzu, indem Sie den folgenden Befehl als `neolane`-Benutzer ausführen. Dadurch werden die Anmeldeinformationen für das **[!UICONTROL Technische Konto]** in die Konfigurationsdatei der Instanz eingefügt.

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Sie müssen den Server anhalten und dann neu starten, damit die Änderung übernommen wird. Sie können auch einen `config -reload`-Befehl ausführen.

### Schritt 3: Überprüfen Sie Ihre Konfiguration

Um zu überprüfen, ob die Integration erfolgreich war, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Client-Konsole und melden Sie sich bei Adobe Campaign an.
1. Gehen Sie zu **Administration > Produktion > Technische Workflows**.
1. Starten Sie den Workflow **Zustellbarkeit** (deliverabilityUpdate) neu. Dies sollte für alle Ihre Campaign-Instanzen (MKT, MID, RT, EXEC) durchgeführt werden. Wenn Hybrid-Kunde sind, wenden Sie sich an Adobe, damit der Workflow in Ihren MID-, RT- und EXEC-Instanzen neu gestartet wird.
1. Überprüfen Sie die Protokolle: Der Workflow sollte fehlerfrei ausgeführt werden.

>[!CAUTION]
>
>Nach der Aktualisierung muss der Workflow **Testnetzwerk-Update für das Inbox Rendering (updateRenderingSeeds)** angehalten werden, da er dann nicht mehr anwendbar ist und fehlschlägt.

## Häufig gestellte Fragen {#faq}

### Welchen Zeitrahmen gibt es für die Aktualisierung?

Der Wechsel zum neuen Zustellbarkeits-Server, der diese verbesserten Funktionen und höhere Sicherheit bietet, beginnt für gehostete Kunden am 22. Juli (Campaign Managed Services). Alle gehosteten Kunden werden bis Ende August aktualisiert.

On-Premise- und Hybrid-Kunden müssen den Wechsel im selben Zeitrahmen durchführen.

### Was passiert, wenn ich meine Umgebung nicht aktualisiere?

Campaign-Instanzen, die nicht bis zum 31. August aktualisiert wurden, können keine Verbindung mehr zum Zustellbarkeits-Server von Campaign herstellen. Dies hat zur Folge, dass der Workflow **Zustellbarkeit** (deliverabilityUpdate) fehlschlägt, was sich auf Ihre Zustellbarkeit auswirkt.

Wenn Sie Ihre Umgebung nicht aktualisieren, werden die E-Mail-Einstellungen nicht mehr synchronisiert (MX-Verwaltungsregeln, Regeln für eingehende E-Mails, Regeln für die Verwaltung von Domains und Regeln für die Bounce-Qualifizierung). Dies kann sich bei Ihnen im Laufe der Zeit auf die Zustellbarkeit auswirken. Wenn eine wesentliche Änderung an diesen Regeln vorgenommen wird, müssen diese ab diesem Zeitpunkt manuell angewendet werden.

Bei MKT-Instanzen ist nur die [globale Unterdrückungsliste](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) betroffen.
