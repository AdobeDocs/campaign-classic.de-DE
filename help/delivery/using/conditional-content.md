---
title: Bedingter Inhalt
seo-title: Bedingter Inhalt
description: Bedingter Inhalt
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Bedingter Inhalt{#conditional-content}

Die Konfiguration bedingter Inhalte erlaubt eine dynamische Personalisierung, beispielsweise auf der Basis des Empfängerprofils. Dabei werden Textbausteine und/oder Bilder ersetzt, wenn eine bestimmte Bedingung erfüllt ist.

## Bedingungen in einer E-Mail verwenden {#using-conditions-in-an-email}

Im folgenden Beispiel erfahren Sie, wie Sie eine Nachricht erstellen und entsprechend dem Geschlecht und den Interessen des Empfängers dynamisch personalisieren können.

* Anzeige mit &quot;Mr.&quot; oder &quot;MS&quot; entsprechend dem Wert des **[!UICONTROL Gender]** Felds (M oder F) in der Datenquelle,
* Individuell auf den Empfänger zugeschnittene Zusammenstellung eines Newsletters oder eines Angebots in Abhängigkeit von seinen angegebenen oder erkannten Interessen:

   * Interessen 1 -- > Baustein 1
   * Interessen 2 -- > Baustein 2
   * Interessen 3 -- > Baustein 3
   * Interessen 4 -- > Baustein 4

Gehen Sie wie folgt vor, um einen von einem Feldwert abhängigen bedingten Inhalt zu erstellen:

1. Klicken Sie auf das Personalisierungssymbol und wählen Sie **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Die Personalisierungselemente werden in den Nachrichten-Textkörper eingefügt.

1. Konfigurieren Sie nun den **If**-Ausdruck.

   Gehen Sie dazu wie folgt vor:

   * Select the first element of the expression, **`<field>`**, (by default, this element is highlighted during insertion of the **if** expression) and click the personalization icon to replace it with the test field.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Ersetzen Sie **`<value>`** dies durch den Wert des Felds, für das die Bedingung erfüllt ist. Dieser Wert muss in Anführungszeichen gesetzt werden.
   * Fügen Sie anschließend den Inhalt ein, der bei Erfüllung der Bedingung für den Versand genutzt werden soll. Hierbei kann es sich um einen Text, ein Bild, ein Formular, einen Link usw. handeln.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Click the **[!UICONTROL Preview]** tab to view the content of the message according to the delivery recipient:

   * Auswahl eines Empfängers, für den die Kriterien zutreffen:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Auswahl eines Empfängers für den die Kriterien nicht zutreffen:

      ![](assets/s_ncs_user_conditional_content06.png)

Sie können weitere Fälle hinzufügen und unterschiedliche Inhalte entsprechend den Werten eines oder mehrerer Felder definieren. Verwenden Sie dazu **[!UICONTROL Conditional content > Else]** und **[!UICONTROL Conditional content > Else if]**. Diese Ausdrücke werden auf dieselbe Weise wie der **if** -Ausdruck konfiguriert.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>In der JavaScript-Syntax müssen die Zeichen **%> &lt;%** bei Verwendung von **Sonst** und **Sonst wenn** entfernt werden.

Click **[!UICONTROL Preview]** and select a recipient to view the conditional content.

![](assets/s_ncs_user_conditional_content08.png)

## Mehrsprachige E-Mail erstellen {#creating-multilingual-email}

Im folgenden Beispiel erfahren Sie, wie Sie eine mehrsprachige E-Mail erstellen. Der Inhalt wird je nach Sprache des Empfängers in der einen oder anderen Sprache angezeigt.

1. Erstellen Sie eine E-Mail und wählen Sie eine Zielpopulation aus. In unserem Beispiel basiert die Bedingung für die Darstellung einer bestimmten Version auf dem Wert **Sprache** des Empfängerprofils, also **EN**, **FR** oder **ES**.
1. In the email HTML content, click the **[!UICONTROL Source]** tab and paste the following code:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Test email content in the **[!UICONTROL Preview]** tab by selecting recipients with different preferred languages.

   >[!NOTE]
   >
   >Da Sie für den E-Mail-Inhalt keine andere Version definiert haben, müssen Sie die Zielpopulation vor dem Versand der E-Mail filtern.
