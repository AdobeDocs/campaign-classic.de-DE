---
product: campaign
title: Anmeldedienste
description: Erfahren Sie mehr über die Workflow-Aktivität "Anmeldedienste".
feature: Workflows, Targeting Activity, Subscription Services Activity
hide: true
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
TQID: 'https://experienceleague.adobe.com/-qfMiHLzlE5uJIV5-ba1MNymo0SHuMYxC6EnurLexI8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
  - id: 2454f09c-f028-5647-8fef-1e986ec2d4e5
    internal-label: Subscription Services Activity
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 100%
---
# Anmeldedienste{#subscription-services}



Über die **Abonnementaktivität** kann eine durch die eingehende Transition bezeichnete Population für einen Informationsdienst angemeldet oder von einem Dienst abgemeldet werden.

Die Konfiguration der Aktivität besteht in der Angabe eines Titels, die Auswahl von Anmeldung oder Abmeldung sowie des betroffenen Informationsdienstes, wie unten abgebildet:

![](assets/edit_service_inscription.png)

1. Benennen Sie die Aktivität.
1. Kreuzen Sie die Option **[!UICONTROL Ausgehende Transition erzeugen an]**, wenn sich weitere Aktivitäten anschließen.

   Im Allgemeinen bildet die Abonnementaktivität den Schlusspunkt eines Workflows. Aus diesem Grund, wird die ausgehende Transition nicht standardmäßig erzeugt.

1. Kreuzen Sie je nach Bedarf **[!UICONTROL Anmeldung]** oder **[!UICONTROL Abmeldung]** an.
1. Aktivieren Sie die Option **[!UICONTROL Benachrichtigung versenden]**, um den Empfänger von seiner An- oder Abmeldung in Kenntnis zu setzen.

   Der Benachrichtigungsinhalt wird in der Versandvorlage des entsprechenden Informationsdienstes definiert. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/managing-subscriptions.md).

## Anwendungsbeispiel: Empfänger einer Liste für einen Newsletter anmelden {#example--subscribe-a-list-of-recipients-to-a-newsletter}

Der folgende Workflow soll in einem einzigen Vorgang eine Liste der Empfänger erstellen, die für einen Newsletter in Frage kommen, der sich an in Paris lebende Berufstätige richtet, um sie zum Abonnieren zu bewegen.

Dabei sollen die Profile, die den Newsletter bereits erhalten, ausgeschlossen werden.

>[!CAUTION]
>
>Bevor Sie Empfänger manuell für einen Dienst anmelden, ist sicherzustellen, dass Letztere mit dem Erhalt von Nachrichten Ihrerseits einverstanden sind.

![](assets/subscription_services_example.png)

1. Erstellen Sie drei Abfragen:

   * Die erste Abfrage ruft alle Empfänger zwischen 18 und 60 Jahre ab.
   * Die zweite Abfrage ruft die in Berlin lebenden Empfänger ab.
   * Die dritte Abfrage ruft die Empfänger ab, die den Newsletter bisher nicht abonniert haben.

1. Schließen Sie eine Schnittmenge an, um die verschiedenen Ergebnisse zu kreuzen.
1. Fügen Sie bei Bedarf ein Listen-Update ein, um stets über eine aktuelle Liste der neuesten Abonnenten zu verfügen.
1. Positionnieren Sie im Anschluss eine Abonnementaktivität und öffnen Sie diese.
1. Benennen Sie die Aktivität und kreuzen Sie die Option **[!UICONTROL Anmeldung]** an.

   Es besteht die Möglichkeit, die neuen Newsletter-Empfänger von ihrer Anmeldung zu informieren, indem Sie die Option **[!UICONTROL Benachrichtigung versenden]** aktivieren.

1. Geben Sie den Ordner an, der den Newsletter enthält und wählen Sie diesen dann aus der Liste der verfügbaren Kommunikationen aus.
1. Lassen Sie die Option **[!UICONTROL Ausgehende Transition erzeugen]** deaktiviert, damit der Workflow mit der Abonnementaktivität endet. Bestätigen Sie die Konfiguration durch Klick auf **[!UICONTROL OK]**.

Bei Ausführung des Workflows werden die Profile, die allen drei Abfragebedingungen entsprechen, zur Abonnentenliste hinzugefügt und für den Newsletter angemeldet.

Im Tab **[!UICONTROL Abonnements]** der Empfängerprofile können Sie prüfen, ob der Workflow das gewünschte Ergebnis erzielt hat.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

