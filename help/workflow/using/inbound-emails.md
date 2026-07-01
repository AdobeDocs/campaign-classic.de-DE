---
product: campaign
title: E-Mail-Empfang
description: Erfahren Sie mehr über die Workflow-Aktivität "E-Mail-Empfang".
feature: Workflows, Channels Activity
hide: true
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
TQID: https://experienceleague.adobe.com/FSudiqp5MAVKsZKdYWLyzdUKMxobJj6Yj7UbAxvDJ38
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 372
ht-degree: 100%

---

# E-Mail-Empfang{#inbound-emails}



Die Aktivität **E-Mail-Empfang** ermöglicht den Abruf und die Verarbeitung von E-Mails aus Mailboxen, die über POP3 abgefragt werden können.

![](assets/email_rec_edit_1.png)

In der ersten Registerkarte der Aktivität **Eingehende E-Mails** können Sie die POP3-Parameter sowie das bei Empfang jeder Nachricht auszuführende Skript angeben. In der zweiten Registerkarte können Sie der Aktivität einen Zeitplan zuweisen und in der dritten Registerkarte die Ablaufbedingungen der Aktivität definieren.

1. **[!UICONTROL E-Mail-Empfang]**

   * **[!UICONTROL Externes Konto verwenden]**

     Wenn diese Option aktiviert wird, können Sie direkt ein externes POP3-Konto auswählen, anstatt die Verbindungsparameter anzugeben. Im Feld **[!UICONTROL Externes Konto]** wird das zu verwendende POP3-Konto angegeben, das für die Verbindung zum E-Mail-Dienst genutzt werden soll. Dieses Feld ist nur sichtbar, wenn die Option „Externes Konto verwenden&quot;aktiviert ist.

     Wenn die zuvor beschriebene Option nicht aktiviert wurde, sind folgende Parameter anzugeben:

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3-Server]**

        Name des POP3-Servers.

      * **[!UICONTROL POP3-Konto]**

        Name des Benutzers.

      * **[!UICONTROL Passwort]**

        Passwort des Benutzerkontos.

      * **[!UICONTROL Port]**

        Port-Nummer der POP3-Verbindung. Der Standard-Port ist 110.

   * **[!UICONTROL Stoppen, sobald eine E-Mail verarbeitet wurde]**

     Mit dieser Option können Sie E-Mails einzeln verarbeiten. Die Transition der Aktivität wird nur einmal aktiviert. Alle nicht verarbeiteten Nachrichten bleiben auf dem Server.

1. **[!UICONTROL Script]**

   Die Angabe eines Skripts ermöglicht die Verarbeitung der Nachricht und die Ausführung von verschiedenen Vorgängen, je nach Nachrichteninhalt. Das Skript wird auf jede Nachricht angewendet und entscheidet, welcher Vorgang auszuführen ist (Nachricht in der Mailbox belassen oder löschen) und ob die ausgehende Transition zu aktivieren ist.

   Der Rückgabe-Code muss einem der folgenden Werte entsprechen:

   * 1 - Löscht die Nachricht auf dem Server und aktiviert die ausgehende Transition.
   * 2 - Lässt die Nachricht auf dem Server und aktiviert die ausgehende Transition.
   * 3 - Löscht die Nachricht auf dem Server.
   * 4 - Lässt die Nachricht auf dem Server.

   Auf den Inhalt der Nachricht kann über die allgemeine Variable **[!UICONTROL mailMessage]** zugegriffen werden.

1. **[!UICONTROL Planung]**

   Gehen Sie in den **[!UICONTROL Planung]**-Tab und kreuzen Sie die Option **[!UICONTROL Ausführung planen an]**. Klicken Sie anschließend auf die Schaltfläche **[!UICONTROL Ändern]**, um den Ausführungsrhythmus der Aktivität zu konfigurieren.

   Die Konfiguration erfolgt analog zum Planungsassistenten. Siehe [Planung](scheduler.md).

1. **[!UICONTROL Ablauf]**

   Im **[!UICONTROL Ablauf]**-Tab können Ablauffristen für die Aktivität definiert werden.

   ![](assets/email_rec_edit_3.png)

   Die Konfiguration erfolgt analog zum Planungsassistenten. Siehe [Timeouts](defining-approvals.md).
