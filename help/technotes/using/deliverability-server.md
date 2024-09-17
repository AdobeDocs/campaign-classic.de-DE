---
product: campaign
title: Aktualisierung auf den neuen Zustellbarkeits-Server
description: Erfahren Sie, wie Sie eine Aktualisierung auf den neuen Zustellbarkeits-Server von Campaign durchführen
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 98%

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
> Die Anmeldedaten für Service-Konten (JWT) werden von Adobe demnächst eingestellt. Campaign-Integrationen mit Adobe-Lösungen und -Apps müssen jetzt mit OAuth-Server-to-Server-Anmeldedaten arbeiten. </br>
>
> * Wenn Sie eingehende Integrationen in Campaign implementiert haben, müssen Sie Ihr technisches Konto migrieren, wie in [dieser Dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank) beschrieben. Vorhandene [Service-Konto (JWT)-Anmeldedaten](oauth-technical-account.md) funktionieren bis zum 27. Januar 2025 weiterhin. </br>
>
> * Wenn Sie ausgehende Integrationen implementiert haben, z. B. die Integration von Campaign mit Analytics oder Experience Cloud Triggers, funktionieren diese noch bis zum 27. Januar 2025. Vor diesem Datum müssen Sie jedoch Ihre Campaign-Umgebung auf v7.4.1 aktualisieren und Ihr technisches Konto auf OAuth migrieren.

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


### Schritt 1: Erstellen/Aktualisieren Ihres Adobe Developer-Projekts {#adobe-io-project}

Um mit der Konfiguration Ihres Adobe Analytics-Connectors fortzufahren, greifen Sie auf die Adobe Developer Console zu und erstellen Sie Ihr OAuth-Server-zu-Server-Projekt.

Auf [dieser Seite](../../integrations/using/oauth-technical-account.md#oauth-service) finden Sie die ausführliche Dokumentation.

### Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

Führen Sie die Schritte aus, die auf [dieser Seite](../../integrations/using/oauth-technical-account.md#add-credentials) beschrieben werden, um Ihre OAuth-Projektanmeldedaten in Adobe Campaign hinzuzufügen.

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
