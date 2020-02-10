---
title: Grundlagen und Datenzyklus von ACS Connector
seo-title: Grundlagen und Datenzyklus von ACS Connector
description: Grundlagen und Datenzyklus von ACS Connector
seo-description: null
page-status-flag: never-activated
uuid: ea62ee69-042e-4c18-aaea-d65872d07dd9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 64d87bea-2376-4684-ac93-6ca56fe0f262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Grundlagen und Datenzyklus von ACS Connector{#acs-connector-principles-and-data-cycle}

## Einleitung {#introduction}

ACS Connector ist das Bindeglied zwischen Adobe Campaign v7 und Adobe Campaign Standard. Diese in Campaign v7 integrierte Funktion repliziert automatisch Daten nach Campaign Standard und vereint somit das Beste beider Anwendungen. Campaign v7 verfügt über fortschrittliche Tools zur Verwaltung der primären Marketing-Datenbank. Durch die Replikation der Daten von Campaign v7 nach Campaign Standard können diese in einer benutzerfreundlichen Umgebung verwendet werden.

![](assets/acs_connect_puzzle_link_01.png)

In Kombination mit ACS Connector richtet sich Campaign Standard wie bisher an Digital Marketer, die damit Kampagnen konzipieren, ausrichten und durchführen können, während Campaign v7 auf datenorientierte Benutzer wie Datenbankmarketer zugeschnitten ist.

>[!CAUTION]
>
>ACS Connector ist nur als Teil des Adobe Campaign Prime-Angebots erhältlich. Mehr zur Lizenzierung von Adobe Campaign Prime erfahren Sie bei Ihrem Kundenbetreuer.
>
>ACS Connector ist nur für gehostete und Hybridarchitekturen verfügbar, nicht aber für vollständige On-Premise-Installationen.
>
>Um diese Funktion verwenden zu können, stellen Sie mithilfe einer Adobe ID (IMS) eine Verbindung zu Campaign her. Siehe [Verbindung mit Adobe ID](../../integrations/using/about-adobe-id.md).

In diesem Dokument wird ACS Connector beschrieben. In den folgenden Abschnitten erhalten Sie Informationen über die Replikation von Daten und eine Anleitung zur Verwendung replizierter Profile.

* [Prozess](#process): Überblick über den ACS Connector und die Verwaltung der Datenreplikation.
* [Implementierung](#implementation): Übersicht über die ersten Schritte mit ACS Connector sowie Anleitungen zur Replizierung grundlegender und erweiterter Daten.
* [Profile](../../integrations/using/synchronizing-profiles.md)synchronisieren: Anleitung zum Replizieren von Profilen und zum Erstellen von Auslieferungen.
* [Synchronisieren von Zielgruppen](../../integrations/using/synchronizing-audiences.md): Anweisungen zum Targeting einer Liste von Empfängern in Campaign v7 und anschließendes Replizieren der Liste in Campaign Standard als Zielgruppe.
* [Synchronisieren von Webanwendungen](../../integrations/using/synchronizing-web-applications.md): Anleitung zum Verknüpfen von Campaign v7-Webanwendungen mit Campaign Standard.
* [Fehlerbehebung beim ACS Connector](../../integrations/using/troubleshooting-the-acs-connector.md): Prüfen Sie die Antworten auf häufig auftretende Probleme.

>[!NOTE]
>
>ACS Connector ist Teil der Campaign v7-Lizenz. Um ACS Connector verwenden zu können, müssen Sie zwischen Campaign v7 und Campaign Standard wechseln können. Wenn Sie sich unsicher bezüglich Ihrer Version und deren Funktionen sind, kontaktieren Sie bitte Ihren Administrator.

## Vorgang {#process}

### Datenreplikation {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS Connector repliziert regelmäßig die folgenden Elemente von Campaign v7 nach Campaign Standard:

* **Bereich Empfänger**
* **Abonnements**
* **Dienste**
* **Landingpages**

Standardmäßig erfolgt die periodische Replikation für ACS Connector alle 15 Minuten. Dieser Zeitraum kann auf Ihre Bedürfnisse angepasst werden. Wenn Sie diese Einstellung ändern möchten, kontaktieren Sie Ihren Consultant.

Die Datenreplikation für Empfänger, Abonnements, Dienste und Einstiegsseiten ist inkrementell. Das bedeutet, dass nur neue Empfänger und Änderungen an vorhandenen Empfängern von Campaign v7 in Campaign Standard repliziert werden. Die Replikation für eine Zielgruppe erfolgt jedoch in einer einzigen Instanz. Sie können eine Zielgruppe in Campaign v7 erstellen und sie dann ein Mal in Campaign Standard replizieren. Die Replizierung erfolgt sofort und kann nicht für regelmäßige Aktualisierungen konfiguriert werden. Anweisungen finden Sie unter [Synchronisieren von Zielgruppen](../../integrations/using/synchronizing-audiences.md).

>[!NOTE]
>
>Die erstmalige Replikation einer großen Datenbank erfordert Geduld, da sie mehrere Stunden dauern kann. Die darauf folgenden Replikationen sind jedoch inkrementell und erfolgen wesentlich schneller.

ACS Connector repliziert regelmäßig die folgenden Elemente von Campaign Standard nach Campaign v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

Die Replikation von Versandkennungen und E-Mail-Logs ermöglicht den Zugriff auf den Verlauf von Sendungen und Tracking-Daten für Ihre v7-Empfänger von Campaign v7.

>[!CAUTION]
>
>Nur E-Mail-Broadlogs und -Trackinglogs werden von Campaign Standard nach Campaign v7 repliziert.

### Datensynchronisation {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS Connector synchronisiert Quarantänen zwischen Campaign v7 und Campaign Standard.

Beispiel: Ein von Campaign v7 nach Campaign Standard repliziertes Profil enthält eine E-Mail-Adresse. Wenn diese E-Mail-Adresse von Campaign Standard unter Quarantäne gestellt wird, werden diese Daten bei der nächsten Synchronisation an Campaign v7 weitergegeben. Weiterführende Informationen zu Quarantänen finden Sie unter [Quarantäne-Verwaltung](../../delivery/using/understanding-quarantine-management.md) und [Quarantäne in Campaign Standard](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### Replizierte Profile verwenden {#using-replicated-profiles}

Replizierte Profile können von Campaign Standard und Campaign v7 für Zielgruppen-Workflows in Marketing-Kampagnen verwendet werden.

Anweisungen zum Senden einer Bereitstellung in Campaign Standard mit replizierten Profilen finden Sie unter Profile [synchronisieren](../../integrations/using/synchronizing-profiles.md). Es werden zusätzliche Anweisungen zur Freigabe der Daten zum Rückgängigmachen des Abonnements zwischen Campaign v7 und Campaign Standard bereitgestellt.

### Einschränkungen {#limitations}

Replizierte Profile sind zwar unmittelbar für Sendungen verfügbar, unterliegen aber gewissen Einschränkungen in Campaign Standard. Beachten Sie die unten aufgeführten Informationen, um entsprechende Fälle ordnungsgemäß zu handhaben.

* **Schreibgeschützte Profile für Campaign Standard**: Replizierte Profile können in Campaign Standard nicht geändert werden. Die Empfänger können jedoch in Campaign v7 bearbeitet werden. Diese Änderungen werden dann automatisch von ACS Connector nach Campaign Standard übertragen.
* **In Campaign Standard erstellte Profile**: ACS Connector repliziert Empfängerdaten in nur eine Richtung, nämlich von Campaign v7 nach Campaign Standard. Deshalb werden von Campaign Standard stammende Profile nicht nach Campaign v7 repliziert.
* **Grundlegende Empfängerdaten für Campaign Standard**: ACS Connector repliziert für Campaign Standard geeignete Daten. Dazu zählen der Empfängername, die Adresse, die E-Mail-Adresse, die Mobiltelefonnummer, die Privatnummer und sonstige relevante Kontaktinformationen. Wenn Sie für Ihren Workflow zusätzliche in Campaign v7 verfügbare Empfängerfelder und benutzerdefinierte Tabellen für die Zielgruppenbestimmung benötigen, wenden Sie sich bitte an Ihren Consultant.
* **Importieren unter Quarantäne gestellter Profile**: Listen mit Profilen, die nicht kontaktiert werden möchten, können in Campaign v7 oder Campaign Standard als unter Quarantäne gestellte Profile importiert werden. Der Status der Profile ist in der Quarantänesynchronisation zwischen den Anwendungen enthalten, weshalb diese Profile nicht in Sendungen eingeschlossen werden.
* **Abmelden eines Dienstes in Campaign Standard**: Die Auswahl, eine Bereitstellung abzubestellen, wird nicht von Campaign Standard auf Campaign v7 synchronisiert. Sie können jedoch eine Campaign Standard-Bereitstellung so konfigurieren, dass der Link zum Abmelden an Campaign v7 weitergeleitet wird. Das Profil eines Empfängers, der auf den Link zum Abmelden klickt, wird in Campaign v7 aktualisiert und die Daten werden in Campaign Standard repliziert. See [Changing the unsubscription link](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link).
* Nur E-Mail-Broadlogs und -Trackinglogs werden von Campaign Standard nach Campaign v7 repliziert.

### Fakturierung {#billing}

Die Fakturierung ist von Ihrer Wahl der Anwendung für den Versand – Campaign v7 oder Campaign Standard – nicht betroffen. Rechnungsinformationen werden zwischen Campaign v7 und Campaign Standard abgestimmt, d. h. wenn Sie über beide Anwendungen Sendungen an denselben Empfänger durchführen, wird er dennoch nur als ein aktives Profil gewertet.

## Umsetzung {#implementation}

Für ACS Connector gibt es zwei Arten von Implementierungen. Beide müssen unbedingt vom Adobe Campaign-Team durchgeführt werden.

>[!CAUTION]
>
>Dieser Abschnitt richtet sich ausschließlich an Spezialisten, die einen allgemeinen Überblick über den Implementierungsvorgang und seine wichtigsten Schritte erhalten sollen.
>
>Versuchen Sie unter keinen Umständen, diese Schritte selbst durchzuführen. Sie dürfen ausschließlich von Adobe-Campaign-Consultants vorgenommen werden.

Mit der **einfachen Implementierung** können Sie Empfänger (vordefinierte Felder), Dienste und Abonnements, Webanwendungen und Zielgruppen replizieren. Diese Replikation erfolgt in nur einer Richtung von Campaign v7 nach Campaign Standard.

The **advanced implementation** will allow you to perform more complex use cases, for example if you have additional recipient fields or custom recipient tables (transaction table for example). Siehe [Erweiterte Implementierung](#advanced-implementation).

### Package-Installation {#installing-the-package}

Um die Funktion verwenden zu können, muss das Package **[!UICONTROL ACS Connector]** installiert werden. Dies wird immer vom technischen Administrator oder Berater von Adobe durchgeführt.

Alle mit dem ACS Connector in Verbindung stehenden technischen Elemente sind im Knoten **[!UICONTROL Administration > ACS Connector]** verfügbar.

### Technische und Replikations-Workflows {#technical-and-replication-workflows}

After the installation of the package, two technical workflows are available under **[!UICONTROL Administration > ACS Connector > Process]**.

>[!CAUTION]
>
>Versuchen Sie niemals, diese Workflows zu verändern. Diese Workflows sollten niemals eine Fehlermeldung aufweisen oder ausgesetzt werden. Wenden Sie sich in diesem Fall an Ihren Adobe Campaign-Consultant.

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (QuarantäneSync): dieser Arbeitsablauf synchronisiert alle Quarantäneinformationen. Alle neuen Quarantäne in Campaign v7 werden in Campaign Standard repliziert. Alle neuen Quarantäne aus Campaign Standard werden in Campaign v7 repliziert. Dadurch wird sichergestellt, dass alle Ausschlussregeln zwischen Campaign v7 und Campaign Standard synchronisiert werden.
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync): dieser Arbeitsablauf wird für die Konvertierung von Rechten verwendet. Siehe [Rights-Konvertierung](#rights-conversion).

Die folgenden Replikations-Workflows sind als gebrauchsfertige Vorlagen verfügbar. Sie müssen von Ihrem Adobe Campaign-Consultant implementiert werden.

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication): dieser inkrementelle Arbeitsablauf repliziert Empfänger in Campaign Standard. Standardmäßig werden alle vordefinierten Empfängerfelder repliziert. Siehe [Standardbegünstigungsfelder](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication): dieser inkrementelle Arbeitsablauf repliziert die ausgewählten Dienste in Campaign Standard. Siehe Verwendungsfall [Synchronisieren von Webanwendungen](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication): dieser inkrementelle Arbeitsablauf repliziert die ausgewählten Webanwendungen in Campaign Standard. Die Campaign v7-Webanwendungen werden als Einstiegsseiten in Campaign Standard angezeigt. Siehe Verwendungsfall [Synchronisieren von Webanwendungen](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (newReplication): Dieser inkrementelle Arbeitsablauf ist ein Beispiel, mit dem eine benutzerdefinierte Tabelle repliziert werden kann. Siehe [Erweiterte Implementierung](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgQualification): dieser inkrementelle Arbeitsablauf repliziert Auslieferungsmeldungen von Campaign Standard zu Campaign v7.
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication): Dieser inkrementelle Arbeitsablauf repliziert Auslieferungs-IDs, E-Mail-breitere Protokolle und E-Mail-Verfolgungsprotokolle von Campaign Standard zu Campaign v7. Dabei werden nur Auslieferungen berücksichtigt, die von Campaign Standard an Profile gesendet werden, die Teil der Tabelle &quot;nms:empfänger&quot;von Campaign v7 sind.
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication): Dieser inkrementelle Arbeitsablauf repliziert Auslieferungs-IDs, E-Mail-breitere Protokolle und E-Mail-Verfolgungsprotokolle von Campaign Standard zu Campaign v7. Dabei werden nur Auslieferungen berücksichtigt, die von Campaign Standard an Profile gesendet werden, die Teil einer bestimmten Tabelle (außer nms:empfänger) von Campaign v7 sind.

### Standard-Empfängerfelder {#default-recipient-fields}

Wenn Sie zusätzliche Felder oder benutzerdefinierte Tabellen (z. B. Transaktionstabelle) haben, werden diese nicht standardmäßig repliziert. Es muss eine erweiterte Konfiguration durchgeführt werden. Siehe [Erweiterte Implementierung](#advanced-implementation).

Unten finden Sie die Liste mit den vordefinierten Empfängerfeldern, die bei der einfachen Implementierung repliziert werden:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Source Id<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> Erstellungsdatum<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> Änderungsdatum<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> Last name<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> First name<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> Middle name<br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> Geburtsdatum<br /> </td> 
   <td> @birthDate<br /> </td> 
  </tr> 
  <tr> 
   <td> Geschlecht<br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> Anrede<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> No longer contact (by any channel)<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> No longer contact by email<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> No longer contact by SMS<br /> </td> 
   <td> @blackListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> Phone<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> Fax<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse 1 (Wohnung)<br /> </td> 
   <td> [location/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse 2<br /> </td> 
   <td> [location/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse 3 (Straße und Hausnr.)<br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse 4 (Ortszusatz)<br /> </td> 
   <td> [location/@address4]<br /> </td> 
  </tr> 
  <tr> 
   <td> Postleitzahl<br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Ort<br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> Code Bundesland/Region<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Ländercode<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Konvertierung der Berechtigungen {#rights-conversion}

Berechtigungen werden in Campaign v7 und Campaign Standard unterschiedlich gehandhabt. In Campaign v7 erfolgt die Berechtigungsverwaltung ordnerbasiert, während sie in Campaign Standard auf Zugriffsrechten auf Einheiten basiert (Unternehmens-/geografische Einheiten). Jeder Benutzer von Campaign Standard gehört einer bestimmten Sicherheitsgruppe an, in der die jeweiligen Einschränkungsinformationen enthalten sind. Deshalb muss das Berechtigungssystem von Campaign v7 in jenes von Campaign Standard konvertiert werden. Für die Durchführung dieser Berechtigungskonvertierung gibt es mehrere Möglichkeiten. Unten finden Sie ein Beispiel dafür.

1. Verwenden Sie **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]** die **[!UICONTROL Synchronize]** Schaltfläche zum Abrufen aller Campaign Standard-Sicherheitsgruppen. Vordefinierte Campaign Standard-Gruppen sind ausgeschlossen.

   ![](assets/acs_connect_implementation_4.png)

1. Wenn die Rights Management auf einer Ordnerbasis ausgeführt wird, navigieren Sie zu **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** und ordnen Sie jeden erforderlichen Ordner einer Sicherheitsgruppe zu.

   ![](assets/acs_connect_implementation_5.png)

1. Diese Informationen werden dann in den Replikations-Workflows verwendet, um jedem zu replizierenden Objekt die entsprechenden Unternehmens-/geografischen Einheiten hinzuzufügen.

### Erweiterte Implementierung {#advanced-implementation}

In diesem Abschnitt werden einige Möglichkeiten beschrieben, die die erweiterte Implementierung bietet.

>[!CAUTION]
>
>Diese Informationen sind nur als allgemeine Richtlinien zu verstehen. Wenden Sie sich bitte bezüglich der Implementierung an Ihren Adobe Campaign-Consultant.

Mit der erweiterten Implementierung werden entsprechend den Kundenbedürfnissen benutzerdefinierte Replikations-Workflows hinzugefügt. Hier sind einige Beispiele:

* Versandreplikation
* Kampagnenreplikation
* Programmreplikation
* Testadressenreplikation
* Transaktionsreplikation
* etc.

**Replizieren erweiterter Empfängerfelder**

Mit der einfachen Implementierung werden die vordefinierten Empfängerfelder repliziert. Wenn Sie benutzerdefinierte, zum Empfängerschema hinzugefügte Felder replizieren möchten, müssen Sie diese identifizieren.

1. Erstellen Sie **[!UICONTROL Administration > ACS Connector > Data mapping]** unter der Tabelle eine Targeting-Zuordnung **[!UICONTROL nms:recipient]** .

   ![](assets/acs_connect_implementation_6.png)

1. Wählen Sie die zusätzlichen zu replizierenden Felder und sonstige benötigte Informationen aus (Index, Links, Identifizierungsschlüssel).

   ![](assets/acs_connect_implementation_7.png)

1. Öffnen Sie den dedizierten Arbeitsablauf zur Profilreplikation (nicht die Vorlage, sondern die Workflow-Instanz selbst). Ändern Sie die Felder **[!UICONTROL Query]** und **[!UICONTROL Update data]** Aktivitäten, um sie einzuschließen. See [Technical and replication workflows](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**Replizieren benutzerdefinierter Profiltabellen**

Mit der einfachen Implementierung wird die vordefinierte Empfängertabelle repliziert. Wenn Sie benutzerdefinierte Empfängertabellen hinzugefügt haben, identifizieren Sie sie folgendermaßen:

1. Erstellen Sie **[!UICONTROL Administration > ACS Connector > Data mapping]** unter &quot;Erstellen&quot;eine Targeting-Zuordnung in Ihrer benutzerdefinierten Profiltabelle.

   ![](assets/acs_connect_implementation_10.png)

1. Definieren Sie die Identifizierungsdaten, den Index, die Links und die Felder, die Sie replizieren möchten.

   ![](assets/acs_connect_implementation_10.png)

1. Wenn Ihre Rights Management ordnerbasiert ist, gehen Sie zu **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** und definieren Sie eine Sicherheitsgruppe für die Ordner, die mit Ihren benutzerdefinierten Tabellen verknüpft sind. Siehe [Rights-Konvertierung](#rights-conversion).
1. Use the **[!UICONTROL New replication]** workflow (not the template, but the workflow instance itself) to include the custom table and the fields to replicate. See [Technical and replication workflows](#technical-and-replication-workflows).

