---
product: campaign
title: Häufig gestellte Fragen zu Campaign-Einstellungen
description: Häufig gestellte Fragen zu Campaign Classic
feature: Troubleshooting, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Campaign-Einstellungen {#settings-faq}



Hier erfahren Sie die wichtigsten Informationen zur Konfiguration, um Ihre Campaign-Instanz an Ihre Anforderungen anzupassen.

## Kann ich die Sprache der Benutzeroberfläche von Campaign ändern? {#can-i-change-the-language-of-campaign-interface-}

Die Sprache von Campaign wird zum Zeitpunkt der Instanzenerstellung gewählt. Danach kann sie nicht mehr geändert werden. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../installation/using/creating-an-instance-and-logging-on.md).

Die Benutzeroberfläche von Adobe Campaign ist in vier Sprachen verfügbar: Englisch, Französisch, Deutsch und Japanisch. Bitte beachten Sie, dass für die Clientkonsole und den Server dieselbe Sprache gewählt werden muss. Jede Campaign-Instanz kann nur in einer einzigen Sprache ausgeführt werden.

Für Englisch können Sie bei der Installation von Campaign entweder die US-amerikanische oder britische Variante wählen. Die beiden Varianten unterscheiden sich durch ihr Datums- und Uhrzeitformat. Weiterführende Informationen zu den Unterschieden finden Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Kann ich Campaign Classic mit anderen Adobe-Lösungen kombinieren? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Sie können die Versand- und Kampagnenverwaltungsfunktionen von Adobe Campaign mit verschiedenen Lösungen kombinieren und damit das Kundenerlebnis personalisieren.

[Hier erfahren Sie, wie Sie andere Adobe-Lösungen einbinden](../../integrations/using/about-campaign-integrations.md) und [IMS in Campaign einrichten](../../integrations/using/about-adobe-id.md).

## Wie kann ich Tracking-Funktionen in meiner Campaign-Instanz einrichten? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Erfahrene Benutzer können die Tracking-Funktionen in der Campaign-Instanz konfigurieren.

[Hier erfahren Sie mehr darüber](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Wie kann ich den E-Mail-Versand konfigurieren? {#how-to-configure-email-deliverability-}

Lesen Sie zusätzlich zum [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de) die technischen Empfehlungen zur Zustellbarkeit, um zu verstehen, wie Sie Ihre Instanz so konfigurieren, dass die Versandfunktionen in Campaign optimal eingerichtet sind.

[Hier erfahren Sie mehr darüber](../../delivery/using/about-deliverability.md).

## Wie kann ich die Inhaltsvalidierung implementieren? {#how-can-i-implement-content-approval-}

Campaign ermöglicht den Einsatz von kollaborativen Validierungsprozessen für die wichtigsten Etappen einer Marketing-Kampagne. Sie können in jeder Kampagne die Zielgruppe der Sendungen, deren Inhalte sowie die anfallenden Kosten validieren. Adobe Campaign-Benutzer können per E-Mail von einer ausstehenden Validierung benachrichtigt werden und diese über die Konsole oder eine Internet-Verbindung akzeptieren oder ablehnen.

[Hier erfahren Sie mehr darüber](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries), wie Sie die Inhaltsvalidierung von Sendungen in Campaign implementieren können.

## Wie kann ich auf in einer externen Datenbank gespeicherte Daten zugreifen? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign bietet die Option Federated Data Access (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

[Hier erfahren Sie mehr darüber](../../installation/using/connecting-to-database.md).

## Welche externen Datenbanken kann ich mit Campaign verknüpfen? {#which-external-databases-can-i-connect-campaign-to-}

Externe Datenbanken, die über Federated Data Access (FDA) mit Campaign kompatibel sind, sind in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgelistet.

## Kann Adobe Campaign mit LDAP integriert werden? {#can-adobe-campaign-integrate-with-ldap-}

On-Premise-/Hybrid-Kunden können Campaign mit ihrem LDAP-Verzeichnis integrieren.

[Hier erfahren Sie mehr darüber](../../installation/using/connecting-through-ldap.md).

## Wie kann ich in Campaign CRM-Connectoren einrichten? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign stellt verschiedene CRM-Connectoren zur Verfügung, die die Verbindung der Adobe Campaign-Plattform mit Drittsystemen ermöglichen. So erlauben die CRM-Connectoren z. B. das Synchronisieren von Kontakten, Konten und Bestellungen. Zudem vereinfachen sie die Integration der Anwendung in bestehende Systeme.

Dank der Connectoren ist eine schnelle und einfache Datenintegration möglich. Mithilfe eines spezifischen Assistenten lassen sich Daten aus den im CRM-System verfügbaren Tabellen auswählen und sammeln. Die Zwei-Wege-Synchronisation der Informationen gewährleistet einen einheitlichen Datenstand auf den verschiedenen Systemen.

Informationen zum Synchronisieren Ihres CRM-Tools mit Adobe Campaign finden Sie unter [CRM-Connectoren konfigurieren](../../platform/using/crm-connectors.md).

![](assets/do-not-localize/how-to-video.png) In diesem Anwendungsfallvideo finden Sie Informationen zur [Integration von Adobe Campaign und Microsoft Dynamics 365](https://helpx.adobe.com/de/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Wie kann der Soft Cache gelöscht werden, wenn die Probleme gerätespezifisch oder benutzerspezifisch sind? {#perform-soft-cache-clear}

Wenn Sie zum Beispiel Probleme damit haben, neue Logos richtig darzustellen oder die Daten, die spezifisch für Rechner und Benutzer sind, erfolgreich zu exportieren, müssen Sie möglicherweise mit Windows (Windows 7, Windows XP, Windows 10) eine Soft-Cache-Löschung durchführen.

Gehen Sie nach der Anmeldung zu **[!UICONTROL Datei]** > **[!UICONTROL Lokalen Cache leeren...]**. Melden Sie sich anschließend ab und wieder an.

![](assets/faq_soft_cache.png)

Wenn auch das nicht hilft, versuchen Sie, den Hard Cache zu löschen, indem Sie die folgenden Schritte ausführen.

## Wie kann der Hard Cache gelöscht werden, wenn die Probleme rechnerspezifisch oder benutzerspezifisch sind? {#perform-hard-cache-clear}

Wenn Sie zum Beispiel Probleme damit haben, neue Logos richtig darzustellen oder die Daten, die spezifisch für Rechner und Benutzer sind, erfolgreich zu exportieren, müssen Sie möglicherweise mit Windows (Windows 7, Windows XP, Windows 10) eine Hard-Cache-Löschung vornehmen.

1. Wählen Sie dazu in der Client-Konsole **[!UICONTROL Datei]** > **[!UICONTROL Lokalen Cache löschen]** aus.

1. Melden Sie sich ab und schließen Sie die Client-Konsole (Rich-Client).

1. Gehen Sie je nach Betriebssystemversion zu den folgenden Speicherorten:

   * Windows 7: C:\Users\ &lt; Benutzername > \AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\ &lt; Benutzername > \Application Data\Neolane\NL_5

   Hier sehen Sie viele XML-Dateien namens „nlclient-config-&lt; alphanumerischer Wert >.xml“.

1. Löschen Sie diese XML-Dateien und die zugehörigen Ordner.

   >[!IMPORTANT]
   >
   >Löschen Sie jedoch nicht die Datei „nlclient_cnx.xml“.

1. Melden Sie sich bei der Clientkonsole an.
