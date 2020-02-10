---
title: Segmente
seo-title: Segmente
description: Segmente
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Segmente{#cells}

Die **[!UICONTROL Cells]** Aktivität bietet eine Ansicht der verschiedenen Untergruppen in Form von Datenspalten. Es erleichtert die Manipulation von Untergruppen und ist auch darauf ausgelegt, Personalisierungsmöglichkeiten zu fördern.

![](assets/wf_split_cells.png)

Diese Aktivität kann so konfiguriert werden, dass sie je nach Benutzeranforderungen bestimmte Parameter eingibt. Standardmäßig werden die Details der einzelnen Untergruppen in einem eigenen Fenster über die Registerkarten **[!UICONTROL Selection]** und **[!UICONTROL Advanced]** beschrieben. Im folgenden Beispiel wurde das Formular geändert: Es wurde eine **[!UICONTROL Data]** Registerkarte hinzugefügt, um die Verknüpfung eines Angebots und eine Prioritätsstufe für jede Untergruppe zu aktivieren.

![](assets/wf_split_cells_with_customization.png)

For this configuration, the following information was added to the workflow form (in the **[!UICONTROL Administration > Configurations > Input forms]** node of the Adobe Campaign tree):

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

Die Personalisierung von Formularen sollte erfahrenen Benutzern vorbehalten bleiben. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../configuration/using/identifying-a-form.md).
