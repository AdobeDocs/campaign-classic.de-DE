---
product: campaign
title: Konfigurieren der Benutzeroberfläche
description: Konfigurieren der Benutzeroberfläche
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 3%

---

# Konfigurieren der Benutzeroberfläche{#configuring-the-interface}

![](../../assets/v7-only.svg)

Gehen Sie wie folgt vor, um die neue Empfängertabelle in der Benutzeroberfläche von Adobe Campaign anzuzeigen und mit ihr zu kommunizieren:

* Erstellen Sie ein neues Formular, um den Inhalt der neuen Empfängertabelle zu bearbeiten.
* Geben Sie im Ordner des Explorer-Baums einen neuen Typ ein.
* Erstellen Sie eine neue Webanwendung, um über die Adobe Campaign-Startseite auf die benutzerdefinierte Tabelle zuzugreifen.

Adobe Campaign verwendet eine globale Variable &quot;Nms_DefaultRcpSchema&quot;, um ein Dialogfeld mit der standardmäßigen Empfängerdatenbank (nms:recipient) zu erstellen. Diese Variable muss daher geändert werden.

1. Wechseln Sie zum Knoten **[!UICONTROL Administration>Plattform>Optionen]** des Explorer.
1. Ändern Sie den Wert der Variablen **Nms_DefaultRcpSchema** durch den Namen des Schemas, das mit der externen Empfängertabelle übereinstimmt (in diesem Fall: cus:einzeln).
1. Speichern Sie Ihre Änderungen.

## Neues Formular erstellen {#creating-a-new-form-}

Die Erstellung eines neuen Formulars ermöglicht die Anzeige und Bearbeitung der Daten der externen Empfängertabelle.

>[!IMPORTANT]
>
>Der Name des Formulars muss mit dem Namen des Schemas übereinstimmen, auf das es sich bezieht.

1. Wechseln Sie zum Knoten **Administration > Konfiguration > Formulare** des Explorer.
1. Erstellen Sie eine neue **xtk:form** Typ **Formular**-Datei.
1. Beschreiben Sie alle Überwachungs- und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen zu **Formular**-Dateien finden Sie auf [dieser Seite](../../configuration/using/identifying-a-form.md).

   In unserem aktuellen Beispiel muss die Datei **form** auf dem Schema **cus:einzeln** basieren und daher das folgende Layout aufweisen:

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

1. Wechseln Sie zum Knoten **[!UICONTROL Administration>Konfiguration>Navigationshierarchien]** .
1. Erstellen Sie ein neues Dokument **xtk:navtree** vom Typ **navtree** .
1. Beschreiben Sie alle Überwachungs- und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen zu **navtree**-Dateien finden Sie auf [dieser Seite](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   Im aktuellen Beispiel muss die Datei **navtree** auf dem Schema **cus:einzeln** basieren und daher das folgende Format aufweisen:

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
