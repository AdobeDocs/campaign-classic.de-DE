---
title: Beispiele für Facebook-Apps
seo-title: Beispiele für Facebook-Apps
description: Beispiele für Facebook-Apps
seo-description: null
page-status-flag: never-activated
uuid: 336f4006-3545-4b04-959d-61cd0446af27
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: annexes
discoiquuid: 07be1d3c-b038-48ca-be37-a33adb8e0fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7f03e1fbb94bbd5b00fa0094a0b5e9be45629ec7

---


# Beispiele für Facebook-Apps{#examples-of-facebook-apps}

Wenn ein Benutzer auf die Registerkarte einer Facebook-Anwendung klickt, wird sie in einem 810 Pixel breiten Bereich angezeigt. Adobe Campaign verwendet eine Webanwendung vom Typ &quot;Facebook&quot;, mit der Sie die in der Facebook-Anwendung angezeigten Inhalte definieren und personalisieren können. Auf diese Weise wird der Erwerb von Profilen erleichtert.

>[!NOTE]
>
>Es ist auch möglich, Adobe Campaign in eine von einem Partner entwickelte Facebook-Anwendung zu integrieren. In diesem Fall müssen Sie die Adobe Campaign-Webanwendung nicht verwenden, um Facebook-Profile zu erwerben. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!CAUTION]
>
>Bitte befolgen Sie die Konfigurationsschritte, die unter [Erstellen einer Facebook-Anwendung](../../social/using/creating-a-facebook-application.md)beschrieben werden.

>[!NOTE]
>
>In diesem Abschnitt werden die Elemente beschrieben, die mit Webanwendungen vom Typ Facebook verknüpft sind. Alle Elemente, die für Standard-Webanwendungen freigegeben wurden, sind in [diesem Abschnitt](../../web/using/about-web-applications.md)ausführlich beschrieben.

Die hier aufgeführten Beispiele für Webanwendungen vom Facebook-Typ sind:

