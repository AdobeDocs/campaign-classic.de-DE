---
product: campaign
title: Audit-Protokoll
description: Erfahren Sie, wie Sie Ihre Instanz mit dem Audit-Protokoll von Campaign überwachen.
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 82%

---

# Audit-Protokoll{#audit-trail}

>[!INFO]
>
>Weitere Informationen zur Funktion des Audit-Protokolls finden Sie in der Dokumentation zu [Adobe Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/audit-trail).

In Adobe Campaign erhalten Sie **[!UICONTROL Audit-Protokoll]** Zugriff auf den vollständigen Verlauf der Änderungen, die in Ihrer Instanz vorgenommen wurden.

**[!UICONTROL Audit-Protokoll]** erfasst in Echtzeit eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten. Es bietet eine Möglichkeit für den Zugriff auf einen Datenverlauf, um zum Beispiel folgende Fragen zu beantworten: Was ist mit Ihren Workflows passiert und wer hat sie zuletzt aktualisiert? Was haben Ihre Benutzenden in der Instanz getan?

>[!NOTE]
>
>Adobe Campaign prüft keine Änderungen an Benutzerrechten, Vorlagen, Personalisierungen oder Kampagnen.\
>Das Audit-Protokoll kann nur von Admins der Instanz verwaltet werden.

![](assets/audit_trail_2.png)

+++ Weitere Informationen über die verfügbaren Entitäten im Audit-Protokoll

* **Schema-Audit-Protokoll**: ermöglicht es Ihnen, die Änderungen an Ihren Schemata zu untersuchen und zu identifizieren, wer diese Änderungen vorgenommen hat und wann sie vorgenommen wurden.

  Ausführliche Informationen zu Schemata finden Sie auf dieser [Seite](../../configuration/using/data-schemas.md).

* Das **Workflow-Audit-Protokoll** verfolgt alle Aktionen im Zusammenhang mit Ihren Workflows, einschließlich:

   * Starten
   * Aussetzen
   * Stoppen
   * Neu starten
   * Bereinigen, was der Aktion „Verlauf bereinigen“ entspricht
   * Simulieren, was der Aktion „Starten“ im Simulationsmodus entspricht
   * Wecken, was der Aktion „Vorgezogene Ausführung der ausstehenden Aufgaben“ entspricht
   * Unbedingter Stopp

  Weiterführende Informationen zu Workflows finden Sie auf [dieser Seite](../../workflow/using/about-workflows.md).

  Weitere Informationen zum Überwachen von Workflows finden Sie in der [&#x200B; zu Campaign v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=de){target="_blank"}.


* Das **Audit-Protokoll für Optionen** ermöglicht Ihnen die Überprüfung der Aktivitäten und der letzten Änderungen an Ihren Optionen.

  Weiterführende Informationen zu Optionen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-options.md).

* Das **Audit-Protokoll für den Versand** ermöglicht Ihnen die Überprüfung der Aktivitäten und der letzten Änderungen an Ihren Sendungen.

  Weiterführende Informationen zu Sendungen finden Sie auf [dieser Seite](../../delivery/using/communication-channels.md).

* **Externes Konto** ermöglicht Ihnen die Überprüfung von Änderungen an externen Konten, die von technischen Prozessen wie technischen Workflows oder Kampagnen-Workflows verwendet werden.

  Weiterführende Informationen zu „Externes Konto“ finden Sie auf [dieser Seite](../../installation/using/external-accounts.md).

* **Versand-Mapping** ermöglicht es Ihnen, Aktivitäten und kürzlich an Ihren Versand-Mappings vorgenommene Änderungen zu überwachen.

  Weiterführende Informationen zu „Versand-Mapping“ finden Sie auf [dieser Seite](../../configuration/using/target-mapping.md).

* **Web-Anwendung** ermöglicht Ihnen das Überprüfen von Änderungen an Web-Formularen in Campaign V8, die zum Erstellen von Seiten mit Eingabe- und Auswahlfeldern verwendet werden und die Daten aus der Datenbank enthalten können.

  Weiterführende Informationen zu „Web-Anwendung“ finden Sie auf [dieser Seite](../../web/using/about-web-applications.md).

* **Angebot** ermöglicht es Ihnen, die Aktivitäten und letzten Änderungen an Ihren Angeboten zu überprüfen.

  Weiterführende Informationen zu „Angebot“ finden Sie auf [dieser Seite](../../interaction/using/interaction-and-offer-management.md).

* **Operator** ermöglicht es Ihnen, Aktivitäten und Änderungen zu überwachen, die vor Kurzem an Ihren Operatoren vorgenommen wurden.

  Weiterführende Informationen zu Benutzerinnen und Benutzern finden Sie auf [dieser Seite](../../platform/using/access-management-operators.md).

+++
