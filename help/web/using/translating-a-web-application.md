---
product: campaign
title: Übersetzen eines Web-Programms
description: Übersetzen eines Web-Programms
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
TQID: https://experienceleague.adobe.com/AVV-TybR3s6d68N7DS0TSKBN46-etor1Ezhlaah-MJs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 384
ht-degree: 100%

---

# Übersetzen eines Web-Programms{#translating-a-web-application}



Sie können Webanwendungsseiten übersetzen, die mit dem Adobe Campaign Digital Content Editor (DCE) erstellt wurden.

Wählen Sie mindestens eine weitere Sprache im Tab **[!UICONTROL Lokalisierung]** in den **[!UICONTROL Eigenschaften]** einer Webanwendung aus. Dadurch wird eine neue Option verfügbar, wenn Sie einen HTML-Inhaltsbaustein auf einer mit dem DCE bearbeiteten Seite hinzufügen.

Mit dieser Option können Sie angeben, ob der Inhaltsbaustein übersetzt werden muss oder nicht.

Zu übersetzende Strings werden auf dieselbe Weise erfasst wie die anderen Strings der Webanwendung, nämlich über den Tab der Anwendung **[!UICONTROL Übersetzungen]**. Weitere Informationen hierzu finden Sie auf [dieser Seite](translating-a-web-form.md).

So kennzeichnen Sie die zu übersetzenden Strings:

1. Öffnen Sie in einer Webanwendung eine mit dem DCE bearbeitete Inhaltsseite.

   ![](assets/dce_translation_3.png)

1. Wählen Sie einen HTML-Baustein aus.
1. In den Parametern auf der rechten Seite können Sie über die Option **[!UICONTROL Lokalisierung]** den Inhalt des ausgewählten Bausteins kennzeichnen. Standardmäßig wird nur der Seitentitel übersetzt.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Strings dürfen maximal 1.023 Zeichen enthalten.

   Es gibt drei Fälle:

   * Wenn der ausgewählte Baustein mehrere Strings/Bausteine enthält, wird er als ein einzelner zu übersetzender String gekennzeichnet. Der String enthält dann den HTML-Code der Elemente innerhalb dieses Bausteins.
   * Wenn Sie einen Baustein kennzeichnen möchten, der mehrere Strings enthält und mindestens einer dieser Strings bereits gekennzeichnet ist, wird ein Warnhinweis angezeigt. Dann können Sie das Flag aus dem isolierten String entfernen und den gesamten Baustein hinzufügen.

     ![](assets/dce_translation_4.png)

   * Wenn Sie die Kennzeichnung von einem String entfernen möchten, der in einem bereits gekennzeichneten Baustein enthalten ist, können Sie die Übersetzungsoption für den String nicht direkt ändern. Sie können jedoch auf den Baustein zugreifen, der den String enthält, um sie zu ändern.

     ![](assets/dce_translation_2.png)

1. Nachdem Sie die Strings fertig gekennzeichnet haben, kehren Sie zur Webanwendung zurück und wählen Sie den Tab **[!UICONTROL Übersetzungen]** aus.
1. Wählen Sie **[!UICONTROL Zu übersetzende Strings abrufen]** aus. Die im DCE gekennzeichneten Strings werden daraufhin zu den Strings der Web-Anwendung hinzugefügt.

   >[!NOTE]
   >
   >Nach dem Erfassen der Strings werden diese auch dann nicht aus der Liste entfernt, wenn Sie das Übersetzungs-Flag im DCE entfernen. Auf diese Weise können sie in der Translation Memory gespeichert werden.

1. Übersetzen und validieren Sie die Strings.

   Sie können die Übersetzungen in der Vorschau betrachten, indem Sie die gewünschte Sprache in der Webanwendung im Tab **[!UICONTROL Vorschau]** auswählen.