* Erstellen einer Facebook-Anwendung in 7 Schritten. Siehe [Kurzanleitung: Erstellen einer Facebook-Anwendung in 7 Schritten](#quick-start--creating-a-facebook-application-in-7-steps).
* Weiterleiten von Einstellungen an eine Facebook-Anwendung. Weitere Informationen finden Sie unter Weiterleiten [von Einstellungen an eine Facebook-Anwendung?](#how-to-forward-settings-to-a-facebook-application-).
* Anleitung zum Erfassen von Lüfterdaten. Weitere Informationen finden Sie unter [Wie erfassen Sie Lüfterdaten?](#how-to-acquire-fan-data-).

>[!CAUTION]
>
>Diese einfachen Anwendungsfälle werden als Beispiele zur Veranschaulichung der Funktionen von Webanwendungen vom Typ Facebook bereitgestellt.

## Empfehlungen {#recommendations}

Die folgenden Einschränkungen sind direkt mit Facebook verknüpft:

* Sie müssen alle Webanwendungen in HTTPS erstellen.
* Eine über eine Registerkarte angezeigte Facebook-Anwendung hat eine Breite von 810 Pixel.

## Kurzanleitung: Erstellen einer Facebook-Anwendung in 7 Schritten {#quick-start--creating-a-facebook-application-in-7-steps}

In diesem Beispiel wird schrittweise beschrieben, wie Sie eine von Adobe Campaign erstellte Anwendung in Facebook anzeigen. In diesem Fall möchten wir eine Anwendung erstellen, mit der Sie die **Begrüßungsmeldung** anzeigen können, wenn der Benutzer auf die Registerkarte &quot;Anwendung&quot;(**App01**) klickt.

Um diese Anwendung zu erstellen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Anwendung auf Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Weitere Informationen finden Sie unter: Erstellen [einer Facebook-Anwendung](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. Erstellen Sie ein **[!UICONTROL Facebook Connect]** externes Konto und geben Sie die Parameter der Facebook-Anwendung ein. For more on this, refer to: [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Geben Sie die Links **[!UICONTROL Terms of service]** und **[!UICONTROL Privacy policy]** Links ein, die im Bildschirm &quot;Facebook-Berechtigungsanforderung&quot;angezeigt werden sollen. Weitere Informationen finden Sie unter: [Eingeben der Links](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links)zu den Servicebedingungen und den Datenschutzrichtlinien.

   ![](assets/social_quick_start_1.png)

1. Erstellen Sie eine Webanwendung vom Typ Facebook in Adobe Campaign. Weitere Informationen finden Sie unter: [Erstellen einer Webanwendung](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)vom Typ &quot;Facebook&quot;.

   ![](assets/social_webapp_005.png)

1. Bearbeiten Sie Ihre Webanwendung. In diesem Beispiel haben wir eine **[!UICONTROL Page]** Aktivität hinzugefügt und einen Titel dafür definiert.

   ![](assets/social_quick_start_4.png)

1. Stellen Sie Ihre Anwendung bereit.

   ![](assets/social_webapp_004.png)

1. Konfigurieren Sie Ihre Facebook-Anwendung so, dass sie als Registerkarte auf Ihrer Facebook-Seite angezeigt wird. For more on this, refer to: [Configuring Facebook tabs](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Überprüfen Sie, ob die Registerkarte der **App01** -Anwendung auf Ihrer Facebook-Seite angezeigt wird. Wenn Sie darauf klicken, wird eine **Begrüßungsmeldung** angezeigt.

![](assets/social_webapp_042.png)

## Wie können Einstellungen an eine Facebook-Anwendung weitergeleitet werden? {#how-to-forward-settings-to-a-facebook-application-}

>[!CAUTION]
>
>Befolgen Sie die Konfigurationsschritte, die unter [Erstellen einer Facebook-Anwendung](../../social/using/creating-a-facebook-application.md)beschrieben sind.

In Beispiel 1 haben wir die Anzeige der Facebook-Seite entsprechend dem Wert im **[!UICONTROL Fan of the page]** Feld personalisiert. Es ist auch möglich, das **[!UICONTROL Application settings]** Feld zu verarbeiten. Mit diesem Feld können Sie Daten wiederherstellen, die in einem Link enthalten sind, der von Adobe Campaign über Facebook generiert wurde.

Nehmen wir das Beispiel eines Unternehmens, das entscheidet, eine E-Mail-Kampagne zu senden. Bei der Bereitstellung verweist ein Link auf die Facebook-Anwendung. Dieser Link ist dank des **[!UICONTROL app_data]** Parameters, der am Ende der URL hinzugefügt wird, personalisiert. Der Wert dieses Parameters könnte ein Indikator sein, der die Kundenrelevanz widerspiegelt. In unserem Beispiel sind die Werte des **[!UICONTROL app_data]** Parameters **[!UICONTROL big]** (signifikanter Kunde) und **[!UICONTROL small]** (weniger bedeutender Kunde).

Nach der Personalisierung sieht die URL wie folgt aus:

* `http://<path of the Facebook application>&app_data=big` (für einen bedeutenden Kunden)
* `http://<path of the Facebook application>&app_data=small` (für einen weniger bedeutenden Kunden)

Unter den anonymen Daten, die von Facebook an Adobe Campaign weitergeleitet werden, wird der Wert des **[!UICONTROL Application parameters]** Felds erfasst, sodass Adobe Campaign die Anwendungsanzeige anhand dieses Parameters personalisieren kann.

Wenn der Benutzer ein bedeutender Kunde ist (der Wert des **[!UICONTROL app_data]** Parameters **[!UICONTROL big]**), wird folgende Abbildung angezeigt:

![](assets/social_webapp_017.png)

Wenn der Benutzer ein weniger bedeutender Kunde ist (der Wert des **[!UICONTROL app_data]** Parameters **[!UICONTROL small]**), wird folgende Abbildung angezeigt:

![](assets/social_webapp_016.png)

Um diesen Anwendungsfall neu zu erstellen, haben wir eine Webanwendung erstellt, die aus den folgenden Elementen besteht:

* Eine **[!UICONTROL Test]** Aktivität, die auf dem **[!UICONTROL Application parameter]** Feld basiert.
* zwei Seiten, die die Bilder enthalten, die entsprechend dem Wert des **[!UICONTROL Application parameter]** Felds angezeigt werden sollen.

![](assets/social_webapp_018.png)

## Wie erfassen Sie Fandaten? {#how-to-acquire-fan-data-}

>[!CAUTION]
>
>Befolgen Sie die Konfigurationsschritte, die unter [Erstellen einer Facebook-Anwendung](../../social/using/creating-a-facebook-application.md)beschrieben sind.

Dieses Beispiel zeigt Ihnen, wie Sie mit Facebook-Benutzern in Kontakt treten und ihnen das Weitergeben ihrer Profilinformationen anbieten können. Nehmen wir das Beispiel eines Unternehmens, das Aussichten erwerben möchte und einen Wettbewerb auf seiner Facebook-Seite organisiert, um sie anzuziehen.

Wenn ein Benutzer auf die **[!UICONTROL App03]** Registerkarte klickt, wird er gefragt, ob er am Wettbewerb teilnehmen möchte.

![](assets/social_webapp_fb_000.png)

Wenn sie sich entscheiden, an dem Wettbewerb teilzunehmen, bieten wir ihnen an, ihre Profilinformationen zu teilen.

![](assets/social_webapp_021.png)

Wenn sie sich damit einverstanden erklären, ihre Informationen freizugeben, wird der folgende Bildschirm angezeigt.

![](assets/social_webapp_022.png)

Um diesen Verwendungsfall zu erstellen, haben wir eine Webanwendung erstellt, die die folgenden Elemente enthält:

* eine **[!UICONTROL Test]** Aktivität
* drei Seiten
* eine **[!UICONTROL Access control]** Aktivität
* eine **[!UICONTROL Pre-loading]** Aktivität
* eine **[!UICONTROL Save]** Aktivität
* eine **[!UICONTROL End]** Aktivität

![](assets/social_webapp_019.png)

### Testaktivität {#test-activity}

Die **[!UICONTROL Test]** Aktivität basiert auf dem **[!UICONTROL ID]** und dem **[!UICONTROL Application parameters]** Feld.

![](assets/social_webapp_023.png)

Es besteht aus drei Zweigstellen:

* **[!UICONTROL identifier (UID) is empty]** : der Bezeichner wird nur dann von Facebook weitergeleitet, wenn der Benutzer der Weitergabe seiner Daten bereits zugestimmt hat. Im ersten Teil der **[!UICONTROL Test]** Aktivität können Sie den Wettbewerb nur Benutzern zur Verfügung stellen, die noch nie angemeldet sind, d. h. Benutzern mit einer leeren ID.
* **[!UICONTROL application parameter equals 'thanks']** : Um einen Anzeigefehler zu umgehen, der mit Facebook verknüpft ist, verweist die Webanwendungs-Endseite auf die URL der Facebook-Anwendung, der der **[!UICONTROL app_data]** Parameter hinzugefügt wird, um den **[!UICONTROL thanks]** Wert zu verwenden (weitere Informationen hierzu finden Sie unter: Aktivität [beenden](#end-activity)). In der zweiten Verzweigung können Sie herausfinden, ob der Benutzer aus der **[!UICONTROL End]** Aktivität der ersten Verzweigung (und gerade in den Wettbewerb eingetreten ist) kommt, um eine Dankesnachricht anzuzeigen. Weitere Informationen zur Verwendung zusätzlicher URL-Parameter finden Sie unter: [Weiterleiten von Einstellungen an eine Facebook-Anwendung?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : Wenn der Benutzer bereits an einem früheren Datum (anders als bei einem anderen Antragsparameter) in den Wettbewerb (bereits eingegebene ID) eingestiegen ist, wird eine Seite angezeigt, auf der angegeben ist, dass er bereits eingetragen **[!UICONTROL thanks]** ist.

### Wettbewerbsseite {#competition-page}

Um den Anzeigefehler zu umgehen, der mit Facebook verknüpft ist, müssen Sie auch auswählen **[!UICONTROL Parent window]** oder **[!UICONTROL In the top window]** im **[!UICONTROL Window]** Feld der Wettbewerbsseite.

![](assets/social_webapp_028.png)

### Zugriffssteuerungsaktivität {#access-control-activity}

Mit der **[!UICONTROL Access control]** Aktivität können Sie die Seite mit der Facebook-Berechtigungsanforderung anzeigen, wenn der Benutzer in den Wettbewerb eintritt. Wenn sie zustimmen, ihre Informationen weiterzugeben, werden sie während des Vorladens wiederhergestellt. For more on this, refer to: [Pre-loading activity](#pre-loading-activity).

Wenn Sie beim Erstellen der Webanwendung zuvor das externe Konto angegeben haben (siehe [Erstellen einer Webanwendung](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)vom Typ Facebook), müssen Sie die Aktivität nicht bearbeiten. Falls nicht, wechseln Sie zum **[!UICONTROL Application]** Feld und wählen Sie das externe Konto aus, das mit der Facebook-Anwendung verknüpft ist.

![](assets/social_webapp_024.png)

### Aktivität vor dem Laden {#pre-loading-activity}

Wählen Sie die Datenquelle aus, die zum Vorausladen verwendet werden soll:

* **[!UICONTROL Marketing database]** : Mit dieser Option können Sie Daten über die Adobe Campaign-Datenbank im Voraus laden.
* **[!UICONTROL Facebook]** : Mit dieser Option können Sie Daten über Facebook vorab laden.

![](assets/social_webapp_029.png)

**Marketing-Datenbank**

Mit dieser Option können Sie die Daten eines Profils wiederherstellen, das in der Tabelle &quot;Besucher&quot;vorhanden ist. Die Überprüfung wird anhand der externen Facebook-ID durchgeführt, die beim Klicken auf die Registerkarte &quot;Facebook-Anwendung&quot;wiederhergestellt wurde. Wenn Sie ein Formular nach der **[!UICONTROL Pre-loading]** Aktivität hinzufügen, werden die Felder, die Informationen in der Datenbank enthalten, vorgeladen.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Weitere Informationen zum Vorabladen von Daten über die Adobe Campaign-Datenbank finden Sie in [diesem Abschnitt](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Mit dieser Option können Sie die Facebook-Profilinformationen definieren, die erfasst werden sollen, darunter die Facebook-Profilinformationen, die der Benutzer im Hinblick auf das Speichern freigegeben hat.

![](assets/social_webapp_025.png)

Mit der **[!UICONTROL Database information]** Option können Sie die folgenden Daten erfassen:

* **[!UICONTROL External ID]**: Benutzer-ID
* **[!UICONTROL Gender]**: Geschlecht des Benutzers
* **[!UICONTROL Verified]** : Dieses Feld gibt an, ob der Benutzer über ein bestätigtes Facebook-Konto verfügt.
* **[!UICONTROL Full name]**: vollständiger Name des Benutzers
* **[!UICONTROL First name]**: Vorname des Benutzers
* **[!UICONTROL Last name]**: Nachname des Benutzers
* **[!UICONTROL Language]**: Sprache des Benutzers

Sie können auch das Profilfoto, die Liste der Freunde, E-Mail-Adresse, Geburtsdatum, Interessen und Ort sammeln, indem Sie die entsprechenden Kästchen markieren.

Markieren Sie vor dem Klicken **[!UICONTROL Ok]** das **[!UICONTROL I agree to comply with Facebook conditions of use]** Kästchen.

>[!NOTE]
>
>Wenn Sie eines oder mehrere Kontrollkästchen im **[!UICONTROL Private information]** Abschnitt aktivieren, wird im Bildschirm &quot;Facebook-Berechtigungsanfrage&quot;automatisch die Zugriffsanforderung für diese Daten angezeigt.
>
>Damit Sie die ausgewählten Informationen erfassen können, muss der Benutzer der Freigabe zustimmen.
>
>Wenn Sie beide Arten des Vorabladens (über Adobe Campaign und über Facebook) verwenden möchten, fügen Sie nacheinander zwei Felder zum Vorausladen hinzu.

### Aktivität speichern {#save-activity}

Mit der **[!UICONTROL Save]** Aktivität können Sie die während der vorherigen Schritte in der Tabelle der Besucher erfassten Informationen speichern.

Wenn das Profil bereits in der Tabelle der Besucher vorhanden ist, werden ihre Daten mit den neu erfassten Daten aktualisiert.

Wenn das Profil nicht in der Datenbank vorhanden ist und die E-Mail-Adresse des Facebook-Benutzers erfasst wurde, wird ein Besucher in der Tabelle der Besucher erstellt.

![](assets/social_webapp_026.png)

1. Wählen Sie im **[!UICONTROL Visitor creation folder]** Feld den Ordner aus, in dem das Profil erstellt werden soll. Bei einer Webanwendung mit Facebook-Typ ist der standardmäßige Erstellungsordner **[!UICONTROL Visitors]**.
1. Wählen Sie im **[!UICONTROL Reconciliation mode]** Feld den gewünschten Abgleichmodus aus:

   * **[!UICONTROL Automatic]** : Die Versöhnung erfolgt auf Basis von E-Mail, Nachname, Vorname und Geburtsdatum.
   * **[!UICONTROL Manual]** : Bitte wählen Sie einen oder mehrere Versöhnungsschlüssel aus.
   * **[!UICONTROL None]** : Es wird keine Versöhnung stattfinden.

1. Wählen Sie im **[!UICONTROL Mapping]** Feld das Schema aus, auf dem Sie die Versöhnung durchführen möchten.

   >[!CAUTION]
   >
   >Vergewissern Sie sich, dass die Felder der **[!UICONTROL Social networks]** Registerkarte in der Zuordnungszuordnung korrekt eingegeben wurden. Bereitstellungszuordnungen werden über den **[!UICONTROL Administration > Campaign management > Target mappings]** Knoten aufgerufen.

1. Sie können einen Suchordner für die Versöhnung und einen Erstellungsordner für neue Profile auswählen. Wenn die Felder leer sind, werden Profile gesucht und im Standardordner des Zuordnungsschemas erstellt.

### Aktivität beenden {#end-activity}

Um den mit Facebook verknüpften Anzeigefehler zu umgehen, müssen Sie das **[!UICONTROL Use an external URL]** Feld markieren und die URL der Facebook-Anwendung, gefolgt vom **[!UICONTROL app_data]** Parameter und einem Wert eingeben. Dieser Wert wird in der **[!UICONTROL Test]** Aktivität verwendet, um festzustellen, ob der Benutzer gerade an dem Wettbewerb teilgenommen hat, und um gegebenenfalls eine Dankesmeldung anzuzeigen. For more on this, refer to: [Test activity](#test-activity).

In unserem Beispiel ist der verwendete Wert **danke**.

![](assets/social_webapp_027.png)

### Detailbildschirm eines Besuchers {#details-screen-of-a-visitor}

Genau wie bei Twitter-Followern (siehe: [Betriebsprinzip](../../social/using/publishing-on-twitter.md#operating-principle)), wiederhergestellte Facebook-Profile werden in der Besuchstabelle gespeichert. Um die Liste der Besucher anzuzeigen, gehen Sie zum **[!UICONTROL Profiles and Targets > Visitors]** Knoten.

Jeder Facebook-Prospekt, der zustimmt, seine Profilinformationen zu teilen, wird der Besucherliste hinzugefügt. Wenn das **[!UICONTROL Friends]** Kontrollkästchen in der **[!UICONTROL Pre-load]** Aktivität aktiviert ist (siehe: Aktivitäten [vor dem Laden](#pre-loading-activity)), werden auch Freunde hinzugefügt.

![](assets/social_webapp_037.png)

Im **[!UICONTROL Summary]** Abschnitt des Besucherdetailfensters gibt es zwei mögliche Zustände für den **[!UICONTROL New Contact]** Indikator:

![](assets/social_webapp_038.png)

Wenn ein grünes Häkchen angezeigt wird, bedeutet dies, dass der Besucher nicht mit den Empfängern abgeglichen wurde. In diesem Fall wird ein neues Profil in der Liste der Empfänger erstellt.

![](assets/social_webapp_039.png)

Ein rotes Kreuz bedeutet, dass der Besucher mit einem Empfänger abgeglichen wurde. Sie können auf die Vergrößerung rechts neben dem **[!UICONTROL Recipient]** Feld klicken, um den passenden Empfänger anzuzeigen.

![](assets/social_webapp_040.png)

Gehen Sie zum Detailfenster eines Empfängers, um den passenden Besucher anzuzeigen, falls zutreffend. Wählen Sie die **[!UICONTROL Others]** Registerkarte und doppelklicken Sie dann auf den Namen des Besuchers im **[!UICONTROL Web identities]** Abschnitt.

![](assets/social_webapp_041.png)

Der **[!UICONTROL Activities]** Bildschirm der Detailseite eines Besuchers enthält die folgenden Informationen:

* &quot;Open Graph&quot;-Typ Fan-Aktivitäten: Musikwiedergaben, angesehene Videos, Artikel und Hinweise zu installierten Anwendungen (Deezer, Spotify, Dailymotion, Yahoo News usw.)

   ![](assets/social_facebook_activities.png)

* &quot;Gefällt mir&quot;-Klicks und Kommentare, die der Fan nach Auslieferung durch Adobe Campaign hinzugefügt hat
* Seiten, auf die der Fan gerne hat
* Check-in durch den Lüfter

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Damit Adobe Campaign die Check-ins eines Fans erfasst, müssen Sie auf die **[!UICONTROL Subscribe]** Schaltfläche im Bildschirm &quot;Dienstkonfiguration&quot;klicken. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Vorladen der Felder eines Formulars mithilfe von Facebook-Profildaten {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

Mit der **[!UICONTROL Social Marketing]** Anwendung können Sie einem Formular auch eine Schaltfläche hinzufügen, um Felder mit Facebook-Profilinformationen vorab zu laden. Diese Option, die in allen Webanwendungsvorlagen verfügbar ist (**[!UICONTROL Page]** Typaktivitäten), ist in [diesem Abschnitt](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)ausführlich beschrieben.

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Bevor Sie mit der Verwendung dieser Funktion beginnen, müssen Sie eine Facebook-Anwendung und ein externes **[!UICONTROL Facebook Connect]** Konto erstellen. For more on this, refer to [Configuring external accounts](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

