---
product: campaign
title: Segmente
description: Segmente
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 58%

---

# Segmente{#cells}



Die **[!UICONTROL Segmente]**-Aktivität bietet eine Ansicht der verschiedenen Teilmengen in Form von Spalten, was den Umgang mit Teilmengen erleichtert, falls diese sehr zahlreich sind. Des Weiteren bietet die Aktivität Vorteile bei Personalisierungen.

![](assets/wf_split_cells.png)

Diese Aktivität kann so konfiguriert werden, dass bestimmte Parameter entsprechend den Benutzeranforderungen eingegeben werden. Standardmäßig werden die Details der einzelnen Teilmengen in einem dedizierten Fenster über die **[!UICONTROL Auswahl]** und **[!UICONTROL Erweitert]** Registerkarten. Im folgenden Beispiel wurde das Formular geändert: a **[!UICONTROL Daten]** wurde hinzugefügt, um die Zuordnung eines Angebots und einer Prioritätsstufe für jede Teilmenge zu ermöglichen.

![](assets/wf_split_cells_with_customization.png)

Öffnen Sie das Workflow-Formular im Knoten **[!UICONTROL Administration > Konfiguration > Formulare]** und fügen Sie folgende Zeilen ein:

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Die Personalisierung von Formularen sollte erfahrenen Benutzern vorbehalten bleiben. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/identifying-a-form.md).
