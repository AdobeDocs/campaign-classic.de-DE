---
product: campaign
title: LINE-Kanal
description: LINE-Kanal
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%
---

# LINE-Kanal{#line-channel}



Die folgenden Workflows werden standardmäßig mit dem Modul **LINE-Kanal** installiert. Weiterführende Informationen zu dem Modul finden Sie in diesem [Abschnitt](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Interner Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aktualisierung des LINE-V2-Zugriffstokens</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Dieser Workflow aktualisiert das Zugriffstoken auf LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bereinigung der gesperrten LINE-Benutzer</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Dieser Workflow stellt sicher, dass die Daten der LINE V2-Benutzer gelöscht werden, nachdem sie das offizielle LINE-Konto 180 Tage lang gesperrt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Migration von MID zu LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Dieser Workflow erzeugt die Kennung von LINE V2-Benutzern für die Migration von LINE V1 nach LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

