---
title: Umsetzung
seo-title: Umsetzung
description: Umsetzung
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Umsetzung{#implementation}

In diesem Diagramm sind die für dieses Anwendungsbeispiel benötigten Schritte zu sehen.

![](assets/message-center-uc1.png)

Erstellen Sie zunächst Ihren Anhang. Lesen Sie dazu diesen [Artikel](../../delivery/using/attaching-files.md#attach-a-personalized-file). Damit können Sie die Dateien an eine E-Mail anhängen, selbst wenn sie nicht in der Ausführungsinstanz gehostet werden.

Sie können E-Mails über einen SOAP-Nachrichtenauslöser senden. Weitere Informationen zu SOAP-Anfragen finden Sie unter [Ereignisbeschreibung](../../message-center/using/event-description.md). Im SOAP-Aufruf gibt es einen URL-Parameter (attachmentURL).

Klicken Sie bei der Erstellung Ihrer E-Mail auf **[!UICONTROL Anhang]**. Geben Sie im Bildschirm **[!UICONTROL Definition eines Anhangs]** den Parameter für den SOAP-Anhang ein:

```
<%= rtEvent.ctx.attachementUrl %>
```

Bei der Verarbeitung/Auslieferung der Nachricht ruft das System die Datei vom Remote-Speicherort (Drittpartei-Server) ab und hängt sie an die jeweilige Nachricht an.

Da es sich bei diesem Parameter um eine Variable handeln kann, sollte sie die über den SOAP-Aufruf gesendete vollständige Remote-URL-Variable Ihrer Datei akzeptieren.

![](assets/message-center-uc2.png)

