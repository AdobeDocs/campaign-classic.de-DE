---
solution: Campaign Classic
product: campaign
title: Konfigurieren der Oberfläche
description: Konfigurieren der Oberfläche
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 3%

---


# Konfigurieren der Oberfläche{#configuring-the-interface}

Gehen Sie wie folgt vor, um die Ansicht und den Dialog mit der neuen Empfänger-Tabelle in der Adobe Campaign-Oberfläche auszuführen:

* Erstellen Sie ein neues Formular, um den Inhalt der neuen Tabelle &quot;Empfänger&quot;zu bearbeiten.
* Geben Sie einen neuen Typ in den Ordner des Explorerbaums ein.
* Erstellen Sie eine neue Webanwendung, um über die Adobe Campaign-Startseite auf die benutzerdefinierte Tabelle zuzugreifen.

Adobe Campaign verwendet eine globale Variable &quot;Nms_DefaultRcpSchema&quot;, um mit der standardmäßigen Empfänger-Datenbank (nms:Empfänger) zu kommunizieren. Diese Variable muss daher geändert werden.

1. Navigieren Sie zum Knoten **[!UICONTROL Administration>Plattform>Optionen]** des Explorers.
1. Ändern Sie den Wert der Variablen **Nms_DefaultRcpSchema** mit dem Namen des Schemas, das der Tabelle des externen Empfängers entspricht (in diesem Fall: cus:individuell).
1. Speichern Sie Ihre Änderungen.

## Creating a new form {#creating-a-new-form-}

Wenn Sie ein neues Formular erstellen, können Sie die Daten der Tabelle für den externen Empfänger Ansicht und bearbeiten.

>[!IMPORTANT]
>
>Der Name des Formulars muss mit dem Namen des betreffenden Schemas identisch sein.

1. Navigieren Sie zum Knoten **Administration > Konfiguration > Eingabefelder** des Explorers.
1. Erstellen Sie eine neue **xtk:form** type- **Formulardatei** .
1. Beschreiben Sie alle Überwachungen und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen zu **Formulartypdateien** finden Sie auf [dieser Seite](../../configuration/using/identifying-a-form.md).

   In unserem aktuellen Beispiel muss die **Formulardatei** auf dem Schema **cus:single** basieren und daher das folgende Layout aufweisen:

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

1. Wechseln Sie zum Knoten **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** .
1. Erstellen Sie ein neues **navtree** -Dokument vom Typ **navtree** .
1. Beschreiben Sie alle Überwachungen und Felder, die Sie je nach Tabellenvorlage benötigen.

   >[!NOTE]
   >
   >Weitere Informationen zu **navtree** -Typdateien finden Sie auf [dieser Seite](../../configuration/using/about-navigation-hierarchy.md).

   Im aktuellen Beispiel muss die **navtree** -Datei auf dem **Schema cus:single** basieren und daher das folgende Formular haben:

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

