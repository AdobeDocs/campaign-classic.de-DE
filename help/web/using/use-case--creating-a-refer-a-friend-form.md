---
solution: Campaign Classic
product: campaign
title: '"Anwendungsbeispiel: ein Freunde-Werben-Formular erstellen"'
description: '"Anwendungsbeispiel: ein Freunde-Werben-Formular erstellen"'
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 100%

---


# Anwendungsbeispiel: ein Freunde-Werben-Formular erstellen{#use-case-creating-a-refer-a-friend-form}

In diesem Beispiel soll den in der Datenbank befindlichen Empfängern ein Gewinnspiel angeboten werden. Das Webformular soll einen Bereich zur Eingabe der Antworten besitzen und einen anderen zur Eingabe der E-Mail-Adresse eines Freundes.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

Die Identifizierungs- und Gewinnspiel-Bereiche werden durch die zuvor beschriebenen Prozesse erstellt.

Um den Freunde-Werben-Bereich zu konfigurieren und zu erstellen, gehen Sie folgendermaßen vor:

1. Erstellen Sie ein Gewinnspiel-Webformular mit Fragen und einem Eingabefeld für die Kontaktinformationen des Angeworbenen wie unten dargestellt:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Im Feld **Ihre Nachricht** kann der Werber eine Nachricht für den Angeworbenen eingeben. Der Werber muss auch seinen **Nachnamen**, **Vornamen** und seine **E-Mail-Adresse** eingeben.

   Die in den Feldern eingegebenen Informationen werden in einer speziellen Tabelle, der Besuchertabelle, gespeichert.

   >[!NOTE]
   >
   >Solange der Angeworbene noch nicht sein Einverständnis gegeben hat, können Sie ihn nicht gemeinsam mit den Werbern in der Datenbank speichern. Er wird deshalb vorübergehend in der **Besuchertabelle** gespeichert (**nms:visitor**), die für Viral-Marketing-Kampagnen verwendet wird. Diese Tabelle wird regelmäßig durch **Bereinigungsprozesse** geleert.
   >
   >In diesem Beispiel möchten wir Angeworbene dazu bewegen, an dem von den Werbern empfohlenen Gewinnspiel teilzunehmen. Zusätzlich möchten wir ihnen ein Abonnement für eines unserer Informationsdienste anbieten. Wenn sie sich dazu anmelden, können sie in der Datenbank gespeichert werden.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   Der Inhalt der Felder für die Angeworbenen wird im Skript zur Profilerstellung und in der an sie gesendeten Nachricht verwendet.

1. Erstellen Sie zunächst ein Skript, das den Werber mit dem Angeworbenen verbindet.

   Es enthält die folgenden Anweisungen:

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   Der Nachname, der Vorname und die E-Mail-Adresse, die in den Identifizierungsbereich der Seite eingegeben werden, werden als Nachname, Vorname und E-Mail-Adresse des Werbers identifiziert. Diese Felder werden schließlich in den Hauptteil der Nachricht eingefügt, die dem Angeworbenen gesendet werden.

   Der APP5-Wert entspricht dem internen Namen des Webformulars: Mit dieser Information können Sie den Ursprung des Angeworbenen ermitteln, d. h. den Besucher mit dem zu seiner Erstellung verwendeten Webformular verbinden.

1. Mithilfe der Speicherungsbox können Sie Informationen erfassen und in der Datenbank speichern.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Erstellen Sie dann die Versandvorlage, die mit dem in Schritt 1 erstellten Informationsdienst verknüpft ist. Sie wird im Feld **[!UICONTROL Choose scenario]** des Informationsdienstes ausgewählt.

   Die Versandvorlage zur Erstellung der Freunde-Werben-Nachricht enthält die folgenden Informationen:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Diese Vorlage hat die folgenden Eigenschaften:

   * Wählen Sie die Besuchertabelle als Zielgruppen-Mapping aus.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * Die Kontaktinformationen des Angeworbenen sowie die Informationen des Werbers werden der Besuchertabelle entnommen. Diese Informationen werden über die Personalisierungs-Schaltfläche eingefügt.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Diese Vorlage enthält einen Link zum Gewinnspielformular und den Abonnementlink, über den der Angeworbene einen Newsletter abonnieren kann.

      Der Abonnementlink wird über einen Gestaltungsbaustein eingefügt. Standardmäßig können Profile für den **Newsletter**-Dienst angemeldet werden. Dieser Gestaltungsbaustein kann entsprechend Ihren Anforderungen angepasst werden, sodass Sie den Empfänger auch für einen anderen Dienst anmelden können.

   * Der interne Name (hier &quot;referrer&quot;) wird im Nachrichtenversand-Skript wie unten dargestellt verwendet.
   >[!NOTE]
   >
   >Weiterführende Informationen zu Versandvorlagen finden Sie auf [dieser Seite](../../delivery/using/about-templates.md).

1. Erstellen Sie das zweite Skript zur Bereitstellung der Abonnement-Nachrichten.

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. Publizieren Sie das Gewinnspielformular und senden Sie den Kontakten der ursprünglichen Zielgruppe eine Einladung. Wenn einer davon einen Freund einlädt, wird ein Versand auf der Basis der **Freunde-Werben**-Vorlage erstellt.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   Der Angeworbene wird zum Besucherordner im Knoten **[!UICONTROL Administration > Besucher]** hinzugefügt:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Sein Profil enthält die vom Werber eingegebenen Informationen. Diese werden entsprechend den Konfigurationen des Formularskripts gespeichert. Wenn der Angeworbene den Newsletter abonniert, werden seine Informationen in der Empfängertabelle gespeichert.

