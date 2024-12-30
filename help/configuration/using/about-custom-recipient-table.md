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

In diesem Abschnitt werden die Prinzipien für die Verwendung einer benutzerdefinierten (oder externen) Empfängertabelle beschrieben.

Standardmäßig bietet Adobe Campaign eine integrierte Empfängertabelle, mit der vordefinierte Funktionen und Prozesse verknüpft sind. Die integrierte Empfängertabelle verfügt über eine Reihe vordefinierter Felder und Tabellen, die mithilfe einer Erweiterungstabelle einfach erweitert werden können.

Wenn diese Erweiterungsmethode eine gute Flexibilität beim Erweitern einer Tabelle bietet, lässt sie nicht zu, die Anzahl der Felder oder Links in ihr zu reduzieren. Die Verwendung einer nicht standardmäßigen Tabelle oder „externen Empfängertabelle“ bietet eine größere Flexibilität, erfordert jedoch bei der Implementierung bestimmte Vorsichtsmaßnahmen.

Diese Funktion ermöglicht es Adobe Campaign, Daten aus einer externen Datenbank zu verarbeiten. Diese Daten werden als ein Satz von Profilen für den Versand verwendet. Die Implementierung dieses Prozesses umfasst mehrere Präzisionen, die je nach den Anforderungen des Kunden relevant sein können. Beispielsweise:

* Kein Update-Stream zur und von der Adobe Campaign-Datenbank: Daten aus dieser Tabelle können direkt über die Datenbank-Engine aktualisiert werden, die sie hostet.
* Keine Änderungen an den Prozessen, die in der vorhandenen Datenbank ausgeführt werden.
* Bei Verwendung einer Profildatenbank ohne Standardstruktur: Es besteht die Möglichkeit, dass der Versand an in verschiedenen Tabellen mit unterschiedlichen Strukturen gespeicherte Profile erfolgt, wobei eine einzelne Instanz verwendet wird.
* Beim Aktualisieren der Adobe Campaign-Datenbank sind keine Änderungen oder Wartungsarbeiten erforderlich.
* Die integrierte Empfängertabelle ist nutzlos, wenn Sie die meisten Tabellenfelder nicht benötigen oder wenn die Datenbankvorlage nicht auf die Empfänger zentriert ist.
* Um effizient zu sein, ist eine Tabelle mit wenigen Feldern erforderlich, wenn Sie eine erhebliche Anzahl von Profilen haben. Die integrierte Empfängertabelle enthält zu viele Felder für diesen speziellen Fall.

In diesem Abschnitt werden die Schlüsselpunkte beschrieben, mit denen Sie bestehende Tabellen in Adobe Campaign zuordnen können, sowie die Konfiguration, die für die Ausführung von Sendungen auf der Grundlage einer beliebigen Tabelle gelten soll. Schließlich wird beschrieben, wie Benutzenden so praktische Schnittstellen zur Verfügung gestellt werden können, wie sie mit der integrierten Empfängertabelle verfügbar sind. Um das in diesem Abschnitt vorgestellte Material zu verstehen, sind gute Kenntnisse der Prinzipien des Bildschirm- und Schemaentwurfs erforderlich.

## Empfehlungen und Einschränkungen            {#recommendations-and-limitations}

Die Verwendung einer benutzerdefinierten Empfängertabelle weist die folgenden Einschränkungen auf:

* Adobe Campaign unterstützt nicht mehrere Empfängerschemata, so genannte Zielgruppenschemata, die mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Dies kann ansonsten zu Anomalien bei der späteren Datenabstimmung führen.

  Die folgende Grafik zeigt die erforderliche relationale Struktur für jedes benutzerdefinierte Empfängerschema:
  ![](assets/custom_recipient_limitation.png)

  Wir empfehlen:

   * die **[!UICONTROL nms:BroadLogRcp]** und **[!UICONTROL nms:TrackingLogRcp]** für das vorkonfigurierte Schema **[!UICONTROL nms:RecipientSchema]**. Diese beiden Protokolltabellen sollten nicht mit einer zusätzlichen benutzerdefinierten Empfängertabelle verknüpft werden.
   * Definieren von dedizierten benutzerdefinierten Broadlog- und Trackinglog-Schemata für jedes neue benutzerdefinierte Empfängerschema. Dies kann beim Einrichten des Zielgruppen-Mappings automatisch erfolgen, siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md).

* Sie können die im Produkt angebotenen **[!UICONTROL Services und Abonnements]** nicht verwenden.

  Dies bedeutet, dass der in [diesem Abschnitt) beschriebene ](../../delivery/using/managing-subscriptions.md) nicht anwendbar ist.

* Die Verknüpfung mit der **[!UICONTROL Besucher]**-Tabelle funktioniert nicht.

  Um das Modul **[!UICONTROL Social Marketing]** verwenden zu können, müssen Sie daher den Speicherschritt so konfigurieren, dass er auf die richtige Tabelle verweist.

  Ebenso muss bei Verwendung von Verweisfunktionen die standardmäßige Vorlage für die anfängliche Nachrichtenübertragung angepasst werden.

* Profile können nicht manuell zu einer Liste hinzugefügt werden.

  Daher ist das in [diesem Abschnitt](../../platform/using/creating-and-managing-lists.md) beschriebene Verfahren ohne eine zusätzliche Konfiguration nicht anwendbar.

  >[!NOTE]
  >
  >Empfängerlisten können weiterhin mithilfe von Workflows erstellt werden. Weitere Informationen hierzu finden Sie unter [ einer Profilliste mit einem Workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Es wird außerdem empfohlen, die in den verschiedenen vordefinierten Konfigurationen verwendeten Standardwerte zu überprüfen: Je nach den verwendeten Funktionen müssen mehrere Anpassungen vorgenommen werden.

Beispiel:

* Bestimmte Standardberichte, insbesondere die von **Interaction** und **Mobile Apps** müssen neu entwickelt werden. Siehe den Abschnitt [Verwalten von Berichten](../../configuration/using/managing-reports.md).
* Die Standardkonfigurationen für bestimmte Workflow-Aktivitäten verweisen auf die standardmäßige Empfängertabelle (**[!UICONTROL nms:recipient]**): Diese Konfigurationen müssen geändert werden, wenn sie für eine externe Empfängertabelle verwendet werden. Siehe den Abschnitt [Verwalten von Workflows](../../configuration/using/managing-workflows.md).
* Der standardmäßige Gestaltungsbaustein **[!UICONTROL Abmelde-Link]** muss angepasst werden.
* Das Zielgruppen-Mapping der Standard-Versandvorlagen muss geändert werden.
* V4-Formulare sind nicht für die Verwendung mit einer externen Empfängertabelle kompatibel: Sie müssen Web-Anwendungen verwenden.
