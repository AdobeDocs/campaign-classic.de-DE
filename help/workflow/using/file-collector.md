---
product: campaign
title: Datei-Wächter
description: Erfahren Sie mehr über die Workflow-Aktivität "Datei-Wächter".
feature: Workflows, Data Management
hide: true
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
TQID: https://experienceleague.adobe.com/P10IkPnf-FyMoIdOZ-t5zUCGN7PL-KPrfn9PgVmHlNk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 565
ht-degree: 100%

---

# Datei-Wächter{#file-collector}



Der **Datei-Wächter** überwacht ein Verzeichnis und aktiviert die Transition der Aktivität bei jedem neuen Eingang von Dateien. Für jedes Ereignis ist der vollständige Name der empfangenen Datei in einer **[!UICONTROL filename]**-Variablen angegeben. Die erfassten Dateien werden zu Archivierungszwecken in ein anderes Verzeichnis verschoben, um sicherzustellen, dass sie nur einmal gezählt werden.

Standardmäßig ist der Datei-Wächter eine persistente Aufgabe, die zu den in der Planung definierten Zeitpunkten das Verzeichnis auf das Vorhandensein von Dateien prüft.

Die Dateien müssen sich auf dem Server befinden, auf dem das wfserver-Modul des betreffenden Workflows ausgeführt wird. Wenn verschiedene wfserver-Module auf derselben Instanz bereitgestellt werden, muss entweder die Affinität der die Dateien verwendenden Aktivitäten oder die des Workflows angegeben werden.

## Eigenschaften {#properties}

Auf dem ersten Tab der Aktivität **[!UICONTROL Datei-Wächter]** können Sie den Quellordner auswählen und die erfassten Dateien bei Bedarf filtern. Die anderen Tabs werden unter [E-Mail-Empfang](inbound-emails.md) (auf den Tabs **[!UICONTROL Planung]** und **[!UICONTROL Ablauf]**) ausführlich beschrieben.

![](assets/file_collect_edit.png)

1. **Abruf der Dateien**

   * **[!UICONTROL Verzeichnis]**

     Ordner, der die herunterzuladende(n) Datei(en) enthält. Das Verzeichnis muss zuvor auf dem Server erstellt worden sein. Wenn es nicht existiert, wird ein Fehler ausgelöst.

   * **[!UICONTROL Filter]**

     Nur Dateien, die diesem Filter entsprechen, werden berücksichtigt. Die anderen Dateien im Verzeichnis werden ignoriert. Wenn kein Filter definiert wurde, werden alle im Verzeichnis enthaltenen Dateien berücksichtigt. Filterbeispiele: **&#42;.zip**, **import-&#42;.txt**.

   * **[!UICONTROL Stoppen, sobald eine Datei bearbeitet wurde]**

     Wenn diese Option aktiviert ist, endet die Aufgabe nach Erhalt der ersten Datei. Wenn mehrere dem Filter entsprechende Dateien im Verzeichnis vorhanden sind, wird nur eine berücksichtigt. Diese Option garantiert, dass nur ein Ereignis gesendet wird. Die berücksichtigte Datei ist die erste in der Liste in alphabetischer Reihenfolge.

     Im Falle einer Aktivität, für die keine Planung definiert wurde, wird ein Fehler erzeugt, wenn keine Datei den Filterkriterien entspricht und die Option **[!UICONTROL Fehlen von Dateien bearbeiten]** nicht aktiviert wurde.

   * **[!UICONTROL Planung]**

     Definiert mithilfe der im Tab **[!UICONTROL Planung]** angegebenen Parameter die Häufigkeit, mit der das Verzeichnis auf die Existenz von Dateien überprüft wird.

1. **Umgang mit Fehlern**

   Zwei Optionen stehen zur Verfügung:

   * **[!UICONTROL Fehlen von Dateien verarbeiten]**

     Bei Ankreuzen dieser Option erscheint eine spezifische Transition, die immer dann aktiviert wird, wenn keine dem Filter entsprechende Datei im angegebenen Verzeichnis vorhanden ist.

     Wenn für die Aufgabe keine Planung definiert wurde, wird diese Transition nur einmal aktiviert.

   * **[!UICONTROL Fehler verarbeiten]**

     Mit dieser Option wird eine spezielle Transition angezeigt, die aktiviert wird, wenn ein Fehler generiert wird. In diesem Fall ändert sich der Workflow nicht in den Fehlerstatus und wird weiter ausgeführt.

     Dies gilt für Fehler des Dateisystems (Datei kann nicht verschoben werden, Zugriff auf das Verzeichnis nicht möglich usw.).

     Fehler, die aus der Konfiguration der Aktivität resultieren, beispielsweise durch Angabe von ungültigen Werten (z. B. inexistentes Verzeichnis), werden nicht verarbeitet.

1. **Verlauf**

   Informationen zum Schritt **[!UICONTROL Verlaufserstellung]** finden Sie unter [HTTP-Übertragung](web-download.md).

Die Reihenfolge der Dateiverarbeitung kann nicht beeinflusst werden. Um eine Reihe von Dateien schrittweise zu verarbeiten, kann die Option **[!UICONTROL Stoppen, sobald eine Datei bearbeitet wurde]** in Verbindung mit einer Schlaufe verwendet werden. In diesem Fall werden die Dateien in alphabetischer Reihenfolge verarbeitet. Die Option **[!UICONTROL Fehlen von Dateien bearbeiten]** beendet die Schlaufe.

![](assets/file_collect_loop.png)

## Ausgabeparameter {#output-parameters}

* filename: vollständiger Dateiname. Dies ist der Dateiname, nachdem er in das Historisierungsverzeichnis verschoben wurde. Der Pfad ist daher anders; der Name unterscheidet sich jedoch ebenfalls, wenn in dem Verzeichnis bereits eine andere Datei mit demselben Namen vorhanden ist. Die Erweiterung bleibt erhalten.
