---
product: campaign
title: Benutzeroberfläche konfigurieren
description: Erfahren Sie, wie Sie die Campaign-Benutzeroberfläche konfigurieren
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Benutzeroberfläche konfigurieren{#configuring-the-interface}

![](../../assets/common.svg)

Gehen Sie wie folgt vor, um die neue Empfängertabelle in der Benutzeroberfläche von Adobe Campaign anzuzeigen und mit ihr zu kommunizieren:

* Erstellen Sie ein neues Formular, um den Inhalt der neuen Empfängertabelle zu bearbeiten.
* Geben Sie im Ordner des Explorer-Baums einen neuen Typ ein.
* Erstellen Sie eine neue Webanwendung, um über die Adobe Campaign-Startseite auf die benutzerdefinierte Tabelle zuzugreifen.

Adobe Campaign verwendet eine globale Variable &quot;Nms_DefaultRcpSchema&quot;, um ein Dialogfeld mit der standardmäßigen Empfängerdatenbank (nms:recipient) zu erstellen. Diese Variable muss daher geändert werden.

1. Navigieren Sie zu **[!UICONTROL Administration > Plattform > Optionen]** -Knoten des Explorer.
1. Ändern Sie den Wert der **Nms_DefaultRcpSchema** mit dem Namen des Schemas, das mit der externen Empfängertabelle übereinstimmt (in diesem Fall: cus:einzeln).
1. Speichern Sie Ihre Änderungen.

## Neues Formular erstellen {#creating-a-new-form-}

Die Erstellung eines neuen Formulars ermöglicht die Anzeige und Bearbeitung der Daten der externen Empfängertabelle.

>[!IMPORTANT]
>
>Der Name des Formulars muss mit dem Namen des Schemas übereinstimmen, auf das es sich bezieht.

1. Navigieren Sie zu **Administration > Konfiguration > Formulare** -Knoten des Explorer.
1. Erstellen Sie eine neue **xtk:form** type **Formular** -Datei.
1. Beschreiben Sie alle Überwachungs- und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter **Formular** Dateitypen, siehe [diese Seite](../../configuration/using/identifying-a-form.md).

   In unserem aktuellen Beispiel wird die **Formular** -Datei muss auf der **cus:einzeln** Schema und haben daher das folgende Layout:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Speichern Sie die Erstellung.

## Erstellen eines neuen Ordnertyps in der Navigationshierarchie {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Navigieren Sie zu **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** Knoten.
1. Erstellen Sie eine neue **xtk:navtree** type **navtree** Dokument.
1. Beschreiben Sie alle Überwachungs- und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen unter **navtree** Dateitypen, siehe [diese Seite](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   Im aktuellen Beispiel wird die **navtree** -Datei muss auf der **cus:einzeln** Schema und haben daher die folgende Form:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Speichern Sie die Erstellung.
