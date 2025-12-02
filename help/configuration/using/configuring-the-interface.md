---
product: campaign
title: Konfigurieren der Benutzeroberfläche
description: Erfahren Sie, wie Sie die Benutzeroberfläche von Campaign konfigurieren
feature: Application Settings
role: Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 3%

---

# Konfigurieren der Benutzeroberfläche{#configuring-the-interface}

Gehen Sie wie folgt vor, um die neue Empfängertabelle in der Adobe Campaign-Benutzeroberfläche anzuzeigen und mit ihr zu kommunizieren:

* Erstellen Sie ein neues Formular, um den Inhalt der neuen Empfängertabelle zu bearbeiten.
* Geben Sie einen neuen Typ in den Ordner der Explorer-Struktur ein.
* Erstellen Sie eine neue Web-Anwendung, um über die Adobe Campaign-Startseite auf die benutzerdefinierte Tabelle zuzugreifen.

Adobe Campaign verwendet eine globale Variable „Nms_DefaultRcpSchema“ für den Dialog mit der standardmäßigen Empfängerdatenbank (nms:recipient). Diese Variable muss daher geändert werden.

1. Wechseln Sie zum Knoten **[!UICONTROL Administration>Plattform]**> Optionen im Explorer.
1. Ändern Sie den Wert der Variablen **Nms_DefaultRcpSchema** mit dem Namen des Schemas, das der externen Empfängertabelle entspricht (in diesem Fall: cus:individual).
1. Speichern Sie Ihre Änderungen.

## Neues Formular erstellen {#creating-a-new-form-}

Durch das Erstellen eines neuen Formulars können Sie die Daten der externen Empfängertabelle anzeigen und bearbeiten.

>[!IMPORTANT]
>
>Der Name des Formulars muss mit dem Namen des betreffenden Schemas übereinstimmen.

1. Wechseln Sie zum Knoten **Administration > Konfiguration > Eingabeformulare** des Explorers.
1. Erstellen Sie eine neue Datei **xtk:form** Typ **form**.
1. Beschreiben Sie alle Monitoring-Felder und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen zu Dateien vom Typ **Formular** finden Sie auf [dieser Seite](../../configuration/using/identifying-a-form.md).

   In unserem aktuellen Beispiel muss die Datei **form** auf dem Schema **cus:individual** basieren und daher das folgende Layout aufweisen:

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

## Erstellen eines neuen Ordnertyps in der Navigationsstruktur {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Wechseln Sie zum Knoten **[!UICONTROL Administration>Konfiguration>]** Navigationshierarchien“.
1. Erstellen Sie ein neues **xtk:navtree** Typ **navtree** Dokument.
1. Beschreiben Sie alle Monitoring-Felder und Felder, die Sie je nach Tabellenvorlage benötigen.

   Im aktuellen Beispiel muss die Datei **navtree** auf dem Schema **cus:individual** basieren und daher die folgende Form haben:

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
