---
title: '"Anwendungsbeispiele: Übersichten erstellen"'
seo-title: '"Anwendungsbeispiele: Übersichten erstellen"'
description: '"Anwendungsbeispiele: Übersichten erstellen"'
seo-description: null
page-status-flag: never-activated
uuid: 404ae82b-2766-4802-8673-aaaa26868f46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: a3834828-4d39-4699-b648-d399797b8ea7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Anwendungsbeispiele: Übersichten erstellen{#use-cases-creating-overviews}

Im folgenden Beispiel werden Webanwendungen vom Typ &quot;Übersicht&quot; erstellt, in denen alle Webanwendungen in Ihrer Datenbank angezeigt werden. Konfigurieren Sie dazu die folgenden Elemente:

* einen Filter für den Ordner (siehe [Hinzufügen eines Filters zu einem Ordner](#adding-a-filter-on-a-folder)),
* eine Schaltfläche zum Erstellen einer neuen Webanwendung (siehe [Hinzufügen einer Schaltfläche zum Konfigurieren einer neuen Webanwendung](#adding-a-button-to-configure-a-new-web-application)),
* Detailanzeige für jeden Eintrag in der Liste (siehe [Hinzufügen von Details zu einer Liste](#adding-detail-to-a-list)),
* ein Filter pro Werkzeug zur Bearbeitung von Links (siehe [Erstellen eines Filters mit einem Link-Editor](#creating-a-filter-using-a-link-editor)),
* einen Link zum Aktualisieren (siehe [Erstellen eines Aktualisierungslinks](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Einseitige Webanwendung erstellen {#creating-a-single-page-web-application}

1. Create a single **[!UICONTROL Page]** Web application and disable outbound transitions and transitions to the next page.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Ändern Sie den Seitentitel.

   Dieser Titel wird im Header der Webanwendungs-Übersicht angezeigt.

1. In the Web application properties, modify the rendering of your application by selecting the **[!UICONTROL Single-page Web application]** template.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Öffnen Sie die **[!UICONTROL Page]** Aktivität Ihrer Webanwendung und eine Liste (**[!UICONTROL Static element > List]**).
1. Wählen Sie auf der **[!UICONTROL Data]** Registerkarte Ihrer Liste den Typ des **[!UICONTROL Web applications]** Dokuments sowie die Spalten **[!UICONTROL Label]** , **[!UICONTROL Creation date]** und **[!UICONTROL Type of application]** Ausgabe aus.
1. Erstellen Sie im Untertab **[!UICONTROL Filter]** (wie unten dargestellt) den folgenden Filter, sodass nur Webanwendungen angezeigt und Vorlagen verborgen werden.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Close the configuration window of your page and click **[!UICONTROL Preview]**.

   Daraufhin wird die Liste der in Ihrer Datenbank verfügbaren Webanwendungen angezeigt.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Ordner-Filter hinzufügen {#adding-a-filter-on-a-folder}

In der Übersicht haben Sie die Möglichkeit, auf Daten abhängig von ihrem Speicherort im Adobe Campaign-Baum zuzugreifen. Dies wird durch einen Ordner-Filter ermöglicht. Gehen Sie folgendermaßen vor, um einen Ordner-Filter zu Ihrer Übersicht hinzuzufügen.

1. Platzieren Sie den Cursor auf den **[!UICONTROL Page]** Knoten Ihrer Webanwendung und fügen Sie ein **[!UICONTROL Select folder]** Element (**[!UICONTROL Advanced controls > Select folder]**) hinzu.
1. Klicken Sie im **[!UICONTROL Storage]** Fenster, das angezeigt wird, auf den **[!UICONTROL Edit variables]** Link.
1. Ändern Sie den Titel der Variablen nach Bedarf.
1. Ändern Sie den Variablennamen in den Wert des Ordners **folder**.

   >[!NOTE]
   >
   >Der Name der Variablen muss mit dem Namen des Elements übereinstimmen, das mit dem (im Schema definierten) Ordner verknüpft ist, d. h. in diesem Fall mit dem **Ordner** . Sie müssen diesen Namen erneut verwenden, wenn Sie auf die Tabelle verweisen.

1. Wählen Sie für die Variable den Typ **[!UICONTROL XML]**.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Wählen Sie die **[!UICONTROL Refresh page]** Interaktion aus.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Platzieren Sie den Cursor in Ihrer Liste und verweisen Sie auf die **[!UICONTROL Advanced]** Registerkarte, die Sie zuvor auf der **[!UICONTROL Folder filter XPath]** Registerkarte der Liste erstellt haben. Sie müssen den Namen des Elements verwenden, das vom Ordnerlink betroffen ist, d. h. den **Ordner**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >In dieser Phase befindet sich die Webanwendung nicht in ihrem Anwendungskontext. Der Filter kann daher nicht am Ordner getestet werden.

## Schaltfläche hinzufügen, um eine neue Webanwendung zu konfigurieren {#adding-a-button-to-configure-a-new-web-application}

1. Platzieren Sie den Cursor auf das **[!UICONTROL Page]** Element und fügen Sie einen Link hinzu (**[!UICONTROL Static elements > Link]**).
1. Ändern Sie den Link-Titel. Dieser wird auf der Schaltfläche in der Übersicht angezeigt.

   In unserem Beispiel lautet der Titel **Neu**.

1. Insert the following URL in the URL field: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** fällt mit dem Webanwendungsschema zusammen.
   >
   >**nms:newWebApp** fällt mit dem neuen Assistenten zum Erstellen von Webanwendungen zusammen.

1. Definieren Sie, dass die URL im selben Fenster erscheinen soll.
1. Add the Web application icon in the image field: **/nms/img/webApp.png**.

   This icon will appear on the **[!UICONTROL New]** button.

1. Enter **button** in the **[!UICONTROL Style]** field.

   This style is referred to in the **[!UICONTROL Single-page Web application]** template selected previously.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Detail zu einer Liste hinzufügen {#adding-detail-to-a-list}

Wenn Sie in der Übersicht eine Liste konfigurieren, können Sie für jeden Eintrag auf der Liste zusätzliche Details anzeigen lassen.

1. Platzieren Sie den Cursor auf das zuvor erstellte Listenelement.
1. Wählen Sie auf der **[!UICONTROL General]** Registerkarte den **[!UICONTROL Columns and additional detail]** Anzeigemodus in der Dropdownliste aus.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. Fügen Sie auf der **[!UICONTROL Data]** Registerkarte die Spalten **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** und und **[!UICONTROL Description]** hinzu und wählen Sie die **[!UICONTROL Hidden field]** Option für jedes Element aus.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   Diese Informationen werden in der Folge nur in der Detailansicht eines jeden Eintrags sichtbar sein.

1. In the **[!UICONTROL Additional detail]** tab, add the following code:

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>Es dauert fünf Minuten, bis JavaScript-Bibliotheken auf dem Server aktualisiert werden. Sie können den Server auch neu starten, um diese Wartezeit zu verkürzen.

## Liste filtern und aktualisieren {#filtering-and-updating-the-list}

In diesem Abschnitt wird ein Filter zum Anzeigen der Webanwendungen erstellt, die von einem bestimmten Benutzer erzeugt wurden. Dieser Filter wird mit einem Link-Editor erstellt. Wählen Sie zuerst einen Benutzer aus und aktualisieren Sie danach die Liste, um den Filter anzuwenden. Dazu muss auch ein Aktualisieren-Link erstellt werden.

Diese beiden Elemente werden im selben Container abgelegt, damit sie in der Übersicht gemeinsam dargestellt werden.

1. Place your cursor on the **[!UICONTROL Page]** element and select **[!UICONTROL Container > Standard]**.
1. Wählen Sie für die Anzahl der Spalten &quot;**2**&quot;, sodass der Link-Editor und der Link nebeneinander platziert werden.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Weiterführende Informationen zum Layout von Elementen erfahren Sie in [diesem Abschnitt](../../web/using/about-web-forms.md).

1. Wenden Sie **dottedFilter** an.

   This style is referred to in the **[!UICONTROL Single-page Web applicatio]** n template selected previously.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Filter mit einem Link-Editor erstellen {#creating-a-filter-using-a-link-editor}

1. Place your cursor on the container created during the previous stage and insert a link editor via the **[!UICONTROL Advanced controls]** menu.
1. In the storage window which opens automatically, select the **[!UICONTROL Variables]** option, then click the **[!UICONTROL Edit variables]** link and create an XML variable for filtering data.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Passen Sie den Titel an.

   Dieser wird in der Übersicht neben dem Feld **[!UICONTROL Filter]** zu sehen sein.

1. Wählen Sie die Benutzer-Tabelle als Anwendungsschema aus.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Place your cursor on the list element and create a filter via the **[!UICONTROL Data > Filter]** tab:

   * **Ausdruck:** Fremdschlüssel des Links &quot;Erstellt von&quot;
   * **Benutzer:** gleich
   * **Wert:** Variablen (variables)
   * **Berücksichtigt wenn:** &#39;$(var2/@id)&#39;!=&#39;&#39;
   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Der Benutzer der Webanwendung muss sich identifizieren und über die entsprechenden Adobe Campaign-Berechtigungen zum Zugriff auf diese Informationen verfügen.

### Aktualisierungslink erstellen {#creating-a-refresh-link}

1. Place the cursor on the container and insert a **[!UICONTROL Link]** via the **[!UICONTROL Static elements]** menu.
1. Passen Sie den Titel an.
1. Auswählen **[!UICONTROL Refresh data in a list]**.
1. Fügen Sie die zuvor erstellte Liste hinzu.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Add the refresh icon on the **[!UICONTROL Image]** field: **/xtk/img/refresh.png **.
1. Ordnen Sie mithilfe der Sortierpfeile die unterschiedlichen Elemente der Webanwendung wie unten dargestellt neu.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Die Webanwendung ist jetzt konfiguriert. Sie können auf die **[!UICONTROL Preview]** Registerkarte klicken, um eine Vorschau anzuzeigen.

![](assets/s_ncs_configuration_webapp_result.png)

