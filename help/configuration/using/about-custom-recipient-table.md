---
product: campaign
title: Über die benutzerdefinierte Empfängertabelle
description: Über die benutzerdefinierte Empfängertabelle
feature: Configuration, Custom Resources
role: User, Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 10%

---

# Verwenden einer benutzerdefinierten Empfängertabelle{#about-custom-recipient-table}

In diesem Abschnitt werden die Grundlagen für die Verwendung einer benutzerdefinierten (oder externen) Empfängertabelle beschrieben.

Standardmäßig bietet Adobe Campaign eine integrierte Empfängertabelle, mit der native Funktionen und Prozesse verknüpft sind. Die integrierte Empfängertabelle verfügt über eine Reihe vordefinierter Felder und Tabellen, die mithilfe einer Erweiterungstabelle einfach erweitert werden können.

Wenn diese Erweiterungsmethode eine gute Flexibilität beim Erweitern einer Tabelle bietet, lässt sie keine Verringerung der Anzahl der Felder oder Links in der Tabelle zu. Die Verwendung einer nicht standardmäßigen Tabelle oder &quot;externen Empfängertabelle&quot;ermöglicht eine größere Flexibilität, erfordert jedoch bei der Implementierung bestimmte Vorsichtsmaßnahmen.

Diese Funktion ermöglicht es Adobe Campaign, Daten aus einer externen Datenbank zu verarbeiten. Diese Daten werden als ein Satz von Profilen für den Versand verwendet. Die Implementierung dieses Prozesses umfasst mehrere Präzisionen, die je nach den Anforderungen des Kunden relevant sein können. Beispiel:

* Kein Update-Stream zur und von der Adobe Campaign-Datenbank: Daten aus dieser Tabelle können direkt über die Datenbank-Engine aktualisiert werden, die sie hostet.
* Keine Änderungen an den Prozessen, die mit der vorhandenen Datenbank ausgeführt werden.
* Bei Verwendung einer Profildatenbank ohne Standardstruktur: Es besteht die Möglichkeit, dass der Versand an in verschiedenen Tabellen mit unterschiedlichen Strukturen gespeicherte Profile erfolgt, wobei eine einzelne Instanz verwendet wird.
* Beim Aktualisieren der Adobe Campaign-Datenbank sind keine Änderungen oder Wartungsarbeiten erforderlich.
* Die integrierte Empfängertabelle ist nutzlos, wenn Sie die meisten Tabellenfelder nicht benötigen oder die Datenbankvorlage nicht auf die Empfänger zentriert ist.
* Um effizient zu sein, ist eine Tabelle mit einigen Feldern erforderlich, wenn Sie über eine erhebliche Anzahl von Profilen verfügen. Die integrierte Empfängertabelle verfügt für diesen Fall über zu viele Felder.

In diesem Abschnitt werden die wichtigsten Punkte beschrieben, anhand derer Sie vorhandene Tabellen in Adobe Campaign zuordnen können, sowie die Konfiguration, die für die Ausführung von Sendungen auf der Basis einer beliebigen Tabelle angewendet werden soll. Schließlich wird beschrieben, wie Sie Benutzern so praktische Abfragen wie in der integrierten Empfängertabelle ermöglichen. Um das in diesem Abschnitt dargestellte Material zu verstehen, sind gute Kenntnisse der Prinzipien des Bildschirms und Schemadesigns erforderlich.

## Empfehlungen und Einschränkungen            {#recommendations-and-limitations}

Die Verwendung einer benutzerdefinierten Empfängertabelle unterliegt folgenden Einschränkungen:

* Adobe Campaign unterstützt nicht mehrere Empfängerschemata, so genannte Zielgruppenschemas, die mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Dies kann andernfalls zu Anomalien bei der Datenabstimmung später führen.

  Die nachstehende Abbildung zeigt die erforderliche relationale Struktur für jedes benutzerdefinierte Empfängerschema:
  ![](assets/custom_recipient_limitation.png)

  Wir empfehlen:

   * Zuweisung der Schemas **[!UICONTROL nms:BroadLogRcp]** und **[!UICONTROL nms:TrackingLogRcp]** zu den nativen Schemas **[!UICONTROL nms:Recipientschema]**. Diese beiden Protokolltabellen sollten keiner zusätzlichen benutzerdefinierten Empfängertabelle zugeordnet werden.
   * Definieren dedizierter benutzerdefinierter Broadlog- und Trackinglog-Schemata für jedes neue benutzerdefinierte Empfängerschema. Dies kann automatisch bei der Einrichtung des Zielgruppen-Mappings erfolgen, siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md).

* Sie können die im Produkt angebotenen standardmäßigen **[!UICONTROL Dienste und Abonnements]** nicht verwenden.

  Das bedeutet, dass der in [diesem Abschnitt](../../delivery/using/managing-subscriptions.md) beschriebene Gesamtvorgang nicht anwendbar ist.

* Die Verknüpfung mit der Tabelle **[!UICONTROL visitor]** funktioniert nicht.

  Um das Modul **[!UICONTROL Social Marketing]** zu verwenden, müssen Sie daher den Speicherschritt so konfigurieren, dass er auf die richtige Tabelle verweist.

  Ebenso muss bei Verwendung von Verweisfunktionen die Standardvorlage für die Erstübermittlung von Nachrichten angepasst werden.

* Es ist nicht möglich, Profile manuell in eine Liste einzufügen.

  Daher ist das in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md) beschriebene Verfahren ohne zusätzliche Konfiguration nicht anwendbar.

  >[!NOTE]
  >
  >Sie können weiterhin Empfängerlisten mithilfe von Workflows erstellen. Weitere Informationen hierzu finden Sie unter [Erstellen einer Profilliste mit einem Workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Es wird außerdem empfohlen, die in den verschiedenen nativen Konfigurationen verwendeten Standardwerte zu überprüfen: Je nach den verwendeten Funktionen müssen verschiedene Anpassungen vorgenommen werden.

Beispiel:

* Bestimmte Standardberichte, insbesondere die von **Interaction** und den **Mobile Apps** angebotenen, müssen überarbeitet werden. Siehe Abschnitt [Verwalten von Berichten](../../configuration/using/managing-reports.md) .
* Die Standardkonfigurationen für bestimmte Workflow-Aktivitäten beziehen sich auf die standardmäßige Empfängertabelle (**[!UICONTROL nms:recipient]**): Diese Konfigurationen müssen geändert werden, wenn sie für eine externe Empfängertabelle verwendet werden. Siehe Abschnitt [Verwalten von Workflows](../../configuration/using/managing-workflows.md) .
* Der standardmäßige Gestaltungsbaustein **[!UICONTROL Abmelde-Link]** muss angepasst werden.
* Das Zielgruppen-Mapping der Standard-Versandvorlagen muss geändert werden.
* V4-Formulare sind nicht für die Verwendung mit externen Empfängertabellen kompatibel: Sie müssen Webanwendungen verwenden.
