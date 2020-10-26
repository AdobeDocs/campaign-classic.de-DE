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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '381'
ht-degree: 100%

---


# Pipeline-Option &quot;NmsPipeline_Config&quot;{#nmspipeline_config}

Sobald die Authentifizierung funktioniert, kann [!DNL pipelined] die Ereignisse abrufen und verarbeiten. Verarbeitet werden nur Auslöser, die in Adobe Campaign konfiguriert wurden; andere werden ignoriert. Der Auslöser muss zuvor mit Analytics erzeugt und in die Pipeline gepusht worden sein.
Die Option kann auch mit einem Platzhalter konfiguriert werden, um alle Auslöser unabhängig vom Namen zu erfassen.

Die Konfiguration der Auslöser erfolgt in einer Option unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]**. Der Optionsname lautet **[!UICONTROL NmsPipeline_Config]**. Der Datentyp ist &quot;Memo&quot; im JSON-Format.

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
>Der [!DNL Trigger]-UID-Wert für einen bestimmten Auslösernamen in der Analytics-Oberfläche wird als Teil der URL-Abfragezeichenfolgen-Parameter in der Auslöser-Oberfläche angezeigt. Die UID &quot;triggerType&quot; wird im Pipeline-Datenstrom weitergeleitet. Außerdem kann Code in die Datei &quot;pipeline.JS&quot; geschrieben werden, um die Auslöser-UID einer anwenderfreundlichen Bezeichnung zuzuordnen, die in einer Spalte namens &quot;Auslösername&quot; im Schema &quot;pipelineEvents&quot; gespeichert werden kann.

## Der Parameter &quot;consumer&quot; {#consumer-parameter}

Die Pipeline arbeitet mit einem &quot;Lieferanten- und Verbrauchermodell&quot;. In einer Warteschlange können viele Verbraucher sein. Nachrichten werden nur für einen einzelnen Verbraucher verwendet. Jeder Verbraucher erhält seine eigene &quot;Kopie&quot; der Nachrichten.

Der Parameter &quot;consumer&quot; identifiziert die Instanz als einen dieser Verbraucher. Die Pipeline wird durch die Identität der Instanz aufgerufen. Sie können den Namen der Instanz eingeben. Der Pipeline-Dienst verfolgt die von jedem Verbraucher abgerufenen Nachrichten. Durch Verwendung unterschiedlicher Verbraucher für verschiedene Instanzen wird sichergestellt, dass jede Nachricht an jede Instanz gesendet wird.

## Konfigurieren der Pipeline-Option {#configure-pipeline-option}

Fügen Sie unter dem Array &quot;Auslöser&quot; Experience Cloud-Auslöser hinzu oder bearbeiten Sie sie. Lassen Sie den Rest unverändert.
Vergewissern Sie sich mithilfe dieser [Website](http://jsonlint.com/), dass die JSON gültig ist.

* &quot;name&quot; ist die Auslöser-ID. Mit einem Platzhalter (*) werden alle Auslöser erfasst.
* &quot;Consumer&quot; ist eine eindeutige Zeichenfolge, die die nlserver-Instanz eindeutig identifiziert. Normalerweise kann dies der Instanzname selbst sein. Bei verschiedenen Umgebungen (dev/stage/prod) müssen Sie jedoch sicherstellen, dass der Name für jede einzelne Instanz eindeutig ist, damit jede Instanz eine Kopie der Nachricht erhält.
* [!DNL Pipelined] unterstützt auch &quot;Aliase&quot;.

Starten Sie [!DNL pipelined] nach Durchführung der Änderungen neu.
