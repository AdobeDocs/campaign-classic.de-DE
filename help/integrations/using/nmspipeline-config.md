---
title: Integration konfigurieren
seo-title: Integration konfigurieren
description: Integration konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9957dabca4c63d504a3d06cf527a97b79fee46d5
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---


# Pipeline-Option NmsPipeline_Config {#nmspipeline_config}

Sobald die Authentifizierung funktioniert, können die Ereignis per Pipeline abgerufen und verarbeitet werden. Es verarbeitet nur Auslöser, die in Adobe Campaign konfiguriert sind, wobei die anderen ignoriert werden. Der Auslöser muss aus Analytics erzeugt und zuvor in die Pipeline gedrängt worden sein.
Die Option kann auch mit einem Platzhalter konfiguriert werden, um alle Auslöser unabhängig vom Namen abzufangen.

Die Konfiguration der Auslöser erfolgt in einer Option unter **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Optionen]**. Der Optionsname lautet **[!UICONTROL NmsPipeline_Config]**. Der Datentyp ist &quot;langer Text&quot;im JSON-Format.

In diesem Beispiel werden zwei Auslöser angegeben.

Fügen Sie den JSON-Code aus dieser Vorlage in den Optionswert ein. Entfernen Sie unbedingt die Kommentare.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

In diesem zweiten Beispiel werden alle Auslöser erfasst.

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>Der [!DNL Trigger] UID-Wert für einen bestimmten Auslösernamen in der Analytics-Oberfläche kann als Teil der URL-Abfrageparameter in der Trigger-Oberfläche gefunden werden. Die UID &quot;triggerType&quot;wird im Pipeline-Datenstrom übergeben und der Code kann in die Spalte &quot;ipeline.JS&quot;geschrieben werden, um die Auslöser-UID einer benutzerfreundlichen Beschriftung zuzuordnen, die in einer Spalte &quot;Auslösername&quot;im Schema &quot;pipeevents&quot;gespeichert werden kann.

## Der Parameter &quot;Consumer&quot; {#consumer-parameter}

Die Pipeline arbeitet mit einem &quot;Lieferanten- und Verbrauchermodell&quot;. Es kann viele Verbraucher in der gleichen Warteschlange geben. Nachrichten werden nur für einzelne Kunden &quot;konsumiert&quot;. Jeder Verbraucher erhält seine eigene &quot;Kopie&quot; der Nachrichten.

Der Parameter &quot;Consumer&quot;identifiziert die Instanz als einen dieser Verbraucher. Es ist die Identität der Instanz, die die Pipeline aufruft. Sie können ihn mit dem Instanznamen füllen. Der Pipeline-Dienst verfolgt die von jedem Verbraucher abgerufenen Nachrichten. Durch die Verwendung unterschiedlicher Konsumenten für verschiedene Instanzen wird sichergestellt, dass jede Nachricht an jede Instanz gesendet wird.

## Konfigurieren der Pipeline-Option {#configure-pipeline-option}

Auslöser von Experience Clouden Hinzufügen oder bearbeiten unter dem Array &quot;Auslöser&quot;; Bearbeiten Sie nicht den Rest.
Vergewissern Sie sich, dass JSON mithilfe dieser [Website](http://jsonlint.com/)gültig ist.

* &quot;name&quot;ist die Auslöser-ID. Ein Platzhalter (*) fängt alle Auslöser.
* &quot;Consumer&quot;ist eine eindeutige Zeichenfolge, die die Instanz &quot;nlserver&quot;eindeutig identifiziert. Normalerweise kann es sich um den Instanznamen selbst handeln. Bei mehreren Umgebung (dev/stage/prod) müssen Sie sicherstellen, dass sie für jede einzelne Instanz eindeutig sind, damit jede Instanz eine Kopie der Nachricht erhält.
* Pipelinated unterstützt auch das Thema &quot;Aliase&quot;.

Starten Sie die Pipeline neu, nachdem Sie Änderungen vorgenommen haben.
