---
title: Informationen zur Tabelle "Benutzerdefinierte Empfänger"
seo-title: Informationen zur Tabelle "Benutzerdefinierte Empfänger"
description: Informationen zur Tabelle "Benutzerdefinierte Empfänger"
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# Informationen zur Tabelle &quot;Benutzerdefinierte Empfänger&quot;{#about-custom-recipient-table}

In diesem Abschnitt werden die Grundsätze für die Verwendung einer nicht standardmäßigen Empfängertabelle erläutert.

Adobe Campaign bietet standardmäßig eine Standard-Empfängertabelle, mit der vordefinierte Funktionen und Prozesse verknüpft werden. Die Standard-Empfängertabelle verfügt über eine Reihe vordefinierter Felder und Tabellen, die mit einer Erweiterungstabelle leicht erweitert werden können.

Wenn diese Erweiterungsmethode eine Tabelle flexibel erweitern kann, lässt sie keine Verringerung der Anzahl der Felder oder Links in ihr zu. Die Verwendung einer nicht standardmäßigen Tabelle oder einer &quot;externen Empfängertabelle&quot;ermöglicht eine größere Flexibilität, erfordert jedoch bei der Implementierung bestimmte Vorsichtsmaßnahmen.

## Abstände {#precisions}

Mit dieser Funktion kann Adobe Campaign Daten aus einer externen Datenbank verarbeiten: Diese Daten werden als Profilsatz für Lieferungen verwendet. Die Implementierung dieses Prozesses umfasst mehrere Präzisionen, die je nach Bedarf des Kunden relevant sein können. Beispiel:

* Kein Updatestream zur und aus der Adobe Campaign-Datenbank: Daten aus dieser Tabelle können direkt über die Datenbank-Engine aktualisiert werden, die sie hostet.
* Keine Änderungen an den Prozessen, die auf der vorhandenen Datenbank ausgeführt werden.
* Verwenden einer Profildatenbank mit einer nicht standardmäßigen Struktur: Möglichkeit der Bereitstellung von Profilen in verschiedenen Tabellen mit verschiedenen Strukturen unter Verwendung einer einzigen Instanz.
* Beim Aktualisieren der Adobe Campaign-Datenbank sind keine Änderungen oder Wartungsarbeiten erforderlich.
* Die standardmäßige Empfängertabelle ist nutzlos, wenn Sie die meisten Tabellenfelder nicht benötigen oder wenn die Datenbankvorlage nicht auf die Empfänger zentriert ist.
* Um effizient zu sein, ist eine Tabelle mit wenigen Feldern erforderlich, wenn Sie über eine beträchtliche Anzahl von Profilen verfügen. Die standardmäßige Empfängertabelle enthält zu viele Felder für diesen speziellen Fall.

In diesem Abschnitt werden die Schlüsselpunkte beschrieben, mit denen Sie vorhandene Tabellen in Adobe Campaign zuordnen können, sowie die Konfiguration, die für die Ausführung von Auslieferungen auf der Grundlage einer beliebigen Tabelle gelten soll. Schließlich wird beschrieben, wie Sie Benutzern so praktische Abfrageschnittstellen wie mit der Standard-Empfängertabelle zur Verfügung stellen. Um das in diesem Abschnitt präsentierte Material zu verstehen, sind gute Kenntnisse der Prinzipien von Bildschirm- und Schemadesign erforderlich.

## Empfehlungen und Einschränkungen  {#recommendations-and-limitations}

Die Verwendung einer externen Empfängertabelle unterliegt folgenden Einschränkungen:

* Adobe Campaign unterstützt nicht mehrere Empfängerschemata, die als Targeting-Schemata bezeichnet werden und mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Andernfalls kann dies zu Anomalien bei der Datenabstimmung im Anschluss führen.

   Die nachstehende Grafik beschreibt die erforderliche relationale Struktur für jedes benutzerdefinierte Empfängerschema:
   ![](assets/custom_recipient_limitation.png)

   Wir empfehlen:

   * Festlegen der **[!UICONTROL nms:BroadLogRcp]** und **[!UICONTROL nms:TrackingLogRcp]** Schemas auf die vordefinierten **[!UICONTROL nms:Recipientschema]** Elemente. Diese beiden Protokolltabellen sollten nicht mit einer zusätzlichen benutzerdefinierten Empfängertabelle verknüpft werden.
   * Definieren dedizierter benutzerdefinierter Broadlog- und Trackinglog-Schemata für jedes neue benutzerdefinierte Empfängerschema. Dies kann beim Einrichten der Zielzuordnung automatisch erfolgen (siehe [Zielzuordnung](../../configuration/using/target-mapping.md)).

* Sie können den im Produkt **[!UICONTROL Services and Subscriptions]** angebotenen Standard nicht verwenden.

   Dies bedeutet, dass der in [diesem Abschnitt](../../delivery/using/managing-subscriptions.md) beschriebene Gesamtbetrieb nicht anwendbar ist.

* Die Verknüpfung mit der **[!UICONTROL visitor]** Tabelle funktioniert nicht.

   Damit Sie das Modul **[!UICONTROLSSocial Marketing]** verwenden können, müssen Sie den Speicherschritt so konfigurieren, dass auf die richtige Tabelle verwiesen wird.

   Bei Verwendung der Verweisfunktionen muss die Standardvorlage für die Erstübermittlung von Nachrichten entsprechend angepasst werden.

* Profile können nicht manuell in einer Liste hinzugefügt werden.

   Daher ist das in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md) beschriebene Verfahren ohne zusätzliche Konfiguration nicht anwendbar.

   >[!NOTE]
   >
   >Sie können Empfängerlisten weiterhin mithilfe von Workflows erstellen. Weitere Informationen finden Sie unter [Erstellen einer Profilliste mit einem Workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Es wird außerdem empfohlen, die Standardwerte in den verschiedenen vordefinierten Konfigurationen zu überprüfen: Je nach den verwendeten Funktionen müssen mehrere Anpassungen vorgenommen werden.

Beispiel:

* Bestimmte Standardberichte, insbesondere die von **Interaction** und den **Mobilanwendungen** angebotenen, müssen überarbeitet werden. Siehe Abschnitt [Verwalten von Berichten](../../configuration/using/managing-reports.md) .
* Die Standardkonfigurationen für bestimmte Workflow-Aktivitäten beziehen sich auf die Tabelle der Standardempfänger (**[!UICONTROL nms:recipient]**): Diese Konfigurationen müssen geändert werden, wenn sie für eine Tabelle mit externen Empfängern verwendet werden. Siehe Abschnitt [Verwalten von Workflows](../../configuration/using/managing-workflows.md) .
* Der Standard- **[!UICONTROL Unsubscription link]** Personalisierungsblock muss angepasst werden.
* Die Zielzuordnung der Standard-Bereitstellungsvorlagen muss geändert werden.
* V4-Formulare sind nicht für die Verwendung mit einer Tabelle mit externen Empfängern kompatibel: müssen Sie Webanwendungen verwenden.

