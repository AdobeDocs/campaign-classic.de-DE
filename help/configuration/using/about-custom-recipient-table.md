---
solution: Campaign Classic
product: campaign
title: Über die benutzerdefinierte Empfängertabelle
description: Über die benutzerdefinierte Empfängertabelle
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 2%

---


# Über die benutzerdefinierte Empfängertabelle{#about-custom-recipient-table}

In diesem Abschnitt werden die Grundsätze für die Verwendung einer nicht standardmäßigen Empfänger-Tabelle erläutert.

Standardmäßig wird von Adobe Campaign eine Standardtabelle für Empfänger Angebot, mit der vordefinierte Funktionen und Prozesse verknüpft sind. Die Standardtabelle für Empfänger enthält eine Reihe vordefinierter Felder und Tabellen, die mit einer Erweiterungstabelle leicht erweitert werden können.

Wenn diese Erweiterungsmethode eine gute Flexibilität beim Erweitern einer Tabelle Angebot, lässt sie keine Verringerung der Anzahl der Felder oder Links darin zu. Die Verwendung einer nicht standardmäßigen Tabelle oder einer &quot;externen Empfänger-Tabelle&quot;ermöglicht eine größere Flexibilität, erfordert jedoch bei der Implementierung bestimmte Vorsichtsmaßnahmen.

## Präzisionen {#precisions}

Mit dieser Funktion kann Adobe Campaign Daten aus einer externen Datenbank verarbeiten: Diese Daten werden als eine Reihe von Profilen für Versand verwendet. Die Implementierung dieses Prozesses umfasst mehrere Präzisionen, die je nach Bedarf des Kunden relevant sein können. Wie zum Beispiel:

* Kein Updatestream zur und von der Adobe Campaign-Datenbank: Daten aus dieser Tabelle können direkt über die Datenbank-Engine aktualisiert werden, die sie hostet.
* Es wurden keine Änderungen an den Prozessen vorgenommen, die auf der vorhandenen Datenbank ausgeführt werden.
* Verwenden einer Profil-Datenbank mit einer nicht standardmäßigen Struktur: Möglichkeit, Profil, die in verschiedenen Tabellen mit verschiedenen Strukturen gespeichert sind, mit einer einzigen Instanz zu liefern.
* Beim Aktualisieren der Adobe Campaign-Datenbank sind keine Änderungen oder Wartungsarbeiten erforderlich.
* Die Standardtabelle für Empfänger ist nutzlos, wenn Sie die meisten Tabellenfelder nicht benötigen oder wenn die Datenbankvorlage nicht auf den Empfängern zentriert ist.
* Um effizient zu sein, ist eine Tabelle mit wenigen Feldern erforderlich, wenn Sie über eine beträchtliche Anzahl von Profilen verfügen. Die Standardtabelle für Empfänger enthält zu viele Felder für diesen speziellen Fall.

In diesem Abschnitt werden die Schlüsselpunkte beschrieben, mit denen Sie vorhandene Tabellen in Adobe Campaign zuordnen können, sowie die Konfiguration, die für die Ausführung von Versänden auf der Grundlage einer beliebigen Tabelle gelten soll. Schließlich wird beschrieben, wie Sie Benutzern so praktische Abfrageschnittstellen wie in der Standardtabelle für Empfänger zur Verfügung stellen. Um das in diesem Abschnitt dargestellte Material zu verstehen, ist eine gute Kenntnis der Prinzipien der Bildschirm- und Schema-Design erforderlich.

## Empfehlungen und Einschränkungen         {#recommendations-and-limitations}

Die Verwendung einer Tabelle mit einem externen Empfänger unterliegt folgenden Einschränkungen:

* Adobe Campaign unterstützt nicht mehrere Empfänger-Schema, die als Targeting-Schema bezeichnet werden und mit denselben Broadlog- und/oder Trackinglog-Schemas verknüpft sind. Andernfalls kann dies zu Anomalien bei der Datenabstimmung im Anschluss führen.

   Die nachstehende Abbildung zeigt die erforderliche relationale Struktur für jedes benutzerdefinierte Empfänger-Schema:
   ![](assets/custom_recipient_limitation.png)

   Wir empfehlen:

   * Deaktivieren Sie die Schema **[!UICONTROL nms:BroadLogRcp]** und **[!UICONTROL nms:TrackingLogRcp]** in das vordefinierte **[!UICONTROL nms:Recipientschema]**. Diese beiden Protokolltabellen sollten nicht mit einer zusätzlichen Tabelle mit benutzerdefiniertem Empfänger verknüpft werden.
   * Definieren dedizierter benutzerdefinierter Broadlog- und Trackinglog-Schema für jedes neue benutzerdefinierte Empfänger-Schema. Dies kann beim Einrichten des Zielgruppen-Mappings automatisch erfolgen, siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md).

* Sie können nicht den Standard **[!UICONTROL Dienste und Abonnement]** verwenden, der im Produkt angeboten wird.

   Das bedeutet, dass der unter [dieser Abschnitt](../../delivery/using/managing-subscriptions.md) beschriebene Gesamtvorgang nicht anwendbar ist.

* Die Verknüpfung mit der Tabelle **[!UICONTROL Besucher]** funktioniert nicht.

   Um das Modul **[!UICONTROL Social Marketing]** zu verwenden, müssen Sie den Schritt &quot;Datenspeicherung&quot;so konfigurieren, dass auf die richtige Tabelle verwiesen wird.

   Bei Verwendung der Verweisfunktionen muss die Standardvorlage für die Erstübermittlung von Nachrichten entsprechend angepasst werden.

* Profil können nicht manuell in eine Liste eingefügt werden.

   Daher ist das in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md) beschriebene Verfahren ohne zusätzliche Konfiguration nicht anwendbar.

   >[!NOTE]
   >
   >Sie können Empfänger-Listen weiterhin mit Workflows erstellen. Weitere Informationen finden Sie unter [Erstellen einer Profil-Liste mit einem Workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Es wird außerdem empfohlen, die Standardwerte zu überprüfen, die in den verschiedenen vordefinierten Konfigurationen verwendet werden: Je nach den verwendeten Funktionen müssen mehrere Anpassungen vorgenommen werden.

Beispiel:

* Bestimmte Standardberichte, insbesondere die von **Interaktion** und **Mobilanwendungen** angebotenen, müssen neu entwickelt werden. Siehe Abschnitt [Verwalten von Berichten](../../configuration/using/managing-reports.md).
* Die Standardkonfigurationen für bestimmte Workflow-Aktivitäten verweisen auf die Standardtabelle für Empfänger (**[!UICONTROL nms:Empfänger]**): Diese Konfigurationen müssen geändert werden, wenn sie für eine Tabelle mit externen Empfängern verwendet werden. Siehe Abschnitt [Verwalten von Workflows](../../configuration/using/managing-workflows.md).
* Der standardmäßige Personalisierungsblock **[!UICONTROL Abmeldung]** muss angepasst werden.
* Das Zielgruppen-Mapping der Standard-Versandvorlagen muss geändert werden.
* V4-Formulare sind nicht für die Verwendung mit externen Empfängern kompatibel: müssen Sie Webanwendungen verwenden.

