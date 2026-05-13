---
product: campaign
title: Erstellen von Testadressen
description: Erfahren Sie, wie Sie Testadressen erstellen und verwenden.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Seed Address
role: User, Developer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
TQID: https://experienceleague.adobe.com/ya4m8nG7m3DUj-buOZMnd2Nzfx1J6lmIiOuo1VcHjwU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a658c786-869b-4194-a780-2594d663adda
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 452
ht-degree: 94%

---

# Erstellen von Testadressen{#creating-seed-addresses}

Testadressen werden separat von Standard-Profilen und -Zielgruppen im Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Testadressen]** verwaltet.

Zur besseren Übersicht können Sie Unterordner anlegen. Klicken Sie hierfür mit der rechten Maustaste auf den **[!UICONTROL Testadressen]**-Knoten und wählen Sie die Option **[!UICONTROL Testadressen-Ordner hinzufügen]** aus. Benennen Sie den neuen Ordner und bestätigen Sie die Eingabe mit **[!UICONTROL Enter]**. Nun können Sie neue Testadressen erstellen oder existierende Adressen in diesen Unterordner kopieren. Weitere Informationen hierzu finden Sie im Abschnitt [Definieren von Adressen](#defining-addresses).

Adobe Campaign bietet auch die Möglichkeit, Testadressenvorlagen zu erstellen, die in Sendungen oder Kampagnen importiert und deren spezifischen Bedürfnissen angepasst werden. Weitere Informationen finden Sie unter [Erstellen von Testadressenvorlagen](#creating-seed-address-templates).

## Definieren von Adressen {#defining-addresses}

Gehen Sie zur Erstellung von Testadressen wie folgt vor:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** oberhalb der Testadressenliste.
1. Geben Sie die mit der Adresse verknüpften Daten in die entsprechenden Felder auf der Registerkarte **[!UICONTROL Empfänger]** ein. Die verfügbaren Felder entsprechen den Standardfeldern in den Profilen der Versandempfängerinnen bzw. -empfänger (Tabelle „nms:recipient“): Name, Vorname, E-Mail usw.

   >[!NOTE]
   >
   >Für die Bezeichnung der Adresse werden automatisch die von Ihnen definierten Vor- und Nachnamen verwendet.
   >
   >Bei der Erstellung einer Testadresse müssen nicht alle Felder einer jeden Registerkarte ausgefüllt werden. Fehlende Personalisierungselemente werden bei der Versandanalyse nach dem Zufallsprinzip eingetragen.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Geben Sie auf der Registerkarte **[!UICONTROL Adressfelder]** die Werte an, die während der Analysephase in die Versandlogs (Tabelle **[!UICONTROL nms:broadLog]**) geschrieben werden sollen.

1. Geben Sie im Tab **[!UICONTROL Zusätzliche Daten]** die Personalisierungsdaten an, die in mit Data Management-Workflows erstellten Sendungen verwendet werden und die durch einen spezifischen Wert ersetzt werden sollen.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass in der Aktivität **[!UICONTROL Anreicherung]** zusätzliche Zielgruppendaten mit einem Alias definiert wurden, der mit &quot;@&quot; beginnt. Andernfalls können Sie sie nicht richtig mit Ihren Testadressen in Ihrer Versandaktivität verwenden.

## Testadressenvorlagen erstellen {#creating-seed-address-templates}

Adressenvorlagen werden importiert und können für jeden Versand geändert werden. Der Vorgang ist derselbe wie bei der Definition einer neuen Testadresse. Der einzige Unterschied besteht darin, dass Adressen von Testadressenvorlagen in einem Ordner vom Typ „Vorlage“ gespeichert werden müssen.

Gehen Sie wie folgt vor, um einen Vorlagenordner zu konfigurieren:

1. Erstellen Sie einen neuen Ordner vom Typ **[!UICONTROL Testadressen]**, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Eigenschaften...]** aus.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Fügen Sie im Tab **[!UICONTROL Einschränkungen]** folgende Filterbedingung hinzu: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Die in diesem Ordner gespeicherten Adressen können nun als Vorlage verwendet werden. Sie können sie in Sendungen oder Kampagnen importieren und entsprechend anpassen (siehe [Hinzufügen von Testadressen](adding-seed-addresses.md)).
