---
title: Webanwendung übersetzen
seo-title: Webanwendung übersetzen
description: Webanwendung übersetzen
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Webanwendung übersetzen{#translating-a-web-application}

Sie können Webseiten mit Adobe Campaign Digital Content Editor (DCE) übersetzen.

If you select at least one additional language via the **[!UICONTROL Localization]** tab in the **[!UICONTROL Properties]** of a Web application, a new option becomes available when adding an HTML content block in a page edited with DCE.

Mit dieser Option können Sie angeben, ob der Inhaltsbaustein übersetzt werden muss oder nicht.

Zu übersetzende Zeichenfolgen werden auf die gleiche Weise wie die anderen Zeichenfolgen der Webanwendung über die **[!UICONTROL Translations]** Registerkarte der Anwendung erfasst. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/translating-a-web-form.md).

So kennzeichnen Sie die zu übersetzenden Strings:

1. Öffnen Sie in einer Webanwendung eine mit dem DCE bearbeitete Inhaltsseite.

   ![](assets/dce_translation_3.png)

1. Wählen Sie einen HTML-Baustein aus.
1. Im Parameterblock auf der rechten Seite können Sie mit der **[!UICONTROL Localization]** Option den Inhalt des ausgewählten Blocks kennzeichnen. Standardmäßig wird nur der Seitentitel übersetzt.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Strings dürfen maximal 1.023 Zeichen enthalten.

   Es gibt drei konkrete Fälle:

   * Wenn der ausgewählte Baustein mehrere Strings/Bausteine enthält, wird er als ein einzelner zu übersetzender String gekennzeichnet. Der String enthält dann den HTML-Code der Elemente innerhalb dieses Bausteins.
   * Wenn Sie einen Baustein kennzeichnen möchten, der mehrere Strings enthält und mindestens einer dieser Strings bereits gekennzeichnet ist, wird ein Warnhinweis angezeigt. Sie haben dann die Möglichkeit, die Kennzeichnung von dem einzelnen String zu entfernen und dem gesamten Baustein hinzuzufügen.

      ![](assets/dce_translation_4.png)

   * Wenn Sie die Kennzeichnung von einem String entfernen möchten, der in einem bereits gekennzeichneten Baustein enthalten ist, können Sie die Übersetzungsoption für den String nicht direkt ändern. Sie können jedoch auf den Baustein zugreifen, der den String enthält, und die Übersetzungsoption dort ändern.

      ![](assets/dce_translation_2.png)

1. Once you have finished flagging the strings, go back to the Web application and select the **[!UICONTROL Translations]** tab.
1.  Wählen Sie **[!UICONTROL Collect the strings to translate]**. Die in DCE gekennzeichneten Zeichenfolgen werden den Zeichenfolgen der Webanwendung hinzugefügt.

   >[!NOTE]
   >
   >Nach dem Erfassen der Strings werden diese auch dann nicht aus der Liste entfernt, wenn Sie die Übersetzungskennzeichnung im DCE entfernen. Die Strings bleiben im Übersetzungsspeicher.

1. Übersetzen und validieren Sie die Strings.

   You can then preview the translations by selecting the desired language from the **[!UICONTROL Preview]** tab in the Web application.

