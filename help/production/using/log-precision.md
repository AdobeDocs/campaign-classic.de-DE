---
product: campaign
title: Protokollgenauigkeit
description: Protokollgenauigkeit
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
TQID: https://experienceleague.adobe.com/-AC3ZgKzganqlheg99fMRyJiYNQkHSnIogq5F-Z9xMQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 346
ht-degree: 78%

---

# Protokollgenauigkeit{#log-precision}



Sie können diesen Vorgang auf alle Adobe Campaign-Module anwenden, um die Protokollgenauigkeit zu erhöhen.

Es umfasst den Neustart der Prozesse mit einer höheren Protokollierungsstufe.

>[!IMPORTANT]
>
>Durch diesen Vorgang werden die in diesem Modul ausgeführten Dienste abgebrochen.

Adobe Campaign kann mit zwei Protokollierungsstufen betrieben werden:

1. Der Modus **Verbose** ist die erste Ebene nach der Standardstufe. Der folgende Befehl aktiviert ihn:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Vergewissern Sie sich, dass der Fehler tatsächlich aufgetreten ist, und starten Sie den Prozess auf die normale Weise neu:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Der **TraceFilter** -Modus, mit dem Sie die größte Anzahl von Protokollen speichern können. Sie wird durch den folgenden Befehl aktiviert:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Wenn Sie **tracefilter:&#42;** verwenden, werden alle Protokolltypen aktiviert: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >Die nützlichsten Protokolltypen sind: **wdbc** (zeigt alle SQL-Abfragen an), **soap** (zeigt alle SOAP-Aufrufe an), **ldap** (zeigt alle LDAP-Abfragen nach der Authentifizierung an), **xtkquery** (zeigt die Liste aller Abfragedef an).\
   >Sie können sie einzeln verwenden (**tracefilter:soap,wdbc** Beispiel). Sie können sie auch alle aktivieren und bestimmte andere ausschließen: **-tracefilter:&#42;,!soap**

   Vergewissern Sie sich, dass der Fehler tatsächlich aufgetreten ist, und starten Sie den Prozess auf die normale Weise neu:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Die Protokolle dieser Befehle werden in der Protokolldatei des Moduls gespeichert.

Hier ist ein Beispiel speziell für das Webmodul. Die anderen Module funktionieren wie oben angegeben.

Vergewissern Sie sich vor dem Senden dieses Befehls, dass kein in Bearbeitung befindlicher Auftrag betroffen ist:

```
nlserver pdump -who
```

Beenden Sie anschließend das Modul im Modus **TraceFilter** und starten Sie es neu:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Ein weiteres Beispiel:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>Im **Tracefile** -Modus können Sie die Protokolle speichern. In den obigen Beispielen werden die Protokolle in den Dateien **var/`<instance-name>`/mta_debug.log** und **var/default/web_debug.log** gespeichert.

>[!IMPORTANT]
>
>Fügen Sie unter Windows nicht die Option LD_PRELOAD hinzu. Der folgende Befehl reicht aus:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Vergewissern Sie sich, dass das Problem erneut auftritt, und starten Sie dann das Modul neu:

```
nlserver restart web -tomcat -noconsole
```

Alle Informationen finden Sie in der Datei **/usr/local/neolane/nl6/var/default/log/web.log**.
