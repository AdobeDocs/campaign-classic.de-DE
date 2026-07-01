---
product: campaign
title: Erstellen einer Freundschaftswerbungsumfrage
description: Lernen Sie die Schritte zum Erstellen eines Freundschaftswerbungsformulars kennen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
TQID: https://experienceleague.adobe.com/n0qp8Q0p18fMbRYxAOu5Qj-0TCf8YgL5vF71F-ZGjbM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 644
ht-degree: 100%

---

# Anwendungsfall: Erstellen eines Empfehlungsformulars{#use-case-creating-a-refer-a-friend-form}



In diesem Beispiel möchten wir den Empfangenden in der Datenbank einen Wettbewerb anbieten. Das Web-Formular soll einen Abschnitt zur Eingabe der Antworten enthalten und einen anderen zur Eingabe der E-Mail-Adresse eines Freundes.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

Die Identifizierungs- und Gewinnspiel-Bereiche werden durch die zuvor beschriebenen Prozesse erstellt.

Um den Freunde-Werben-Bereich zu konfigurieren und zu erstellen, gehen Sie folgendermaßen vor:

1. Erstellen Sie ein Gewinnspiel-Webformular mit Fragen und einem Eingabefeld für die Kontaktinformationen des Angeworbenen wie unten dargestellt:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Im Feld **Ihre Nachricht** können Sie eine Nachricht für die angeworbene Person eingeben. Die werbende Person muss auch ihren **Nachnamen**, **Vornamen** und ihre **E-Mail-Adresse** eingeben.

   Die in den Feldern eingegebenen Informationen werden in einer speziellen Tabelle, der Besuchertabelle, gespeichert.

   >[!NOTE]
   >
   >Solange der Angeworbene noch nicht sein Einverständnis gegeben hat, können Sie ihn nicht gemeinsam mit den Werbern in der Datenbank speichern. Er wird deshalb vorübergehend in der **Besuchertabelle** (**nms:visitor**) gespeichert, die für virale Marketing-Kampagnen verwendet wird. Diese Tabelle wird regelmäßig durch **Bereinigungsprozesse** geleert.
   >
   >In diesem Beispiel möchten wir Empfangende dazu bewegen, an dem von ihren Werbenden empfohlenen Wettbewerb teilzunehmen. In dieser Nachricht möchten wir ihnen jedoch auch ein Abonnement für einen unserer Informationsdienste anbieten. Wenn sie sich anmelden, können sie in der Datenbank gespeichert werden.

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

   Der Nachname, der Vorname und die E-Mail-Adresse, die in den Identifizierungsbereich der Seite eingegeben werden, werden als Nachname, Vorname und E-Mail-Adresse des Werbers identifiziert. Diese Felder werden erneut in den Nachrichtentext eingefügt, der an die angeworbene Person gesendet wird.

   Der APP5-Wert entspricht dem internen Namen des Webformulars: Mit dieser Information können Sie den Ursprung des Angeworbenen ermitteln, d. h. den Besucher mit dem zu seiner Erstellung verwendeten Webformular verbinden.

1. Mithilfe der Speicherungsbox können Sie Informationen erfassen und in der Datenbank speichern.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Erstellen Sie dann die Versandvorlage, die mit dem in Schritt 1 erstellten Informationsdienst verknüpft ist. Sie wird im Feld **[!UICONTROL Choose scenario]** des Informationsdienstes ausgewählt.

   Die Versandvorlage zur Erstellung der Freunde-Werben-Nachricht enthält die folgenden Informationen:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Diese Vorlage hat die folgenden Eigenschaften:

   * Wählen Sie die Besuchertabelle als Zielgruppen-Mapping aus.

     ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * Die Kontaktinformationen der angeworbenen Person sowie die Informationen der werbenden Person werden der Besuchertabelle entnommen. Sie werden mithilfe der Schaltfläche „Personalisierung“ eingefügt.

     ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Diese Vorlage enthält einen Link zum Gewinnspielformular und den Abonnementlink, über den der Angeworbene einen Newsletter abonnieren kann.

     Der Abonnementlink wird über einen Gestaltungsbaustein eingefügt. Standardmäßig können Profile für den **Newsletter**-Dienst angemeldet werden. Dieser Gestaltungsbaustein kann entsprechend Ihren Anforderungen angepasst werden, sodass Sie den Empfänger auch für einen anderen Dienst anmelden können.

   * Der interne Name (hier „referrer“) wird im Nachrichtenversand-Skript wie unten dargestellt verwendet.

   >[!NOTE]
   >
   >Weiterführende Informationen zu Versandvorlagen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=de){target="_blank"}.

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

1. Veröffentlichen Sie das Gewinnspielformular und senden Sie den Kontakten der ursprünglichen Zielgruppe eine Einladung. Wenn einer davon einen Freund einlädt, wird ein Versand auf der Basis der **Freunde-Werben**-Vorlage erstellt.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   Der Angeworbene wird zum Besucherordner im Knoten **[!UICONTROL Administration > Besucher]** hinzugefügt:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Das Profil enthält die Informationen, die von der werbenden Person eingegeben wurden. Es wird basierend auf den im Formularskript eingegebenen Konfigurationen gespeichert. Wenn sich die angeworbene Person für ein Abonnement des Newsletters entscheidet, wird sie in der Empfängertabelle gespeichert.
