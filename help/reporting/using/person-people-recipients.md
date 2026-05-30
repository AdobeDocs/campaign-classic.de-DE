---
product: campaign
title: Personen und Empfänger
description: Personen und Empfänger
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Reporting, Monitoring
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
TQID: https://experienceleague.adobe.com/ZvTALeh3LgGQxNwaQv-usFMAfVvyQFe-rmf6WQDHqTE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 800
ht-degree: 56%

---

# Personen und Empfänger {#person-people-and-recipients}



Dieses Beispiel hilft Ihnen, den Unterschied zwischen einer Person/einer Person und einer Empfängerin bzw. einem Empfänger in Adobe Campaign zu verstehen. Wir senden eine Lieferung an mehrere Personen, um den Unterschied zwischen Personen und Empfängern hervorzuheben, während wir die Berechnungsmethode für die folgenden Indikatoren detailliert beschreiben:

* **[!UICONTROL Klicks]**
* **[!UICONTROL Unique Clicks der erreichten Population]**
* **[!UICONTROL Unique Opens der erreichten Population]**
* **[!UICONTROL Schätzung der Weiterleitungen]**
* **[!UICONTROL Brutto-Reaktionsrate]**

>[!NOTE]
>
>Diese Indikatoren werden im Bericht **[!UICONTROL Trackingindikatoren]** verwendet. Weitere Informationen hierzu finden Sie unter [Trackingindikatoren](../../reporting/using/delivery-reports.md#tracking-indicators).

Einem Versand werden drei Links hinzugefügt. Es wird an 4 Empfänger gesendet:

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** öffnet die E-Mail nicht und klickt demzufolge auf keinen der Links.
* **[!UICONTROL Marie Stuart]** öffnet die E-Mail, klickt jedoch auf keinen der Links.
* **[!UICONTROL Florian David]** : öffnet die E-Mail und klickt 9 Mal auf die Links. Er leitet die E-Mail auch an jemanden weiter, der sie öffnet und zweimal klickt.
* **[!UICONTROL Henry Macdonald]** : Dieser Empfänger hat seinen Internet-Browser so konfiguriert, dass Cookies abgelehnt werden. Er öffnet die E-Mail und klickt viermal auf die Links.

Folgende Trackinglogs werden ausgegeben:

![](assets/s_ncs_user_indicators_example_2.png)

Für ein besseres Verständnis des Zählmechanismus von Personen und Empfängern werden die den jeweiligen Profilen entsprechenden Logs im Folgenden nacheinander analysiert.

## &#x200B;1. Schritt: John {#step-1--john}

**[!UICONTROL John Davis]** öffnet die E-Mail nicht und klickt demzufolge auf keinen der Links.

![](assets/s_ncs_user_indicators_example_8.png)

Da John weder geöffnet noch geklickt hat, erscheint er nicht in den Trackinglogs.

**Zwischenrechnung:**

|   | Empfänger, die geklickt haben | Personen, die geklickt haben | Empfänger, die geöffnet haben |
|---|---|---|---|
| John | - | - | - |
| Zwischenergebnis | 0 | 0 | 0 |

## &#x200B;2. Schritt: Marie {#step-2--marie}

**[!UICONTROL Marie Stuart]** öffnet die E-Mail, klickt jedoch auf keinen der Links.

![](assets/s_ncs_user_indicators_example_7.png)

Maries Öffnung der E-Mail erscheint in folgendem Log:

![](assets/s_ncs_user_indicators_example_4bis.png)

Die offene Stelle wurde einer Empfängerin bzw. einem Empfänger zugewiesen: Marie. Adobe Campaign fügt daher einen neuen Empfänger zur Zählung hinzu.

**Zwischenrechnung:**

|   | Empfänger, die geklickt haben | Personen, die geklickt haben | Empfänger, die geöffnet haben |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Zwischenergebnis | 0 | 0 | 1 |

## &#x200B;3. Schritt: Florian {#step-3--florian}

**[!UICONTROL Florian David]** öffnet die E-Mail und klickt 9 Mal auf die Links. Er leitet die E-Mail auch an jemanden weiter, der sie öffnet und zweimal klickt.

![](assets/s_ncs_user_indicators_example_9.png)

Florians Handlungen (eine Öffnung, neun Klicks) erscheinen in folgenden Logs:

![](assets/s_ncs_user_indicators_example_3bis.png)

**Empfänger**: Die Öffnungen und Klicks werden demselben Empfänger (Florian) zugewiesen. Da sich dieser Empfänger vom vorherigen unterscheidet (Marie), fügt Adobe Campaign einen neuen Empfänger zur Zählung hinzu.

Personen: Da der Browser dieses Empfängers Cookies akzeptiert, können wir sehen, dass allen Klickprotokollen dieselbe Kennung (UUID) zugewiesen wird: **`fe37a503 [...]`**. Adobe Campaign kennzeichnet diese Klicks korrekt als zu derselben Person gehörend. und zählt eine neue Person.

**Zwischenrechnung:**

|   | Empfänger, die geklickt haben | Personen, die geklickt haben | Empfänger, die geöffnet haben |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Zwischenergebnis | 1 | 1 | 2 |

Folgende Logs entsprechen der Öffnung und den zwei Klicks der Person, an die Florian die E-Mail weitergeleitet hat:

![](assets/s_ncs_user_indicators_example_6bis.png)

**Empfänger**: Die Öffnungen und Klicks werden dem Empfänger zugewiesen, der die E-Mail weitergeleitet hat (Florian). Da dieser Empfänger bereits gezählt wurde, bleibt die Empfängeranzahl gleich.

![](assets/s_ncs_user_indicators_example_12.png)

**Personen**: Bei Klicks können wir sehen, dass allen Protokollen dieselbe Kennung (UUID) zugewiesen ist: **`9ab648f9 [...]`**. Diese Kennung wurde noch nicht gezählt. Es wird daher eine neue Person gezählt.

![](assets/s_ncs_user_indicators_example_13.png)

**Zwischenrechnung:**

|   | Empfänger, die geklickt haben | Personen, die geklickt haben | Empfänger, die geöffnet haben |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Unbekannte Person | - | +1 | - |
| Zwischenergebnis | 1 | 2 | 2 |

## &#x200B;4. Schritt: Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** hat seinen Internet-Browser so konfiguriert, dass Cookies abgelehnt werden. Er öffnet die E-Mail und klickt viermal auf die Links.

![](assets/s_ncs_user_indicators_example_10.png)

Henrys Handlungen (eine Öffnung, vier Klicks) erscheinen in folgenden Logs:

![](assets/s_ncs_user_indicators_example_5bis.png)

**Empfänger**: Die Öffnungen und Klicks werden demselben Empfänger (Henry) zugewiesen. Da dieser Empfänger noch nicht gezählt wurde, fügt Adobe Campaign einen Empfänger zur Anzahl hinzu.

**Personen**: Da Henrys Browser keine Cookies akzeptiert, wird für jeden Klick eine neue Kennung (UUID) generiert. Jeder der vier Klicks wird als von einer anderen Person kommend interpretiert. Da diese Kennungen noch nicht gezählt wurden, werden sie der Anzahl hinzugefügt.

**Zwischenrechnung:**

|   | Empfänger, die geklickt haben | Personen, die geklickt haben | Empfänger, die geöffnet haben |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Unbekannte Person | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Zwischenergebnis | 2 | 6 | 3 |

## Zusammenfassung {#summary}

Auf Versandniveau stellt sich das Ergebnis wie folgt dar:

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Klicks]** (Empfänger, die geklickt haben): 2
* **[!UICONTROL Unique Clicks der erreichten Population]** (Personen, die geklickt haben): 6
* **[!UICONTROL Unique Opens der erreichten Population]** (Empfänger, die geöffnet haben): 3

Die Brutto-Reaktionsrate und die Weiterleitungen werden wie folgt berechnet:

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Schätzung der Weiterleitungen]** = **B - A** (also 6 - 2 = 4)
* **[!UICONTROL Brutto-Reaktionsrate]** = **A / C** (also 2 / 3 = 66,67%)

>[!NOTE]
>
>In oben stehenden Formeln bezeichnet:
>
>* A den Indikator **[!UICONTROL Klicks]** (Empfänger, die geklickt haben).
>* B den Indikator **[!UICONTROL Unique Clicks der erreichten Population]** (Personen, die geklickt haben).
>* C den Indikator **[!UICONTROL Unique Opens der erreichten Population]** (Empfänger, die geöffnet haben).
