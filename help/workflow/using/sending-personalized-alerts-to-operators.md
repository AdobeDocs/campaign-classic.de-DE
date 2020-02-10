---
title: Benutzern personalisierte Warnungen senden
seo-title: Benutzern personalisierte Warnungen senden
description: Benutzern personalisierte Warnungen senden
seo-description: null
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Benutzern personalisierte Warnungen senden{#sending-personalized-alerts-to-operators}

In diesem Beispiel möchten wir einem Benutzer eine Warnung senden, die den Namen der Profile enthält, die einen Newsletter geöffnet, aber nicht auf den darin enthaltenen Link geklickt haben.

Die Felder für Vor- und Nachnamen der Profile sind mit der **[!UICONTROL Recipients]** Targeting-Dimension verknüpft, während die **[!UICONTROL Alert]** Aktivität mit der **[!UICONTROL Operator]** Targeting-Dimension verknüpft ist. Daher steht zwischen den beiden Targeting-Dimensionen kein Feld zur Verfügung, um eine Abstimmung durchzuführen und die Felder mit dem Vor- und Nachnamen abzurufen und sie in der Warnhinweisaktivität anzuzeigen.

Deshalb muss der folgende Workflow erstellt werden:

1. Use a **[!UICONTROL Query]** activity to target data.
1. Add a **[!UICONTROL JavaScript code]** activity into the workflow to save the population form the query to the instance variable.
1. Verwenden Sie die Aktivität **[!UICONTROL Test]**, um die Populationsgröße festzustellen.
1. Use an **[!UICONTROL Alert]** activity to send an alert to an operator, depending on the **[!UICONTROL Test]** activity result.

![](assets/uc_operator_1.png)

## Die Population in der Instanzvariablen speichern {#saving-the-population-to-the-instance-variable}

Add the code below into the **[!UICONTROL JavaScript code]** activity.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Achten Sie darauf, dass der JavaScript-Code mit Ihren Workflow-Informationen übereinstimmt.

* Das Tag **[!UICONTROL queryDef schema]** sollte mit dem Namen der in der Abfrageaktivität verwendeten Zielgruppendimension übereinstimmen.
* Das Tag **[!UICONTROL node expr]** sollte mit dem Namen der Felder übereinstimmen, die Sie abrufen möchten.

![](assets/uc_operator_3.png)

Um diese Informationen abzurufen, gehen Sie wie folgt vor:

1. Klicken Sie mit der rechten Maustaste auf den ausgehenden Übergang aus der **[!UICONTROL Query]** Aktivität und wählen Sie dann **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Klicken Sie mit der rechten Maustaste auf die Liste und wählen Sie **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Die Zielgruppendimension der Abfrage und die Feldnamen werden in der Liste angezeigt.

   ![](assets/uc_operator_6.png)

## Populationsgröße überprüfen {#testing-the-population-count}

Fügen Sie den unten stehenden Code in die **[!UICONTROL Test]**-Aktivität ein, um zu überprüfen, ob die ausgewählte Population zumindest 1 Profil enthält.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Warnung einrichten {#setting-up-the-alert}

Now that the population has been added into the instance variable with the desired fields, you can add these information into the **[!UICONTROL Alert]** activity.

To do this, add into the **[!UICONTROL Source]** tab the code below:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>The **[!UICONTROL <%= item.target.recipient.@fieldName %>]** command lets you add one of the fields that have been saved to the instance variable through the **[!UICONTROL JavaScript code]** activity.\
>Sie können beliebig viele Felder hinzufügen, vorausgesetzt diese wurden in den JavaScript-Code eingefügt.

![](assets/uc_operator_8.png)

