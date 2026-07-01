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
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 452
ht-degree: 100%

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

Die Erstellung von Adressenvorlagen, die importiert und für jeden Versand angepasst werden können, erfolgt wie die Definition einer neuen Testadresse. Der einzige Unterschied besteht darin, dass Adressen von Testadressenvorlagen in einem Ordner vom Typ „Vorlage“ gespeichert werden müssen.

Gehen Sie wie folgt vor, um einen Vorlagenordner zu konfigurieren:

1. Erstellen Sie einen neuen Ordner vom Typ **[!UICONTROL Testadressen]**, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Eigenschaften...]** aus.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Fügen Sie im Tab **[!UICONTROL Einschränkungen]** folgende Filterbedingung hinzu: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Die in diesem Ordner gespeicherten Adressen können nun als Vorlage verwendet werden. Sie können sie in Sendungen oder Kampagnen importieren und entsprechend anpassen (siehe [Hinzufügen von Testadressen](adding-seed-addresses.md)).
